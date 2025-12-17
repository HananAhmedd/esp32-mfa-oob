# Authentication Logic Flow (Design B: Approval-based)

## States (User Session)
- LOGGED_OUT
- PENDING_MFA
- AUTHENTICATED

## Enrollment (Pairing) – one-time
1. User logs in normally.
2. User starts device enrollment.
3. ESP32 is registered as the trusted approval device for the user.

## Login Flow – every login
1. User enters username + password on the web app.
2. If password is correct, server creates a login challenge with status = PENDING.
3. User is redirected to a waiting page (PENDING_MFA).
4. Out-of-band page shows the pending request.
5. User approves using ESP32.
6. Serial bridge forwards approval to the server endpoint.
7. Server marks challenge as APPROVED.
8. Waiting page detects approval and login becomes AUTHENTICATED.

## Challenge States
- PENDING → APPROVED
(optional later: DENIED / EXPIRED)