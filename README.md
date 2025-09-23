<p align="center">
# osticket-lifecycle-examples
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Ticket Lifecycle: Intake Through Resolution</h1>

This guide walks you through a complete ticket lifecycle in **osTicket** from intake to resolution. You’ll play the roles of the **end user** and the **three agents** you created earlier. Each step includes a short note on **why it matters**. We will not be able to perform the actual work but we will act as if we did.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

## Table of Contents
- [Overview — Support Center](#overview--support-center)
- [Overview — Agent Panel](#overview--agent-panel)
- [STEP 1 — Create a Ticket (End-User)](#step-1--create-a-ticket-end-user)
- [STEP 2 — View the Ticket (Agent)](#step-2--view-the-ticket-agent)
- [Ticket Status — Resolved vs Closed](#ticket-status--resolved-vs-closed)
- [Ticket 1 — Account Issues → Password Reset](#ticket-1--account-issues--password-reset)
- [Ticket 2 — Report a Problem → Hardware](#ticket-2--report-a-problem--hardware)

---

## Open two windows
  1. **Agent/Admin Panel:** `http://localhost/osTicket/scp/login.php`  
  2. **Support Center (End-User Portal):** `http://localhost/osTicket/`<br />

---

## Overview — Support Center
The **Support Center** is the web portal where users submit and track tickets.

<p>
<img width="837" height="482" alt="0 0 user interface" src="https://github.com/user-attachments/assets/b7ad4b17-462c-4118-8c02-5f4cc1724d11" />
</p>

**Why this matters:** It’s the **intake** channel. The **Help Topic** chosen here can auto-set **Priority** and **SLA**, affecting routing and due dates.

---

## Overview — Agent Panel
Agents use the **Agent Panel** for day-to-day ticket work.

**What agents can do**
- View/create/manage tickets, reply to users
- Assign/transfer to **Departments**, **Teams**, or **Agents**
- Track **Status**, **Priority**, **SLA**, **Due** dates
- See user info and ticket history
- Add **internal notes** for collaboration
- Use **Help Topics** and **Canned Replies** for consistency

**Why this matters:** This is where you **triage, communicate, and drive resolution** (system configuration is in the Admin Panel).

---

## STEP 1 — Create a Ticket (End-User)

- From the Support Center home page click **Open a New Ticket** → enter **Email** and **Name** → select a **Help Topic** → fill **Summary** and **Description**.

<p>
<img width="836" height="924" alt="0 1 create a ticket" src="https://github.com/user-attachments/assets/1726b511-60b3-44c4-8799-6403fe8fcba6" />
</p>

**Why this matters:**
- Help Topics can **auto-apply Priority/SLA** (e.g., “Business Critical Outage” → Emergency/P1).  
- Users often choose the **wrong** topic. Agents should review details and **reclassify** topic/priority/SLA when needed. If you lack permissions, escalate to a supervisor/admin and **document** your reasoning in the ticket.

---

## STEP 2 — View the Ticket (Agent)

- Log in to the **Agent Panel** and find the ticket. The list view shows **Last Updated, Subject, Requester, Priority, Assignee**.

<p>
<img width="954" height="372" alt="0 2 view ticket as agent" src="https://github.com/user-attachments/assets/36166834-556a-4583-9d57-bf239ff1b7b1" />
</p>

- Open the ticket to see **Status, Priority, Department, SLA, Due**, and the **conversation thread**.

<p>
<img width="956" height="905" alt="0 3 view ticket details" src="https://github.com/user-attachments/assets/7daf0d72-59a9-4f26-94c5-9a2a65928aba" />
</p>

**Why this matters:**
- Agents validate **topic/priority/SLA**, gather missing info, and **document** all actions.  
- If details are unclear, contact the requester, ask specific questions, and record interactions in **internal notes**.

---

## Ticket Status — Resolved vs Closed

- Resolved → Solution provided; ticket can reopen if the user replies (often auto-closes after N days).
- Closed → Final; no further action expected (users typically cannot reopen).
- Tip: Use Resolved when you want a short feedback window; use Closed when it’s definitively done.

---

## Ticket 1 — Account Issues → Password Reset
Password resets can apply to many services (e.g., Microsoft 365/Email/Teams, VPN, Wi-Fi, CRM/ERP). We’ll keep this **generic**.

- First lets create a ticket as the **End-User (Support Center)**  
Submit: *“Forgot password, need password reset.”*  
**Help Topic:** `Account Issues / Password Reset`

<p>
<img width="835" height="684" alt="ticket 1 0 submit" src="https://github.com/user-attachments/assets/3ab2340f-5989-48e8-aa84-dab28372d5fc" />
</p>

- Next lets login as your Tier 1 Agent:
**Agent (Tier 1) → Check auto-routing**

<p>
<img width="953" height="356" alt="ticket 1 1 login agent" src="https://github.com/user-attachments/assets/309a4cff-0c81-47d1-8540-cb6e99c397f0" />
</p>

- Dept **Help Desk** → Team **Accounts & Passwords** → Priority **Normal** → SLA **P3**

<p>
<img width="955" height="268" alt="ticket 1 2 confirm routing" src="https://github.com/user-attachments/assets/d31f7e5a-937d-45da-89c3-f14ac12fb343" />
</p>

### Resolution Steps

**1) Verify identity (before any changes)**
- Callback to **phone-on-file** (directory/HRIS), or  
- **Manager approval** from corporate mailbox, or  
- Authenticated **portal** challenge (user confirms a known, non-sensitive detail), or  
- In-person **badge** check  
- For higher risk, require **two** strong factors. **Never** rely on caller ID/SMS alone.

Add an **Internal Note** (example):
- Identity verified via callback to phone-on-file and employee ID.

<p>
<img width="948" height="336" alt="ticket 1 3 verify" src="https://github.com/user-attachments/assets/a665535f-9099-418f-b487-93fe6b52ce67" />
</p>

**2) Check state (no changes yet)**
- Directory status: Enabled/Locked? Password Expired?
- Recent failed sign-ins?
- MFA status (lost/stolen device? re-register needed?)

**3) Reset / clear lock**

- Unlock if locked
- Reset password per policy (temporary; force change on next sign-in if required)
- If MFA device is lost, remove old factor(s) so the user can re-register

Add an **Internal Note** (example):
- Actions: Cleared lockout; set temporary password (communicated verbally).

<p>
<img width="948" height="380" alt="ticket 1 4 actions" src="https://github.com/user-attachments/assets/5ec7dbcb-1220-46b2-bf6d-610dbb0c2408" />
</p>


**4) Live test with the user**

- User signs in; if MFA was reset, guide MFA re-registration
- Optionally confirm email/Teams/SSO/VPN

**5) Closeout**

Add a **Public Reply** (example):
- Per our call at 2:35 PM ET, we reset your password and confirmed sign-in. If anything stops working, just reply to this email and we’ll reopen the ticket.

<p>
<img width="947" height="503" alt="ticket 1 4 final reply" src="https://github.com/user-attachments/assets/dc0bb3b6-e92e-4956-989f-0f713fd65957" />
</p>

**Finishing: Set Status to Resolved (reopen allowed) or Closed (final), per policy.**

---


## Ticket 2 — Report a Problem → Hardware

- First lets create another ticket as the **End-User (Support Center)**  
Submit: *“Recently moved to a new office; now my laptop won’t turn on.”*  
**Help Topic:** `Report a Problem / Hardware`

<p>
<img width="822" height="671" alt="ticket 2 0 submit" src="https://github.com/user-attachments/assets/1a5e5792-72bb-4b33-8c04-14ff2e110320" />
</p>

- Next lets login as your Tier 1 Agent:
**Agent (Tier 1) — Check auto-routing**

<p>
<img width="950" height="333" alt="ticket 2 1 login agent" src="https://github.com/user-attachments/assets/371b12c5-8d58-4bac-8623-c91860a37e08" />
</p>

- Dept **Help Desk** → Team **PC Fix** → Priority **Normal** → SLA **P3**

<p>
<img width="955" height="264" alt="ticket 2 2 confirm routing" src="https://github.com/user-attachments/assets/567fde11-921a-41f3-a8a9-5818e0ee22b1" />
</p>

### Resolution Steps

**1) Identity/ownership check (risk-based)**
- Light: reply from corporate email or asset tag + desk location
- Strong (for swaps/data access): callback to phone-on-file and badge/manager approval

Add **Internal Note** (example):
- Identity verified via in-person badge check.

<p>
<img width="947" height="278" alt="ticket 2 3 verify" src="https://github.com/user-attachments/assets/4238b682-7810-4e46-8dc6-919c631e2408" />
</p>

**2) Power path & basics (laptop/desktop)**
- Different outlet/strip; check AC adapter LED (use correct-wattage, known-good adapter)
- Battery reset (if applicable); hold power 30s
- Bypass dock (fully disconnect USB-C/power/video), power laptop directly
- Desktop: PSU switch I/0, power cable, beeps/LEDs

