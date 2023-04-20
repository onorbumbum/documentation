===============
Email templates
===============

Writing effective emails is vital in order for businesses to continuously earn high response rates.
Email templates allow users to send quality communications, without having to compose (or rewrite)
the same structure repeatedly, which saves time and improves efficiency.

Creating different templates that are tailored to specific situations and audiences lets users
choose the right message for the right audience, which increases the quality of the message and
enhances the overall engagement rate.

.. note::
   Email templates in Odoo use QWeb or XML, which allows the user to edit emails in their final
   rendering, making customizations more robust without having to edit any code whatsoever.

Editing email templates
=======================

In Odoo 15, the *Powerbox* feature can be used when working with email templates. This feature
provides the ability to directly edit the format/text in an email template, as well as the ability
to add links, buttons, appointment options, or images.

Additionally, the XML/HTML code of the email template can be edited directly, via the
:guilabel:`</>` icon. Dynamic placeholders (referencing fields within Odoo) are only available in
the :guilabel:`Email Configuration` fields, the :guilabel:`Subject`, and the :guilabel:`Language` in
Odoo 15.

Powerbox feature
----------------

The *Powerbox* feature is an enriched text editor with various formatting, layout, and text options.
It can also be used to add XML/HTML features in an email template. The powerbox feature is
activated, by typing a forward slash `/` in the body of the email template.

When a forward slash `/` is typed in the body of an email template, a drop-down menu appears with
the following options:

**Basic Blocks**

- :guilabel:`Heading 1`: Big section heading.
- :guilabel:`Heading 2`: Medium section heading.
- :guilabel:`Heading 3`: Small section heading.
- :guilabel:`Text`: Paragraph block.
- :guilabel:`Bulleted list`: Create a simple bulleted list.
- :guilabel:`Numbered list`: Create a list with numbering.
- :guilabel:`Checklist`: Track tasks with a checklist.
- :guilabel:`Table`: Insert a table.
- :guilabel:`Switch direction`: Switch the text's direction.
- :guilabel:`Separator`: Insert a horizontal rule separator.
- :guilabel:`Quote`: Add a blockquote section.
- :guilabel:`Code`: Add a code section.
- :guilabel:`Appointment`: Add a specific appointment.
- :guilabel:`Calendar`: Schedule an appointment.

**Navigation**

- :guilabel:`Link`: Add a link.
- :guilabel:`Button`: Add a button.

**Medias**

- :guilabel:`Image`: Insert an image.

To activate any of these options, click on the desired feature from the powerbox drop-down menu.

If it's a text-related option (e.g. :guilabel:`Heading 1`, :guilabel:`Switch direction`, etc.)
highlight the text, then type in the activator key `/`, and select the desired option from the
drop-down menu.

.. image:: email_template/powerbox-feature.png
   :align: center
   :alt: Powerbox feature in the email template.

Editing via XML/HTML code
-------------------------

To access the XML/HTML editor for an email template, first enter :ref:`developer mode
<developer-mode>`. To enter developer mode, navigate to :menuselection:`Main Odoo dashboard -->
Settings`, scroll down to :guilabel:`Developer Tools` section, and click :guilabel:`Activate the
developer mode`.

When clicked, the page will auto-refresh, return to the main Odoo dashboard, and a "bug" icon is
present on the top of the screen, beside the login and communication icons.

Once in developer mode, access to the XML/HTML editor is available on email templates. To access the
XML/HTML editor on email templates, click the :guilabel:`</>` icon in the upper-right corner of the
template, and proceed to edit the XML/HTML.

.. image:: email_template/html-code-editor.png
   :align: center
   :alt: HTML editor in the email template.

Dynamic placeholders
--------------------

Dynamic placeholders are encoded to display fields from within the database. In Odoo 15, dynamic
placeholders can **only** be used in the fields present in the :guilabel:`Email Configuration` tab,
the :guilabel:`Subject` and the :guilabel:`Language`.

Dynamic placeholders can be used with the following fields:

- :guilabel:`Subject` (Email Configuration tab)
- :guilabel:`From` (Email Configuration tab)
- :guilabel:`To (Emails)` (Email Configuration tab)
- :guilabel:`To (Partners)` (Email Configuration tab)
- :guilabel:`CC` (Email Configuration tab)
- :guilabel:`Reply-to` (Email Configuration tab)
- :guilabel:`Subject` (Main Template)
- :guilabel:`Language` (Settings Tab)

While the :guilabel:`Dynamic Placeholder Generator` is present as the last tab on the template, it
only creates placeholders for aforementioned fields. Dynamic placeholders may also be inserted in
the HTML code, but this task is out of the scope of Odoo Support.

