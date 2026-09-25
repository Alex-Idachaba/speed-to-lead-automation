# Speed-to-Lead Automation

**Pattern:** Routing · **Stack:** n8n, Gmail API (send + threading) · **Status:** Complete (tested with sample leads)

Replies to every new inquiry within minutes with a personalized email and qualifying questions, then matches each reply back to the right conversation, so no lead waits until Monday for a response.

**Property management application:** rental inquiries and property-owner inquiries answered instantly, day or night, with qualifying questions already asked before your team steps in.

---

## The problem

Leads contacted within minutes convert far better than leads that wait hours, but most small teams can't staff an inbox around the clock. An inquiry sent after hours usually waits until the next business day, and by then the lead has often moved on.

## How it works

**Workflow 1:** new lead → personalized first-touch email with qualifying questions

**Workflow 2:** incoming reply → match to lead by Gmail threadId → capture qualifying answers → hand off to the team

- The first workflow fires the moment a lead arrives and gathers the information a person would normally ask for on a first call.
- The second workflow handles replies independently, matching each one to its originating lead using Gmail's `threadId`.

## Workflow structure

- **Workflow 1:** Lead Intake & First-Touch Reply
- **Workflow 2:** Reply Matching & Qualification

The two workflows are decoupled, so a delay or failure in reply handling never blocks new leads from getting their first response.

## Reliability

| Rung | How it shows up |
|---|---|
| Idempotency | Replies are matched by `threadId`, not by message order or timing, so they always attach to the correct lead |
| Decoupling | Intake and reply handling run independently, so one can't stall the other |

## Repository contents

- n8n workflow exports (JSON), one per workflow
- Workflow screenshots

## Running it yourself

1. Import both workflow JSON files into n8n.
2. Create a Gmail OAuth credential in n8n. Credentials are **not** included in the exports.
3. Connect Workflow 1's trigger to your lead source (form, webhook, or inbox).
4. Edit the first-touch email and qualifying questions for your business.
5. Send a test lead and reply to the email to confirm threading works.

## Limitations

- Email only. SMS follow-up is not implemented in this build.
- Qualifying questions are fixed per deployment, not adapted per lead.

---

Built by [Alex Idachaba](https://alexidachaba.com) — AI automation for property management operations.
