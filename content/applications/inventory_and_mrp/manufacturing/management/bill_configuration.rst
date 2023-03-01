================================
Create a bill of materials (BoM)
================================

A *Bill of Materials* (or *BoM*) is a document that defines the quantity of each component required
to manufacture (or deliver) a finished product. It can also include various operations types,
steps, and instructions for the individual guidelines needed to complete a production process.

In Odoo Manufacturing, multiple :abbr:`BoMs (bills of materials)` can be linked to a product, so
even product variants can have their own specific :abbr:`BoMs (bills of materials)`.

Correctly setting up a :abbr:`BoM (bill of materials)` helps optimize the manufacturing process,
and saves time.

Set up a BoM
============

:abbr:`BoMs (bills of materials)` can be set up with (or without) operations steps or instructions.
They can include as many (or as few) components, as needed. The simplest setup is one without
operations (or instructions). In that case, the production is solely managed with *manufacturing
orders*.

To create a :abbr:`BoM (bill of materials)`, navigate to :menuselection:`Manufacturing -->
Products --> Bills of Materials`, and click :guilabel:`Create`. Then, in the :guilabel:`Product`
field, choose the product that will be associated with the :abbr:`BoM (bill of materials)`.

.. image:: bill_configuration/bill-configuration-bom-creation.png
   :align: center
   :alt: Bill of materials creation screen.

There are three :guilabel:`BoM Types` that can be chosen for any bill of materials:

- :guilabel:`Manufacture this product` indicates that this product is manufactured in-house, from
  start to finish using the components listed on the :abbr:`BoM (bill of materials)`.
- :guilabel:`Kits` are sets of unassembled components that may be sold as products, and are useful
  for managing more complex :abbr:`BoMs (bills of materials)`.
- :guilabel:`Subcontracting` outsources the production of some (or all) components or products to
  outside manufacturers. This feature needs to be enabled in :menuselection:`Manufacturing -->
  Configuration --> Settings`, under the :guilabel:`Operations` section.

.. note::
   A :abbr:`BoM (bill of materials)` can also be created directly from the :abbr:`BoM (bill of
   materials)` smart button on the product template, in which case the
   :guilabel:`Product` field is pre-filled.

The most common :guilabel:`BoM Type` is :guilabel:`Manufacture this product`. Once the
:guilabel:`BoM Type` is chosen, click :guilabel:`Add a Line` to add all the :guilabel:`Components`
that go into the production of the final product, as well as the :guilabel:`Quantity` of each
component. Finally, click :guilabel:`Save` to finish creating the :abbr:`BoM (bill of materials)`.

.. tip::
   New components can be created on-the-fly directly from the :abbr:`BoM (bill of materials)`.
   After selecting :guilabel:`Add a line`, create the new component and select :guilabel:`Create`
   or :guilabel:`Create and Edit`. Components can also be created by going to
   :menuselection:`Manufacturing --> Products --> Products`, and clicking :guilabel:`Create`.

Specify a BoM for a product variant
-----------------------------------

:abbr:`BoMs (bills of materials)` can also be assigned to specific *product variants*, with two
setup options available to choose from.

.. image:: bill_configuration/bill-configuration-product-variants.png
   :align: center
   :alt: Bill of materials product variants and apply on variants options.

The first method is to create one :abbr:`BoM (bill of materials)` per product variant, by
specifying the :guilabel:`Product Variant` every time a new :abbr:`BoM (bill of materials)` is
created. The second method is to create **one** master :abbr:`BoM (bill of materials)` that
contains all components, and specify which variant each component applies to in the
:guilabel:`Apply on Variants` column.

.. note::
   The :guilabel:`Apply on Variants` column is hidden by default and can be accessed by clicking on
   the :guilabel:`Additional Options` menu icon at the right of the :guilabel:`Components` tab.

.. important::
   To assign *product variants* to :abbr:`BoMs (bills of materials)`, the feature must be enabled
   in :menuselection:`Inventory --> Configuration --> Settings`, under the :guilabel:`Products`
   section by selecting :guilabel:`Variants` and clicking :guilabel:`Save`.

Set up operations steps
=======================

Some :abbr:`BoMs (bills of materials)` require multiple operations and steps during the
manufacturing process. To create :guilabel:`Operations` on a :abbr:`BoM (bill of materials)`, first
enable the :guilabel:`Work Orders` feature in :menuselection:`Manufacturing --> Configuration -->
Settings --> Operations`.

.. image:: bill_configuration/bill-configuration-create-operation.png
   :align: center
   :alt: An example of a Bill of Materials operation and the steps creation tab.

When creating a new :abbr:`BoM (bill of materials)`, click the :guilabel:`Operations` tab and click
:guilabel:`Add a line` to add a new operation. In the :guilabel:`Create Operations` box, give the
operation a name, specify the :guilabel:`Work Center` and the :guilabel:`Default Duration`
settings. Under the :guilabel:`Work Sheet` tab, the type of :guilabel:`Work Sheet` can also be
chosen, if assembly instructions need to be attached.

The :guilabel:`Work Sheet` types that can be added are: :guilabel:`Text` (with a
:guilabel:`Description`); :guilabel:`PDF` files; and :guilabel:`Google Slide` presentations. When
all the information has been filled out, select :guilabel:`Save & Close`.

.. image:: bill_configuration/bill-configuration-operations-popup.png
   :align: center
   :alt: Bill of materials create operations popup on operations tab.

Add by-products to a BoM
========================

A *by-product* is a residual product that is created during production of a :abbr:`BoM (bill of
materials)`. Unlike the finished product, there can be more than one by-product on a :abbr:`BoM
(bill of materials)`.

To add by-products to a :abbr:`BoM (bill of materials)`, first enable the :guilabel:`By-Products`
feature in :menuselection:`Manufacturing --> Configuration --> Settings --> Operations`.

Once the feature is enabled, by-products can be added to a :abbr:`BoM (Bill of Materials)` from the
:guilabel:`By-products` tab by clicking :guilabel:`Add a line`. The by-product can be named, its
:guilabel:`Quantity` specified, and a :guilabel:`Unit of Measure` chosen.

If the :abbr:`BoM (bill of materials)` has :guilabel:`Operations` steps, specify exactly which
operation the by-product is produced from in the :guilabel:`Produced in Operation` field. Finally,
click :guilabel:`Save` to save changes.

.. seealso::
   - :doc:`kit_shipping`
   - :doc:`product_variants`
   - :doc:`routing_kit_bom`
