======================
How to list a product?
======================

In order to list a product on eBay there are two methods in Odoo to do so:

#. Make a product in eBay and list the item eBay.

   - Click :guilabel:`List Item on eBay` in the top menu of the product template.
#. List the item (product) on eBay and then link the product in Odoo to the item in eBay (through
   Odoo).

   - Click :guilabel:`Link With Existing eBay Listing` in the top menu on the product template.

.. note::
   If an order comes in and the listing from the order is not linked to a product, eBay will create
   a consumable product.product in its place. These consumables should be altered on the Sales Order
   while in draft state to represent a storable product, and then the user can link to the listing
   as they come in.

Listing without variation
=========================

In order to list a product, check the :guilabel:`Sell on eBay` field on a product form. The eBay tab
will be available.

.. image:: manage/manage-01.png
  :align: center
  :alt: The eBay template form listed in the product template in Odoo.

When the :guilabel:`Use Stock Quantity` field is checked, the quantity set on eBay will be the Odoo
**Forecast Quantity**.

The :guilabel:`Description Template` allows the administrator to use templates in listings. The
default template only use the :guilabel:`eBay Description` field of the product. Html can be used
inside the :guilabel:`Description Template` and in the :guilabel:`eBay Description` in Odoo 14.
Starting in Odoo 15, the powerbox feature is available to use in the template and description.
Simply type a forward slash `/` and a menu will be revealed allowing to add images and other
formatting options.

To use images in the listing, another option is to add them as **Attachments** on the product
template.

Listing with variations
=======================

When the :guilabel:`Sell on eBay` is checked on a product containing variations with
:guilabel:`Fixed Price` as :guilabel:`Listing Type`, the eBay form is slightly different. Go to the
:guilabel:`Variants` tab to or click :guilabel:`Configure Variants` in the top menu to configure the
variant settings. Pricing can be configured for each variation.

Product Identifiers
===================

Products identifiers such as EAN, UPC, Brand or MPN are required in most of the eBay categories.

EAN and UPC identifiers
-----------------------

The module manages the EAN and UPC identifiers with the :guilabel:`Barcode` field of the product
variant. If the :guilabel:`Barcode` field is empty or is value is not valid, the EAN and UPC values
will be set as 'Does not apply' as recommended by eBay.

Listing with item specifics
---------------------------

In order to add item specifics, one should create a product attribute with a single value in the
:guilabel:`Variants` tab on the product form. Examples of item specifics include: `MPN` or `Brand`.
The Brand and MPN values are working as item specifics and should be defined in the
:guilabel:`Variants` tab on the product form. If these values are not set, 'Does not apply' will be
used for the eBay listing.

Process Invoices and Payments
=============================

Posting payment
---------------

When eBay orders are placed they are always paid for up front, via the eBay site. At no point will
users pay for items on eBay through Odoo. Therefore, once orders are synced into Odoo from eBay they
are already paid for, and Odoo's invoice / payment functionality will not need to be utilized.
However, invoices need to be created and marked as Paid to “close” the sale order.

Users can opt to mass create and post invoices in batches. To do so, navigate to Quotations in the
list view by going to :menuselection:`Sales app --> Orders --> Quotations`. In the upper right
corner select the list view icon. Then check the boxes that invoices should be made for and go to
the :guilabel:`Action` menu. Click on :guilabel:`Create Invoices`.

A pop-up will appear and click on :guilabel:`Create and view invoice`. A new screen will populate
with the newly created invoices. Next, select all of them by clicking on the box icon next to
:guilabel:`Number` in the header row of the list, this will select all the records. Then navigate to
the :guilabel:`Action` menu and click :guilabel:`Post entries`. Following this step, a pop-up will
appear and click on :guilabel:`Post journal entries`. This will take the invoices out of *draft* and
set them to *posted*.

Reconciling payments
--------------------

Users typically utilize PayPal to receive payment from eBay, and then send lump sums from PayPal
into their bank account. To reconcile this income, users can reconcile the one PayPal transfer
with all related invoices.

First navigate to the :guilabel:`Accounting Dashboard` by going to the :menuselection:`Accounting
app --> Dashboard --> Bank`. :guilabel:`Create` a new transaction and enter the :guilabel:`Label`
as `eBay Sales`. Fill out the :guilabel:`Amount` and enter a :guilabel:`Statement` date in. Click on
:guilabel:`Create and edit`.

For the :guilabel:`Ending Balance` enter the same account that was entered for the
:guilabel:`Amount` above. Click on :guilabel:`Save`. Next, open the new balance that needs to be
reconciled. Under the tab marked: :guilabel:`Match Existing Entries` select the entries that are
included in this balance.

Finally, click :guilabel:`Validate` after all of the appropriate entires are added in. The
reconciliation is complete, now navigate to the customer invoices by going to
:menuselection:`Customers --> Invoices`. The **Paid** label should appear under the
:guilabel:`Payment Status` column.
