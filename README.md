# DPDzero Collection Calls Pipeline

A data pipeline for analyzing loan collection call performance

[Open In Colab](https://colab.research.google.com/github/iChetanRaval/DPDzero-Data-Ops-Assignment/blob/main/DPDzero_Data_Ops_Assignment.ipynb)

# Overview
This pipeline processes daily call campaign data to generate agent performance metrics, including:

📞 Call volume and connect rates

⏱️ Average call duration

👥 Agent presence tracking

# Prerequisites
Google account (for Colab)

Basic Python knowledge (to customize if needed)

# Quick Start
1) Click the "Open in Colab" button above

2) Upload your data files when prompted:

  call_logs.csv

  agent_roster.csv

  disposition_summary.csv

3) Run all cells (Runtime > Run all in Colab)

# Detailed Instructions
**Option 1: Using Your Own Data**
Prepare your CSV files with these required columns:

  * call_logs.csv: call_id, agent_id, status, call_date, duration

  * agent_roster.csv: agent_id, users_first_name, org_id

  * disposition_summary.csv: agent_id, call_date, login_time

In Colab:

#Replace these paths if your files have different names
pipeline.ingest_data(
    call_logs_path='call_logs.csv',
    agent_roster_path='agent_roster.csv',
    disposition_summary_path='disposition_summary.csv'
)

Outputs
📄 agent_performance_summary.csv (saved in Colab's runtime)

📊 Interactive visualizations (displayed in notebook)

📝 Slack-style summary in the logs:

Agent Performance for 2025-04-28
---------------------------
  Top Performer: Ravi Sharma (98% connect rate)
  Total Active Agents: 45
  Average Duration: 6.5 min

# FAQ
**❓ Where does the data get stored?**
→ All processing happens in Colab's temporary runtime. Files disappear when the session ends unless downloaded.

**❓ Can I run this locally?**
→ Yes! Install dependencies with pip install pandas matplotlib seaborn and run as a standard Python script.

**❓ How do I analyze multiple days?**
→ Modify the call_date filter in the transform_data() method.

Pro Tip: To automatically save outputs to Google Drive, add this cell before running:

from google.colab import drive
drive.mount('/content/drive')

#Then change output paths like:
output_path = '/content/drive/MyDrive/agent_performance.csv'
