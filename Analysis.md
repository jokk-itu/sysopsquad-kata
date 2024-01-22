# Analysis of the Sysop Squad Architecture Kata

## Description of Kata

[Sysop Squad](https://fundamentalsofsoftwarearchitecture.com/katas/kata?id=SysopSquad).

An electronics giant needs a new trouble-ticket system for their customer-facing IT consultants (the Sysop Squad) in their stores nationwide

- Users: thousands of customers, hundreds of consultants, hundreds of store staff.

- Requirements: 
  - trouble tickets can be entered by either call-center receptionists, store staff, or customers online.
  - tickets route to the appropriate consultant based on location, availability and skill.
  - consultants should only need a mobile device.
  - customers enter consultant evaluation after service.
  - consultant tracks work performed in customer record(s) for future reference.

- Additional Context:
  - uptime is critical to th e company's reputation.
  - the site's performance must degrade gracefully under heavy load.
  - good routing of requests is critical to making a profit.


## Analysis on Architecture Characteristics

The amount of users is a fixed amount, all located nationwide.
It seems there is no need for scaling, based on users, since the amount is fixed. It can be assumed that the amount is fixed throughout the day and almost zero outside of work hours.

The different kinds of users requires a need for authorization, preferably role based authorization. If there is a need for authorization, then authentication is also needed.
There is also a need for authorization based on ticket submission, ticket assignment, providing evaluation and consultants track work in ticket.

The need for submitting tickets, evaluating consultants and consultants needing their mobile devices only. Calls for a portal which can provide the needs, and it must support desktops and mobile screens, which is for portability.

Uptime is critical, and it is assumed that covers 24/7.
It is therefore important to consider robustness and if the system should experience downtime, it is important to consider recoverability.

### Main Archictecture Characteristica

<b>Portability</b> portal for desktop and mobile screens.
<b>Authorization</b> on portal to distinguish users.
<b>Robustness</b> to handle errors gracefully and require uptime.
<b>Recoverability</b> to get the system up again fast to reduce downtime.

## Analysis on Functional Requirements

How to enter tickets and who can do it.

How are tickets routed to the correct consultant.

How customers enter evaluation on consultant.