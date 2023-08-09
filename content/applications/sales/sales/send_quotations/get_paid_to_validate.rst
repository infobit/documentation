=================================
Online payment order confirmation
=================================

The Odoo *Sales* application provides customers with the ability to confirm orders, via an online
payment, directly on a sales order. Once the sales order is electronically paid for by the customer,
the salesperson attached to the sales order is instantly notified that the order is confirmed.

Activate online payments
========================

In order to have customers confirm orders with an online payment, the *Online Payment* **must** be
activated.

To activate the *Online Payment* feature, go to :menuselection:`Sales app --> Configuration -->
Settings`, scroll to the :guilabel:`Quotations & Orders` heading, and activate the :guilabel:`Online
Payment` feature by checking the box next to it, and clicking :guilabel:`Save`.

.. image:: get_paid_to_validate/online-payment-setting.png
   :align: center
   :alt: The online payment setting in the Odoo Sales application.

.. note::
   When making a standard quotation, this option is the :guilabel:`Payment` feature option, located
   in the :guilabel:`Online confirmation` field, under the :guilabel:`Other Info` tab.

   .. image:: get_paid_to_validate/online-payment-option-quotation.png
      :align: center
      :alt: The online payment setting on a standard quotation in Odoo Sales.

   When making a quotation template, this option is the :guilabel:`Payment` feature option, located
   in the :guilabel:`Online confirmation` field of the quotation template form.

   .. image:: get_paid_to_validate/online-payment-option-quotation-template.png
      :align: center
      :alt: The online payment setting on quotation template forms in Odoo Sales.

Beneath the :guilabel:`Online Payment` option on the *Sales* :guilabel:`Settings` page, there's a
:guilabel:`Default Quotation Validity` field. In this field, there's the option to add a specific
number of days for quotations to remain valid by default.

Payment providers
=================

After checking the box beside the :guilabel:`Online Payment` feature on the :guilabel:`Settings`
page, a link to the :guilabel:`Payment Providers` appears beneath it.

Clicking that link reveals a separate :guilabel:`Payment Providers` page, in which a large variety
of payment providers can be enabled, customized, and published.

.. image:: get_paid_to_validate/payment-providers-page.png
   :align: center
   :alt: Payment providers page in Odoo Sales.

.. seealso::
   - :doc:`/applications/finance/payment_providers`

Register a payment
==================

After opening quotations in their customer portal, and customers click :guilabel:`Accept & Pay` to
confirm their order with an online payment.

.. image:: get_paid_to_validate/accept-and-pay-button.png
   :align: center
   :alt: The accept and pay button on an online quotation in Odoo Sales.

After clicking :guilabel:`Accept & Pay`, customers are presented with :guilabel:`Validate Order`
pop-up window containing different options for them to make online payments, in the :guilabel:`Pay
with` section.

.. image:: get_paid_to_validate/validate-order-pay-with.png
   :align: center
   :alt: How to register a payment on a validate order pop-up window in Odoo Sales.

.. note::
   Odoo will **only** offer payment options on the :guilabel:`Validate Order` pop-up window that
   have been published and configured on the :guilabel:`Payment Providers` page.

Once the customer selects their desired method of payment, they will click the :guilabel:`Pay`
button on the pop-up window, thus officially confirming the order. Odoo will instantly notify the
salesperson attached to the order when the customer confirms the order with an online payment.

.. seealso::
   - :doc:`/applications/sales/sales/send_quotations/quote_template`
   - :doc:`/applications/sales/sales/send_quotations/get_signature_to_validate`
   - :doc:`/applications/finance/payment_providers`