**3) Display & POST**
- External monitor input/cable/port; Fn display toggle
- Vendor logo/POST? Beep codes?
- BIOS/UEFI reachable? Is SSD/HDD detected?

**4) Decide: hardware vs OS**

- No lights/fans/POST ⇒ likely hardware
- Repair loop/BSOD ⇒ likely OS/image/driver

Add **Internal Note** (example):
- Bypass: USB-C from dock fully disconnected. OEM 130W barrel adapter direct to laptop → powers on and POSTs OK.
Assessment: Failed dock (WD19); user needs external display/power via dock.
Action: Created Task → Maintenance to replace dock.

<p>
<img width="948" height="446" alt="ticket 2 4 actions" src="https://github.com/user-attachments/assets/85195360-578d-4b8b-ac0b-a873880a4abd" />
</p>

**5) Create Task → Maintenance (onsite hardware/peripheral)**

```text
Title: Onsite: Replace dock
Description (template):

User: Karen (5E-112) | Callback (ending **3045**)
Ticket: #828576
Device: Laptop | Asset: LPT-09341 | Dock model: Dell WD19

Symptom:
- Laptop does not power on when connected via dock.

Remote triage:
- Disconnected USB-C from dock.
- Connected OEM 130W barrel adapter directly to laptop → powers on and POSTs OK.

Diagnosis:
- Failed dock (Dell WD19). Replacement required to restore external display, charging, and USB peripherals.

Bring:
- Replacement WD19 dock, 130W PSU, DisplayPort cable.

Window:
- 10:00–12:00 or 14:00–16:00
```

