=====================================
Removal Strategies (FIFO, LIFO, FEFO)
=====================================

Usually, **Removal Strategies** are defined in picking operations to select the best products,
optimize the distance for the worker, for quality control purposes, or to move products with the
soonest expiration date.

When a product needs to be moved, Odoo finds available products that can be assigned to the
transfer. The way Odoo assigns these products depends on the :guilabel:`Removal Strategy` defined in
the :guilabel:`Product Category` or on the :guilabel:`Location`.

What happens inside the warehouse?
==================================

Imagine a generic warehouse plan, with receiving docks and areas, storage locations, picking and
packing areas, and shipping docks. All products go through all these locations, but some rules, such
as removal strategies, can have an effect on which products are taken when.

.. image:: removal/empty-dock.png
   :align: center
   :alt: Empty stock waiting for deliveries at the docks.

Here, vendor trucks unload pallets of goods at the docks. Then, operators scan the products in the
receiving area with the reception date and, if the product has an expiration date, the expiration
date. After that, products are stored in their respective locations.

.. image:: removal/entering-stocks.png
   :align: center
   :alt: Products entering stock via the receiving area.

Next, several orders for the same product are made, but in this example, the goods weren't received
on the same day and they don't have the same expiration date. In that situation, logically, sending
those with the closest expiration date is preferred. Depending on the chosen removal strategy, Odoo
generates a transfer with the products that fit the settings best.

.. image:: removal/packing-products.png
   :align: center
   :alt: Products being packed at the packing area for delivery, taking expiration dates into
         account.

.. note::
   To pick for delivery, the product's lot/serial number can be found on the transfer form.

How does it work?
=================

First In, First Out (FIFO)
--------------------------

When using a :guilabel:`First In, First Out (FIFO)` strategy, a demand for a product triggers a
removal rule, which requests a transfer for the lot/serial number that entered the stock first.
For example, imagine there are three lots of nails in the warehouse. Those three have the following
lot numbers: 00001, 00002, 00003, each with five boxes of nails in it.

Lot 00001 entered the stock on May 23, lot 00002 on May 25, and lot 00003 on June 1. A customer
orders six boxes on June 11. With the FIFO removal strategy selected, a transfer is requested for
the five boxes from lot 00001 and one of the boxes in lot 00002, since lot 00001 entered the stock
first. The box from lot 00002 is taken next because it has the oldest receipt date after lot 00001.
So, for every order of a product with the FIFO strategy selected, Odoo requests a transfer for the
products that have been in stock for the longest time.

Last In, First Out (LIFO)
-------------------------

Similar to FIFO, the :guilabel:`Last In, First Out (LIFO)` strategy moves products based on the date
they entered the stock. Here, a demand for a product triggers a removal rule that requests a
transfer for the lot/serial number that has most recently entered the stock.

For example, imagine there are three lots of screws in the warehouse. Those three have the following
numbers: 10001, 10002, and 10003, each with 10 boxes of screws in it.

Lot 10001 entered the stock on June 1st, lot 10002 on June 3rd, and lot 10003 on June 6th. A
customer orders seven boxes on June 8th. With the LIFO removal strategy selected, a transfer is
requested for seven boxes from lot 10003 because that lot is the last one to have entered the stock.
Basically, for every order of a product with the LIFO strategy used, a transfer for the last lot
that entered the stock is requested.

.. note::
   The LIFO strategy is banned in many countries and can lead to only having old or obsolete products
   in stock.

First Expired, First Out (FEFO)
-------------------------------

The :guilabel:`First Expired, First Out (FEFO)` strategy is a bit different from the other two
removal strategies. For FEFO, the expiration date is important, not the date the product was
received.

For example, imagine there are three lots of six-egg boxes (in this specific case, don't forget to
use units of measure). Those three lots have the following lot numbers: 20001, 20002, and 20003,
each with five boxes in it.

Lot 20001 entered the stock on July 1st and expires on July 15th, lot 20002 entered on July 2nd and
expires on July 14th, and lot 20003 entered on July 3rd and expires on July 21st. A customer orders
six boxes on July 5th. With the FEFO strategy selected, a transfer is requested for the five boxes
from lot 20002 and one from lot 20001. All the boxes in lot 20002 are transferred because they have
the earliest expiration date. The transfer also requests one box from lot 20001 because it has the
next closest expiration date after lot 20002.

Basically, for every sales order of a product with the FEFO strategy, a transfer is requested for
the product that has the earliest expiration date from the order date.

Using removal strategies
========================

