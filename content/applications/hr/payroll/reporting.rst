=========
Reporting
=========

The :guilabel:`Reporting` section offers a variety of reports to choose from. The
:guilabel:`Payroll`, :guilabel:`Meal Vouchers`, :guilabel:`Attachment of Salary`, and
:guilabel:`DMFA` reports are universal and available for all companies regardless of location. The
:guilabel:`Paid Time Off Allocation`, :guilabel:`273S Sheet`, and :guilabel:`274.XX Sheets` reports
are specific to Belgian companies only.

To view a report, go to :menuselection:`Payroll --> Reporting` and click on the specific report.

.. image:: reporting/reports.png
   :align: center
   :alt: Report dashboard view.

If a report is unavailable to a company, a user error will pop up, stating “You must be logged in a
Belgian company to use this feature.”

At the top of each report, click on :guilabel:`Filters` to display the optional filters for the
specific report. All reports have the option to add a custom filter, and each will have different
default custom filter options. Select the parameters, then click the :guilabel:`Apply` smart button.

.. image:: reporting/custom-filter.png
   :align: center
   :alt: Report dashboard view.

Clicking on :guilabel:`Favorites` allows for three options: :guilabel:`save the current search`,
:guilabel:`add the search to the dashboard`, or :guilabel:`insert the search to a Google
spreadsheet`.

.. image:: reporting/favorites.png
   :align: center
   :alt: Favorite options for reports.

Payroll
-------

Clicking on :menuselection:`Payroll --> Reporting --> Payroll` will display the *Payroll Analysis*
report.

.. image:: reporting/payroll-report.png
   :align: center
   :alt: Report dashboard view.

This will show all the payslips generated in the last 365 days. The report can display metrics for a
variety of parameters. Click the :guilabel:`Measures` box and a drop-down will appear with the
various options to display. The options available are: # Payslip, Basic Wage, Basic Wage for Time
Off, Days of Paid Time Off, Days of Unforeseen Absence, Days of Unpaid Time Off, Gross Wage, Net
Wage, Number of Days, Number of Hours, Work Days, Work Hours, and Count.

.. image:: reporting/measures.png
   :align: center
   :alt: Report dashboard view.

Bar chart
~~~~~~~~~

To display the data in a bar chart, click on the :guilabel:`Bar Chart` icon (first icon) in the menu
bar.

.. image:: reporting/bar-chart.png
   :align: center
   :alt: Report dashboard view.

When this is selected, an option to display the chart as stacked appears. Click the middle
:guilabel:`Stacked` icon to view the bar chart in a stacked format (where multiple values appear in
each column). An option to display the columns in ascending or descending order appears at the end
of the options.

.. tip::
   Clicking an option will enable it. To disable the option, click it again. When the option is
   enabled it will appear grey. When it is inactive, it will appear white.

Line chart
~~~~~~~~~~

A line chart is the default view for the *Payroll Analysis* report. If a different view was
selected, click on the :guilabel:`Line Chart` icon (last icon) in the menu bar to change the view
back to a line chart. An option to display the line chart in ascending or descending order appears
at the end of the options.

.. image:: reporting/line-chart.png
   :align: center
   :alt: Report dashboard view.

Pie chart
~~~~~~~~~

To display the data in a pie chart, click on the :guilabel:`Pie Chart` icon (last icon) in the menu
bar. There are no other options available in this view.

.. image:: reporting/pie-chart.png
   :align: center
   :alt: Report dashboard view.

Lower half chart
~~~~~~~~~~~~~~~~

The bottom half of the screen presents a graph no matter which measures are selected for the main
chart. The default information displayed is the number of payslips, net wage, gross wage, days of
paid time off, and days of unpaid time off. The information is divided by department. To display
more information on the report, select the :guilabel:`Measures` drop-down, then click on any other
items to display.

.. image:: reporting/measures-bottom.png
   :align: center
   :alt: Report dashboard view.

