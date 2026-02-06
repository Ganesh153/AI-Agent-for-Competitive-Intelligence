# AI Agent for Competitive Intelligence

An intelligent n8n workflow that automates competitive intelligence research and analysis using AI-powered tools and APIs.

## 📋 Overview

This n8n workflow analyzes competitors and generates detailed competitive intelligence reports by:
- Identifying top competitors in a given industry
- Gathering real-time news and market data
- Analyzing competitor strengths, weaknesses, and market positioning
- Generating actionable insights and recommendations
- Storing results in Google Sheets
- Sending formatted reports via email

## 🚀 Features

- **Automated Competitor Identification**: Uses Perplexity AI to identify top 3 competitors in any industry
- **Real-time News Aggregation**: Fetches latest news articles using Tavily Search API
- **AI-Powered Analysis**: Leverages Cohere LLM for intelligent report generation
- **Structured Intelligence Reports**: Creates formatted competitive analysis with key metrics
- **Data Persistence**: Automatically stores reports in Google Sheets
- **Email Delivery**: Sends formatted reports directly to your inbox
- **Webhook Integration**: Accepts requests via webhook for seamless integration

## 📦 Prerequisites

Before importing this workflow into n8n, ensure you have the following API keys and credentials:

### Required API Keys

1. **Perplexity AI API Key**
   - Sign up at: https://www.perplexity.ai/
   - Generate API key from your account settings
   - Used for: Competitor identification and research analysis

2. **Tavily Search API Key**
   - Sign up at: https://tavily.com/
   - Get your API key from the dashboard
   - Used for: Real-time news and information retrieval

3. **Cohere LLM API Key**
   - Sign up at: https://cohere.com/
   - Generate API key from your account
   - Used for: Advanced text analysis and report generation

4. **Google OAuth Credentials**
   - Set up Google Cloud Project: https://console.cloud.google.com/
   - Enable Google Sheets API and Gmail API
   - Create OAuth 2.0 credentials (Desktop application)
   - Used for: Google Sheets integration and Gmail delivery

## 🔧 Setup Instructions

### Step 1: Prepare Your Credentials

Gather all the API keys and credentials mentioned above before proceeding.

### Step 2: Import the Workflow

1. Open your n8n instance
2. Click **Workflows** → **New**
3. Click **Import from file** or **Import from URL**
4. Select the `AI Agent for Competitive Intelligence.json` file
5. Click **Import**

### Step 3: Configure Credentials

After importing, you'll need to set up credentials for each node:

#### Perplexity AI Credentials
1. In the workflow, find nodes labeled "HTTP Request", "Information", "HTTP Request2", "Information1"
2. Click on each node → **Credentials** → **Create New**
3. Select **HTTP Bearer Auth**
4. Enter your Perplexity API key
5. Name it "Perplexity AI (G)"

#### Tavily Search Credentials
1. Find nodes labeled "HTTP Request1", "HTTP Request3"
2. Click on each node → **Credentials** → **Create New**
3. Select **HTTP Bearer Auth**
4. Enter your Tavily API key
5. Name it "Tavily Search"

#### Cohere LLM Credentials
1. Find nodes labeled "Cohere Chat Model", "Cohere Chat Model1", "Cohere Chat Model2", "Cohere Chat Model3"
2. Click on each node → **Credentials** → **Create New**
3. Select **Cohere API**
4. Enter your Cohere API key
5. Name it "Cohere Model"

#### Google Sheets & Gmail Credentials
1. Find nodes labeled "Create sheet", "Append row in sheet", "Update row in sheet", "Send a message"
2. Click on each node → **Credentials** → **Create New**
3. Select **Google Sheets OAuth2 API** or **Gmail OAuth2 API**
4. Follow the OAuth flow to authenticate with your Google account
5. Name them "Google Sheets account" and "Gmail account"

### Step 4: Configure Webhook

1. Find the **Webhook** node at the start of the workflow
2. Copy the webhook URL provided
3. This URL will be used to trigger the workflow

### Step 5: Update Configuration Values

Update the following hardcoded values in the workflow:

- **Email Address**: In the "Send a message" node, update `ganeshsai2003.elr@gmail.com` to your email address
- **Google Sheets ID**: Update the spreadsheet ID in Google Sheets nodes if you want to use a different sheet
- **Interest Areas**: Customize the focus areas for competitive analysis as needed

## 📡 Workflow Trigger

### Webhook Request Format

Send a POST request to your webhook URL with the following JSON payload:

```json
{
  "name": "Company Name",
  "interest": [
    "Product Features",
    "Pricing Strategy",
    "Market Share",
    "Customer Reviews",
    "Recent Partnerships"
  ]
}
```

### Example cURL Command

```bash
curl -X POST https://your-n8n-instance.com/webhook/hackathon-workflow \
  -H "Content-Type: application/json" \
  -d '{
    "name": "OpenAI",
    "interest": [
      "AI Models",
      "Pricing",
      "Market Position",
      "Recent News"
    ]
  }'
```

## 🔄 Workflow Steps

1. **Webhook Trigger**: Receives company name and areas of interest
2. **Competitor Identification**: Uses Perplexity to identify top 3 competitors
3. **Data Collection**: Gathers competitor information and recent news via Tavily
4. **Analysis**: Processes data through Cohere LLM for intelligent analysis
5. **Report Generation**: Creates formatted competitive intelligence report
6. **Data Storage**: Saves results to Google Sheets
7. **Email Delivery**: Sends formatted report via Gmail

## 📊 Output

The workflow generates:

- **Competitive Analysis Report**: Detailed analysis of competitors including:
  - Competitor strengths and weaknesses
  - Market positioning
  - Recent developments
  - Opportunities and threats
  
- **Google Sheets Record**: Stores all reports with timestamps for historical tracking

- **Email Report**: Formatted HTML email with key findings and recommendations

## 🔐 Security Best Practices

- **Never commit API keys** to version control
- Store credentials securely in n8n's credential management
- Use environment variables for sensitive data
- Regularly rotate API keys
- Restrict API key permissions to minimum required scope
- Monitor API usage for unusual activity

## 🐛 Troubleshooting

### Common Issues

**Issue**: Credentials not working
- **Solution**: Verify API keys are correct and have not expired
- Check that APIs are enabled in respective dashboards

**Issue**: Google Sheets integration fails
- **Solution**: Ensure Google Sheets API is enabled in Google Cloud Console
- Verify OAuth credentials have proper permissions
- Check that the spreadsheet ID is correct

**Issue**: Workflow execution timeout
- **Solution**: Check API rate limits for Perplexity and Tavily
- Consider adding delays between API calls
- Verify network connectivity

**Issue**: Email not sending
- **Solution**: Confirm Gmail OAuth credentials are valid
- Check that "Less secure app access" is enabled if using Gmail
- Verify recipient email address is correct

## 📝 Customization

### Modify Analysis Focus Areas

Edit the "Input" node to change the default interest areas for analysis.

### Change Report Format

Modify the "Structured Output Parser" nodes to customize report structure and formatting.

### Add Additional Data Sources

Extend the workflow by adding more HTTP Request nodes to integrate additional APIs.

## 🤝 Support

For issues or questions:
- Check n8n documentation: https://docs.n8n.io/
- Review API documentation for Perplexity, Tavily, and Cohere
- Consult Google Cloud documentation for authentication issues

## 📄 License

This workflow is provided as-is for competitive intelligence research purposes.

---

**Last Updated**: February 2026
**Workflow Version**: 1.0
