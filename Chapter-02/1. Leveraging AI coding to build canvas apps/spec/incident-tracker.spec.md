# Incident Tracker - specification

## Purpose
Field technicians at a computer store visit customers to repair hardware.
They need to see the incidents reported to them, open the details on a
tablet while on site, and record progress before leaving.

## Users
Field technicians. They read every field of an incident, and they update
only Status and Comments. Nobody creates customers from this app.

## Data
Two Dataverse tables:
- Customer: Name, Address, Phone, Email.
- Incident: Name, Customer (lookup), Reported on, Priority (choice:
  High, Medium, Low), Status (choice: New, In progress, Resolved),
  Comments.

## Screens
1. Incidents. A gallery of incidents sorted by the reported date, newest
   first, showing the name, the customer, and the priority. A search box
   filters by name. Selecting a row opens the Incident detail screen.
2. Incident detail. Read-only name, customer, date, and priority. An
   editable Status dropdown and a multiline Comments box. A Save button
   writes both fields back to the table and returns to the Incidents
   screen. A Call customer button dials the customer's phone number.

## Rules
- Priority is shown as a coloured badge: red for High, amber for Medium,
  grey for Low.
- Resolved incidents stay in the gallery but are dimmed.
- Saving without a change is allowed and does nothing harmful.

## Acceptance criteria
- A technician can go from opening the app to a saved status change in
  three taps.
- Every screen is usable on a tablet held in landscape orientation.

## Out of scope
- Creating, editing, or deleting customers.
- Offline use.
- Attachments and photographs.