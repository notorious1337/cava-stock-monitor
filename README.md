🛍️ CAVA Stock Monitor
Automated Shopify inventory tracker with HTML reports & daily GitHub Actions monitoring

This repository contains a fully automated Shopify product availability monitoring tool that scans the entire CAVA Athleisure store daily, tracks size-level stock changes, and sends a clean HTML email report with color-coded tables.

Built using Python + GitHub Actions, it requires no servers, runs entirely in the cloud, and only emails you when something truly changes.

🚀 Features
🔎 Full Store Inventory Scan

Uses Shopify’s /products.json endpoint to fetch the full product catalog efficiently.

📦 Variant-Level Stock Tracking

The tool detects availability for every size of every product.

🟢🟠🔴 Product Classification

Every product is categorized into:

🟢 Fully Available – all sizes in stock

🟠 Partially Sold-Out – some sizes out of stock

🔴 Fully Sold-Out – all sizes unavailable

💌 Beautiful HTML Email Report

You receive a formatted email showing:

Product name

Product link

Available sizes

Sold-out sizes

Color-coded tables for clarity

🔁 Change Detection (Optimized Notifications)

A state.json file tracks yesterday’s inventory.
You receive an email only when something changes, such as:

A size becoming unavailable
A sold-out size returning
A product moving between categories

☁️ Runs Automatically in GitHub Actions

No cron jobs
No servers
Fully cloud-based
Automatic daily triggers

📝 Self-Updating State Tracking

After each run, the workflow commits updated state.json to the repo to ensure accurate diffing.

🏗️ How It Works

GitHub Action triggers daily (09:00 AM IST by default).
The Python script:
Fetches all products
Builds a full stock map
Compares with previous state
Generates a structured HTML email
If differences are found → email is sent.
The script updates state.json.

GitHub Actions commits and pushes that updated file.

📂 Repository Structure
cava-stock-monitor/
│
├─ cava_stock_monitor.py       # Main Python script
├─ requirements.txt            # Python dependencies
├─ state.json                  # Auto-updated inventory state (do not edit)
└─ .github/
   └─ workflows/
      └─ cava-stock-monitor.yml   # GitHub Actions workflow

⚙️ Setup Instructions
1. Fork or clone this repository

Modify it for your Shopify store or keep as-is for CAVA.

2. Add GitHub Secrets

Go to:

Repository → Settings → Secrets and Variables → Actions

Add these:

Secret Name	Value
SMTP_USER	Your email (ex: you@gmail.com
)
SMTP_PASSWORD	Your SMTP/App password (Gmail App Password recommended)
TO_EMAIL	Where reports should be sent
3. Commit & Push

GitHub Actions will automatically detect the workflow.

4. Manually run once

Go to Actions → CAVA Stock Monitor → Run workflow
This will generate the first state.json.

5. Done 🎉

Everything now runs daily and automatically.

📧 Example HTML Email

You will receive something like this:

🟠 Partially sold-out products in orange

🟢 Fully available products in green

🔴 Fully sold-out products in red

Size tables

Clickable product links

Clean layout for mobile and desktop

(Exact styling depends on your custom HTML template in cava_stock_monitor.py.)

🧩 Customization

You can modify the script to:

Track only selected collections

Monitor only specific products (watchlist mode)

Add Telegram/Discord/Slack notifications

Generate weekly summary reports

Track price changes

Attach CSV/PDF exports

Just ask — I can generate the code for any of these.

🛠️ Technologies Used

Python 3.11

GitHub Actions

SMTP (Email)

Shopify /products.json API

HTML Reporting

📝 License

This project is released under the MIT License.
Feel free to use, modify, and extend it.

⭐ Want Improvements?

If you’d like:

Watchlist alerts

Real-time Telegram notifications

Images in HTML tables

Back-in-stock SMS

A dashboard UI

Just tell me — I can extend this tool any way you want.
