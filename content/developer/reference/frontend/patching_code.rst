=============
Patching code
=============

Sometimes, we need to customize the way the UI works.  Many common needs are
covered by some supported API. For example, all registries are good extension
points: the field registry allows adding/removing specialized field components,
or the main component registry allows adding components that should be displayed
all the time.

However, there are situations for which it is not sufficient. In those cases, we
may need to modify an object or a class in place. To achieve that, Odoo
provides the utility function `patch`. It is mostly useful to override/update
the behavior of some other component/piece of code that one does not control.

Description
===========

The patch function is located in `@web/core/utils/patch`:

.. js:function:: patch(reference, extension)

    :param object reference: an object that should be patched
    :param object extension: an object mapping each key to an extension
    :returns: a function to remove the patch

    The `patch` function modifies in place the `reference` object (or class) and
    applies all key/value described in the `extension` object.  An unpatch
    function is returned, so it can be used to remove the patch later if necessary.

    Most patch operations provide access to the parent value by using the
    native `super` keyword (see below in the examples).

Patching a simple object
========================

Here is a simple example of how an object can be patched:

.. code-block:: javascript

  import { patch } from "@web/core/utils/patch";

  const object = {
    field: "a field",
    fn() {
      // do something
    },
  };

  patch(object, {
    fn() {
      // do things
    },
  });


When patching functions, we usually want to be able to access the ``parent``
function.  To do so, we can use the native ``super`` keyword:

.. code-block:: javascript

  patch(object, {
    fn() {
      super.fn(...arguments);
      // do other things
    },
  });

.. warning::

    ``super`` can only be used in a method not a function. This means that syntaxes
    ``{ a: function () { super.a(); } }`` and ``{ a: () => { super.a(); } }``
    are invalid.

Getters and setters are supported too:

.. code-block:: javascript

    patch(object, {
      get number() {
        return super.number / 2;
      },
      set number(value) {
        super.number = value;
      },
    });

Patching a javascript class
===========================

The ``patch`` function is designed to work with anything: object or ES6 class.

However, since javascript classes work with the prototypal inheritance, when
one wishes to patch a standard method from a class, then we actually need to patch
the `prototype`:

.. code-block:: javascript

  class MyClass {
    static myStaticFn() {...}
    myPrototypeFn() {...}
  }

  // this will patch static properties!!!
  patch(MyClass, {
    myStaticFn() {...},
  });

  // this is probably the usual case: patching a class method
  patch(MyClass.prototype, {
    myPrototypeFn() {...},
  });


Also, Javascript handles the constructor in a special native way which makes it
impossible to be patched. The only workaround is to call a method in the original
constructor and patch that method instead:

.. code-block:: javascript

  class MyClass {
    constructor() {
      this.setup();
    }
    setup() {
      this.number = 1;
    }
  }

  patch(MyClass.prototype, {
    setup() {
      super.setup(...arguments);
      this.doubleNumber = this.number * 2;
    },
  });

.. warning::

    It is impossible to patch directly the `constructor` of a class!

Patching a component
====================

Components are defined by javascript classes, so all the information above still
holds.  For these reasons, Owl components should use the `setup` method, so they
can easily be patched as well (see the section on :ref:`best practices<frontend/owl/best_practices>`).

.. code-block:: javascript

  patch(MyComponent.prototype, {
    setup() {
      useMyHook();
    },
  });

Removing a patch
================

The `patch` function returns its counterpart. This is mostly useful for
testing purposes, when we patch something at the beginning of a test, and
unpatch it at the end.

.. code-block:: javascript

    const unpatch = patch(object, { ... });
    // test stuff here
    unpatch();
