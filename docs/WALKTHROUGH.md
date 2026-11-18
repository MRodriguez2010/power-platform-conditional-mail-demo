# Walkthrough

1. Explain the business problem in one sentence: Prepare conditional messages with optional attachments, suppress previously contacted or prepared records, and hold uncertain or missing-attachment cases.
2. Show the source workbook(s) and the named table(s).
3. Open the native flow and show the input, validation/routing and receipt actions.
4. Run the seeded baseline with blank optional inputs, then inspect the output values.

| Record | Expected outcome |
|---|---|
| E001 | PreviewReady |
| E002 | PreviewReady |
| E003 | SuppressedAlreadyContacted |
| E004 | MissingAttachment |
| E005 | HoldUncertainOutcome |

This flow contains no email-send action. PreviewReady is recorded as Prepared only after its receipt is written; the real-contact count stays unchanged. A repeated run should suppress Prepared records. The sample supports one campaign per unique EmployeeId. Cross-flow writers and crash-safe exactly-once delivery are not implemented.

For certification, enter a new synthetic request ID and the required fields on one run. Use a later run’s certifier fields to submit Approve, Deny or Postpone against that same ID. These forms are practice interfaces in Power Automate; they are not separate Power Apps or identity-enforced approval screens. Inputs use revision 1. Repeated IDs do not append another intake row, but production edit/revision workflows are outside this sample.

For survey intake, a new ID adds one row; blank ID reprocesses saved rows. For mail, there are no input fields and no real sends.

If the live service is unavailable, show the captured native evidence and say it is a prior run. Do not describe a screenshot or local receipt check as a live execution.
