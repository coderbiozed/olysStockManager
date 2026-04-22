Olysproduct Pro | Stock & Sync

A premium, cloud-synced inventory management system built with Vue.js, Tailwind CSS, and Firebase. This application provides a real-time "Public View" dashboard and automates data logging to Google Sheets via a custom Google Apps Script bridge.

🚀 Key Features

Real-time Synchronization: Powered by Firestore with onSnapshot for instant updates across all devices.

Cloud Sheet Bridge: Automatically syncs every new product addition to a Google Spreadsheet.

Visual Analytics: Live tracking of total inventory value and low-stock alerts.

One-Click Export: Generate CSV reports of your current stock levels.

Modern UI: High-fidelity interface with glassmorphism effects and responsive design.

🛠️ Technical Stack

Frontend: Vue.js 3 (Composition API)

Styling: Tailwind CSS

Database/Auth: Firebase Firestore & Anonymous Authentication

Automation: Google Apps Script (Web App Deployment)

📦 Installation & Setup

1. Web Interface

Open index.html in any modern browser.

The app will automatically initialize an anonymous session to begin saving data to the public cloud path.

2. Google Sheets Integration (Cloud Sync)

To enable the "Git-style" sync to your private spreadsheet:

Create a new Google Sheet.

Go to Extensions > Apps Script.

Paste the following bridge code:

function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  // Appends: Date, Name, SKU, Quantity, Price
  sheet.appendRow([new Date(), data.name, data.sku, data.quantity, data.price]);
  return ContentService.createTextOutput("Success");
}


Click Deploy > New Deployment.

Select Web App.

Set Access to "Anyone" (This is required for the app to talk to the sheet).

Copy the Web App URL and paste it into the Sync Center within the Olysproduct app.

📂 Data Structure

The application adheres to strict public data paths for global visibility:

Collection Path: /artifacts/{appId}/public/data/inventory

📄 License

Custom internal use for Olysproduct.