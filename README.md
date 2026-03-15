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

```
Full Name | Email Address | Phone Number | Company | Position or Role | Event they wish to attend | Preferred Session | Number of Tickets Required | How they heard about us
````

This form acts as the entry point for the entire automation workflow.

## Workflow Design and Planning

Before implementing the automation, a visual flowchart of the system architecture was created using Miro.<br>

![Diagram](image/flowchart.png) <br>

This diagram helped map the complete process including:
- Data collection
- Data formatting
- Conditional filtering
- Event-specific email communication
- Reminder scheduling
- Internal notifications

The visual planning ensured the workflow was logically structured and scalable before implementation in Zapier.

## Registration Form Creation and Data Processing

The first operational step in the automation pipeline was the creation of the event registration form using Google Forms. This form serves as the primary interface for participants to register for the event, and it feeds structured data directly into the automation workflow.

**Form Creation Using Google Forms**

A Google Form was designed to be simple, intuitive, and easy to complete in order to minimize friction during registration. Each field was carefully configured to ensure the data collected would be compatible with the downstream automation steps.

The following fields were created in the form:

| Field | Type | Purpose |
|------|------|------|
| Full Name | Short answer | Captures the participant’s full name for identification and personalization |
| Email Address | Short answer | Used to send confirmation and reminder emails |
| Phone Number | Short answer | Allows organizers to contact participants if necessary |
| Company | Short answer | Captures the organization the participant represents |
| Position or Role | Short answer | Helps understand the professional background of participants |
| Event they wish to attend | Dropdown | Determines which automation path the participant follows |
| Preferred Session | Dropdown | Indicates the session time the participant prefers |
| Number of Tickets Required | dropdown | Helps estimate attendance and capacity |
| How did you hear about us? | Multiple Choice | Used to enforce the company’s marketing policy filter |

The `Event they wish to attend` field plays a critical role because it determines which conditional automation path the participant will follow later in the Zapier workflow.

Similarly, the `How did you hear about us?` field is used to enforce the organization's policy regarding participant eligibility for automated communication.

Once the form structure was finalized, Google Forms automatically generated a linked response sheet in Google Sheets, which serves as the primary data source for the automation.

## Data Processing and Formatting

After form submission, the raw data collected from the form is processed using Zapier Formatter tools to standardize and prepare the data for communication and storage.

The following transformations are applied:

**Name Formatting**
- Convert the participant's full name into Title Case to maintain a consistent format.
- Extract the first name from the full name for use in personalized email greetings.

Example:

```
Input:
john doe
```

```
Processed Output:
John Doe
```
```
First Name extracted:
John
```

**Phone Number Standardization**

The phone number is formatted into a consistent standard format to improve readability and ensure compatibility with potential communication systems.

Example format:
```
Input:
08081234567
```

```
Output:
2348081234567
```
These processing steps ensure that participant data is clean, structured, and suitable for automated communication, enabling the rest of the workflow to operate reliably.

## Policy-Based Filtering

A key business rule was implemented during the automation process.

Company Policy
```
If a participant selects “Other” in the field:

“How did you hear about us?”
```
then the system does not send confirmation emails or reminder messages to that participant.

This condition ensures that the organization only engages with participants acquired through approved marketing channels.

Zapier filters automatically enforce this rule before any communication is sent.
