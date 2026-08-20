# 🛡️ AI SOC Assistant

An AI-powered Security Operations Center (SOC) dashboard that helps security analysts detect, analyze, and triage cyber threats from one place — built to automate the repetitive parts of an analyst's day without requiring enterprise-grade infrastructure or budget.

---

## 💡 The Problem

Security analysts spend hours every day manually reviewing logs, checking suspicious URLs, and triaging alerts. Most of this work is repetitive and follows recognizable patterns — exactly the kind of task software can pre-filter, so analysts spend their time on judgment calls instead of raw pattern-matching.

Enterprise tools (Splunk, CrowdStrike, etc.) solve this well, but come at a price and complexity most students, small teams, and startups can't justify. This project fills that gap: real detection logic, zero enterprise overhead.

---

## ✅

This is a phased build. 

| Phase | Module | Status |
|---|---|---|
| 1 | Foundation (dashboard, database, navigation) | ✅ Done |
| 2 | Log Analyzer | ✅ Done |
| 3 | URL Reputation Checker | ✅ Done |
| 4 | IOC Extractor | 🚧 Planned |
| 5 | Incident Report Generator | 🚧 Planned |
| 6 | Phishing Email Analyzer | 🚧 Planned |
| 7 | File Hash Checker | 🚧 Planned |
| 8 | AI Chat Assistant | 🚧 Planned |

---

### Dashboard
Real-time overview of every incident found across all modules, with automatic severity scoring.



### Log Analyzer — Brute-Force Detection
Upload any Linux auth log. Detects failed-login clustering per IP within a configurable time window, and flags a possible compromise if a login succeeds right after a string of failures.



### URL Reputation Checker — Phishing Detection
Scores any URL 0–100 based on IP-based links, shorteners, typosquatting (via edit-distance matching), suspicious keywords, and high-risk TLDs — no external API required.



---

## ⚙️ How It Works

```
User → Streamlit Dashboard → Detection Module → Shared SQLite Database → Dashboard
```

Every detection module (Log Analyzer, URL Checker, and future modules) is fully independent — each one parses its own input, runs its own scoring logic, and optionally saves a finding to one shared database. The Dashboard reads from that same database, giving a unified view without any module needing to know about the others. New detectors can be added without touching existing code.

---

## 🧰 Tech Stack

 Language : Python 3 ; Core logic, parsing, detection algorithms 
 Frontend : Streamlit ; Interactive dashboard, zero HTML/JS written 
 Database : SQLite ; Lightweight, zero-config shared data layer 
 Data handling : Pandas ; Structured log parsing 
 Reporting : ReportLab ; Planned — automated PDF incident reports 
 Detection engine : Regex  No external API lock-in 

---

## 🚀 Getting Started

**Requirements:** Python 3.10+pip

```bash
# Clone the repo
git clone https://github.com/Kapish-Singh/TCS332-SOC-Assistant.git
cd TCS332-SOC-Assistant

# Creates and activate a virtual environment
python3 -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run the app
streamlit run app.py
```

Then open the URL it prints (usually `http://localhost:8501`) in your browser.

---

## 📂 Project Structure

```
soc_assistant/
├── app.py                  # Main entry point — sidebar nav, dashboard
├── requirements.txt
├── db/
│   └── database.py         # SQLite schema + save/query functions
└── modules/
    ├── log_analyzer.py     # ✅ Brute-force detection engine
    ├── url_checker.py      # ✅ URL phishing risk scoring
    ├── ioc_extractor.py    # 🚧 Placeholder — Phase 4
    ├── report_generator.py # 🚧 Placeholder — Phase 5
    ├── email_analyzer.py   # 🚧 Placeholder — Phase 6
    └── hash_checker.py     # 🚧 Placeholder — Phase 7
```

---

## 🗺️ Roadmap

- [ ] **IOC Extractor** — automatically pull IPs, domains, emails, and hashes from any log or email
- [ ] **Incident Report Generator** — auto-produce PDF reports from saved incidents
- [ ] **Phishing Email Analyzer** — parse `.eml` files for phishing indicators
- [ ] **File Hash Checker** — MD5/SHA1/SHA256 lookups against known-malicious samples
- [ ] **AI Chat Assistant** — natural-language Q&A over findings ("why is this flagged?")
- [ ] VirusTotal / AbuseIPDB live threat intelligence integration
- [ ] MITRE ATT&CK technique mapping per incident
- [ ] Nmap-based network recon module (authorized lab use only)

---

## 👤 Author-Kapish Singh
B.Tech CSE — Cybersecurity 
Semester 3
Graphic Era Deemed University
