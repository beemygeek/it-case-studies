# 5. A "random" feature that wasn't random

**Environment:** WordPress/WooCommerce, MySQL

## Situation
Two complaints with the same theme: the shop page showed the **same products every visit**, and a homepage "Featured This Week" section that was supposed to rotate never changed.

## Investigation
- **Shop page:** WooCommerce's default sort is menu order + title — deterministic by design. Nothing was broken; the expectation didn't match the configuration.
- **Featured section:** the code *did* try to shuffle, using `ORDER BY RAND(seed)` with a seed based on the date so picks stayed stable for a few days. Testing the query directly showed the same order every time.
  The bug: with a **constant** seed, MySQL's `RAND(seed)` produces one value per *query*, not per row, so every row sorts identically and nothing is shuffled.

## Action
- Shop: when the shopper hasn't chosen a sort, default to random ordering via the platform's catalog-ordering hook. An explicit choice ("price low to high") is still respected.
- Featured section: changed the expression to `RAND(seed + post_id)` so each row gets its own value while the date-based seed keeps the selection stable for the intended period.
- Verified by reloading repeatedly and comparing product sets.

## Result
Both sections now rotate as intended, without breaking the shopper's explicit sorting.

## Lessons
- Distinguish **"broken"** from **"working as configured."**
- Test the assumption at the lowest level (the actual SQL), not just the page.
