=================================
Product images with Google Images
=================================

Having appropriate product images in Odoo is useful for a number of reasons. However, if a lot of
products need images, it can become incredibly time-consuming.

But, with *Google Custom Search* API configured within the Odoo database, finding product images for
products (based on their barcode) is extremely efficient.

.. _product_images/configuration:

Configuration
=============

In order to utilize *Google Custom Search* within an Odoo database, configuration **must** be
completed on both -- Google and Odoo.

.. note::
   Free Google accounts allow up to 100 free images per day. If a higher amount is needed, a billing
   upgrade is required.

.. _product_images/google-api-dashboard:

Google API dashboard
--------------------

#. Go to the `Google Cloud Platform API & Services <https://console.developers.google.com/>`_ page
   to generate Google Custom Search API credentials. Then, log in with a Google account. Next, agree
   to their :guilabel:`Terms of Service` by checking the box, and clicking :guilabel:`Agree and
   Continue`.

#. Select (or create) an API project to store the credentials. Give it a memorable
   :guilabel:`Project Name`, select a :guilabel:`Location` (if any), then click :guilabel:`Create`.

#. With the :guilabel:`Credentials` selected in the left sidebar. Click :guilabel:`Create
   Credentials`, and selecting :guilabel:`API key` from the drop-down menu.

   .. image:: product_images/credentials-api-key.png
      :align: center
      :alt: API & Services page on Google Cloud Platform.

#. Doing so reveals an :guilabel:`API key created` pop-up window, containing a custom :guilabel:`API
   key`. Copy and save :guilabel:`Your API key` in the pop-up window -- it will be used later. Once
   the key is copied (and saved for later use), click :guilabel:`Close` to remove the pop-up window.

   .. image:: product_images/api-key-pop-up.png
      :align: center
      :alt: The API key created pop-up window that appears.

#. Use the search bar on the page, and search for `Custom Search API`, and select it.

   .. image:: product_images/custom-search-api-search-bar.png
      :align: center
      :alt: Search bar containing "Custom Search API" on Google Cloud Platform.

#. From the :guilabel:`Custom Search API` page, enable the API by clicking :guilabel:`Enable`.

   .. image:: product_images/gcp-custom-search-api-page.png
      :align: center
      :alt: "Custom Search API" page with Enable button highlighted on Google Cloud Platform.

.. _product_images/google-pse-dashboard:

Google Programmable Search dashboard
------------------------------------

#. Next, go to `Google Programmable Search Engine <https://programmablesearchengine.google.com/>`_,
   and click either of the :guilabel:`Get started` buttons. Log in with a Google account, if not
   already.

   .. image:: product_images/google-pse-get-started.png
      :align: center
      :alt: Google Programmable Search Engine page with the Get Started buttons.

#. Fill out the :guilabel:`Create a new search engine` form that appears, with the name of the
   search engine, what the engine should search, and be sure to enable :guilabel:`Image Search` and
   :guilabel:`SafeSearch`.

   .. image:: product_images/create-new-search.png
      :align: center
      :alt: Create new search engine form that appears with search engine configurations.

#. Validate the form by clicking :guilabel:`Create`.

#. Doing so reveals a new page with the heading: :guilabel:`Your new search engine has been
   created`.

   .. image:: product_images/new-search-engine-has-been-created.png
      :align: center
      :alt: The Your New Search Engine Has Been Created page that appears with copy code.

#. From this page, click :guilabel:`Customize`, and on the :menuselection:`Overview --> Basic` page,
   copy the ID in the :guilabel:`Search engine ID` field because it's needed for the Odoo
   configuration.

   .. image:: product_images/basic-overview-search-engine-id.png
      :align: center
      :alt: Basic overview page with search engine ID field.

.. _product_images/setup-in-odoo:

Odoo
----

#. In the Odoo database, go to :menuselection:`Settings app` and scroll to the
   :guilabel:`Integrations` section. From here, check the box beside :guilabel:`Google Images`.
   Then, click :guilabel:`Save`.

   .. image:: product_images/google-images-setting.png
      :align: center
      :alt: The Google Images setting in the Odoo Settings app page.

#. Next, re-enter the :menuselection:`Settings app`, and scroll to the :guilabel:`Integrations`
   section. Then, enter the :guilabel:`API Key` and :guilabel:`Search Engine ID` in the fields
   beneath the :guilabel:`Google Images` feature.

#. Click :guilabel:`Save`.

.. _product_images/get-product-images:

Product images in Odoo with Google Custom Search API
====================================================

Adding images to products in Odoo can be done on any products or product variants. This process can
be completed in any Odoo application that provides access to those pages (e.g. *Sales* app,
*Inventory* app, etc.).

Below is a step-by-step guide detailing how to utilize *Google Custom Search API* for automatic
product images in Odoo using the Odoo *Sales* application:

#. Navigate to the :guilabel:`Products` page in the *Sales* app (:menuselection:`Sales app -->
   Products --> Products`. Or, navigate to the :guilabel:`Product Variants` page in the *Sales* app
   (:menuselection:`Sales app --> Products --> Product Variants`).

#. Select the desired products that needs an image.

   .. note::
      Only the products, or product variants, with a barcode and do **not** an image are processed.

      If a product selected with one or more variants, each variant matching the previous criteria
      is processed.

#. In the :guilabel:`Action ⚙️ gear` icon menu of the product page, select :guilabel:`Get Pictures
   from Google Images`.

      .. image:: product_images/get-pictures-from-google-action.png
         :align: center
         :alt: The Get Pictures from Google Images option from the Action drop-down menu in Odoo.

#. On the pop-up window that appears, click :guilabel:`Get picture`.

      .. image:: product_images/click-get-picture-from-pop-up.png
         :align: center
         :alt: The pop-up that appears in which the user should click Get Picture in Odoo Sales.

#. Once clicked, an image(s) will appear incrementally.

   .. note::
      Only the 10 first images are fetched immediatly. If you selected more than 10, the rest are
      fetched as a background job.

      The background job process about 100 images in a minute. If the quota authorized by Google
      (either with a free or a paid plan) is reached, the background job puts itself on hold for 24
      hours. Then, it will continue where it stopped the day before.

.. seealso::
   - `Create, modify, or close your Google Cloud Billing account
     <https://cloud.google.com/billing/docs/how-to/manage-billing-account>`_
