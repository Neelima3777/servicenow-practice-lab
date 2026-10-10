# Task 01: Add resolution details to the "Incident resolved" email

## Ticket
**INC0045 (P2):** Users said the "Incident resolved" email didn't show the resolution notes, so they had to open the ticket to see what was fixed.

## Analysis
- The email is sent by the out-of-box **Incident resolved** notification (Incident table, sent to the Caller when the state changes to Resolved).
- It uses the shared **Employee notification template**, but has its own **Message HTML**, which overrides the template's message. So I changed only this notification, and other emails using the template weren't affected.
- The notification is an out-of-box, "High Risk" record. Customizing it means it becomes a skipped record during upgrades, which I documented. This change was required by the client.

## Solution
Added two lines to the notification's Message HTML:
```
Resolution code: ${close_code}
Resolution notes: ${close_notes}
```

## Testing
Used **Preview Notification** with a resolved incident. The email now shows the resolution code and notes under the title.

## Lessons learned
- Check whether a template is shared before editing it.
- Always confirm the current update set before starting work. My change first landed in the Default update set, and I moved it into the task's own update set.
