# 📊 Telecom ETL Project (SSIS)

## 📌 Overview
Designed and implemented an end-to-end ETL solution using SQL Server Integration Services (SSIS) in Visual Studio to process telecom CSV files and load them into a Data Warehouse.

---

## 🖼️ Control Flow
![Control Flow](telecom/Details/Screenshot%202026-03-25%20074048.png)

---

## 🖼️ Data Flow
![Data Flow](telecom/Details/Screenshot%202026-03-25%20074122.png)

---

## 📥 Source
- CSV files generated every 5 minutes  
- Columns:
  - ID, IMSI, IMEI, CELL, LAC, EVENT_TYPE, EVENT_TS  

---

## 🔧 Transformations

### 🔹 Lookup (IMSI → subscriber_id)
- Join IMSI with reference table  
- If not found → `subscriber_id = -99999`  

---

### 🔹 Handle Nulls
- Replace NULL `subscriber_id` with `-99999`  

---

### 🔹 Derived Columns (IMEI Processing)
- **TAC** = first 8 digits of IMEI  
- **SNR** = last 6 digits of IMEI  
- If IMEI is NULL or length < 14 → `-99999`  

---

## 📤 Destination

### ✔️ Fact_Transaction Output
![Fact Output](telecom/Output/Screenshot%202026-03-25%20074639.png)

---

### ❌ Error Output
![Error Output](telecom/Output/Screenshot%202026-03-25%20074711.png)

---

## 📂 File Handling
- Processed files moved to:
  - `Archive/Processed` folder  
- Prevents duplicate processing  

---

## ✅ Features
- Automated file processing using Foreach Loop  
- Data validation and transformation  
- Lookup integration with reference data  
- Error handling and redirection  
- File archiving after processing  
