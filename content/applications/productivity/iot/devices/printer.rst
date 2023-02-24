=================
Connect a printer
=================

A printer can be attached to the :abbr:`IoT (Internet of Things)` box on an Odoo database.
Installation is easy and convenient and can be done in a few easy steps. The printer can be used to
print receipts, labels, orders or even reports from the different Odoo apps. In addition printer
actions can be assigned as an action on a trigger during the manufacturing process or added onto a
*Quality Control Point* or *Quality Check*.


Connection
==========

The :abbr:`IoT (Internet of Things)` box supports printers connected through :abbr:`USB (Universal
Serial Bus)`, network connection or Bluetooth. `Supported printers
<https://www.odoo.com/page/iot-hardware>`__ will be detected automatically and will appear in the
:guilabel:`Devices` list of the :menuselection:`IoT` app.

.. image:: printer/printer-detected.png
   :align: center
   :alt: The printer as it would appear in the IoT app devices list.

.. note::
   The printer can take up to two minutes to appear in the :menuselection:`IoT` app devices list.

Link the printer
================

Link printer to work orders
---------------------------

*Work Orders* can be linked to printers via a *Quality Control Point* to print labels for
manufactured products.

In the :menuselection:`Quality` app, a device can be set up on a :guilabel:`Quality Control Point`.
Go to the :menuselection:`Quality Control --> Control Points` and open the :guilabel:`Control Point`
which will be linked with the printer.

.. note::
   A *Manufacturing Operation* and *Work Order Operation* need to be attached to the *Quality
   Control Point* before the :guilabel:`Type` will allow for :guilabel:`Print Label` to be
   selected.

Now, edit the :guilabel:`Control Point` by selecting the :guilabel:`Type` field and clicking on
:guilabel:`Print Label` from the dropdown. A field called :guilabel:`Device` will appear where
the attached *device* can be selected. :guilabel:`Save` the changes if required.

.. image:: printer/printer-controlpoint.png
   :align: center
   :alt: This is the quality control point setup.

The printer can be used with the selected :guilabel:`Quality Control Point`. When the
:guilabel:`Quality Control Point` is reached during the manufacturing process, the database will
prompt the operator to take a picture.

.. image:: printer/printer-prompt.png
   :align: center

.. seealso::
   In a *Quality Check* the :guilabel:`Type` of check can also be specified to :guilabel:`Print
   Label`. Access *Quality Checks* by navigating to :menuselection:`Quality app --> Quality Control
   --> Quality Checks --> New`.

.. seealso::
   - :doc:`../../../inventory_and_mrp/manufacturing/quality_control/quality_control_points`
   - :doc:`../../../inventory_and_mrp/manufacturing/quality_control/quality_alerts`

Link a printer to a work center in the manufacturing app
--------------------------------------------------------

To link the printer to an action, it needs to be configured on a *work center*. Navigate to
:menuselection:`Manufacturing --> Configuration --> Work Centers`. Go to the :guilabel:`Work Center`
the printer will be used in and add the device in the :guilabel:`IoT Triggers` tab under
:guilabel:`Device` by selecting :guilabel:`Add a Line`. Then, it can be linked to either of the
following :guilabel:`Actions`: :guilabel:`Print Labels`, :guilabel:`Print Operation`, or
:guilabel:`Print Delivery Slip`. A key can be added to trigger the action.

It should be noted that the trigger that is first in the list will be chosen first. So, the order
matters and these triggers can be dragged into order.

.. note::
   On the :guilabel:`work order` screen, a status graphic indicates whether the database is
   correctly connected to the printer.

.. seealso::
   :ref:`workcenter_iot`

Link the printer to reports
---------------------------

It's also possible to link a type of report to a certain printer. In the :menuselection:`IoT` app,
go to the :menuselection:`Devices` menu and select the printer that needs to be configured.

Now, go to the :guilabel:`Printer Reports` tab. :guilabel:`Edit` the page and select :guilabel:`Add
a line`. In the window that appears, check all the types of :guilabel:`Reports` that should be
linked to this printer.

.. image:: printer/printers-listed.png
   :align: center
   :alt: The printer devices listed in the IoT Devices menu.

Now, each time :guilabel:`Print` is selected in the control panel, instead of downloading a PDF,
Odoo will send the report to the selected printer and automatically print it.

.. seealso::
   :doc:`POS Order Printing <../../../sales/point_of_sale/restaurant/kitchen_printing>`

.. note::
   Reports can also be configured in the :guilabel:`Technical Menu` while in :ref:`debug mode
   <developer-mode>`. Navigate to :menuselection:`Settings App --> Technical Menu --> Actions -->
   Reports`. The individual report can be found in this list, where the :guilabel:`IOT Device` can
   be set on the report.
