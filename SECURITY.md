# Security

## Reporting a weakness

Write to **support@snns.dev** with the subject "Security report", or choose *A security report* on
[noetic.lol/support](https://noetic.lol/support). Reports go to a queue only the owner and admins can open.

Please include: what you found, where, how to see it again, and what you think it lets someone do. Do not put the
details in a public GitHub issue.

## What we ask

- Test only against your **own** account and your own data.
- Stop at proof. If you can read something that is not yours, show that you could and go no further.
- No floods, no load tests, no automated scanning. The service shuts out addresses that scan or flood, automatically,
  for seven days, and reports them. If you want to test seriously, write first and say which address you will use.
- No social engineering of S&NS staff or other users, and no physical attacks.
- Give us a reasonable time to fix a problem before you talk about it publicly.

## What you can expect from us

- An answer from a person, usually within a few days.
- Credit, if you want it, when the fix is out.
- We will not pursue someone who found a problem in good faith, kept to the points above, and told us about it.

There is no paid bounty at the moment. We say so plainly so nobody spends a week expecting one.

## In scope

`noetic.lol` and the Noetic Suite Windows app. The other S&NS projects take reports at the same address; say which
project it is about.

## Out of scope

- Findings that need a device that is already compromised, or a browser years out of date.
- Missing headers or settings with no shown consequence.
- Anything on the addresses that exist only as decoys. They are there to be found by scanners; finding them is not a
  finding.
- Third-party services we use. Report those to them.

## Joining the red team

We sometimes ask people who report well to test with us, with an agreed scope and an address that will not be shut
out. Say so in your report if you are interested.

## What protects your account

- Passwords are stored as salted scrypt hashes. Secrets and what you write to support are encrypted at rest.
- You can add an authenticator app and passkeys (user menu → *Sign-in and security*).
- Staff accounts are bound to their own devices, every staff action is recorded, and reaching for something above a
  role is flagged to the owner automatically.
