# LendKit — MVP Feature Spec

White-label **Lending-as-a-Service** platform. Lenders sign up, configure their workspace, build loan products and application forms, publish a borrower-facing link, receive applications, run automated checks (bank statement analysis + BVN credit check), route through their own configurable approval workflow, and disburse / collect.

Borrowers reach the platform through the lender's branded form, never see Solon-the-platform's name, and have their own portal to track and repay loans.

This is a side project — no compliance / regulatory features in scope.

Colour palette
Indigo + Off-white, with a single green accent.

Primary: Indigo #4F46E5 (or a touch deeper, #4338CA)
Background: Off-white #FAFAFA
Surface: White #FFFFFF
Text primary: Near-black #111827
Text secondary: Slate grey #6B7280
Border: Light grey #E5E7EB
Success accent: Green #10B981 (for approvals, paid loans, positive states)
Warning: Amber #F59E0B (overdue, attention)
Danger: Red #EF4444 (declines, defaults, errors)

Typography
Inter for everything.

Display / Headings: Inter, weights 600 (semibold) and 700 (bold)
Body: Inter, weight 400 (regular) and 500 (medium)
Numbers in tables / dashboards: Inter with font-variant-numeric: tabular-nums enabled
Code / IDs / references (transaction refs, loan IDs): JetBrains Mono, weight 400



---

## User roles

- **Lender Owner** — the person who signs up the lender account, has full control
- **Lender Staff** — any role the Owner creates (e.g., Junior Officer, Credit Analyst, Risk Manager, Admin) with custom permissions
- **Borrower** — end user who applies for a loan via a lender's published link
- **Platform Admin** — Solon-side super user (out of scope for borrower-facing flows)

Lender Staff roles are **fully customisable** — the Owner names them and configures the permission matrix per role.

---

## Module 1 — Lender Onboarding & Workspace

### Sign-up & verification

- As a Lender Owner, a user can sign up with name, business name, email, and phone number, and must verify both email (link) and phone (OTP) before accessing the workspace.
- A user will be able to upload an optional business identifier (CAC number, etc.) for their own records — the platform does not gate access on this for v1.
- A user must complete a short onboarding wizard: business type, expected loan volume, primary loan use case.

### Workspace branding

- As a Lender Owner, a user can configure their workspace: business display name, logo upload, primary brand colour, accent colour, and a custom subdomain (`yourbrand.solonlending.app` or similar).
- A user will be able to upload a favicon and a banner image for the borrower-facing application page.
- A user can preview how the borrower application page will look with their branding before publishing.
- The borrower-facing experience must never display Solon's platform name or logo — it is fully white-label.

### Team management

- As a Lender Owner, a user can **create custom roles** by name (e.g., "Credit Analyst", "Branch Manager") and configure a permission matrix per role with the following permission categories:
  - Loan products (view / create / edit / archive)
  - Forms (view / create / edit / publish)
  - Applications (view all / view assigned / comment / take workflow action)
  - Workflow actions per stage (configured per workflow, see Module 5)
  - Borrower data (view full / view masked / export)
  - Loans (view / disburse / record repayment / restructure / write off)
  - Team (view / invite / edit roles)
  - Settings (view / edit)
  - Reports (view / export)
- A user can invite staff by email, assign them a role, and the invitee must accept via email link and set their password.
- A user will be able to deactivate any staff member, which immediately revokes their session and reassigns any open applications they hold to a fallback (Owner or another staff member of the same role).
- A user can view a directory of all staff with their role, last active timestamp, and a count of applications currently assigned to them.

---

## Module 2 — Loan Products

### Product builder

