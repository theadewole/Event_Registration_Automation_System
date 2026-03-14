# Case Study
We are setting up a simple registration system for our event scheduled for mm-dd-yyyy. The objective is to create a clean, user-friendly form that collects the following information from attendees:
```
Full Name | Email Address | Phone Number | Company | Position or Role | Event they wish to attend | Preferred Session | Number of Tickets Required | How they Heard About Us
```

**Expected Workflow**
Once a participant submits the form, the system should automatically:
- Send a personalized confirmation email to the attendee.
- Add the participant’s details to the attendee list for record keeping.
- Schedule reminder emails as the event date approaches.
- The entire process should operate seamlessly without manual follow-ups.

**Important Condition**

If a participant selects “Other” in the “How did you hear about us?” field, they must not receive confirmation emails or reminder messages. This aligns with the company’s policy of excluding participants who did not learn about the event through the approved channels.

**Additional Automation**

One hour after the reminder email has been sent, the system should automatically send an update to the Slack team for each event session. 
The update should include the list of participants registered for that specific event time.

# Project Overview

This project implements an automated event registration workflow designed to streamline the process of collecting participant information, managing attendee records, and communicating with registrants.

The automation is built using Google Forms, Google Sheets, Zapier, Gmail, and Slack to ensure that once a participant registers for an event, the required actions—confirmation, reminders, and internal notifications—are executed automatically without manual intervention.

The primary objective is to create a reliable, scalable, and organized registration pipeline for events scheduled for 15th December 2025, while maintaining a smooth experience for both participants and the event management team.

## Data Collection

A Google Form was used to collect participant registration information.

The form captures the following fields:

Full Name | Email Address | Phone Number | Company | Position or Role | Event they wish to attend | Preferred Session | Number of Tickets Required | How they heard about us

This form acts as the entry point for the entire automation workflow.

## Workflow Design and Planning




