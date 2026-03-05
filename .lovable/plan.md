## Fix: Remove "পাজামা" from checkout form pack options & align data

### Problem

The `checkout-form` section (`checkout-1`) in the database still has outdated packOptions:

- "কম্বো প্যাক (জুব্বা + পাজামা)" with description "জুব্বা ও পাজামা একসাথে - সেরা ডিল!"

The `hero-product` section was already fixed, but the checkout form section was missed.

### Fix (1 step)

**Update checkout-form packOptions via SQL migration:**

- Change `checkout-1` section's packOptions to match the hero section:
  - Single: `label: "শুধু জুব্বা"`, `description: "প্রিমিয়াম জুব্বা"`, `price: 1700`
  - Combo: `label: "কম্বো প্যাক"`, `description: "প্রিমিয়াম Islamic Combo Pack"`, `price: 2000`
- Also align the pack IDs to `single`/`combo` (currently `jubba_only`/`combo_pack`) so the state management works consistently across hero and checkout sections.

No code changes needed -- this is purely a database data fix.