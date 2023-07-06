=======
Vietnam
=======

Add Vietnamese QR banking codes to invoices
===========================================

**Vietnamese QR banking** is a payment service platform that allows customers to make instant
domestic payments to individuals and merchants in Vietnamese dong (VND) via online and mobile
banking.

Activate QR codes
-----------------

Go to :menuselection:`Accounting --> Configuration --> Settings`, and under the :guilabel:`Customer
Payments` section, activate the :guilabel:`QR Codes` feature.

QR codes bank account configuration
-----------------------------------

Go to :menuselection:`Contacts --> Configuration --> Bank Accounts` and select the bank account for
which you want to activate **Vietnamese QR banking**. Set the :guilabel:`Bank Identifier Code` on
the bank, then set the :guilabel:`Proxy Type` and fill in the :guilabel:`Proxy Value` field
depending on the type you chose.

.. important::
   - The account holder's country must be set to :guilabel:`Vietnam` on its contact form. The
     :guilabel:`Proxy Value` field only appears if the holder's country is :guilabel:`Vietnam`.
   - You can also include the **invoice number** in the QR code by checking the :guilabel:`Include
     Reference` checkbox.

.. image:: vietnam/vn-paynow-bank-setting.png
   :alt: Vietnamese QR banking bank account configuration

.. seealso::
   :doc:`../accounting/bank`

Bank journal configuration
--------------------------

Go to :menuselection:`Accounting --> Configuration --> Journals`, open the bank journal, then fill
out the :guilabel:`Account Number` and :guilabel:`Bank` fields under the :guilabel:`Journal Entries`
tab.

.. image:: vietnam/vn-bank-account-journal-setting.png
   :alt: Bank Account's journal configuration

Issue invoices with QR codes
----------------------------

When creating a new invoice, open the :guilabel:`Other Info` tab and set the :guilabel:`Payment
QR-code` option to :guilabel:`EMV Merchant-Presented QR-code`.

.. image:: vietnam/vn-qr-code-invoice-setting.png
   :alt: Select EMV Merchant-Presented QR-code option

Ensure that the :guilabel:`Recipient Bank` is the one you configured, as Odoo uses this field to
generate the **Vietnamese QR banking** QR code.
