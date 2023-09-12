===========================
Set up your barcode scanner
===========================

.. _barcode/setup/hardware:

Follow this guide to choose and set up a barcode scanner compatible with Odoo's *Inventory* and
*Barcode* apps.

.. image:: hardware/barcode-scanner.png
   :align: center
   :alt: An image of an example barcode scanner.

Scanner types
=============

To determine which barcode scanner is most compatible with Odoo and the business' needs, refer to
the following section:

- **USB scanners** are connected to a computer and are suitable for businesses that scan products at
  a fixed location, like at the checkout in a grocery store. Ensure the chosen USB scanner is
  compatible with the keyboard layout of the computer.

- **Bluetooth scanners** pair with a smartphone or tablet, making them an ideal cost-effective and
  portable barcode scanner option. In this scenario, Odoo is installed on the smartphone, allowing
  warehouse operators to handle operations and check stock directly through their mobile devices.

- **Mobile computer scanners** are mobile devices with a built-in barcode scanner. Ensure the device
  can run the Odoo mobile app properly, and recent models that use Android OS with the Google Chrome
  browser or Windows OS with Internet Explorer Mobile should work. However, testing is crucial due
  to the variety of available models and configurations.

Configuration
=============

When setting up the barcode scanner, ensure the following configurations are correctly set to ensure
the scanner can interpret barcodes properly in Odoo.

Keyboard layout
---------------

When using a USB barcode scanner, match its keyboard layout with the operating system's layout for
proper interpretation of characters. To configure the keyboard layout, scan the keyboard wedge
barcode in the user manual for corresponding to the barcode scanner.

Automatic carriage return
-------------------------

Odoo has a default 50-millisecond delay between scans to prevent accidental double scanning. To
remove this delay, configure the scanner to add a carriage return at the end of each barcode.
Typically, this is the default setting and can be explicitly set by scanning a specific barcode in
the user manual, like 'CR suffix ON' or 'Apply Enter for suffix.'

Zebra scanner
-------------

When using Zebra scanners, ensure the correct keystroke configurations are set to prevent errors:

Begin on the Zebra scanner's home screen and select the :guilabel:`DataWedge` app (the icon for the
app is a light blue barcode). In the :guilabel:`DataWedge Profiles` page, select the profile option
to access the Zebra scanner's settings.

Scroll down to the :guilabel:`Keyboard Output` option and ensure the option
:guilabel:`Enable/disable keystroke output` is :guilabel:`Enabled`.

.. image:: hardware/enable-keystroke.png
   :align: center
   :alt: Show keystroke option in the Zebra scanner's DataWedge app.

Now, go back to the :guilabel:`Profile` options page and select :guilabel:`Key event options`. Here,
ensure the :guilabel:`Send Characters as Events` option is checked.
