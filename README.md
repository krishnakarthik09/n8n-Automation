# 📊 Nathan's Automated Weekly Sales Reporting Workflow

An **n8n automation workflow** built for Nathan, Analytics Manager at ABCorp, to fully automate his weekly sales reporting process — eliminating manual errors and saving hours of repetitive work every week.

---

## 🧩 Problem Statement

Nathan had to manually:
- Fetch sales data from a **legacy data warehouse** every week
- Separate orders into **"Processing"** and **"Booked"** categories
- Calculate the **total value of Booked orders**
- Post a summary to the **company Discord** every Monday
- Maintain a **table of Processing orders** for Sales Managers to review

This repetitive process was **error-prone**, caused **miscalculations**, and was sometimes **not completed on time** — leading to criticism from management.

---

## ✅ Solution

A fully automated **n8n workflow** that runs every **Monday at 9:00 AM** and handles everything end-to-end — no human involvement needed.

---

## ⚙️ Workflow Overview

```
[Schedule Trigger - Every Monday 9AM]
            │
            ▼
[Fetch Data from Warehouse API]
            │
            ▼
[Check Order Status]
       │            │
       ▼            ▼
 [Processing]     [Booked]
       │            │
       ▼            ▼
[Set Order Data] [Calculate Total]
       │            │
       ▼            ▼
[Save to Table]  [Post to Discord]
```

---

## 🔧 Nodes Used

| Node | Purpose |
|------|---------|
| `Schedule Trigger` | Runs automatically every Monday at 9:00 AM |
| `Manual Trigger` | For testing the workflow manually |
| `HTTP Request` | Fetches sales data from the warehouse API |
| `IF (CheckOrderStatus)` | Splits orders into Processing vs Booked |
| `Set (SetProcessingData)` | Extracts orderID and employeeName |
| `Data Table (Upsert)` | Saves Processing orders for Sales Manager review |
| `Code (CalculateBookedOrders)` | Calculates total count and value of Booked orders |
| `Discord` | Posts the weekly Booked summary to company Discord |

---

## 🚀 How to Use This Workflow

### Step 1 — Import the Workflow
1. Open your **n8n instance**
2. Go to **Workflows → Import**
3. Upload the `Nathan's Work Flow.json` file

### Step 2 — Set Up Credentials
You need to configure these credentials in n8n:

- **HTTP Header Auth** — for the warehouse API (`x-assessment-id` header)
- **Discord Webhook** — for posting messages to Discord

### Step 3 — Activate the Workflow
- Toggle the workflow to **Active**
- It will now run automatically every **Monday at 9:00 AM**
- Or click **"Trigger Manually"** to test it instantly

---

## 📤 Output

### Discord Message (every Monday):
```
This week we've X booked orders with a total value of $YYYY.YY
```

### Data Table (Processing Orders):
| orderID | employeeName |
|---------|-------------|
| 1001 | John Smith |
| 1002 | Jane Doe |

---

## 🛠️ Tech Stack

- **n8n** — Workflow automation platform
- **Warehouse API** — REST API with HTTP Header Authentication
- **JavaScript** — Custom code node for calculations
- **Discord Webhook** — For team notifications
- **n8n Data Table** — For storing Processing orders

---

## 💡 Key Features

- ✅ **Fully Automated** — No manual work needed
- ✅ **Scheduled** — Runs every Monday at 9 AM automatically
- ✅ **Error-Free Calculations** — JavaScript handles all math
- ✅ **Real-Time Notifications** — Instant Discord updates
- ✅ **Data Storage** — Processing orders saved for manager review

---

## 📁 File Structure

```
📦 nathans-sales-workflow
 ┗ 📄 Nathan's Work Flow.json   ← n8n workflow file
 ┗ 📄 README.md                 ← Project documentation
```

---

## 👤 Author

**Krishna Karthik**
- GitHub: [@krishnakarthik09](https://github.com/krishnakarthik09)
- Project built as part of **n8n Automation Learning** — solving real client problems

---

## 📌 Note

> This workflow was built as a **hands-on learning project** from the official n8n quickstart course, simulating a real-world automation scenario for a business analytics use case.