To differentiate some units of products from others, the units need to be tracked, either by
:guilabel:`Lot` or by :guilabel:`Serial Number`. To do so, go to :menuselection:`Inventory -->
Configuration --> Settings`. Then, activate the :guilabel:`Storage Location`, :guilabel:`Multi-Step
Routes`, and :guilabel:`Lots & Serial Numbers` settings.

.. image:: removal/traceability.png
   :align: center
   :alt: :alt: Traceability settings.

.. image:: removal/warehouse-settings.png
   :align: center
   :alt: :alt: Warehouse settings.

.. note::
   To work with the FEFO strategy, also activate the Expiration Dates feature.

Next, go to :menuselection:`Inventory --> Configuration --> Product Categories` to define the
removal strategy on a product category.

.. image:: removal/product-category-removal.png
   :align: center
   :alt: :alt: Removal strategy on a product category.

FIFO (First In, First Out)
--------------------------

As explained, a :guilabel:`FIFO` removal strategy implies that products stocked first move out
first. Companies should use this method if they are selling products with short demand cycles, such
as clothes, to ensure they are not stuck with outdated styles in stock.

In this example, there are three lots of white shirts. The shirts are from the All/Clothes category,
where :guilabel:`FIFO` is set as the removal strategy. In the
:guilabel:`Inventory Valuation Report`,  the three different receipts are listed with the amounts.

.. image:: removal/inventory-valuation.png
   :align: center
   :alt: View of the lots of white shirts in the inventory valuation report.

Lot 000001 contains five shirts, lot 000002 contains three shirts, and lot 000003 contains two
shirts.

As seen above, lot 000001 entered the stock first. :guilabel:`Create` and :guilabel:`Confirm` a
sales order for six white shirts. All five shirts from lot 000001 and one shirt from lot 000002 will
be selected to be sent to the customer.

Once the sales order is confirmed, the delivery order will be created and linked to the picking, and
the oldest lot numbers will be reserved thanks to the FIFO strategy.

LIFO (Last In, First Out)
-------------------------

With a :guilabel:`LIFO` strategy, the opposite is true. The products that are received last move out
first. :guilabel:`LIFO` is mostly used for products without a shelf life.

In this example, the white shirts will be used again to test the :guilabel:`LIFO` strategy. First,
open the product category via :menuselection:`Inventory --> Configuration --> Product Categories`
and change the :guilabel:`Force Removal Strategy` to :guilabel:`LIFO`.

.. image:: removal/last-in-first-out.png
   :align: center
   :alt: Last in first out strategy set up as forced removal strategy.

Then, :guilabel:`Create` a sales order for four white shirts and :guilabel:`Confirm` it. Check that
the reserved products are from lots 000003 and 000002 by looking at the :guilabel:`Detailed
Operations` in the  :guilabel:`Sales Order`.

.. important::
   Don't forget that the :abbr:`LIFO (Last In, First Out)` strategy is banned in many countries!

FEFO (First Expired, First Out)
-------------------------------

With the :guilabel:`FEFO` removal strategy, the way products are picked is not based on the
reception date. In this case, they are picked according to their expiration date.

.. note::
   For more information about expiration dates, please have a look at
   :doc:`the related doc <../../management/lots_serial_numbers/expiration_dates>`.

By activating the :guilabel:`Expiration Dates` feature, it becomes possible to define different
expiration dates on the serial/lot numbers. Expiration dates can be set by going to
:menuselection:`Inventory --> Products --> Lots/Serial Numbers`, or they can be entered when
validating the received products.

.. image:: removal/removal-date.png
   :align: center
   :alt: View of the removal date for 0000001.

Lots are picked based on their removal date, from earliest to latest. Lots without a removal date
defined are picked after lots with removal dates.

.. note::
   If products are not removed from stock when they should be, lots that are past the expiration
   date may still be picked for delivery orders!

To use the FEFO strategy, go to :menuselection:`Inventory --> Configuration --> Product Categories`
and set :guilabel:`FEFO` in the :guilabel:`Force Removal Strategy` field.

.. image:: removal/fefo.png
   :align: center
   :alt: FEFO forced removal strategy.

For this particular example, there are three different lots of hand cream.

.. list-table::
   :header-rows: 1
   :stub-columns: 1

   * - Lot/Serial No
     - Product
     - Expiration Date
     - Amount In Stock
   * - 0000001
     - Hand Cream
     - 09/30
     - 20
   * - 0000002
     - Hand Cream
     - 11/30
     - 10
   * - 0000003
     - Hand Cream
     - 10/31
     - 10

When a sales order for 25 units of Hand Cream is created, Odoo automatically reserves the lots with
the closest expiration date, 20 from lot 0000001 and 5 from lot 0000003.

.. image:: removal/pick-hand-cream.png
   :align: center
   :alt: Hand cream lot numbers selected for the sales order.
