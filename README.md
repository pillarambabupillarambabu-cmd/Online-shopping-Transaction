# Orbit Commerce — Online Shopping Transaction Analysis System

A B.Tech CSE (AI & ML) full-stack project featuring a Flask REST API, SQLAlchemy relational database, Pandas/NumPy analytics, and a responsive anti-gravity-inspired dashboard.

## Features
- KPI dashboard: revenue, orders, units sold and average order value.
- Product CRUD with search and pagination-ready API.
- Multi-item order creation with stock validation and transactional updates.
- Analytics: monthly revenue, category contribution and top products.
- CSV order export and database health endpoint.
- Responsive glassmorphism UI, animated gradient orbs, theme toggle and reduced-motion support.
- Synthetic sample data and automated API tests.

**Metric rule:** Cancelled and refunded orders are excluded from sales, revenue and units-sold analytics. Pending and completed orders are included.

## 1. Requirements
- Python 3.10 or newer
- pip
- Optional: MySQL Server 8.x

## 2. Setup (Windows PowerShell)
```powershell
cd online-shopping-analysis
py -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
Copy-Item .env.example .env
```
If PowerShell blocks activation, run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` and activate again.

## 3. Database configuration
### Easiest first run: SQLite
The supplied `.env.example` uses SQLite. No database server setup is needed. The app creates its tables automatically.

### MySQL
1. Create a database:
```sql
CREATE DATABASE online_shopping CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```
2. Edit `.env`:
```env
DATABASE_URL=mysql+pymysql://YOUR_USERNAME:YOUR_PASSWORD@localhost:3306/online_shopping
SECRET_KEY=replace-with-a-long-random-value
```
Use your actual local MySQL username and password. Do not commit `.env`.

## 4. Initialize and seed sample data
```powershell
python -m scripts.init_db
python -m scripts.generate_sample_data
```
The sample script creates 6 products, 3 customers and 12 sample orders. It skips insertion if products already exist.

## 5. Run
```powershell
python run.py
```
Open **http://127.0.0.1:5000** in your browser.

Pages:
- `/` — Dashboard
- `/products` — Product catalogue
- `/orders` — Orders
- `/analytics` — Analytics
- `/health` — Health check

## 6. Test
```powershell
pytest -q
```

## 7. Git and GitHub
Create an empty repository on GitHub (do not initialize it with README if you already have this project README). Then run:
```powershell
git init
git add .
git commit -m "Initial commit: Online Shopping Transaction Analysis System"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/online-shopping-analysis.git
git push -u origin main
```
Replace the URL with your repository URL. If Git asks you to authenticate, complete the browser sign-in or use GitHub's supported credential manager. Never commit passwords, API keys or `.env`.

For later changes:
```powershell
git add .
git commit -m "Describe your changes"
git push
```

## 8. Common issues
- **`py` not recognized:** Install Python from python.org and enable “Add Python to PATH”.
- **MySQL connection error:** Check that MySQL is running, database exists, credentials are correct, and the URL begins with `mysql+pymysql://`.
- **Module not found:** Activate `.venv` and run `pip install -r requirements.txt`.
- **Port in use:** Stop the other process using port 5000 or change the port in `run.py`.
- **No chart data:** Run the sample-data script, then refresh the dashboard.

## Project layout
See the source folders: `app/models`, `app/routes`, `app/services`, `app/templates`, `app/static`, `database`, `scripts`, `tests` and `docs`.

## Academic note
This is a learning/demo application with synthetic data. It does not process real payments and does not include authentication. Add authentication and authorization before exposing it publicly.
