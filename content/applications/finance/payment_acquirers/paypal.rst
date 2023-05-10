======
PayPal
======

`Paypal <https://www.paypal.com/>`_ is an American online payments acquirer available worldwide. As
it does not charge any subscription fee and creating an account is easy, it is recommended for Odoo
starters.

Settings in PayPal
==================

.. _paypal/auto-return:

Auto Return
-----------

The **Auto Return** feature automatically redirects customers to Odoo once the payment is processed.

From :guilabel:`Website payments`, go to :menuselection:`Website preferences --> Update --> Auto
return for website payments --> Auto return` and select :guilabel:`On`. Enter the address of your
Odoo database (e.g., `https://yourcompany.odoo.com`) in the :guilabel:`Return URL` field, and
:guilabel:`Save`.

.. note::
   - Any URL will do the job. Odoo only needs the setting to be enabled since it uses another URL.
   - Turning :guilabel:`Auto Return` *off* disables the :ref:`Payment Data Transfer
     <paypal/pdt>` feature.

.. _paypal/pdt:

Payment Data Transfer (PDT)
---------------------------

:guilabel:`Payment Data Transfer` allows to receive payment confirmations, displays the payment
status to the customers, and verifies the authenticity of the payments. :abbr:`PDT (Payment Data
Transfer)`. From :menuselection:`Website preferences --> Update`, scroll down to :guilabel:`Payment
data transfer` and select :guilabel:`On` (if desired). **PDT** is *not* mandatory, and :ref:`IPN
(Instant Payment Notifications) <paypal/ipn>` can be used instead.

.. note::
   To use **PDT**, :ref:`Auto Return <paypal/auto-return>` must also be enabled.
.. tip::
   PayPal **recommends** using **IPN**. For more information on **PDT** and **IPN**, click `here. <https://developer.paypal.com/api/nvp-soap/ipn/IPNPDTAnAlternativetoIPN/>`_

PDT Identity Token
******************

PayPal displays your **PDT Identity Token** as soon as :ref:`Auto return <paypal/auto-return>` and
:ref:`Payment Data Transfer (PDT) <paypal/pdt>` are enabled. If you need the **PDT Identity Token**,
disable and re-enable :guilabel:`Payment data transfer` to display the token again.

.. _paypal/ipn:

Instant Payment Notification (IPN)
----------------------------------

:abbr:`IPN (Instant Payment Notifications)` is similar to **PDT**, but allows for more
notifications, such as chargeback notifications. To enable **IPN**, go to :menuselection:`Website
payments --> Instant payment notifications --> Update` and click :guilabel:`Choose IPN settings`.
Enter a :guilabel:`Notification URL`, select :guilabel:`Receive IPN messages (Enabled)`, and
:guilabel:`Save`. **IPN** is an alternative to :ref:`DPT <paypal/pdt>`, and is *not* mandatory.

.. tip::
   It is possible to enable both **PDT** and **IPN** simultaneously. More info `here. <https://developer.paypal.com/api/nvp-soap/ipn/IPNPDTAnAlternativetoIPN/>`_

Paypal Account Optional
-----------------------

We advise you not to prompt customers to log in with a PayPal account upon payment. It is better and
more accessible for customers to pay with a debit/credit card. To disable that prompt, go to
:menuselection:`Account Settings --> Website payments --> Update` and select :guilabel:`On` for
:guilabel:`PayPal account optional`.

Payment Messages Format
-----------------------

In case you use accented characters (or anything else than primary Latin characters) for customer
names or addresses, then you **must** configure the encoding format of the payment request sent by
Odoo to PayPal. Otherwise, some transactions fail without notice.

To do so, go to `your production account <https://www.paypal.com/cgi-bin/customerprofileweb
?cmd=_profile-language-encoding>`_. Then, click :guilabel:`More Options` and set the two default
encoding formats as :guilabel:`UTF-8`.

.. tip::
   - For Encrypted Website Payments & EWP_SETTINGS error, please check the `Paypal documentation
     <https://developer.paypal.com/docs/classic/paypal-payments-standard/integration-guide/
     encryptedwebpayments#encrypted-website-payments-ewp>`_.
   - Configure your :ref:`Paypal Sandbox account <paypal/testing>`, then follow this
     `link <https://sandbox.paypal.com/cgi-bin/customerprofileweb?cmd=_profile-language-encoding>`_
     to configure the encoding format in a test environment.

Settings in Odoo
================

.. seealso::
   - :ref:`payment_acquirers/add_new`

Credentials tab
---------------

Odoo needs your **API Credentials** to connect with your PayPal account. To do so, go to
:menuselection:`Accounting --> Configuration --> Payment Acquirers` and :guilabel:`Activate` PayPal.
Then, enter your PayPal account credentials in the :guilabel:`Credentials` tab:

- :guilabel:`Email`: the login email address in Paypal;
- :guilabel:`PDT Identity Token`: the key used to verify the authenticity of transactions;
- :guilabel:`Use IPN`: whether you want to use **Instant Payment Notifications**.

To set the :guilabel:`PDT Identity Token`, switch to :ref:`developer mode <developer-mode>` and
retrieve the token by following the configuration steps at :ref:`paypal/pdt`.

.. note::
   The PayPal **Merchant ID** is not required.
.. important::
   If you are trying PayPal as a test, using a :ref:`PayPal Sandbox account <paypal/testing>`,
   change the :guilabel:`State` to :guilabel:`Test Mode`. We recommend doing this on a test Odoo
   database rather than on your main database.

Fees tab
--------

You can charge **extra fees** to customers choosing to pay with PayPal in order to cover the
transaction fees PayPal charges you. Once redirected to Paypal, your customer sees an extra amount
applied to the order amount.

To activate this, go to the :guilabel:`Fees` tab in Odoo and activate :guilabel:`Add Extra Fees`.

You can refer to `Paypal Fees <https://www.paypal.com/webapps/mpp/paypal-fees>`_ to set up fees.

.. note::
   `Traders in the EU <https://europa.eu/youreurope/citizens/consumers/shopping/pricing-payments/
   index_en.htm>`_ are not allowed to charge extra fees for paying with credit cards.

.. _paypal/testing:

Test environment
================

Configuration
-------------

Thanks to PayPal sandbox accounts, you can test the entire payment flow in Odoo.

Log into the `Paypal Developer Site <https://developer.paypal.com/>`_ using your PayPal credentials,
which creates two sandbox accounts:

-  A business account (to use as merchants, e.g.,
   `pp.merch01-facilitator@example.com <mailto:pp.merch01-facilitator@example.com>`_);
-  A default personal account (to use as shoppers, e.g.,
   `pp.merch01-buyer@example.com <mailto:pp.merch01-buyer@example.com>`_).

Log into PayPal sandbox using the merchant account and follow the same configuration instructions.
Enter your sandbox credentials in Odoo (:menuselection:`Accounting --> Configuration --> Payment
Acquirer --> PayPal` in the :guilabel:`Credentials` tab, and make sure the status is set on
:guilabel:`Test Mode`. We recommend doing this on a test Odoo database rather than your main
database.

Run a test transaction from Odoo using the sandbox personal account.

.. seealso::
   - :doc:`../payment_acquirers`