To sort the entries by a specific column, such as *Net Wage*, click on the column name twice. The
first click will select the column, the second click will sort the information in descending order.

.. image:: reporting/net-wage.png
   :align: center
   :alt: To sort information by descending order, click the column head twice.

To export the data in an XLSX format, click the :guilabel:`Download xlsx` icon. The information will
be downloaded into an Excel spreadsheet.

.. image:: reporting/export.png
   :align: center
   :alt: Download an Excel spreadsheet of the data by clicking the download button.

The data can be inserted into a spreadsheet by clicking the :guilabel:`Insert in Spreadsheet` smart
button. A pop-up will appear asking which spreadsheet to place the information in. Select an
existing spreadsheet or enter the name for a new spreadsheet. Click the :guilabel:`Confirm` smart
button to move to a spreadsheet view with all the information populated.

.. image:: reporting/spreadsheet.png
   :align: center
   :alt: Send the data to a spreadsheet.

Once in the spreadsheet view, click on :guilabel:`File`, then select :guilabel:`Save` to save the
data, or :guilabel:`Save as Template` to save the setting as a template to use in the future.

Meal Vouchers
-------------

:guilabel:`Meal Vouchers` provides an overview of the meal vouchers used by employees, and can be
shown by day, week, month, quarter, or year. The default view is by month.

.. image:: reporting/meal-vouchers.png
   :align: center
   :alt: Meal voucher

To change the displayed view, click on :guilabel:`Total`. The data will collapse, showing only the
count column. Click on :guilabel:`Total` again, then hover over *Day*, then click on one of the
other time-period options available.

.. image:: reporting/voucher-day.png
   :align: center
   :alt: Meal voucher

It is possible to compare the current meal voucher report to the one for the previous time period or
the previous year. To view these comparisons, click on the on the :guilabel:`Comparison` drop-down
at the top, then select either :guilabel:`Date: Previous Period` or :guilabel:`Date: Previous Year`.

.. image:: reporting/meal-comparison.png
   :align: center
   :alt: Meal voucher

To export the data in an XLSX format, click the :guilabel:`Download xlsx` icon. The information will
be downloaded into an Excel spreadsheet.

.. image:: reporting/voucher-download.png
   :align: center
   :alt: Download an Excel spreadsheet of the data by clicking the download button.

The data can be inserted into a spreadsheet by clicking the :guilabel:`Insert in Spreadsheet` smart
button. A pop-up will appear asking which spreadsheet to place the information in. Select an
existing spreadsheet or enter the name for a new spreadsheet. Click the :guilabel:`Confirm` smart
button to move to a spreadsheet view with all the information populated.

Once in the spreadsheet view, click on :guilabel:`File`, then select :guilabel:`Save` to save the
data, or :guilabel:`Save as Template` to save the settings as a template to use in the future.

Attachment of Salary
--------------------

The :guilabel:`Attachment of Salary` report shows all deductions or allocations per employee,
such as child support payments and wage garnishments.

.. image:: reporting/attachment-of-salary.png
   :align: center
   :alt: View the Attachment of Salary report that shows all salary garnishments.

The employees are listed in the left-side column, while the different deductions are listed in the
top row, organized by month.

The report can be exported as a XLSX file, or inserted into a spreadsheet, using the corresponding
smart buttons at the top.

Clicking on the :guilabel:`Measures` smart button will show options for how the data is displayed.
Assignment of salary, attachment of salary, child support, and count, can all be selected or
deselected by clicking on the item. If an item has a check mark, it will be displayed.

.. image:: reporting/attachment-measures.png
   :align: center
   :alt: Select the options that be displayed in the report.

The salary attachment report can be compared to the one for the previous time period or the previous
year. To view these comparisons, click on the on the :guilabel:`Comparison` drop-down at the top,
then select either :guilabel:`Payslip End Date: Previous Period` or :guilabel:`Payslip End Date:
Previous Year`.
