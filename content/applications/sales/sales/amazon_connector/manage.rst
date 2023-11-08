=======================
Amazon order management
=======================

Order synchronization
=====================

Orders are automatically fetched from Amazon, and synchronized in Odoo, at regular intervals.

The synchronization is based on the Amazon status: only orders whose status has changed since the
last synchronization are fetched from Amazon.

For *FBA* (Fulfilled by Amazon), only *Shipped* and *Canceled* orders are fetched.

For *FBM* (Fulfilled by Merchant), the same is done for *Unshipped* and *Canceled* orders. For each
synchronization order, a sales order and customer are created in Odoo, if they aren't already
registered.

.. note::
   When an order is canceled in Amazon, and was already synchronized in Odoo, the corresponding
   sales order is automatically canceled in Odoo.

Force synchronization
=====================

In order to force the synchronizationof an order, whose status has **not** changed since the
previous synchronization, start by activating the :ref:`developer mode <developer-mode>`.

Then, navigate to the Amazon account, and modify the date under :menuselection:`Orders Follow-up
--> Last Order Sync`. Be sure to pick a date that occurs prior to the last status change of the
desired order to synchronize and save.

.. tip::
   To immediately synchronizethe orders of an Amazon account, switch to :ref:`developer mode
   <developer-mode>`, head to the Amazon account, and click :guilabel:`Sync Orders`. The same can be
   done with pickings by clicking :guilabel:`Sync Pickings`.

Manage deliveries in FBM
========================

Whenever an *FBM* (Fulfilled by Merchant) order is synchronized in Odoo, a picking is instantly
created, along a sales order and customer. Then, decide to either ship all the ordered products to
the customer at once, or ship products partially using backorders.

When a picking related to the order is confirmed, a notification is then sent to Amazon, who, in
turn, notify the customer that the order (or a part of it) is on its way.

.. important::
   Amazon requires users to provide a tracking reference with each delivery. This is needed to
   assign a carrier.

   If the carrier doesn't automatically provide a tracking reference, one must be set manually. This
   rule applies to all marketplaces.

.. tip::
   - If the chosen carrier isn't supported by Odoo, a carrier with the same name can still be
     created (e.g. create carrier named, `Colissimo`). The name used is *not* case sensitive, but be
     mindful to avoid typos. If there are typos, Amazon will *not* recognize them.
   - Next, create a delivery carrier named, `Self Delivery`, to inform Amazon that the user will
     make the deliveries. Even with this route, a tracking reference still **must** be entered.
   - Remember, the customer is notified by email about the delivery, and the carrier, along with the
     tracking reference are displayed in the email to the customer.

.. seealso::
   - :doc:`../../../inventory_and_mrp/inventory/shipping/setup/third_party_shipper`

Follow deliveries in FBA
========================

When an *FBA* (Fulfilled by Amazon) order is synchronized in Odoo, a stock move is recorded for each
sales order item. That way, it's saved in the system.

Inventory managers can access these stock moves by navigating to :menuselection:`Inventory app -->
Reporting --> Moves History`.

These managers pick up products in a specific inventory location called, *Amazon*. This specific
location represents stock in Amazon's warehouses, and allows users to manage the stock of products
under the *FBA* program.

.. tip::
   To follow *Amazon (FBA)* stock in Odoo, make an inventory adjustment after replenishing it. An
   automated replenishment from reordering rules can also be triggered on the Amazon location.

The Amazon location is configurable by accessing the Amazon account managed in Odoo. All accounts of
the same company use the same location, by default. However, it is possible to follow the stock
filtered by marketplace.

To do that, first remove the marketplace, where the desired stock to follow separately can be found,
from the list of synchronized marketplaces.

Next, create another registration for this account, and remove all marketplaces -- *except* the
marketplace this is desired to be isolated from the others.

Lastly, assign another stock location to the second registration of the account.

Invoices and register payments
==============================

Issue invoices
--------------

Due to Amazon's policy of not sharing customer email addresses, it is *not* possible to send
invoices directly to Amazon customers from Odoo. However, it *is* possible to manually upload the
generated invoices from odoo to the Amazon back-end.

Additionally, for B2B clients, it is currently required to manually retrive VAT numbers from the
Amazon back-end *before* creating an invoice in Odoo.

.. note::
   For :doc:`TaxCloud <../../../finance/accounting/taxes/taxcloud>` users: invoices created from
   Amazon sales orders are **not** synchronized with TaxCloud, since Amazon already includes them in
   its own tax report to TaxCloud.

.. warning::
   TaxCloud integration will be decommissioned in Odoo 17+.

Register payments
-----------------

Since customers pay Amazon as an intermediary, creating a dedicated *Bank* journal (e.g. named
`Amazon Payments`), with a dedicated *Bank and Cash* intermediary account is recommended.

Additionally, as Amazon makes a single monthly payment, selecting all the invoices linked to a
single payment is necessary when registering payments.

To do that, used the appropriate :guilabel:`Journal` dedicated to Amazon payments, and select
:guilabel:`Batch Deposit` as the :guilabel:`Payment Method`.

Then, select all the generated payments, and click :menuselection:`Actions --> Create batch payment
--> Validate`.

.. tip::
   This same action can be performed with vendor bills from Amazon dedicated to commissions.

   When the balance is received in the bank account at the end of the month, and the bank statements
   are recorded, credit the Amazon intermediary account by the amount received.

Follow Amazon sales in sales reporting
======================================

On the Amazon account, a sales team is set under the :guilabel:`Order Follow-up` tab.

This gives quick access to important metrics related to Sales reporting. By default, the account's
sales team is shared between all the company's accounts.

If desired, the sales team on the account can be changed for another, in order to perform a separate
reporting for the sales of this account.

.. tip::
   It is also possible to perform reporting on a per-marketplace basis in a similar fashion.

   First, remove the desired marketplace from the list of synchronized marketplaces.

   Then, create another registration for this account, and remove all other marketplaces, *except*
   the one to isolate.

   Lastly, assign another sales team to one of the two registrations of the account.

.. seealso::
   - :doc:`features`
   - :doc:`setup`
