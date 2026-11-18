# Isolated Outlook delivery test

The reusable imported flow remains preview-only. For the owner-approved delivery check, a separate manual copy of the connected seed retained its Excel read and SharePoint connection-check write, then appended two Office 365 Outlook **Send an email (V2)** actions.

1. Use only an explicitly authorized test mailbox. Connect Office 365 Outlook with the intended account.
2. Set the first action To to that mailbox, Subject to `[SYNTHETIC DEMO 1/2] No attachment`, and a body identifying the message as a synthetic test with no employee, customer or benefits data. Leave attachments empty.
3. Set the second action To to the same mailbox, Subject to `[SYNTHETIC DEMO 2/2] Harmless text attachment`, and a synthetic-test body. Add attachment Name `demo-action-guide.txt` and ContentBytes containing base64 of the exact file in `fixtures/`. Configure run-after Succeeded on the first action.
4. Set Settings → Retry policy → None on both send actions. Save and inspect code view: attachments must be a Name/ContentBytes array. No other recipients, CC or BCC were configured.
5. After explicit authorization for both messages, run once. If a send has an uncertain result, inspect the mailbox and run history before attempting anything else.
6. Confirm both action statuses and received messages, including attachment flags. Turn the isolated test flow Off afterward.

The recorded test used this UI configuration and succeeded. No portable export of this separate test is included. The production concerns of delivery reconciliation, per-campaign keys, contention and crash recovery remain design work; the preview flow does not claim to solve them.

[Microsoft Office 365 Outlook connector](https://learn.microsoft.com/en-us/connectors/office365/)
