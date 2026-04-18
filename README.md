Stock Management System
This project implements a comprehensive stock management system with a Flask REST API, an interactive ipywidgets mini-app, and various reporting and visualization capabilities.

Table of Contents
Introduction
Features
Setup and Installation
How to Use
Interactive Mini-App
Flask REST API
File Structure
Troubleshooting
Further Development
1. Introduction
This system provides tools to manage inventory, record sales and incoming stock, generate reports, and monitor stock levels. It is designed with both an interactive notebook interface using ipywidgets for daily operations and a Flask-based REST API for potential integration with external applications (e.g., mobile apps).

2. Features
SQLite Database: Persistent storage for Users, Items, StartingStock, Sales, and Incoming records in stock_app.db.
Core Stock Management:
Accurate calculation of remaining stock (get_remaining_stock).
Sales validation to prevent overselling (validate_sale).
Low-stock alerts based on configurable thresholds (check_stock_alerts).
CRUD operations for Items.
Reporting:
Sales transaction summaries.
Daily Excel reports (export_daily_report_to_excel) with sheets for 'Daily Sales', 'Daily Incoming', and 'Current Stock Snapshot'.
Interactive ipywidgets Mini-App: A user-friendly interface within the Colab notebook for:
Adding new items.
Recording incoming stock (restocks).
Recording sales.
Checking current stock and stock alerts.
Generating daily Excel reports.
Editing and deleting existing sales and incoming stock records.
Flask REST API: A thread-safe API exposing endpoints for:
Item management (/items - GET, POST, PUT, DELETE).
Incoming stock management (/incoming - POST, PUT, DELETE).
Sales management (/sales - POST, PUT, DELETE).
Stock levels (/stock/<item_id>, /stock/alerts).
Reports (/reports/daily_excel, /reports/sales_summary, /reports/daily_sales_trend, /reports/sales_by_item, /reports/sales_by_cashier).
Dashboard Visualizations:
Daily total sales trend.
Total sales by item.
Total sales by cashier.
3. Setup and Installation
Clone or Download: Obtain the project files (e.g., by downloading stock_management_api.zip).
Extract: If downloaded as a zip, extract it to your desired working directory.
Dependencies: Install the required Python packages:
!pip install Flask openpyxl pandas matplotlib seaborn ipywidgets requests
(Note: Some might already be installed in Colab).
Database: The stock_app.db SQLite database will be created automatically upon the first execution of the schema definition cell (usually inoYLPyxr97g).
4. How to Use
Interactive Mini-App
Run all the cells in the notebook sequentially. The interactive sections (### 1. Add New Item, ### 2. Record Incoming Stock, etc.) will render widgets allowing direct interaction with the system via the notebook UI. Make sure to run the cells for create_incoming_widget() and create_sale_widget() if you add new items or users to refresh their dropdown options.

Flask REST API
Start the Flask Server: Execute the cell containing the run_flask_app function and the flask_thread initialization (e.g., 5207f968 or 6a8b7b84). This starts the Flask server in a separate thread.
Base URL: The API is accessible at http://127.0.0.1:5000 (or BASE_URL).
Testing Endpoints: The notebook includes a comprehensive API test script (871a38d4) that uses the requests library to demonstrate calls to all implemented endpoints (items, incoming, sales, stock, reports). This script verifies functionality and prints responses.
Thread-Safety: The API is refactored to handle SQLite connections in a thread-safe manner, ensuring stability in concurrent environments.
5. File Structure
The extracted project directory (extracted_stock_app) contains:

.xlsx files (e.g., daily_report_2023-01-07.xlsx, mvp_daily_report_2026-04-18.xlsx): Generated Excel reports.
stock_app.db: The SQLite database file.
sample_data/: Contains sample data files (Colab default).
.config/: Configuration files (Colab default).
extracted_stock_app/: An nested directory that might appear if the zip was extracted recursively.
6. Troubleshooting
AssertionError or Address already in use: If you encounter errors related to Flask routes not being found or the address being in use, it usually means the Flask server was started multiple times or not properly reset. The most reliable fix is to restart your Colab runtime (Runtime -> Restart runtime) and then re-run all necessary cells from the beginning.
SQLite Threading Errors: If you see errors like SQLite objects created in a thread can only be used in that same thread, ensure that the refactored, thread-safe Flask application code (using get_db_session and passing conn_local/cur_local to helper functions) is fully implemented and running.
7. Further Development
User Authentication: Implement a proper user authentication and authorization system for the API.
Error Handling: Enhance error handling and logging within the Flask API.
Frontend Integration: Develop a dedicated frontend (e.g., React, Angular, Vue) that consumes the Flask API.
Advanced Reports: Add more complex reporting features and custom report generation options.
Unit/Integration Tests: Write comprehensive unit and integration tests for all functions and API endpoints.
