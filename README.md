# Financial Reporting & Analytics Dashboard (Power BI)

This project demonstrates **financial reporting and analytics** using **Power BI**, focused on **Executive Finance Summary** and **Accounts Receivable (AR)** dashboards. It is designed to showcase **FP&A, AR, and AP analysis capabilities** using a consolidated single-table finance dataset based in India.

## 🧱 Dashboard Pages

### 1️⃣ Executive Finance Summary

<img width="900" height="500" alt="Screenshot 2026-01-19 145629" src="https://github.com/user-attachments/assets/2afd59bb-3da7-4b52-843a-be7c6c4a559e" />


### 2️⃣ Accounts Receivable (AR)

<img width="900" height="500" alt="Screenshot 2026-01-19 145606" src="https://github.com/user-attachments/assets/3609dd28-1c30-46c0-808d-d4ffd91e790e" />

---

## 🧮 Measures Used (DAX)

```DAX
-- Core Finance
Total Invoice = SUM(Finance_Data[Invoice_Amount])
Total Paid = SUM(Finance_Data[Paid_Amount])
Total Outstanding = SUM(Finance_Data[Outstanding_Amount])

-- Budget & Variance
Total Budget = SUM(Finance_Data[Budget_Amount])
Variance Amount = [Total Invoice] - [Total Budget]
Variance % = DIVIDE([Variance Amount], [Total Budget])

-- Accounts Receivable (AR)
AR Outstanding = CALCULATE([Total Outstanding], Finance_Data[Transaction_Type] = "AR")

-- Overdue
Overdue Amount = CALCULATE([Total Outstanding], Finance_Data[Due_Date] < TODAY())

-- Time Intelligence
YTD Revenue = TOTALYTD([Total Invoice], Dim_Date[Date])
MTD Revenue = TOTALMTD([Total Invoice], Dim_Date[Date])
