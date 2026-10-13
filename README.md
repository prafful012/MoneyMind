# MoneyMind — Personal Finance Tracker

**MoneyMind** is a modern, calming, and responsive personal finance dashboard built purely with **HTML5, CSS3, and Vanilla JavaScript**. It stores all records directly on your machine using browser **LocalStorage**, giving you complete privacy with zero cloud dependencies and no backend or database setup required.

---

## 🌟 Key Features & Functional Checklist

### 1. Dashboard (`index.html`)
- [x] **Live Balance Calculation**: Dynamic total net wealth calculated strictly from opening balances + transactions (no hardcoded figures).
- [x] **Monthly Financial Health**: Real-time monthly income, expenses (transfers strictly excluded), net savings, and savings rate percentage.
- [x] **Income vs Expenses Chart**: Interactive 6-month historical bar chart powered by Chart.js.
- [x] **Category Spending Doughnut**: Instant visual breakdown of current month expenses.
- [x] **Upcoming Bills Widget**: At-a-glance list of upcoming and overdue bills with days remaining.
- [x] **Monthly Budget Progress**: Visual progress bars showing consumption of category spending limits.
- [x] **Recent Transactions**: Real-time list of latest transactions with color-coded badges.
- [x] **Calm Empty State**: Dedicated onboarding banner and friendly zero-balance guidance for new users.

### 2. Transaction Management (`transactions.html`)
- [x] **Add, Edit & Delete**: Full lifecycle management for Income, Expense, and Account Transfer transactions.
- [x] **Transfer Logic**: Deducts source account and increments destination account equally without inflating income or expense totals.
- [x] **Search & Multi-Filter**: Live text search (description/notes), filter by type, category, account, and date range.
- [x] **Sorting**: Sort by date (newest/oldest) and amount (highest/lowest).
- [x] **Pagination**: Configurable page sizes (10, 25, 50 rows per page) with page navigation controls.
- [x] **CSV Export**: RFC-compliant CSV download of all transactions with safe escaping.
- [x] **CSV Import**: Parse and validate user-supplied CSV files, preview valid/skipped rows, and import transactions.

### 3. Account Management (`accounts.html`)
- [x] **Account Types**: Cash Wallets, Bank Accounts, UPI / Digital Wallets, and Other Accounts.
- [x] **Dynamic Balance Engine**: Computed as `Opening Balance + Income - Expenses - Transfers Out + Transfers In`.
- [x] **Account Transaction History**: Clickable transaction history modal for each individual account.
- [x] **Archive & Unarchive**: Hide inactive or closed accounts from active dropdowns while preserving history.
- [x] **Delete Guard**: Prevents accidental deletion of accounts containing transaction history, offering archiving instead.

### 4. Budget Management (`budgets.html`)
- [x] **Category Limits**: Define monthly spending ceilings by expense category.
- [x] **Month Switcher**: Browse previous and future months with dedicated month navigation controls.
- [x] **Visual Progress**: Color-coded progress indicators (`<75%` Green, `75%-99%` Warning Amber, `>=100%` Exceeded Red).
- [x] **Alert Banners**: Proactive notifications when budgets approach or cross their thresholds.

### 5. Recurring Bills & Subscriptions (`bills.html`)
- [x] **Frequencies**: Weekly, Monthly, Quarterly, and Yearly schedules.
- [x] **Status Categorization**: Grouped into Upcoming, Overdue, and Payment History.
- [x] **Mark as Paid Action**: Generates transaction record exactly once in LocalStorage and advances the next due date to the subsequent cycle.
- [x] **Duplicate Prevention**: Safeguard prevents paying the same bill twice for the same cycle.

### 6. Analytics & Reports (`reports.html`)
- [x] **Custom Timeframes**: Past 6 Months, Past 12 Months, Current Month, or All Time.
- [x] **Net Savings Trajectory**: Smooth line chart showing cumulative savings over time.
- [x] **Monthly Trend Comparison**: Bar chart comparing income vs expense distributions.
- [x] **Detailed Spending Breakdown**: Category share table with percentage allocations and transaction counts.

### 7. Settings, Categories & Backups (`settings.html`)
- [x] **Category Customization**: Add, edit, or delete income and expense categories.
- [x] **Safe Category Deletion**: Reassigns associated transactions to "Other Income" or "Other Expense".
- [x] **Currency Configuration**: Choose currency symbol ($, €, £, ₹, ¥, CA$, AU$, R$) and symbol placement (prefix or suffix).
- [x] **Full JSON Backup**: One-click download of all application data, accounts, categories, transactions, budgets, and bills.
- [x] **JSON Restore with Preview**: Inspect backup date, record counts, and select "Replace All" or "Merge" modes before restoring.
- [x] **Danger Zone (Reset)**: Safe data reset requiring typing the keyword `RESET` to prevent accidental loss.

