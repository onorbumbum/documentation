=============
Configuration
=============

.. _fiscal_localizations/colombia/installation:

Modules installation
====================

:ref:`Install <general/install>` the following modules to get all the features of the Colombian
localization:

.. list-table::
   :header-rows: 1
   :widths: 25 25 50

   * - Name
     - Technical name
     - Description
   * - :guilabel:`Colombia - Accounting`
     - `l10n_co`
     - Default :ref:`fiscal localization package <fiscal_localizations/packages>`
   * - :guilabel:`Colombia E-invoice Integration`
     - `l10n_co_edi`
     - Carvajal e-invoicing integration

.. _fiscal_localizations/colombia/carvajal:

Configure credentials for Carvajal web service
==============================================

Once the modules are installed, the user credentials need to be configured in order to connect with
Carvajal Web Service. First, navigate to :menuselection:`Accounting --> Configuration --> Settings`
and look for the :guilabel:`Colombian Electronic Invoice` section. Then, fill in the required
configuration information provided by Carvajal.

.. image:: configuration/carvajal-credential-config.png
   :align: center
   :alt: Configure credentials for Carvajal web service in Odoo.

Check the :guilabel:`Test mode` checkbox to connect with the Carvajal testing environment. This
allows users to test the complete workflow and integration with the :abbr:`CEN (Centro Electrónico
de Negocios)` Financiero portal, which is accessible here:

`CTS (Carvajal T&S) <https://cenflab.cen.biz/site/>`_.

`CSC (Carvajal Servicios de Comunicación) <https://web-stage.facturacarvajal.com/>`_.

:abbr:`CSC (Carvajal Servicios de Comunicación)` is the default for new databases.

Once Odoo and Carvajal are fully configured and ready for production, the testing environment can
be disabled by unchecking the :guilabel:`Test mode` checkbox.

.. _fiscal_localizations/colombia/configure_report:

Configure report data
=====================

Report data can be defined for the fiscal section and the bank information in the PDF as part of
the configurable information that is sent in the XML.

Navigate to :menuselection:`Accounting --> Configuration --> Settings` and look for the
:guilabel:`Colombian Electronic Invoice` section.

.. image:: configuration/report-config.png
   :align: center
   :alt: Configure the report data in Odoo.

.. _fiscal_localizations/colombia/configure_xml:

Configure data required in the XML
==================================

Partner
-------

Configure the identification number and fiscal structure.

Identification
~~~~~~~~~~~~~~

As part of the Colombian Localization, the document types defined by the :abbr:`DIAN (Dirección de
Impuestos y Aduanas Nacionales)` are now available on the Partner form. Colombian partners have to
have their identification number (:guilabel:`VAT`) and :guilabel:`Document Type` set:

.. image:: configuration/partner-rut-doc-type.png
   :align: center
   :alt: The document type of RUT set in Odoo.

.. tip::
   When the :guilabel:`Document Type` is `RUT` the identification number needs to be configured in
   Odoo including the verification digit, Odoo will split this number when the data to the third
   party vendor is sent.

Fiscal structure (RUT)
~~~~~~~~~~~~~~~~~~~~~~

The partner's responsibility codes (section 53 in the RUT document) are included as part of the
electronic invoice module given it is part of the information required by the :abbr:`DIAN (Dirección
de Impuestos y Aduanas Nacionales)`.

The required fields can be found in :menuselection:`Partner --> Sales & Purchase Tab --> Fiscal
Information`.

.. image:: configuration/partner-fiscal-information.png
   :align: center
   :alt: The fiscal information included in the electronic invoice module in Odoo.

Additionally, two boolean fields were added in order to specify the fiscal regimen of the partner.

Taxes
-----

If sales transactions include products with taxes, the :guilabel:`Value Type` field in the
:guilabel:`Advanced Options tab` needs to be configured per tax.

Retention tax types (ICA, IVA, Fuente) are also included in the options to configure taxes.
This configuration is used in order to correctly display taxes in the invoice PDF.

.. image:: configuration/retention-tax-types.png
   :align: center
   :alt: The ICA, IVA and Fuente fields in the Advanced Options tab in Odoo.

Users
-----

The default template that is used by Odoo on the invoice PDF includes the job position of the
salesperson, so the :guilabel:`Job Position` field should be configured.

.. seealso::
   - :doc:`workflows`
   - :doc:`reports`