<p>
<img width="744" height="629" alt="ticket 2 5 task" src="https://github.com/user-attachments/assets/3fdb0406-1072-4bc7-b8fd-97183e6bb422" />
</p>

**Include: user name/location, asset/serial, symptoms, steps tried, photos (if helpful), diagnosis, what to bring, and an access window.**

**6) Maintenance works the Task**
- Log out of **Agent (Tier 1)** profile and log into the **Maintenance Technicians** profile. Click on **Tasks** tab and view the task.

<p>
<img width="953" height="354" alt="ticket 2 6 view task as maintenance worker" src="https://github.com/user-attachments/assets/9e2481b7-cf0b-4ebd-8019-906cd2ba9874" />
</p>

**Maintenance workers expected steps:**
- Test with spare adapter/dock; check power LED
- Brief hardware diagnostics (if it powers)
- If still no power → device swap per SOP; capture new asset

Add Maintenance **Close Task** Note (example):

- Replaced dock (Dell WD19). Laptop powers on; passes POST/boot.
Task closed. User confirms normal operation.

<p>
<img width="642" height="306" alt="ticket 2 7 close task and post internal note" src="https://github.com/user-attachments/assets/c913093e-5a1d-415b-b399-21dfe6286b1a" />
</p>

**7) Help Desk closes the Ticket**
- Log out of **Maintenance Technicians** profile and log into the **Agent (Tier 1)** profile. Add a closing public reply and then close the ticket.
Post a short public wrap-up, then close.

Add a **Public Reply** (example):

- We replaced your desk dock and confirmed your laptop powers on, boots, and the external display works.
If anything regresses, just reply here and we’ll reopen the ticket.


Add an **Internal Closing Note** (example):

- Replaced dock (Dell WD19). Laptop powers on; passes POST/boot.
Task closed. User confirms normal operation.

<p>
<img width="642" height="306" alt="ticket 2 7 close task and post internal note" src="https://github.com/user-attachments/assets/01f61d7b-bc65-471b-a79c-8bde3eec8a64" />
</p>


**Why this matters:** Tickets remain owned/closed by Help Desk (single point of accountability). Tasks track onsite work separately for Maintenance.



<br />
