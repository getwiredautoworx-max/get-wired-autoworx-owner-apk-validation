# Get Wired AutoWorx — Catalogue / Pricelist Import Control

Updated: 2026-09-29

## Controlled workflow
1. Import source into staging only.
2. Match each row by verified SKU; never rely on row position alone.
3. Validate product/SKU/cost pairing against the source.
4. Calculate advertised price using cost × 1.15 × 1.35.
5. Flag missing SKU, duplicate SKU, invalid cost, unexpected price or category mismatch.
6. Reconcile proposed stock changes against existing verified production stock.
7. Produce a QA report before any production mutation.
8. Apply only validated rows.
9. Recheck counts, prices, categories and stock after write.

## Non-destructive rule
Absence from a new supplier file is not evidence that a production SKU is out of stock. Existing verified production stock must remain intact unless a validated stock update explicitly changes it.

## Known historical issue
The earlier 1,109-row September Buyer's Guide extraction was not reliable and must not be imported. Any replacement extraction must be independently reconciled before production use.
