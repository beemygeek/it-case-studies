# IT Case Studies

Real problems from running IT for my own business and for a community nonprofit — written up in **Situation → Investigation → Action → Result** format. Client and organization names are omitted.

| # | Case study | Skills |
|---|---|---|
| 1 | [Checkout outage on a live e-commerce site](01-ecommerce-checkout-outage.md) | Incident response, root-cause analysis, verification |
| 2 | [Expired SSL certificate — same-day recovery at $0](02-ssl-certificate-expiry.md) | TLS/PKI, cPanel, Let's Encrypt, change planning |
| 3 | [Building a $0 Microsoft 365 help desk for a nonprofit](03-nonprofit-m365-helpdesk.md) | Microsoft 365, Power Apps, Teams, access control, documentation |
| 4 | ["Only one page looks wrong" — finding a hidden override](04-hidden-per-page-override.md) | Systematic troubleshooting, ruling out caching |
| 5 | [A "random" feature that wasn't random](05-database-random-ordering-bug.md) | SQL, debugging assumptions, testing a fix |
| 6 | [Cleaning up a site flagged as low quality](06-site-content-and-trust-cleanup.md) | Auditing, change control, recoverable changes |

## How I approach problems

1. **Reproduce it** and write down exactly what "broken" means.
2. **Check the evidence, not the assumption** — logs, config, the actual data.
3. **Change one thing at a time** and prefer reversible changes (trash, not delete; disable, not remove).
4. **Verify from the user's point of view** — e.g. load the page logged out, not as an admin.
5. **Document** what happened and how to prevent it.
