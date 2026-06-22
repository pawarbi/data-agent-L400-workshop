# mfg-ops-data — Manufacturing Ops source CSVs

The **single source of truth** for the workshop data. These 11 CSVs build the
**Manufacturing Ops** semantic model, and a subset is reused to build the Lab 3
**Lakehouse** tables (`downtime_reasons`, `sales_orders`) — so there is no separate
lakehouse dataset to maintain.

> The messy column/file names (`Sheet1.csv`, `sales_data_FINAL.csv`, `Down`, `Qty`, `Mfr`)
> are **intentional teaching traps** for the Lab 1 modeling/debugging exercises.

## Files → semantic model tables

| CSV | Model table | Notes |
|-----|-------------|-------|
| `Plants.csv` | Plants | Dimension |
| `lines.csv` | Lines | Dimension |
| `Assets.csv` | Assets | Dimension |
| `PRODUCTS.csv` | Products | Dimension |
| `Customers_Master.csv` | Customers | Dimension |
| `vendor list.csv` | Vendors | Dimension |
| `ProductionLog.csv` | ProductionLog | Fact (production, downtime `Down`) |
| `sales_data_FINAL.csv` | Sales | Fact (revenue/units) |
| `Sheet1.csv` | SalesSummary | Pre-aggregated sales summary |
| `inventory.csv` | Inventory | Fact |
| `PO_Data.csv` | PurchaseOrders | Fact |

## Used by the Lab 3 Lakehouse build

`NB_Build_OpsRefLakehouse` derives both lakehouse tables **deterministically** from a
subset of the files above (no extra raw data):

- **`downtime_reasons`** ← `ProductionLog.csv` + `lines.csv` + `Plants.csv`
  (splits `Down` minutes across reason categories; reconciles exactly to model downtime).
- **`sales_orders`** ← `PRODUCTS.csv` + `Plants.csv`
  (deterministic revenue/units/margin per product × plant × month).

## Regenerating / re-anchoring dates

These CSVs are produced by `generate_workshop_data.py` (date self-correcting via the
`AsOfDate` Power Query parameter). See the semantic-model README for details.
