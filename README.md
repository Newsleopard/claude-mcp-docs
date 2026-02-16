> 🇹🇼 [繁體中文版](zh-tw)

# NewsLeopard MCP Server Documentation

## Server Description

NewsLeopard (電子豹) is Taiwan's leading email marketing and SMS automation platform, serving 15,000+ businesses with 30-40% market share in Taiwan's email marketing industry. The platform processes billions of emails annually with 99%+ deliverability.

The NewsLeopard MCP Server connects your NewsLeopard account to Claude, enabling you to manage email campaigns, view reports, analyze performance, and automate email marketing — all using natural language.

**Server URL:** `https://mcp.newsleopard.com/mcp`

---

## Features

### Campaign Management

- Create, draft, and send email campaigns with interactive forms
- Edit campaign content (text, sections, or full HTML)
- Pause running campaigns
- Pre-flight validation before sending

### Analytics & Reporting

- View campaign performance metrics (open rates, click rates, bounce rates)
- Get AI-powered analysis with optimization recommendations
- Compare multiple campaigns side-by-side
- Track per-link click breakdown and e-commerce revenue data
- Export detailed per-recipient CSV reports

### Contact Management

- View and manage subscriber lists/groups
- Create new contact groups
- See open rate rankings across groups

### Templates & Automation

- Browse and use official and custom email templates
- Save new templates for reuse
- Start and stop automation workflows

### Account Management

- Check sending quota and account balance
- View verified sender addresses
- Get optimal send time recommendations based on historical data

---

## Setup Instructions

### Claude.ai (Web)

> **Requirement:** Claude Pro, Max, Team, or Enterprise plan

1. Go to [Claude.ai](https://claude.ai) and sign in
2. Click your **avatar** (bottom-left) → **Settings** → **Connectors**
3. Scroll to the bottom and click **Add custom connector**
4. Enter the URL:

   ```text
   https://mcp.newsleopard.com/sse
   ```

5. Click **Add** — you will be redirected to the NewsLeopard login page
6. Enter your NewsLeopard credentials and click **Allow** to authorize
7. You will be returned to Claude.ai — the connector shows as **Connected**

After connecting:

- You can enable or disable individual tools in the Connectors settings
- Connectors sync automatically to Claude iOS and Android apps
- No additional setup needed on mobile devices

> **Note:** Claude.ai uses OAuth authentication only (no API Key).

### Claude Desktop

> **Requirement:** Claude Pro, Max, Team, or Enterprise plan

#### Option A: Connectors UI (Recommended)

Same as Claude.ai — uses OAuth, no additional software required:

1. Open Claude Desktop → click your **avatar** → **Settings** → **Connectors**
2. Click **Add custom connector**
3. Enter the URL:

   ```text
   https://mcp.newsleopard.com/sse
   ```

4. Click **Add** — your browser will open for OAuth login
5. Enter your NewsLeopard credentials and authorize
6. Return to Claude Desktop

Connectors added via the UI sync across Claude.ai and mobile devices.

#### Option B: mcp-remote (API Key)

For API Key authentication, use the `mcp-remote` bridge. Requires [Node.js](https://nodejs.org/).

Config file location:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude