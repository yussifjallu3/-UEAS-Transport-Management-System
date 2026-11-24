# -UEAS-Transport-Management-System
Transport management system for the University of Engineering and Agricultural Sciences, built with Google Sheets, Apps Script and Arkesel SMS.
UEAS Transport Logbook & Fleet Dispatch System

Overview

The UEAS Transport Logbook is a transport management and trip request workflow designed for a university transport office. It streamlines how staff submit vehicle trip requests, how approvers review and decide on requests, and how transport officers allocate vehicles and drivers while tracking fleet readiness, trip logs, fuel usage, maintenance, and incidents.

Tools & Technologies

Google Sheets: Acts as the central operational database and reporting workspace across sheets such as Trip Requests, Form Responses, Drivers, Vehicles, Dashboard, Fleet Board, Trip Log, Fuel Log, Maintenance, and Email Log.

Google Apps Script: Automates status-change and form-submission handlers, one-time approval token links (doGet), double-booking conflict detection, email notifications (GmailApp with sender display name TRANSPORT_OFFICE (UEAS-Trip)), scheduled digests/archiving, and custom Transport Office spreadsheet menu helpers.

Google Forms: Captures incoming staff trip requests and routes entries into the spreadsheet workflow.

Arkesel SMS: Sends SMS alerts (using sender ID UEAS-Trip and Ghana phone normalization 233XXXXXXXXX) for approval requests, status updates, driver assignments/revocations, and 24-hour driver digests.

Main Features

Trip Request & Status Workflow: Tracks requests through statuses such as Pending, Hold, Approved, Allocated, Completed, Rejected, and Cancelled, including optional placeholder/hold choices so dispatchers can pause or take no action without unintended alerts.

One-Time Approval Links: Sends Approve/Reject links via email and SMS with a 48-hour expiration window, plus menu utilities to resend fresh links for a selected row or a specific row/request number.

Driver & Vehicle Allocation: Supports assigning or revoking drivers and vehicles, auto-populating driver contact details, and keeping blank/placeholder selections safe.

Double-Booking Conflict Detection: Checks for overlapping driver or vehicle schedules within a configurable departure time window, highlights conflicting cells in red with explanatory notes, and alerts the transport office.

Notifications, Retries & Archiving: Logs outbound email and SMS activity in Email Log, provides menu actions to retry failed rows or check SMS balance and email quota, sends a 24-hour upcoming trip digest to drivers, and archives completed trips.

Fleet & Operational Tracking: Organizes dashboard summaries, live fleet board views, trip logs, fuel records, maintenance tracking, and incident logs.

Setup Guide

Prepare the Google Sheet & Google Form:

Create or copy the spreadsheet containing the expected tabs (Trip Requests, Form Responses, Drivers, Approvers, Email Log, etc.) and link your Google Form to the form responses tab.

Ensure dropdown source ranges (ReqStatusList, DriverList) and Approvers details are configured.

Add Apps Script Files:

Open Extensions > Apps Script in the spreadsheet and add your script files (such as Code.gs and approval.gs).

Configure Script Properties:

In Apps Script under Project Settings > Script Properties, add ARKESEL_API_KEY with your Arkesel API key (and optionally TEST_PHONE for testing).

Deploy the Approval Web App:

In Apps Script, click Deploy > New deployment > Web app, set Execute as to Me, set Who has access to Anyone (or your organization's policy), and paste the resulting web app URL into the approval configuration in your script.

Authorize & Install Triggers:

Run a setup/diagnostic function once to grant permissions.

Set up triggers in Apps Script (or via setup helpers) for form submissions, spreadsheet edits, and time-driven tasks (such as overdue trip completion, 24-hour driver digests, or archiving).

Refresh the spreadsheet to load the Transport Office menu.

Note on Sample Data

All names, phone numbers, email addresses, staff IDs, vehicle/trip entries, and preview screenshots provided in sample files or documentation for this project are fictional and used strictly for demonstration, testing, and layout reference.
