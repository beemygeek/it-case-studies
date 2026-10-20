# 1. Checkout outage on a live e-commerce site

**Environment:** WordPress + WooCommerce store, ~1,000 products, shared hosting

## Situation
Customers could browse and add items to the cart, but the **Cart and Checkout pages returned errors**. Every attempted purchase failed — a full revenue outage that nobody had noticed from the storefront's homepage.

## Investigation
- Reproduced it as a logged-out shopper: add to cart → cart link → error.
- Checked WooCommerce's page assignments (Settings → Advanced → Page setup): the Cart and Checkout pages were still assigned, so the configuration *looked* correct.
- Looked at the page objects themselves: both pages had been sitting in **Trash** for weeks. WooCommerce still pointed at them, but WordPress doesn't serve trashed pages.

## Action
- Restored both pages from Trash and confirmed their WooCommerce shortcodes/blocks were intact.
- Re-verified the page assignments.
- Ran a **full test purchase path logged out**: product → cart → checkout → payment form rendered.

## Result
Checkout restored the same session. Because the pages were trashed rather than permanently deleted, nothing had to be rebuilt.

## Lessons / prevention
- "Settings look right" ≠ "it works" — always verify the object the setting points to.
- Test critical paths **as a customer** (logged out). Admin sessions can see content visitors can't.
- Added the checkout path to a routine post-change smoke test.
