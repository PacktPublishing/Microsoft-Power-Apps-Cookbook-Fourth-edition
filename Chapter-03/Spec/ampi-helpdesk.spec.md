# AMPI Helpdesk - specification

## Purpose
A computer services company resolves incidents raised by its customers
against the projects it runs for them. Support agents record each ticket,
work through it as a series of operations carried out on site, and close
it once the fix is confirmed. Managers need to see where the open work is.

## Users
- Support agent. Creates and updates tickets, records the operations
  carried out for each one, and reads project and customer information.
- Support manager. Everything an agent does, plus the overview of open
  work across every project.

## Data
Four Dataverse tables in one solution:
- Ticket: Title, Description, Resolution, Ticket status (choice: New,
  Pending, Resolved, Closed), Ticket priority (choice: Low, Medium,
  High), Ticket validation (choice: Phone, Email). Tickets carry notes
  and attachments.
- Ticket operation: Title, Description, Operation status reusing the same
  choice as Ticket status, Duration as a whole number in duration format,
  Latitude and Longitude as decimals with six decimal places.
- Project: Title, Description, Start and End as date only.
- Account: reuse the standard Dataverse table, do not create a new one.

Relationships: one Ticket has many Ticket operations, one Project has
many Tickets, and one Account has many Projects.

## App
A model-driven app called AMPI Helpdesk, with a Helpdesk group in the
navigation holding Tickets, Projects, and the overview.
- Ticket form: every ticket column, the project it belongs to, and a
  sub-grid of that ticket's operations.
- Ticket operation form: every column of the table.
- Pending Tickets view on Ticket: Title, Ticket priority, Ticket status,
  and Created On, newest first, excluding tickets that are Resolved or
  Closed.
- Charts on Ticket: tickets by priority as a pie, and tickets by status
  as a column chart.
- Overview: those two charts beside a list of pending tickets.

## Rules
- Ticket validation stays hidden on the ticket form until Ticket status
  is Resolved or Closed.

## Sample data
A handful of accounts, projects, tickets, and ticket operations spread
across every priority and status, so the charts and the overview have
something to show.

## Out of scope
- The business process flow that walks a ticket from New to Closed.
- The canvas app embedded in the Project form.
- Deployment to another environment.