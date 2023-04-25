===============
Recurring tasks
===============

When handling a project, the same task often needs to be performed several times: for example,
a weekly meeting or status report. The **recurring tasks** feature allows you to automate the
creation of those tasks.

.. seealso::
   `Odoo Tutorials: Recurring tasks <https://www.odoo.com/slides/slide/recurring-tasks-1946>`_

Configuration
=============

To enable recurring tasks, go to :menuselection:`Project --> Configuration --> Settings`, then
activate :guilabel:`Recurring Tasks`.

Once configured in :guilabel:`Settings`, the recurring tasks feature is activated by default on all
existing projects. If needed, it can be deactivated on an individual project by clicking the ...
icon next to the project name, then going to :menuselection:`Settings --> Settings --> Task
Management` and unchecking the :guilabel:`Recurring Tasks`.

.. image:: recurring_tasks/project-settings.png
   :align: center
   :alt: Press the ... icon next to the project, then go to Settings

Set up recurrence on a task
---------------------------

In an existing task, go to the :guilabel:`Recurrent` tab, then check the :guilabel:`Recurrent` box.
A set of options allows you to configure the frequency (daily, monthly, weekly, or other) and the
number of recurrences.

.. important::
   A new recurrence will be created on the scheduled date. If you would like to have the task in
   your pipeline before that, consider setting up the recurrence date to a day earlier.

On the scheduled recurrency date, a new task will be created in the pipeline with the following
configuration:

- :guilabel:`Stage`: 1st stage of the pipeline (:guilabel:`New` or equivalent).
- :guilabel:`Name, Description, Project, Assignees, Customer, Tags`: copied from the original task.
- :guilabel:`Milestones, Deadline, Timesheets, Chatter, Activities`: blank.
- :guilabel:`Subtasks`: copied from the original task, which becomes a parent of all the tasks in
  recurrence.
- A **smart button** on the task displays the total number of existing recurrences.

Edit or stop recurrence
-----------------------

When editing a recurring task, a prompt will show up at the top of your screen. It allows you to
choose whether you wish to apply your changes to one task only, or to a sequence of tasks.

To stop the recurrence, go to the :guilabel:`Recurrency` tab of the task and deactivate the option.
