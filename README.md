# Farmer's Text Alert – Offline Warning System
> *“Timely Weather Warnings. Safer Farming. Stronger Communities.”*

A modern, responsive, offline-first agricultural weather early warning and crop advisory platform built with **React**, **TypeScript**, **Vite**, and **Tailwind CSS**.

---

## 1. Project Overview & Objective

In rural India, internet connectivity remains intermittent and unpredictable. Millions of smallholder farmers rely on basic 2G/3G feature phones without smartphones or data plans.

**Farmer’s Text Alert** solves this gap by delivering timely, localized meteorological warnings and crop-specific precautionary advice directly to farmers via **ordinary GSM SMS text messages**. Farmers do not need an internet connection or any mobile app. The web application serves as the administrative command center for agrometeorology officers, agricultural university extension wings (KVKs), and disaster management cells.

### Supported Weather Hazards:
- **Heavy Rainfall & Coastal Depressions** (e.g., Cauvery Delta, Konkan coast)
- **Severe Heatwaves & High Evaporation Stress** (e.g., Deccan Plateau, Andhra plains)
- **Flash Floods & Lowland Inundation** (e.g., Gangetic plains, Terai belt)
- **Drought & Soil Moisture Deficits** (e.g., Semi-arid Karnataka & Rayalaseema)
- **Extreme Low Temperatures & Ground Frost** (e.g., Northern plains, Punjab wheat belt)

---

## 2. Technology Stack & Architecture

- **Frontend Framework**: React 19 with Vite & TypeScript
- **Styling**: Tailwind CSS v4 with custom agricultural design tokens (dark forest green `#064e3b`, emerald `#059669`, warm earth tones, crisp slate backgrounds)
- **Icons**: Lucide React
- **Data Visualizations**: Recharts (Pie/Donut crop distribution, Bar regional breakdown, outcome telemetry)
- **State & Persistence**: LocalStorage with schema verification, pre-loaded realistic datasets, and instant CSV export/import
- **Rule Engine**: Transparent, deterministic risk matching without fictitious machine learning claims

---

## 3. Main Application Modules

The application features 9 fully functional modules accessible from the dark-green sidebar:

1. **Dashboard (`/`)**:
   - Live KPI stat cards (Registered Farmers, Active Alerts, Dispatched Messages, Simulated Delivery Rate)
   - Interactive **Regional Threat & Agronomy Overview** mapping surveillance nodes to districts and registered farmer holdings
   - Recharts visualizers for **Farmers Grouped by Crop** and **Farmers Grouped by State**
   - Quick-action buttons to launch SMS broadcasts or create alerts
   - Live activity feeds for Recent Weather Warnings and Recent SMS Broadcasts
   - Transparent *“Demo Data Mode”* banner

2. **Farmer Registration**:
   - Enrollment form with strict validation: full name (3+ chars), 10-digit Indian mobile number (`+91`), state, district, village, crop type, and preferred language
   - Duplicate prevention engine: detects and prevents re-registering existing phone numbers
   - Celebratory visual feedback and instant local storage persistence

3. **Farmer Directory**:
   - Searchable, filterable database by name, phone, village, crop, district, and state
   - Toggle between responsive **Table View** and **Card Grid View**
   - **Privacy Phone Masking**: toggle between masked numbers (`98••••3456`) and unmasked numbers
   - **Farmer Profile Dossier Modal**: inspect registration metadata, crop type, and complete SMS delivery history for that individual farmer
   - **CSV Export & Import**: one-click CSV download and bulk CSV file uploader

4. **Weather Alerts**:
   - Meteorological hazard catalog with severity tiers (*Severe Warning, Warning, Advisory, Watch*)
   - Quick-preset alert creator for Heavy Rain, Heatwave, Flood, Drought, and Frost
   - **Preview Affected Farmers Modal**: before broadcasting, inspect exactly how many farmers reside in the affected districts, their standing crops, and preview their translated SMS messages

5. **Crop Advisory Library**:
   - Scientific advisory rules linked by hazard, standing crop, region, and language
   - Review status badges: **Reviewed by Agro Experts**, **Pending Expert Review**, and **Inactive**
   - Agronomic governance notice requiring validation by ICAR / KVK agronomists

6. **SMS Campaigns Wizard**:
   - Step 1: Select verified weather alert
   - Step 2: Transparent risk-matching engine previews eligible farmers, checks 12-hour duplicate thresholds, and formats messages in each farmer's registered language
   - Step 3: Launch simulated telecom SMS broadcast
   - **Live Telemetry Console**: real-time animated progress bar (0%–100%), status tickers (*Submitted, Delivered (Simulated), Failed (Simulated)*), and streaming GSM transmission logs

7. **Message History & Feature Phone Inspector**:
   - Comprehensive audit trail of all transmitted SMS packets
   - Search and filter by status, hazard, date, and language
   - **Feature Phone Mockup Inspector**: displays how the SMS appears on a basic 2G feature phone screen in the farmer's native script
   - CSV export for administrative auditing

8. **Reports & Analytics**:
   - Operational performance analytics with delivery success rates and duplicate SMS savings
   - Recharts outcome distribution and hazard frequency charts
   - Campaign historical audit logs
   - Honest academic metrics disclaimer (no fictitious rupee savings or inflated claims)

9. **Settings & Security**:
   - Configurable app branding and tagline
   - Dynamic crop registry manager (add/remove supported crops)
   - Simulated telecom gateway status and API endpoint telemetry
   - Weather API sync cadence preferences
   - **Reset Demo Data** tool to restore default sample records

