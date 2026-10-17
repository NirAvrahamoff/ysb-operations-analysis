# Data

Raw exports from YSB's ERP system, published with the company's permission. Column names are in Hebrew, as exported. The notebook translates the columns it uses into English.

| File | Rows | Period | Content |
|---|---|---|---|
| `customer_orders_2025.csv` | 7,279 | 1 Jan to 8 Jun 2025 | Customer order lines: order, customer, project, item, quantity, value, status |
| `supplier_orders_2025.csv` | 1,977 | 1 Jan to 30 May 2025 | Purchase order lines: supplier, order, item, quantity, value, requested date |
| `supplier_goods_receipts_2025.csv` | 1,532 | 1 Jan to 29 May 2025 | Goods received from suppliers, linked to purchase orders |
| `inventory_movements_jan_apr_2025.csv` | 8,819 | 2 Jan to 31 Mar 2025 | Inventory movements: receipts, transfers, counts, write-offs |
| `inventory_movements_apr_on_2025.csv` | 4,937 | 1 Apr to 31 May 2025 | Same structure, continued |
| `inventory_valuation_2024_12_31.csv` | 8,186 | 31 Dec 2024 | Year-end stock quantity, unit cost and value per item |

## Main columns used

| Hebrew column | English name in the notebook | Meaning |
|---|---|---|
| מק"ט / מק'ט / קוד פריט | `item` | Item code |
| תאור מוצר / תיאור פריט | `description` | Item description |
| תאריך | `date` / `po_date` | Transaction or order date |
| כמות | `qty` | Quantity |
| הזמנה | `order_id` / `po_id` | Customer or purchase order number |
| סטטוס הזמנה | `status` | Customer order status |
| שם ספק | `supplier` | Supplier name |
| ת. אספקה | `requested_date` | Requested delivery date on a purchase order |
| סוג תנועת מלאי | `movement_type` | Inventory movement type |
| ערך מלאי | `value_ils` | Stock value in ILS |
| מחיר אחרון שחושב | `unit_cost_ils` | Last calculated unit cost in ILS |

## Notes

- Dates are in US format (month/day/year).
- Customer order lines with status cancelled (מבוטלת), rejected (נדחה) or draft (טיוטא) are excluded from demand.
- The requested delivery date on purchase orders equals the order date in 92% of lines, so it is not used to measure supplier performance.
