# 📍 Google Maps Lead Generation B2B Workflow (n8n)

An enterprise-grade **n8n workflow** designed to automate local B2B lead generation. It systematically loops through target ZIP codes and business subcategories, queries the official **Google Places (New) API**, filters out duplicates, and saves fresh leads straight into **Google Sheets** with built-in API error handling.

---

## 🛠️ How It Works

The workflow functions through a structured automated pipeline divided into major zones:

1. **⚙️ Settings & Triggers:** Initializes configuration pointing to your target Google Sheet URL containing target subcategories and ZIP codes. Can be triggered manually or via a scheduled cron interval.
2. **🧹 Data Prep & Filtering:** Pulls fresh data from the sheet, runs a batch loop, and filters out ZIP codes or subcategories that have already been processed or marked as "Ignore".
3. **🗺️ Google Maps API Integration:** Queries the `places.googleapis.com` search endpoint matching the current `Subcategory + ZIP Code` combination to fetch rich data (Name, Phone, Address, Reviews, Website, Coordinates, Rating, etc.).
4. **🧠 Smart Data Processing:** Extracts individual elements from the JSON payload array, strips out potential duplicate place IDs, and maps fields accurately.
5. **📊 Google Sheets Sync & Retries:** Appends rows to your final database. Includes native JavaScript **Exponential Backoff** mechanics to automatically pause and retry operations if Google Sheets API rate limits hit standard thresholds.

---

<img width="599" height="250" alt="image" src="https://github.com/user-attachments/assets/388972c3-b4c3-4543-aff6-77de4471c307" />

---

## 🎯 Captured Data Fields

This pipeline extracts highly targeted lead parameters including:
* 🏢 Business Title / Display Name
* 📞 National Phone Number
* 🌐 Website URL
* 📍 Formatted Physical Address & GPS Coordinates
* 🌟 Rating & User Reviews Count
* 🏷️ Business Categories & Place ID

---

## 🚀 How to Use This Workflow

### Prerequisites
* An active **n8n** instance.
* **Google Maps API Credentials** (OAuth2/API Key enabling the Places API).
* A **Google Sheets** spreadsheet structured to manage targeted locations and catch final lead outputs.

### Installation Steps
1. **Import the Workflow:** Download the JSON code provided in this repo, open your n8n dashboard, click the top-right menu (`...`), and select **Import from File**.
2. **Configure Settings:** Click the `Settings` node and paste your specific Google Sheets document URL, along with the correct names of your categories and location sheets.
3. **Link Credentials:** Authenticate your Google Sheets and HTTP Request (`GMaps API`) nodes using your secure private developer credentials.
4. **Execute:** Fire the manual trigger or activate the production schedule to start extracting hyper-local business data completely on autopilot.

---

## 📄 License
This workflow blueprint is open-source and available under the [MIT License](LICENSE).
