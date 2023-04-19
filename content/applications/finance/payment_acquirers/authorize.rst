=============
Authorize.Net
=============

`Authorize.Net <https://www.authorize.net>`__ is a United States-based online payment solution
provider, allowing businesses to accept **credit cards**.

.. image:: authorize/authorize-net.png
   :align: center
   :alt: Authorize.Net logo

This Payment Acquirer offers additional options that are not available for other :doc:`Payment
Acquirers <../payment_acquirers>`, such as the ability to process your customer's payment after
delivery.

Authorize.Net account
=====================

If not done yet, choose a plan and `Sign Up for an Authorize.Net account
<https://www.authorize.net/sign-up.html>`__.

Odoo needs your **API Credentials & Keys** to connect with your Authorize.Net account, which
comprise:

- API Login ID
- Transaction Key
- Signature Key

To retrieve them, log into your Authorize.Net account, go to :menuselection:`Account --> Security
Settings --> General Security Settings --> API Credentials & Keys`, and generate your **Transaction
Key** and **Signature Key**.

.. image:: authorize/authorize-api-keys.png
   :align: center
   :alt: Generate your Transaction Key and Signature Key on your Authorize.Net account

.. seealso::

   - `Authorize.Net: Getting Started Guide
     <https://support.authorize.net/s/article/Authorize-Net-Getting-Started-Guide>`__

Payment Acquirer Configuration
==============================

To configure Authorize.Net as Payment Acquirer in Odoo, go to :menuselection:`Accounting -->
Configuration --> Payment Acquirers`, open **Authorize.Net**, and change the **State** to *Enabled*.
Don't forget to click on *Save* once you've set everything up.

.. note::
   Please refer to the :doc:`Payment Acquirers documentation <../payment_acquirers>` to read how to
   configure this payment acquirer.

Credentials
-----------

Copy your credentials from your Authorize.Net account (API Login Id, API Transaction Key, and API
Signature Key), paste them in the related fields under the **Credentials** tab, then click on
**Generate Client Key**.

.. note::
   The **API Client Key** is necessary only if you select *Payment from Odoo* option as
   :ref:`Payment Flow <payment_acquirers/payment_flow>`.

.. important::
   If you are trying Authorize.Net as a test, with a *sandbox account*, change the :guilabel:`State`
   to :guilabel:`Test Mode`. We recommend doing this on a test Odoo database, rather than on your
   main database.

   If you set :guilabel:`Test Mode` on Odoo and use an authorize.net account instead of a
   sandbox.authorize.net account, it results in the following error: *The merchant login ID or
   password is invalid or the account is inactive*.

Payment Flow
------------

The **Payment Flow** lets you decide if to redirect the user to the payment acquirer's portal to
authenticate the payment, or if to stay on the current page and authenticate the payment from Odoo.
This field is under the **Configuration** tab.

If you select *Redirection to the acquirer website*, make sure you add a **Default Receipt URL** and
a **Default Relay Response URL** to your Authorize.net account.

To do so, log into your Authorize.Net account, go to :menuselection:`Account --> Transaction Format
Settings --> Transaction Response Settings --> Response/Receipt URLs`, and set the default links:

- | Default Receipt URL:
  | *https://[yourcompany.odoo.com]*/**payment/authorize/return**
- | Default Relay Response URL:
  | *https://[yourcompany.odoo.com]*/**shop/confirmation**

.. note::
   | Failing to complete this step results in the following error:
   | *The referrer, relay response or receipt link URL is invalid.*

Capture the payment after the delivery
--------------------------------------

The **Capture Amount Manually** field is under the **Configuration** tab. If enabled, the funds are
reserved for 30 days on the customer's card, but not charged yet.

.. image:: authorize/authorize-configuration.png
   :align: center
   :alt: Authorize.Net Configuration tab on Odoo

To capture the payment, go to the related Sales Order and click on *Capture Transaction*. If the
order is canceled, you can click on *Void Transaction* to unlock the funds from the customer's card.

.. image:: authorize/authorize-capture.png
   :align: center
   :alt: Hold the credit card payment until you capture or revoke it on Odoo

.. warning::
   After **30 days**, the transaction is **voided automatically** by Authorize.net.

.. note::
   With other payment acquirers, you can manage the capture in their own interfaces, not from Odoo.

Authorize.Net statement export
==============================

.. _excel-file-template:

.. admonition:: Template

   You can find the Excel import template `here. <https://docs.google.com/spreadsheets/d/1CMVtBWLLVIrUpYA92paw-cL7-WdKLbaa/edit?usp=share_link&ouid=105295722917050444558&rtpof=true&sd=true>`_

