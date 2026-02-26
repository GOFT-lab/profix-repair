# 🔧 ProFix Appliance Repair — Landing Page

A fast, responsive, single-file landing page for **ProFix Appliance Repair** — a professional appliance repair service targeting the US market.

Live demo can be deployed via https://profixrepair.netlify.app/ in minutes.

---

## 📋 About the Service

**ProFix Appliance Repair** provides same-day and next-day repair services for all major household appliances across the United States. With over 12 years of experience, certified technicians, and a 90-day parts & labor warranty, ProFix is committed to getting your home running again — fast.

### Services Offered

| Appliance | Common Issues We Fix |
|---|---|
| 🧊 Refrigerator | Cooling failure, ice maker, compressor, leaks |
| 🫧 Washing Machine | Won't drain/spin, vibration, error codes |
| 🍽️ Dishwasher | Not cleaning, water not draining, door latch |
| 🔥 Oven & Stove | Uneven heating, igniters, burners, sensors |
| 🌬️ Dryer | No heat, drum not turning, long drying times |
| ❄️ AC & HVAC | Cooling issues, tune-ups, filter cleaning |

---

## 🌐 Features

- **Single HTML file** — no build tools, no dependencies, deploys anywhere
- **Fully responsive** — mobile-first design, works on all screen sizes
- **Repair booking form** with full client-side validation:
  - US phone number format validation `(123) 456-7890`
  - All fields required with inline error messages
  - Submits to Google Sheets via Google Apps Script
- **Smooth scroll navigation** with sticky header
- **Hover animations** on service cards and buttons
- **Modern design** — Syne + DM Sans fonts, navy/blue/orange palette

---

## 🚀 Deployment

### Option 1 — GitHub Pages (recommended)

1. Create a new GitHub repository
2. Upload `index.html` to the root
3. Go to **Settings → Pages → Source → main branch**
4. Your site goes live at `https://yourusername.github.io/repo-name`

### Option 2 — Netlify Drop (fastest)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag and drop `index.html`
3. Get a live URL instantly — no account required

> ⚠️ **Important:** The booking form will not work when opened as a local file (`file://`) due to browser CORS restrictions. Always use a deployed URL.

---

## 📬 Google Sheets Integration

The booking form submits data to a Google Apps Script endpoint. To connect your own spreadsheet:

**1. Create a Google Apps Script (`Extensions → Apps Script`) with this code:**

```javascript
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  sheet.appendRow([
    new Date(),
    e.parameter.name,
    e.parameter.phone,
    e.parameter.appliance,
    e.parameter.problem
  ]);
  return ContentService.createTextOutput("ok");
}
```

**2. Deploy as a Web App:**
- Click **Deploy → New Deployment**
- Type: **Web App**
- Execute as: **Me**
- Who has access: **Anyone**
- Copy the deployment URL

**3. Replace the script URL in `index.html`:**

```javascript
await fetch("YOUR_APPS_SCRIPT_URL_HERE", {
  method: "POST",
  mode: "no-cors",
  body: fd,
});
```

---

## 📁 Project Structure

```
/
└── index.html       # Complete site — HTML, CSS, and JS in one file
└── README.md        # This file
```

---

## 📞 Contact Info (Demo)

| | |
|---|---|
| **Phone** | (800) 555-9876 |
| **Email** | support@profix.com |
| **Hours** | Mon–Sat 7am–8pm, Sun 9am–5pm |

---

## 📄 License

This project is for demonstration and commercial use. Replace all placeholder contact details, the Google Apps Script URL, and branding before going live.
