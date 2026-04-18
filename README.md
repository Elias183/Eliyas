# Stock Management System

This project implements a comprehensive stock management system with a **Flask REST API**, an **interactive ipywidgets mini-app**, and various **reporting and visualization capabilities**.

---

## 📖 Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Setup and Installation](#setup-and-installation)
- [How to Use](#how-to-use)
  - [Interactive Mini-App](#interactive-mini-app)
  - [Flask REST API](#flask-rest-api)
- [File Structure](#file-structure)
- [Troubleshooting](#troubleshooting)
- [Further Development](#further-development)

---

## 🧩 Introduction
This system provides tools to:
- Manage inventory
- Record sales and incoming stock
- Generate reports
- Monitor stock levels

It is designed with:
- An **interactive notebook interface** using ipywidgets for daily operations
- A **Flask-based REST API** for integration with external applications (e.g., mobile apps)

---

## 🚀 Features
- **SQLite Database**: Persistent storage for Users, Items, StartingStock, Sales, and Incoming records.
- **Core Stock Management**:
  - Accurate calculation of remaining stock (`get_remaining_stock`)
  - Sales validation to prevent overselling (`validate_sale`)
  - Low-stock alerts based on configurable thresholds (`check_stock_alerts`)
  - CRUD operations for Items
- **Reporting**:
  - Sales transaction summaries
  - Daily Excel reports (`export_daily_report_to_excel`) with sheets for:
    - Daily Sales
    - Daily Incoming
    - Current Stock Snapshot
- **Interactive ipywidgets Mini-App**:
  - Add new items
  - Record incoming stock (restocks)
  - Record sales
  - Check current stock and alerts
  - Generate daily Excel reports
  - Edit/delete records
- **Flask REST API**:
  - Endpoints for items, incoming stock, sales, stock levels, and reports
  - Thread-safe SQLite connections
- **Dashboard Visualizations**:
  - Daily total sales trend
  - Total sales by item
  - Total sales by cashier

---

## ⚙️ Setup and Installation
1. **Clone or Download**  
   ```bash
   git clone https://github.com/yourusername/stock-management-system.git
   cd stock-management-system
2, dependencies
pip install Flask openpyxl pandas matplotlib seaborn ipywidgets requests
3. Datbases
The stock_app.db SQLite database will be created automatically upon first execution of the schema definition.
How to Use
Interactive Mini-App
Run all cells in the notebook sequentially.

Use widgets to:

Add items

Record incoming stock

Record sales

Generate reports

Refresh dropdowns by re-running widget cells after adding new items/users.

Flask REST API
python app.py
Base URL: http://127.0.0.1:5000

Example endpoints:

/items (GET, POST, PUT, DELETE)

/sales (POST, PUT, DELETE)

/stock/<item_id>

/reports/daily_excel

File Structure
stock-management-system/
│
├── app.py                # Flask API
├── db_schema.py          # SQLite schema
├── utils.py              # Stock functions (validate_sale, alerts)
├── notebooks/            # Colab notebooks
├── reports/              # Excel outputs
├── stock_app.db          # SQLite database (auto-generated)
└── requirements.txt      # Dependencies
🛠 Troubleshooting
Address already in use: Restart runtime or kill duplicate Flask processes.

SQLite threading errors: Ensure thread-safe connection handling is implemented.

Excel not generating: Verify openpyxl is installed and writable permissions exist.

🔮 Further Development
User authentication & authorization

Enhanced error handling & logging

Dedicated frontend (React, Angular, Vue)

Advanced reporting features

Unit & integration tests



