> 🇹🇼 [繁體中文版](zh-tw)

# Newsleopard MCP Server Documentation

## Server Description

Newsleopard (電子豹) is Taiwan's leading email marketing and SMS automation platform, serving 15,000+ businesses with 30-40% market share in Taiwan's email marketing industry. The platform processes billions of emails annually with 99%+ deliverability.

The Newsleopard MCP Server connects your Newsleopard account to Claude, enabling you to manage email campaigns, view reports, analyze performance, and automate email marketing — all using natural language.

**Server URL:** `https://mcp.Newsleopard.com/mcp`

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

## Usage Examples

Once connected, you can ask Claude in natural language. Here are three end-to-end examples covering different capabilities:

### 1. Analyze recent campaign performance

**You ask:** "Show me my 10 most recent campaigns and tell me which performed best."

**What Claude does:** Calls `get_recent_campaigns_summary` to list campaigns with open/click/bounce rates, then `compare_campaigns` to highlight the top performers.

**You see:** A ranked list with key metrics, plus an interactive comparison widget that lets you drill into any campaign's per-link clicks and e-commerce revenue.

### 2. Create a Black Friday promotional email

**You ask:** "Help me draft a Black Friday newsletter for my VIP subscribers."

**What Claude does:** Calls `get_verified_senders` to confirm which sender address to use, `get_top_lists` to locate your VIP list, runs `preflight_check_campaign` to validate readiness, then opens `draft_campaign` — an interactive form where you fill in subject, sender, and body.

**You see:** An in-chat form; after you review and submit, a draft campaign is created in your Newsleopard account ready for final review before sending.

### 3. Find the optimal send time

**You ask:** "What day and time should I send my newsletter for the best engagement?"

**What Claude does:** Calls `get_best_send_time` which analyzes your subscribers' historical open behavior.

**You see:** A heatmap showing the best send windows (day-of-week × hour-of-day) based on your actual audience — typically identifies a 2-3 hour peak window specific to your list.

---

## Setup Instructions

### Claude.ai (Web)

> **Requirement:** Claude Pro, Max, Team, or Enterprise plan

1. Go to [Claude.ai](https://claude.ai) and sign in
2. Click your **avatar** (bottom-left) → **Settings** → **Connectors**
3. Scroll to the bottom and click **Add custom connector**
4. Enter the URL:

   ```text
   https://mcp.Newsleopard.com/sse
   ```

5. Click **Add** — you will be redirected to the Newsleopard login page
6. Enter your Newsleopard credentials and click **Allow** to authorize
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
   https://mcp.Newsleopard.com/sse
   ```

4. Click **Add** — your browser will open for OAuth login
5. Enter your Newsleopard credentials and authorize
6. Return to Claude Desktop

Connectors added via the UI sync across Claude.ai and mobile devices.

#### Option B: mcp-remote (API Key)

For API Key authentication, use the `mcp-remote` bridge. Requires [Node.js](https://nodejs.org/).

Config file location:

- **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

Example config:

```json
{
  "mcpServers": {
    "Newsleopard": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://mcp.Newsleopard.com/sse"]
    }
  }
}
```

Restart Claude Desktop after editing the config.

---

## Legal & Support

- **Privacy Policy:** <https://mcp.Newsleopard.com/legal/privacy-policy>
- **Terms of Use:** <https://mcp.Newsleopard.com/legal/terms-of-use>
- **Support:** <service@Newsleopard.com>
- **Website:** <https://www.Newsleopard.com>
