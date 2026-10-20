# 2. Expired SSL certificate — same-day recovery at $0

**Environment:** Business website on shared hosting with cPanel

## Situation
Visitors started getting a full-page browser security warning. The site's paid SSL certificate had **expired**, which blocks most visitors, hurts search ranking, and breaks payment trust.

## Investigation
- Confirmed the expiry date and issuer from the browser certificate viewer.
- Compared options: renew the paid certificate (recurring cost) vs. a free **Let's Encrypt** certificate (90-day validity, same browser trust for a domain-validated site).
- Checked the host: this shared plan did **not** offer automatic Let's Encrypt renewal, so any free cert would need a manual renewal process.

## Action
- With the owner's decision, issued a Let's Encrypt certificate for the domain and installed it through cPanel's SSL/TLS manager (certificate, private key, CA bundle).
- Verified the full chain from an external checker and in multiple browsers, and confirmed HTTP → HTTPS redirects still worked.
- Documented the renewal procedure and scheduled a reminder well before the 90-day expiry.

## Result
Warning gone the same day; certificate cost reduced to **$0/year**.

## Lessons / prevention
- Certificate expiry is a **monitoring** problem, not a technical one — track expiry dates for every domain.
- When automation isn't available, a written procedure + calendar reminder is the control.