.. seealso::
   :doc:`../../../../services/support/what_can_i_expect`

To use the :guilabel:`Dynamic Placeholder Generator` navigate to the :guilabel:`Dynamic Placeholder
Generator` tab. Select the :guilabel:`Field` that the *dynamic placeholder* should reference by
clicking on the :guilabel:`Field` dropdown. Should a :guilabel:`Sub-Model` or :guilabel:`Sub-Field`
need to be specified, set those by selecting the corresponding dropdown. The *dynamic placeholder*
will appear in the :guilabel:`Placeholder Expression` field. Copy and paste the *dynamic
placeholder* in the appropriate field as listed above.

Configuring a default reply on email templates
==============================================

Under the :guilabel:`Email Configuration` tab on an email template, there is a :guilabel:`Reply To`
field. In this field, email addresses can be added, to which replies will be redirected when sending
emails in mass using that template.

.. image:: email_template/reply-to-template-sales.png
   :align: center
   :alt: Reply-to field on template.

The :guilabel:`Reply To` field is **only** used for mass mailing endeavors (sending emails in bulk).
Emails can be sent in bulk in almost every Odoo application that has a `List` view option.

To send mass mails (while in `List` view), select the desired records where the emails are to be
sent, click the :guilabel:`Action` button, represented by a `Gear` icon (:guilabel:` ⚙️`), and
select the desired email option from the :guilabel:`Action` drop-down menu. If it is possible to
send an email, a mail composer pop-up, with values that can be defined and customized, appears.

.. image:: email_template/composer-mass-mailing.png
   :align: center
   :alt: Composer in mass mailing mode after selecting multiple quotations.

Transactional emails and corresponding URLs
===========================================

In Odoo, multiple events can trigger the sending of automated emails. These emails are known as
*transactional emails*, and sometimes contain links redirecting to the Odoo database.

By default, links generated by the database use the dynamic web.base.url key defined in the system
parameters. For more information about this, see :ref:`parameter <domain-name/web-base-url>`.

If the website application isn't installed, the web.base.url key will always be the default
parameter used to generate all the links.

It's important to know that the web.base.url key can only have a single value, meaning that, in a
multi-website/company database environment, even there is a specific domain name for each website,
the links generated to share a document (or within a transactional email) may remain the same,
regardless of which website/company is related to the sending of the email/document.

.. example::
   If the value of the web.base.url system parameter is equal to `https://www.mycompany.com` and
   there are two separate websites in Odoo with different URLS: `https://www.mycompany2.com` and
   `https://www.mycompany1.com`, the links created by Odoo to share a document or send a
   transactional email will come from the domain: `https://www.mycompany.com`.

This is not always the case as some Odoo applications have a link established in the database with
the website application. In that case, if a specific domain is defined for the websites, the URL
generated in the email template will use the domain defined on the corresponding website of the
company.

.. caution::
   A document shared using the documents application will always use the web.base.url key, as the
   document shared isn't associated with any particular website. Meaning that the URL will always be
   the same (the web.base.url key value), no matter what company it's shared from. This is a known
   limitation.

On the other hand, sales orders made by a customer, on an Odoo eCommerce website, have a link
established with the website, from which the order was made. As a result, the e-mail sent for sales
orders uses the domain name defined for the corresponding website to generate the links.

For more information about how to configure domains, check out :doc:`our domain name documentation
</administration/maintain/domain_names>`.

Updating translations within email templates
--------------------------------------------

In Odoo, email templates are automatically translated. Changing the translations shouldn't be
necessary. However, if for a specific reason, some of the translations need to be changed, it can be
done.

However, like any modification in the code, if they aren't done correctly (for example,
modifications leading to bad syntax), it can break the template, and as a result, the template will
appear blank.

In order to edit translations, follow these steps from the template:

#. To access the translations, first enter :ref:`developer mode <developer-mode>`. To enter
   developer mode, navigate to :menuselection:`Main Odoo dashboard --> Settings`, scroll down to
   :guilabel:`Developer Tools` section, and click :guilabel:`Activate the developer mode`.

#. Click on the :guilabel:`Edit` button, then on the language button, represented by the initials of
   the language currently being used.

   .. image:: email_template/edit-language-template.png
      :align: center
      :alt: Edit the language of a template.

#. A pop-up window with the different languages installed on the database appears. From this pop-up,
   the editing of translations is possible. When the desired changes have been made, click the
   :guilabel:`Save` button to save the changes.

   .. image:: email_template/translation-body.png
      :align: center
      :alt: Translation of the body of the Appointment Booked template.

.. note::
   When editing the translations the language set in the database will appear in **bold**.