---

## 4. Multi-Language (i18n) Support

The system natively supports 5 regional Indian languages:
- **English** (`en`)
- **Tamil / தமிழ்** (`ta`)
- **Telugu / తెలుగు** (`te`)
- **Hindi / हिन्दी** (`hi`)
- **Kannada / ಕನ್ನಡ** (`kn`)

When a language is selected in the top navigation bar, the dashboard labels, navigation menus, alerts, and advisories translate dynamically. Crucially, when an SMS campaign runs, **each farmer receives the text in their own registered preferred language**, not the administrator's UI language!

---

## 5. Transparent Rule-Based Risk Matching Engine

Instead of relying on opaque or simulated machine learning, the system follows a transparent 6-step deterministic process:

```
[1. Read Weather Alert] ➔ [2. Validate Validity & Districts] ➔ [3. Identify Registered Farmers in Region]
                                                                          │
[6. Broadcast via SMS Gateway]  [5. Translate to Native Script]  [4. Match Crop Precautionary Rule]
```

1. **District Geofencing**: Matches farmer's registered district against the alert's affected zone.
2. **Crop-Specific Advisory Lookup**: Finds verified guidance for the farmer's specific crop (e.g., Rice drainage outlets vs. Cotton ridge-furrow management).
3. **General Fallback**: If no crop-specific rule is available, safely falls back to standard verified hazard guidance.
4. **Language Localization**: Pulls reviewed advisory text in the farmer's saved `preferredLanguage`.
5. **Anti-Spam Duplicate Filter**: Checks past 12-hour history to avoid spamming the farmer repeatedly for the same ongoing hazard.

---

## 6. How to Run Locally

### Prerequisites
- Node.js (v18 or higher recommended)
- npm

### Installation & Execution
```bash
# 1. Clone or navigate to the project directory
cd farmer

# 2. Install dependencies
npm install

# 3. Start development server
npm run dev
```

The application will be live at:
**`http://localhost:5173/`**

### Build for Production
```bash
npm run build
```
Generates an optimized bundle in `dist/`.

---

## 7. College Demonstration Walkthrough Script

To demonstrate the application during an evaluation:

1. **Dashboard Overview**:
   - Open `http://localhost:5173/`. Point out the natural agricultural palette, KPI stat cards, and the **Demo Data** disclaimer banner.
   - Click on district cards in the **Regional Threat & Agronomy Overview** (e.g. *Thanjavur* or *Guntur*) to demonstrate real-time inspector updates.
2. **Register a New Farmer**:
   - Navigate to **Farmer Registration**.
   - Enter: Full Name: `R. Kannan`, Mobile: `9840998877`, State: `Tamil Nadu`, District: `Thanjavur`, Village: `Papanasam`, Crop: `Rice`, Preferred Language: `Tamil (தமிழ்)`.
   - Click **Complete Farmer Registration**. Note the toast notification and celebratory confetti.
3. **Verify in Directory**:
   - Go to **Farmer Directory**. Show the newly enrolled farmer.
   - Toggle **Masked Numbers** to show privacy protection for farmers' mobile numbers.
   - Click **Dossier** to view the farmer's complete profile.
4. **Inspect Weather Alerts**:
   - Go to **Weather Alerts**. Locate alert `ALT-2026-001` (Heavy Rainfall in Thanjavur, Nagapattinam).
   - Click **Preview Affected Farmers**. Point out that the engine matched our newly registered farmer and translated the message into Tamil.
5. **Launch Simulated SMS Campaign**:
   - Click **Proceed to SMS Campaign** (or go to **SMS Campaigns** in the sidebar).
   - Review the recipient count and anti-duplicate protection.
   - Click **Launch Simulated SMS Broadcast**.
   - Watch the animated progress bar, telemetry tickers (Submitted, Delivered, Failed), and live logs in real time.
6. **Inspect Message History**:
   - Navigate to **Message History**.
   - Click **View** on our farmer's message to open the **Feature Phone Mockup**, showing how the SMS looks on a 2G keypad phone.
7. **Demonstrate Multilingual UI**:
   - Switch language in the top navbar to **தமிழ் (Tamil)** or **हिन्दी (Hindi)**. Show how navigation and headers update seamlessly.
   - Switch back to English.
8. **View Analytics**:
   - Open **Reports & Analytics**. Note the updated delivery success rate, outcome distribution chart, and export the CSV report.

---

## 8. Demonstration Limitations & Future Roadmap

### Academic Demonstration Mode (Current)
- **SMS Gateway**: Simulated locally with realistic network variance (92% delivery success, 8% tower/coverage failure rate). No paid SMS credits required.
- **Weather Feeds**: Simulated meteorological bulletins with clear `demoFlag` attribution.
- **Persistence**: Browser LocalStorage with automatic schema initialization and CSV backup/restore.

### Production Integration Roadmap
1. **SMS Gateway Integration**: Connect to **CDAC Mobile Seva** (Government of India SMS gateway) or telecom SMPP aggregators using backend webhooks.
2. **Weather API Sync**: Schedule cron ingestion from the **IMD Open Data Portal API** (Mausam / Agromet bulletins).
3. **PostgreSQL / PostGIS Database**: Replace local storage with a spatial database for polygon-based farm boundary geofencing.
4. **Role-Based Access Control (RBAC)**: Enforce strict role authorization so district officers only access records in their jurisdiction.
