# Multi-Commerce-News-Site
# Multi-Commerce News Monitoring System

This project is an **automated news monitoring and summarisation pipeline** focused on circular economy topics, resale, refurbish, and AI trends for a curated set of major brands.

## Features

- **Automated, scheduled news discovery** via Perplexity API (brand + keyword queries)
- **AI-powered summarisation and enrichment** using OpenAI (text clean-up, highlight extraction)
- **Storage of daily news digests** in Google Sheets for easy access and audit
- **Daily email digest** of curated articles, formatted for readability
- **Live HTML news feed** accessible via a secure n8n webhook endpoint (viewable in browser, iframe, etc.)
- **Modular n8n workflow** (easy to maintain, extend, or migrate)

## Brands & Keywords Tracked

- Brands: Brooks Running, Volvo Cars, Samsonite, H&M, SONY, Stanley 1913, Carhartt, IKEA (EU + USA)
- Keywords: take-back programs, circular economy, resale, refurbish, AI

## Workflow Overview

1. **Scheduled trigger** (every 24 hours)
2. **Query generation** for each brand/keyword combination
3. **Perplexity API** call for news articles (rate-limited for API health)
4. **AI-based summarisation** of each article (OpenAI)
5. **Storage**: Save digest (HTML and summary data) to Google Sheets
6. **Email Delivery**: Send HTML digest to configured recipients
7. **HTML Feed**: Serve latest digest as a web page via n8n webhook

## How It Works

- All news discovery, validation, and summarisation happens on a schedule (cron).
- Results are appended to a Google Sheet (with date and article count).
- An n8n webhook workflow fetches the latest digest from Google Sheets and serves it as styled HTML.
- Email delivery uses the same HTML digest for consistency.

## Quick Start

1. **Clone or import the n8n workflow** provided.
2. **Set up Google Sheets API credentials** in n8n.
3. **Add your Perplexity and OpenAI API keys**.
4. **Configure the email and webhook output nodes** (recipient, webhook auth, etc).
5. **Activate the main workflow** (scheduled trigger).
6. **Open the webhook URL** in your browser to view the latest digest.

## Example Output

![Workflow Screenshot](./docs/workflow-screenshot.png)
![Email Digest Screenshot](./docs/email-screenshot.png)
![HTML Feed Screenshot](./docs/html-feed-screenshot.png)

## Customisation

- **Add or remove brands/keywords** in the query builder node.
- **Change storage** from Google Sheets to DB, Notion, or file.
- **Tweak the email or HTML template** for your brand/design.

## Tech Stack

- **n8n (Cloud or Self-hosted)**
- **Google Sheets**
- **Perplexity API**
- **OpenAI API**

## License

MIT

---

*Built by Tim Finch, 2025.*