---

## 💻 Tech Stack & Architecture

- **Markup & Styling**: HTML5, Vanilla CSS3 with CSS Variables, Flexbox, CSS Grid.
- **Scripting**: Vanilla ECMAScript (ES6+), modular JavaScript architecture.
- **Charts**: [Chart.js](https://cdn.jsdelivr.net/npm/chart.js) via CDN (with responsive wrappers and graceful offline fallbacks).
- **Storage**: Browser `window.localStorage` with schema versioning (`SCHEMA_VERSION: 1`).

### Directory Structure

```
moneymind/
├── index.html            # Dashboard overview
├── transactions.html     # Transaction management & CSV tools
├── accounts.html         # Account cards & dynamic balances
├── budgets.html          # Category budgets & progress alerts
├── bills.html            # Recurring bills & subscription tracker
├── reports.html          # Analytics charts & spending tables
├── settings.html         # Category manager, currency & backups
├── css/
│   ├── style.css         # Core design system & component styles
│   └── responsive.css    # Breakpoints & mobile drawer navigation
├── js/
│   ├── storage.js        # Centralized LocalStorage service & schema
│   ├── calculations.js   # Dynamic balance & analytics engine
│   ├── charts.js         # Chart.js initialization & themes
│   ├── app.js            # UI controller, toasts, modals & navigation
│   ├── transactions.js   # Transaction list, filter & CSV parser
│   ├── accounts.js       # Accounts manager & history modal
│   ├── budgets.js        # Budget progress & month switcher
│   ├── recurring-bills.js# Bill cycle scheduler & payment recorder
│   ├── reports.js        # Reports controller & timeframe filters
│   └── backup.js         # JSON export, preview restore & reset
└── README.md             # Documentation & setup guide
```

---

## 🚀 Setup & Running Locally

Because MoneyMind uses zero backend services and pure client-side web technologies, you can run it immediately without `npm install` or server dependencies:

### Method 1: Direct File Opening
Double-click `index.html` in your file explorer to open it directly in Google Chrome, Microsoft Edge, Mozilla Firefox, or Safari.

### Method 2: VS Code Live Server
1. Open the `MoneyMind` folder in **VS Code**.
2. Right-click `index.html` and click **"Open with Live Server"**.
3. The app will open at `http://127.0.0.1:5500/index.html`.

### Method 3: Local Apache (XAMPP)
Since this repository resides inside `c:\xampp\htdocs\MoneyMind`, simply start **Apache** from the XAMPP Control Panel and open:
```
http://localhost/MoneyMind/
```

### Method 4: Python Simple HTTP Server
Open PowerShell in the project directory and run:
```bash
python -m http.server 8080
```
Then visit `http://localhost:8080`.

---

## 🔒 Security & Privacy Model

* **No Credentials Stored**: MoneyMind does not ask for, accept, or store bank credentials, passwords, card CVVs, or UPI PINs.
* **No Server Calls**: All financial logs stay in your browser. There is no server communication, tracking, or telemetry.
* **XSS Defense**: User input rendered onto the DOM is sanitized through `MoneyMindApp.escapeHtml()` and safe DOM assignments.
* **Safe JSON / CSV Processing**: Imported files are validated against expected schemas before being committed to storage. No `eval()` calls are used.
* **LocalStorage Isolation**: LocalStorage is isolated by the browser origin protocol and port. Keep regular offline JSON backups via **Settings & Backup** to ensure you never lose data when clearing browser history.

---

## 🧪 Testing Scenarios Guide

1. **Add Income & Expense**:
   - Click `+ Income` in the header, enter an amount and description. Check dashboard metric and account balance update instantly.
   - Click `+ Expense`, assign to "Food & Groceries". Check category spending doughnut and recent transactions list update.
2. **Transfer Funds**:
   - Click `Transfer`, select "Bank Account" to "Cash Wallet". Verify total net balance remains unchanged while individual account balances update properly.
3. **Set & Track Budget**:
   - Go to `budgets.html`, set a budget for "Food & Groceries". Verify the progress bar and remaining amount match recorded expenses.
4. **Recurring Bills**:
   - Go to `bills.html`, create a bill. Click **"Mark Paid"**. Confirm that exactly one expense transaction is added and the due date advances to next cycle.
5. **Search & Filters**:
   - Go to `transactions.html`, search by keyword and filter by category or type. Confirm real-time filtering and pagination work accurately.
6. **Backup & Restore**:
   - Go to `settings.html`, click **"Export Complete JSON Backup"**.
   - Modify or delete a transaction, then click **"Restore from JSON Backup"**. Verify preview displays accurate counts, and restore completes reliably.
7. **Reset Data**:
   - Test data reset with confirmation. Typing `RESET` restores factory default accounts and categories.
