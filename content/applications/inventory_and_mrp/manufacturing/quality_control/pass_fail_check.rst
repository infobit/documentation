=========================
Pass - Fail quality check
=========================

.. |QCP| replace:: :abbr:`QCP (Quality Control Point)`
.. |QCPs| replace:: :abbr:`QCP (Quality Control Points)`

In Odoo *Quality*, a *Pass - Fail* check is one of the quality check types that can be selected when
creating a new quality check or :ref:`Quality Control Point
<manufacturing/quality_control/quality-control-points>` (QCP). Pass - Fail checks consist of a text
field that allows the creator to specify a certain criteria that a product must meet to pass the
check.

This documentation will only detail the configuration options and processing steps that are unique
to Pass - Fail quality checks and |QCPs|. For a full overview of all the configuration options
available when creating a single check or a |QCP|, see the documentation on :ref:`Quality checks
<manufacturing/quality_control/quality-checks>` and :ref:`Quality Control Points
<manufacturing/quality_control/quality-control-points>`.

Create a Pass - Fail quality check
==================================

There are two distinct ways that Pass - Fail quality checks can be created. A single check can be
manually created. Alternatively, a |QCP| can be configured that will automatically create checks at
a predetermined interval.

Quality check
-------------

To create a single Pass - Fail quality check, navigate to :menuselection:`Quality --> Quality
Control --> Quality Checks`, and click :guilabel:`New`. Fill out the new quality check form as
follows:

- In the :guilabel:`Type` drop-down field, select the :guilabel:`Pass - Fail` quality check type.
- In the :guilabel:`Team` drop-down field, select the quality team responsible for managing the
  check.
- In the :guilabel:`Instructions` text field of the :guilabel:`Notes` tab, enter instructions for
  how to complete the quality check and the criteria that must be met for the check to pass.

If the check is being processed immediately, click the :guilabel:`Pass` button at the top of the
screen if the specified criteria is met. If the criteria has not been met, click the
:guilabel:`Fail` button.

.. image:: pass_fail_check/quality-check-form.png
   :align: center
   :alt: A quality check form configured for a Pass - Fail quality check.

Quality Control Point (QCP)
---------------------------

To create a |QCP| that will generate Pass - Fail quality checks automatically, begin by navigating
to :menuselection:`Quality --> Quality Control --> Control Points`, and click :guilabel:`New`. Fill
out the new QCP form as follows:

- In the :guilabel:`Type` drop-down field, select the :guilabel:`Pass - Fail` quality check type.
- In the :guilabel:`Team` drop-down field, select the quality team responsible for managing the
  checks created by the |QCP|.
- In the :guilabel:`Instructions` text field, enter instructions for how to complete the quality
  check and the criteria that must be met for the check to pass.

.. image:: pass_fail_check/qcp-form.png
   :align: center
   :alt: A Quality Control Point (QCP) form configured to create a Pass - Fail quality check.

Process a Pass - Fail quality check
===================================

To process a Pass - Fail quality check, select a manufacturing order or inventory order (receipt,
delivery, return, etc.), for which a check is required. Manufacturing orders can be selected by
navigating to :menuselection:`Manufacturing --> Operations --> Manufacturing Orders`, and clicking
on an order. Inventory orders can be selected by navigating to :menuselection:`Inventory`, clicking
the :guilabel:`# To Process` button on an operation card, and selecting an order.

On the selected inventory or manufacturing order, a purple :guilabel:`Quality Checks` button appears
at the top of the order. Click the button to open the :guilabel:`Quality Check` pop-up window, which
shows all of the quality checks required for that order.

To process a Pass - Fail quality check, follow the instructions shown on the :guilabel:`Quality
Check` pop-up window. If the criteria for the check is met, click the :guilabel:`Pass` button at the
bottom of the window. If the criteria is not met, click the :guilabel:`Fail` button.

.. image:: pass_fail_check/pass-fail-check-pop-up.png
   :align: center
   :alt: A Pass - Fail quality check pop-up window on a manufacturing or inventory order.

If a quality alert must be created, click the :guilabel:`Quality Alert` button that appears at the
top of the manufacturing or inventory order after the check fails. Clicking :guilabel:`Quality
Alert` opens a quality alert form on a new page. For a complete guide on how to fill out quality
alert forms, view the documentation on :ref:`Quality alerts
<manufacturing/quality_control/quality-alerts>`.

Process a work order Pass - Fail quality check
==============================================

When configuring a |QCP| that is triggered during manufacturing, a specific work order can also be
specified in the :guilabel:`Work Order Operation` field on the |QCP| form. If a work order is
specified, a Pass - Fail quality check is created for that specific work order, rather than the
manufacturing order as a whole.

Pass - Fail quality checks configured for work orders must be completed from the tablet view. To do
so, begin by navigating to :menuselection:`Manufacturing --> Operations --> Manufacturing Orders`.
Select a manufacturing order that includes a work order for which a quality check is required. Open
the tablet view for that work order by selecting the :guilabel:`Work Orders` tab, and then clicking
the :guilabel:`📱 (tablet)` button on the order's line.

With tablet view open, complete the steps listed on the left side of the screen until the Pass -
Fail quality check step is reached. Upon reaching the check, follow the instructions that appear at
the top of the screen. If the criteria for the check is met, click the :guilabel:`Pass` button at
the top of the screen. If the criteria is not met, click the :guilabel:`Fail` button.

.. image:: pass_fail_check/work-order-pass-fail-check.png
   :align: center
   :alt: A Pass - Fail check for a manufacturing work order.

If a quality alert must be created, do so by clicking the :guilabel:`☰ (menu)` button in the tablet
view, and selecting :guilabel:`Quality Alert` from the :guilabel:`Menu` pop-up window. A
:guilabel:`Quality Alerts` pop-up window appears, from which a quality alert can be created. For a
complete guide to quality alert creation, view the documentation on :ref:`Quality alerts
<manufacturing/quality_control/quality-alerts>`.