- As an authorised staff member, a user can create a loan product with: product name, description (internal + borrower-facing), product type (Standard Loan / Buyover / Top-up), and status (Draft / Published / Archived).
- A user will be able to configure loan terms: minimum and maximum principal (₦), tenor options (in days / weeks / months), interest rate (flat % or reducing % monthly), processing fee (flat ₦ or % of principal), late payment fee structure, and acceptable repayment frequencies (one-time / weekly / monthly).
- A user can set eligibility hard-stops: minimum age, maximum age, employment status filter, minimum monthly income, maximum existing debt obligations, BVN required (yes/no), bank statement required (yes/no).
- A user must attach an **application form** (built in Module 3) and a **workflow** (configured in Module 5) before a product can be published.

### Buyover product type

- As a user creating a Buyover product, a user can add buyover-specific fields to the form: existing lender name, outstanding balance, monthly repayment amount, and proof of existing loan (file upload).
- The platform does not automate buyover settlement in v1 — the lender handles existing-lender settlement outside the platform and records it as a manual note on the loan after approval.

### Top-up product type

- As a user creating a Top-up product, a user can restrict it to borrowers who have at least one active loan on the platform with this lender.
- A user will be able to set top-up rules: maximum top-up as % of original principal, minimum % of original loan that must be repaid before top-up is allowed.

### Publishing

- As an authorised staff member, a user can publish a product, which generates a **unique shareable application link** and an embeddable widget snippet.
- A user will be able to copy the link, generate a QR code, or copy WhatsApp / SMS share text with the link pre-populated.
- A user can unpublish or archive a product at any time — archived products stop accepting new applications but existing applications continue through their workflow.

---

## Module 3 — Form Builder

### Building forms

- As an authorised staff member, a user can create application forms attached to a loan product, using a drag-and-drop or list-based builder.
- A user will be able to add fields of these types in v1:
  - Short text
  - Long text
  - Number (with optional ₦ formatting)
  - Date
  - Single-choice dropdown
  - Multi-choice checkbox
  - Yes/No toggle
  - Phone number (auto-validated for Nigerian formats)
  - Email
  - BVN (auto-validated for 11 digits)
  - File upload (PDF, JPG, PNG, with size cap configurable per field, max 10MB)
  - Bank statement upload (special field — triggers Module 4 analysis)
  - Section header / instructional text
- A user can mark any field as required or optional, add help text, and add basic validation rules (min/max length, regex pattern, file type restriction).
- A user will be able to reorder fields, group them into sections, and preview the form as a borrower would see it.

### Form logic (light)

- As a user building a form, a user can configure simple conditional visibility — "show field X only if field Y equals Z."
- A user cannot build branching logic, calculations, or multi-page conditional flows in v1 — only single-condition show/hide.

### Form versions

- As a user, a user can edit a published form, but in-flight applications remain on the form version they submitted with.
- A user will be able to view past form versions and which applications used which version.

---

## Module 4 — Borrower Application Flow

### Application submission

- As a Borrower, a user accesses the lender's published link and sees the branded application page with the lender's logo, colours, and product description.
- A user can start an application without creating an account — only basic identifiers (full name, phone, email, BVN) are collected up front to enable later sign-in.
- A user will be able to fill out the configured form, upload required documents, and submit.
- A user must complete a phone OTP verification before final submission.
- A user can save progress and resume later via a link sent to their email or phone.
- After submission, a user receives a confirmation with a tracking reference and a link to the Borrower Portal.

### Bank statement upload & connection

- As a Borrower, if the form requires a bank statement, a user can either:
  - **Upload a PDF statement** (must be at least 3 months, max 12 months)
  - **Connect their bank account** via an integration (Mono or Okra) to pull statements directly
- A user will be able to upload multiple bank statements if they have accounts at different banks.
- A user must consent to the lender accessing and analysing the statement before submission.

### BVN consent

- As a Borrower, if the form requires a BVN, a user must enter their BVN and explicitly consent to the lender running a credit bureau check.
- A user will be shown a plain-language explanation of what the credit check involves before consenting.

### Borrower Portal

