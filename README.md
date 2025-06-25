# 🎨 Telegram Content Creation Request Bot

A Telegram bot built using **Google Apps Script**, **Google Sheets**, and **Notion API** to streamline the process of submitting, organizing, and tracking design/content requests for internal teams or organizations.

This bot allows users to select a department, enter project details step-by-step, and submit content requests. All data is logged in Google Sheets and optionally synced to Notion.

---

## 📦 Features

- Step-by-step interactive form inside Telegram
- Inline keyboard buttons for quick selection (departments, design types)
- Request summary generation with unique Request ID
- Google Sheets integration for data logging
- Notion integration for centralized tracking (optional)
- Admin-only command to manually sync specific requests to Notion
- Status tracking and summaries for users
- Automatically clears session after submission

---

## 🛠 Tech Stack

- **Telegram Bot API**  
- **Google Apps Script** (backend + deployment)  
- **Google Sheets** (data storage)  
- **Notion API** (optional content dashboard)  

---

## 🧰 Requirements

- Google Workspace account (for Apps Script and Sheets)
- A Telegram bot token (from [@BotFather](https://t.me/BotFather))
- A Google Sheet with headers matching your structure
- (Optional) A Notion integration and database ID for storing requests

---

## ⚙️ Setup Instructions

### 1. Set Up Google Sheet
Create a Google Sheet with headers like:
```

Request ID | Chat ID | Department | Name | Completion Date | Design Type | Content Description | Status | Link (optional)

```

### 2. Create a Telegram Bot
- Talk to [@BotFather](https://t.me/BotFather)
- Use `/newbot` and save your **bot token**

### 3. Set Up Google Apps Script
- Go to [script.google.com](https://script.google.com) and create a new project
- Paste the full script into `Code.gs`
- Replace:
  - `token` with your Telegram bot token
  - `ssId` with your Google Sheet ID
  - `webAppUrl` (after deployment)

### 4. Deploy as Web App
- Click **Deploy > Manage deployments > New deployment**
- Select type: **Web app**
  - Execute as: `Me`
  - Who has access: `Anyone`
- Copy the deployment **Web App URL**
- Update the script’s `webAppUrl` variable
- Run `setWebhook()` to connect the bot to Telegram

---

## 📝 User Flow

1. `/start`  
   Begins a new design request. User selects their department.

2. Prompted sequentially for:  
   - Name  
   - Completion date  
   - Design type (Digital / Print)  
   - Content requirements and dimensions

3. Summary is generated and logged in the Google Sheet.  
   Request is marked "Pending" by default.

4. **/status** – Lists current requests and their statuses  
5. **/updateNotion [row number]** – (Admin-only) Syncs a row to Notion

---

## 🔧 Commands

| Command | Description |
|---------|-------------|
| `/start` | Begin a new content request |
| `/status` | View your current requests |
| `/updateNotion [row]` | Admin-only: manually sync a specific row to Notion |

---

## 📑 Data Flow

- All submissions are stored row-by-row in Google Sheets
- Data is optionally synced to Notion using the `addPageToNotionDatabase()` function
- Each request is assigned a UUID
- Summaries are returned to the user in Telegram upon submission

---

## 🔒 Admin Options

- Only a specific chat ID (e.g., `"79869704"`) can run `/updateNotion`
- Admin can trigger row-level Notion syncs in case of webhook failure or retroactive updates

---

## ✅ Planned Features

- Request editing before final submission  
- File upload support for logos/reference material  
- Email confirmation (via Google Apps Script MailApp)  
- Dashboard for reviewing and managing requests  

---

## 👨‍💻 Author

**Parthkumar Joshi**  
Built for managing internal design requests during event planning and operations.

---

## 📄 License

This project is licensed under the MIT License. You are free to use, adapt, and share it with attribution.

---

## 🤝 Contributions

Pull requests and improvements are welcome. Please open an issue or submit a PR if you'd like to contribute.

```

---

Would you like this saved as a `.md` file for download? I can also help package your `Code.gs` file and `README.md` into a GitHub repo structure if needed.