To import a statement, log into your Authorize.Net account, and go to :menuselection:`Account -->
Statements --> eCheck.Net Settlement Statement`. Then, define an export range using an **opening**
and **closing** batch settlement. All transactions within the two batch settlements will be exported
to Odoo. Select all transactions within the desired range, and copy/paste them into the
:guilabel:`Report 1 Download` sheet of the :ref:`Excel sheet <excel-file-template>`.

.. image:: authorize/authorize-report1.png
   :align: center
   :alt: Select all transactions for the desired range on Authorize.net, and copy them into
         'report1' of the Excel template.

.. example::
   .. image:: authorize/authorize-settlement-batch.png
      :align: center
      :alt: Settlement batch of the an Authorize.Net statement

   In this case, the first batch (01/01/2021) of the year belongs to the settlement of 12/31/2020,
   so the **opening** settlement is from 12/31/2020.

Once you have pasted the data into the :guilabel:`Report 1 Download` sheet, go to
:menuselection:`Authorize.net --> Transaction Search --> Search for a Transaction`, enter the
previously used range of batch settlement dates, and click :guilabel:`Search`.

When the list has been generated, click :guilabel:`Download to File`. In the pop-up window, select
:guilabel:`Expanded Fields with CAVV Response/Comma Separated`, enable :guilabel:`Include Column
Headings`, and click :guilabel:`Submit`. Open the text file, select :guilabel:`All`, copy the data
and paste it into the :guilabel:`Report 2 Download` sheet of the Excel file.

Transit lines are automatically filled in and updated in the :guilabel:`transit for report 1` and
:guilabel:`transit for report 2` sheets of the Excel file. Make sure all entries are present, and if
not, copy the **formula** from previously filled-in lines of the :guilabel:`transit for report 1` or
:guilabel:`2` and paste it into the empty lines.

.. important::
   To get the correct closing balance, do *not* remove any line from the Excel sheets.

Import into Odoo
----------------

To import the data into Odoo, open the Excel file, copy the data from the :guilabel:`transit for
report 2` sheet and **paste special** only the **values** in the :guilabel:`Odoo Import to CSV`
sheet. Then, look for *blue* cells in the :guilabel:`Odoo Import to CSV` sheet. These are
**chargeback** entries without any **reference** number. As they cannot be imported as such, go to
:menuselection:`Authorize.Net --> Account --> Statements --> eCheck.Net Settlement Statement`, look
for :guilabel:`Charge Transaction/Chargeback`, and click it. Copy the **invoice description**, paste
it into the :guilabel:`Label` cell of the :guilabel:`Odoo Import to CSV` sheet, and add
"**Chargeback /**" before the description. If you have multiple invoices, add a line into the Excel
sheet for each invoice and copy/paste the description into each respective :guilabel:`Label` line.

.. note::
   For combined **chargeback/returns** in the payouts, you need to create a new line in the Excel
   file for each invoice.

.. example::
   .. image:: authorize/authorize-chargeback-desc.png
      :align: center
      :alt: Chargeback description

Next, delete **zero transaction** and **void transaction** line items, and change the **format** of
the :guilabel:`Amount` column in the :guilabel:`Odoo Import to CSV` sheet to **Number**. Go back to
:menuselection:`eCheck.Net Settlement Statement --> Search for a Transaction` and search again for
the previously used batch settlements dates. Verify that the batch settlement dates on
**eCheck.Net** match the related payments' dates found in the :guilabel:`Date` column of the
:guilabel:`Odoo Import to CSV`. If it does not match, replace the date with the one from
**eCheck.Net**. Sort the column by *date*, and make sure the format is `MM/DD/YYYY`. Finally, copy
the data (column headings included) from the :guilabel:`Odoo Import to CSV` sheet, paste into a new
Excel file of your choice, and save it as .CSV format.

Open your Accounting app, go to :menuselection:`Configuration --> Journals`, tick the
:guilabel:`Authorize.Net` box, and click :menuselection:`Favorites --> Import records --> Load
file`. Select the file saved as .CSV, and upload it into Odoo.

.. tip::
   List of eCheck.Net `return codes. <https://support.authorize.net/knowledgebase/Knowledgearticle/?code=000001293>`_

.. seealso::
   - `Authorize.Net: Getting Started Guide
     <https://support.authorize.net/s/article/Authorize-Net-Getting-Started-Guide>`__
   - :doc:`../payment_acquirers`
   - :doc:`../../websites/ecommerce/shopper_experience/payment_acquirer`
