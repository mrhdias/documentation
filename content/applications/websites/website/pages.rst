:show-content:

=====
Pages
=====

Odoo allows you to create pages for your website and customize them to your need, be it in its
content or appearance.

Create a page
=============
There are **two ways** to create a page: from the **frontend** and from the **backend**.

From the **frontend**: open the **Website** app and log into your site if necessary. Then, click on
:guilabel:`+ New` in the top-right corner, and select :guilabel:`Page`. Enter a **page title**,
select whether the page should appear in the **bar menu** by enabling or disabling :guilabel:`Add to
menu`, and click :guilabel:`Create`.

.. example::
   The bar where your page(s) appear.

   .. image:: pages/menu-bar.png
      :alt: Menu bar where website pages appear.

From the **backend**: Open the **Website** app and log into your site if necessary. Then, go onto
the page you wish to modify, click :guilabel:`Site`, and in the **This page** section, select
:guilabel:`Properties`. From here, you have access to **two tabs**:

:guilabel:`Name`:

- :guilabel:`Page Name`: You can rename the page if desired;
- :guilabel:`Page URL`: You can change the **URL** of the page if desired.

:guilabel:`Publish`:

- :guilabel:`Show in Top Menu`: Enable if you want the page to appear in the **bar menu** at the
  top;
- :guilabel:`Use as Homepage`: Enable if you want the page to be the homepage of your website;
- :guilabel:`Indexed`: Enable if you want the page to be **indexed**;
- :guilabel:`Published`: Enable if you want the page to be **published** and accessible to all
  visitors;
- :guilabel:`Publishing Date`: Select a date and time if you want to automatically **publish** your
  page on the set date and time;
- :guilabel:`Visibility`: Select who can access the page: :guilabel:`All`, :guilabel:`Signed In`,
  :guilabel:`Restricted Group`, or :guilabel:`With Password`.

You can also :guilabel:`Duplicate Page` or :guilabel:`Delete Page` from either tab. Alternatively,
you can access *some* of those options by going to :menuselection:`Website --> Site --> Pages`.

.. note::
   (note on URLs)

.. seealso::
   :doc:`pages/seo`

.. _website/customization:

Customization
~~~~~~~~~~~~~

You can customize both new and already existing pages through the website builder. When on a page,
click the :guilabel:`🖉 Edit` button to access the customization options. You can add **images**,
**text**, etc. by drag-and-dropping the **building blocks** found under the :guilabel:`Blocks`
column onto the page. Once placed onto the page, building blocks and other elements can be
customized further.

Customization is **contextual** and specific to each page and block, meaning content-related
customization only applies to the page being edited. To customize a building block or menu, simply
click on it while having the website builder *open*. Note that menus or building block can have
customization options specific to their nature or context, and therefore each element may have
options available only for that element. To access these customization options, click the
:guilabel:`Customize` column.

.. note::
   While the :guilabel:`Blocks` and :guilabel:`Customize` columns are page-specific, the
   :guilabel:`Theme` column is website-wide.

.. toctree::
   :titlesonly:

   pages/seo
