# Setup Guide

This guide will help you set up the Sentiment Analysis Automation workflow in n8n.

## Prerequisites

Before starting, ensure you have:
- [ ] n8n instance running (cloud or self-hosted)
- [ ] OpenAI API account and key
- [ ] Google account with Sheets API access
- [ ] Basic understanding of n8n workflows

## Step-by-Step Setup

### 1. Import the Workflow

1. Download the `Sentiment_Analyse.json` file from this repository
2. Open your n8n instance
3. Navigate to **Workflows** in the left sidebar
4. Click **Import** button
5. Select the downloaded JSON file
6. Click **Import** to load the workflow

### 2. Configure OpenAI Integration

1. Click on the **OpenAI Chat Model** node
2. In the **Credentials** field, click **Create New**
3. Enter your OpenAI API key
4. Set a name for the credential (e.g., "OpenAI API")
5. Click **Save**
6. Verify the model is set to `gpt-4o-mini`

### 3. Set Up Google Sheets Integration

1. Click on the **Google Sheets** node
2. Configure credentials:
   - Create new Google API credentials
   - Enable Google Sheets API in Google Cloud Console
   - Download the service account key
   - Add credentials to n8n
3. Update the `documentId` parameter:
   - Replace the existing ID with your Google Sheets document ID
   - Find this in your sheet URL: `https://docs.google.com/spreadsheets/d/[DOCUMENT_ID]/edit`
4. Configure the sheet name (default is "Tabellenblatt1")
5. Verify column mappings:
   - Name → Name
   - Review → Review

### 4. Configure Form Settings

1. Click on the **On form submission** node
2. Review form fields:
   - Name (required text field)
   - Your Review (required textarea)
3. Customize form title and description if needed
4. Note the webhook URL that will be generated

### 5. Test the Workflow

1. Click **Test workflow** to run a manual test
2. Use the form trigger to submit a test review
3. Check that:
   - Sentiment analysis returns a result
   - Data is written to Google Sheets
   - All nodes execute successfully

### 6. Activate the Workflow

1. Click the **Activate** toggle in the top right
2. The workflow is now live and ready to receive form submissions
3. Copy the webhook URL for integration with your website

## Configuration Options

### Customizing Sentiment Analysis

Edit the prompt in the **Basic LLM Chain** node:

```
You are an expert in sentiment analysis.
You conduct evaluations and determine which of the three options applies:

Positive
Negative
Neutral
You respond with only one word.
```

You can modify this to:
- Add more sentiment categories
- Include confidence scores
- Analyze specific aspects (product, service, etc.)

### Adding Email Notifications

To receive email notifications:

1. Add an **Email** node after the **Merge** node
2. Configure SMTP settings
3. Set up email templates with review data
4. Connect to the workflow

### Database Alternatives

Instead of Google Sheets, you can use:
- **Airtable** - For better data management
- **PostgreSQL** - For enterprise applications
- **MongoDB** - For document-based storage
- **Webhook** - To send data to your own API

## Troubleshooting

### Common Issues

**OpenAI API Errors:**
- Verify API key is correct and active
- Check OpenAI account has sufficient credits
- Ensure rate limits aren't exceeded

**Google Sheets Access Denied:**
- Verify API credentials are correctly configured
- Check that the service account has access to the sheet
- Ensure the document ID is correct

**Form Not Triggering:**
- Check webhook URL is accessible
- Verify form field names match node configuration
- Test with n8n's webhook test feature

**Data Not Appearing in Sheets:**
- Verify column mappings are correct
- Check sheet permissions
- Ensure data format matches expected schema

### Testing Individual Nodes

1. Use the **Execute Node** feature to test individual components
2. Check the **Execution Log** for detailed error messages
3. Verify data flow between nodes using the **Data Panel**

## Performance Optimization

- **Rate Limiting**: Add delays between API calls for high-volume processing
- **Error Handling**: Implement retry logic for failed API calls
- **Caching**: Store frequently accessed data to reduce API calls
- **Batch Processing**: Process multiple reviews in single requests when possible

## Security Best Practices

- Store all API keys in n8n credentials, never in code
- Use environment variables for sensitive configuration
- Implement input validation for form data
- Set up proper access controls for Google Sheets
- Regular backup of workflow configurations

## Next Steps

After setup, consider:
- Adding more sophisticated sentiment analysis
- Implementing data visualization
- Setting up automated reporting
- Integrating with other business systems
- Adding webhook endpoints for real-time updates

For additional help, consult the n8n documentation or community forums.