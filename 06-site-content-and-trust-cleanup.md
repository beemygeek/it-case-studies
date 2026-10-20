# 6. Cleaning up a site flagged as low quality

**Environment:** WordPress/WooCommerce storefront, ~1,000 products, ad-network application

## Situation
The site's application to an advertising network was rejected for **"low value content."** The rejection notice gave no specifics.

## Investigation
Audited the live site the way a reviewer would, instead of guessing:
- **21 of 24 blog posts were leftover theme demo content** — vacation rentals, motorcycle auctions, a "Hello world!" post, fake demo comments — completely unrelated to the business.
- A **dead product card** on the homepage linked to an item that no longer existed (404).
- **Duplicate product categories** in the shop filters and dozens of **mangled product titles** imported verbatim from a supplier feed (cut off mid-sentence, stray quotes).
- Product descriptions were copied directly from the supplier feed — identical to every other reseller.

## Action
- Moved all demo posts to **Trash** (recoverable) rather than permanently deleting; kept the genuine posts.
- Removed the dead homepage card.
- Merged duplicate categories and reassigned their products; fixed malformed titles catalog-wide.
- Rewrote descriptions with original copy; items that couldn't be described accurately were set to Draft rather than deleted.
- Published new, original educational content relevant to the business.
- Verified every change logged out, then requested re-review.

## Lessons
- Audit the system from the reviewer's/user's perspective.
- Favor **reversible** changes and keep a record of exactly what changed — one bulk action briefly trashed three real posts along with the demo content; because nothing was permanently deleted, they were restored in minutes.
