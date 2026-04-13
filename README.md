# owasp-api-scanner
Automated OWASP API Top 10 security scanner built with Postman and Newman

A beginner cybersecurity project that automatically scans APIs for common security vulnerabilities using Postman and Newman.

## 🎯 What does this do?
This scanner fires a series of security tests against a target API and generates a HTML report showing which vulnerabilities were found.

## 🚨 What vulnerabilities did it find?
| # | Vulnerability | What it means | Result |
|---|---|---|---|
| API1 | BOLA | User A can secretly view User B's private GPS location | 🚨 VULNERABLE |
| API2 | Broken Authentication | Expired/fake tokens are correctly rejected | ✅ SECURE |
| API8 | Security Misconfiguration | Server is leaking its software version in response headers | 🚨 VULNERABLE |

## 🛠️ Tools Used

| Tool | What it does |
|---|---|
| Postman | Used to build and write the security tests |
| Newman | Runs all the tests automatically from command line |
| Docker | Runs crAPI (the vulnerable target app) locally |
| crAPI | A deliberately vulnerable API made by OWASP for testing |
| Git + GitHub | Stores and shares the project code |

## 💻 How to run it yourself

### Step 1 — Install the required tools
- [Download Node.js](https://nodejs.org) — LTS version
- [Download Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Download Postman](https://www.postman.com/downloads)
- [Download Git](https://git-scm.com/download/win)

### Step 2 — Start the target API (crAPI)
Open Command Prompt and run:
docker-compose up -d

Wait 2-3 minutes, then open http://localhost:8888 in your browser.
You should see the crAPI login page.

### Step 3 — Install Newman
npm install -g newman newman-reporter-htmlextra

### Step 4 — Clone this repo
git clone https://github.com/geek4lyfeu-cloud/owasp-api-scanner.git
cd owasp-api-scanner

### Step 5 — Run the scanner
newman run OWASP-Scanner.postman_collection.json -e crAPI-Local.postman_environment.json --reporters cli,htmlextra --reporter-htmlextra-export reports/owasp-report.html

### Step 6 — View the report
start reports/owasp-report.html


---

## 🔮 Planned Improvements
- [ ] Host crAPI on a cloud server
- [ ] Enable GitHub Actions for fully automated scheduled scans
- [ ] Add more OWASP API Top 10 test coverage
- [ ] Add Slack/email notification when vulnerabilities are found

---
## 👩‍💻 About
Built as a portfolio project to demonstrate API security testing skills using industry-standard tools.