- As a Borrower, a user can sign in to a Borrower Portal using their phone number + OTP (no password in v1).
- A user will be able to see all applications they've submitted across all lenders using the platform (filtered by lender to maintain white-label separation in the UI).
- A user can view their current application status using **generic stages only**: Submitted → Under Review → Decision Made (Approved / Declined).
- A user must not see internal workflow stages, internal notes, or staff names — only the generic public-facing status.
- The Lender Owner can **customise the wording** of the four generic borrower-facing statuses (e.g., "Under Review" can be renamed to "We're reviewing your application").

---

## Module 5 — Workflow Engine

This is the configurable approval / rejection routing layer. Every loan product is attached to a workflow.

### Workflow builder

- As an authorised staff member, a user can create a workflow with a sequence of **stages**, where each stage has:
  - A name (e.g., "Pre-screening", "Credit Analysis", "Final Review")
  - A stage type: **Review** (human action required), **Automated** (system runs check), **Borrower** (sent back to borrower for info), or **Decision** (terminal)
  - One or more assigned roles (any staff with this role can pick up applications at this stage)
  - Available actions for staff at this stage (configured per role)
  - Optional SLA in hours (after which the application is flagged as overdue)
- A user will be able to add, remove, and reorder stages. Workflows are linear in v1 — no conditional branching.
- Every workflow must end with a **Decision stage** that produces either Approved or Declined.

### Actions available at Review stages

- As a staff member viewing an application at a Review stage, a user can take one of these actions (subject to role permissions):
  - **Forward to next stage** (with optional internal note)
  - **Send back to a previous stage** (with required reason)
  - **Request info from borrower** (the application leaves staff queues and goes back to the borrower with a specific question; re-enters the same stage when borrower responds)
  - **Decline outright** (skips remaining stages, goes to Declined — only if role has decline-authority at this stage)
  - **Approve outright** (skips remaining stages, goes to Approved — only if role has approve-authority at this stage)
  - **Add internal note** (no state change, supports @mentions of other staff)

### Automated stages

- As a user configuring a workflow, a user can insert Automated stages that run: BVN credit check, bank statement analysis, eligibility hard-stop check, or a combination.
- A user will be able to set the auto-pass criteria (e.g., "auto-decline if credit score below 400", "auto-flag for senior review if average monthly income below stated income by 30%").
- An Automated stage that fails its criteria must either auto-decline or route to a configured fallback stage — never silently pass.

### Decline workflows

- As a user, a user can configure decline workflows separately — declines can either be terminal (single click, done) or routed (a Junior Officer flags decline → Senior Officer confirms → Final decline issued).
- A user will be able to attach a required reason code from a configurable list (Insufficient Income, Failed Credit Check, Incomplete Documents, Suspected Fraud, Other) plus a free-text note.

### Workflow versioning & integrity

- As a user, a user can edit a workflow, but applications already in-flight continue on the version they were submitted under.
- A user will be able to view all past versions of a workflow and which applications used which version.
- A user cannot delete a workflow that has any applications in-flight under it — only archive it.

### Application assignment

- As a staff member with the appropriate role for a stage, a user will see all applications waiting at that stage in their queue (unassigned pool + any specifically assigned to them).
- A user can claim an application (it becomes assigned to them, removing it from peers' queues), unclaim it (returns to the unassigned pool), or reassign to another staff member with the same role.
- A user must see an SLA indicator on every application showing time-since-stage-start vs the stage's SLA.

---

## Module 6 — Bank Statement Analysis

### Ingestion

- The system must accept bank statements via PDF upload (parsed) or direct bank connection (Mono / Okra integration in v1, one provider chosen).
- The system must support all major Nigerian banks supported by the chosen provider, with manual PDF fallback for unsupported banks.
- The system must reject statements shorter than 3 months and warn on statements older than the most recent full month.

### Analysis output

- As a staff member viewing an application, a user can see an automated **Bank Statement Analysis** card with:
  - **Income detection**: detected salary credits, business income credits, other recurring credits, with confidence score and frequency
  - **Average monthly inflow** (last 3 / 6 / 12 months)
  - **Average monthly outflow** (last 3 / 6 / 12 months)
  - **Closing balance trend** (line chart)
  - **Recurring debits** (existing loan repayments detected, subscriptions, utilities) with monthly total
  - **Bounced cheques / failed direct debits** count and dates
  - **Days in negative / overdrawn** count
  - **Behavioural flags**: gambling-related debits, suspected loan-stacking (multiple lender debits), large unexplained inflows, salary timing irregularity
  - **Affordability summary**: estimated disposable income after recurring obligations
- A user will be able to drill down into any flagged item to see the underlying transactions.

### Manual override

- As a staff member, a user can manually correct any analysis classification (e.g., reclassify a transaction labelled "gambling" as "transfer to family") and the system must log the override in the audit trail.

---

## Module 7 — BVN Credit Check

### Pulling the check

- The system must pull a credit report from one credit bureau in v1 (CRC, CreditRegistry, or FirstCentral — single integration chosen during build).
- The pull is triggered either automatically at an Automated workflow stage or manually by a staff member with the appropriate permission.
- A user will be able to see the cost of each pull (configured per lender — pass-through or absorbed by Solon at platform level).

### Display

- As a staff member, a user can view a **BVN Credit Check** card showing:
  - Borrower full name, DOB, and gender as returned by the bureau (reconciled against application form data with mismatch flag)
  - Credit score (where bureau provides one)
  - Existing credit facilities (count, total balance, total monthly obligation)
  - Active facilities with current arrears status per loan
  - Closed / settled facilities count
  - Any reported defaults or write-offs with dates
  - Number of bureau enquiries in the last 30 / 90 / 180 days (signals loan-shopping behaviour)
- A user will be able to download the raw bureau report PDF for record-keeping.
- A user must see a clear indicator if the bureau returned no record for the BVN.

---

## Module 8 — Decisioning & Disbursement

### Application detail view

- As a staff member with an application at any stage, a user can see a single unified application view showing:
  - Borrower details and submitted form responses
  - Bank Statement Analysis (Module 6)
  - BVN Credit Check (Module 7)
  - Workflow timeline (every action taken, by whom, when, with notes)
  - Available actions for this stage (based on role permissions)
  - Internal comments thread (@mentions notify other staff)
- A user will be able to view supporting documents (bank statements, ID uploads, etc.) inline.

### Approval

- As a staff member at the final Decision stage with approval authority, a user can approve an application, which must require confirming:
  - Final approved principal (defaults to requested, editable within product limits)
  - Final approved tenor (defaults to requested, editable within product limits)
  - Final interest rate (defaults to product rate, editable if role permits)
  - Disbursement account (defaults to borrower's primary account from statement, editable)
- A user will be able to attach an approval note that becomes part of the loan record.
- On approval, the borrower must receive an email + SMS notification with the loan terms and a link to accept.
- The borrower must explicitly accept the offer (one-click confirmation in the Borrower Portal) before disbursement is triggered.

### Disbursement (v1 = pass-through)

- As a Lender Owner, a user can connect a payment processor (Paystack or Flutterwave) for disbursement, OR mark disbursement as **manual** (the lender pays out from their own bank and records the disbursement on the platform).
- For pass-through disbursement, the platform must trigger the transfer via the lender's connected processor on borrower acceptance.
- For manual disbursement, a staff member must record: amount disbursed, date, reference, and upload proof of transfer.
- On disbursement, the loan moves to status **Active**.

### Decline

- As a staff member at a Decision stage with decline authority, a user can decline an application, which must require selecting a reason code and optionally adding a note.
- A user can choose whether the borrower sees the reason code or a generic decline message (default: generic message, lender can override per product).
- On decline, the borrower receives a notification matching the lender's configured wording.

---

## Module 9 — Active Loans & Repayment

### Loan ledger

- As a staff member with loan-view permission, a user can see all active loans with: borrower name, principal, outstanding balance, status (Active / Overdue / Paid Off / Written Off / Restructured), next repayment date, next repayment amount.
- A user will be able to drill into any loan to see: full repayment schedule, repayments received, repayments missed, accrued interest, accrued fees.

### Repayment collection (v1)

- The platform must support these repayment methods in v1:
  - **Borrower-initiated card payment** via Paystack / Flutterwave checkout in the Borrower Portal
  - **Direct debit mandate** via Mono / Paystack mandates set up at borrower acceptance, auto-debited on schedule
  - **Manual repayment recording** by lender staff (lender received cash / transfer outside the platform, records it manually with reference)
- A user will be able to mark any payment as cleared, pending, or failed, with auto-update from payment processor webhooks for automated methods.

### Overdue handling

- The system must automatically mark a loan as Overdue when a scheduled repayment is missed by more than 24 hours past due date.
- As a staff member, a user can see an overdue queue with days-overdue, amount-overdue, and last-contact-date.
- A user will be able to log communication attempts (call, SMS, email, WhatsApp) with notes — no automated dunning in v1.

### Borrower-side repayment

- As a Borrower, a user can see their active loan(s) in the portal with outstanding balance, next due amount, next due date, full schedule, and payment history.
- A user will be able to make a repayment from the portal using card or transfer (one-off or against the schedule).
- A user can request an early full payoff and see the payoff amount inclusive of any early-settlement adjustments configured by the lender.

### Top-up & restructuring (v1 = manual)

- As a Borrower, a user can request a top-up if the lender has a Top-up product published and the borrower qualifies — this creates a new application under the Top-up product.
- As a staff member, a user can manually restructure an active loan (change tenor, defer payments, adjust schedule) — this requires the appropriate permission and triggers an audit-trail entry. No automated restructure workflow in v1.

---

## Module 10 — Notifications & Audit

### Notifications

- The system must send notifications via:
  - **Email** (transactional — application received, decision made, repayment due, repayment received, payment failed)
  - **In-app dashboard** (staff queue alerts, @mentions, application stage changes, SLA breaches)
- SMS and WhatsApp are deferred to v2.
- As a staff member, a user can configure their personal notification preferences per category (email on/off, in-app on/off).
- As a Lender Owner, a user can customise the wording and sender name on all borrower-facing email templates.

### Audit trail

- The system must log every state-changing action: application submitted, stage entered, action taken (forward / decline / approve / send-back / request-info), assignment changes, document uploads, bureau pulls, statement uploads, disbursements, repayments, loan-record edits.
- Each log entry must include: actor (user or system), timestamp, action type, before/after state where relevant, and any associated note.
- As a staff member with audit-view permission, a user can view the full audit trail for any application or loan as a timeline.
- A user will be able to export the audit trail for any application or loan as CSV / PDF.

### System audit log

- A separate platform-level log must record: lender account changes, role and permission changes, integration connection/disconnection events, login events, and any failed authorisation attempts.
- The Lender Owner can view this log for their workspace.

---

## Cross-cutting MVP requirements

- The platform must be **fully responsive** — borrower flow is mobile-first (most Nigerian borrowers will use phones); lender dashboard works on desktop and tablet.
- The platform must operate on **2G/3G connections** for the borrower flow, with offline form-progress saving and resume.
- All file uploads must be virus-scanned before being made available to staff.
- All borrower PII (BVN, bank statements, ID documents) must be encrypted at rest.
- Every lender's data is logically isolated — no cross-lender data leakage at the borrower portal, application, or analytics level.
- The platform must support a single currency (₦) in v1 — multi-currency deferred to v2.
 & analytics dashboards beyond basic counts (v1 has lists + filters; rich reporting is v2)