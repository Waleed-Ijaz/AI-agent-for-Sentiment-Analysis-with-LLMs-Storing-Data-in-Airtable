# Sentiment Analysis Automation with n8n

An automated sentiment analysis workflow built with n8n that processes user reviews, analyzes sentiment using OpenAI's GPT model, and stores results in Google Sheets.

## 🚀 Features

- **Real-time Form Processing**: Collects user reviews through web forms
- **AI-Powered Sentiment Analysis**: Uses OpenAI GPT-4o-mini to classify sentiments as Positive, Negative, or Neutral
- **Automated Data Storage**: Saves results directly to Google Sheets
- **Webhook Integration**: Triggers automatically when new reviews are submitted
- **Merge Data Processing**: Combines form data with sentiment analysis results

## 🏗️ Architecture

The workflow consists of 5 main nodes:

1. **Form Trigger** - Captures user reviews via web form
2. **Basic LLM Chain** - Processes reviews through OpenAI
3. **OpenAI Chat Model** - Performs sentiment analysis
4. **Merge Node** - Combines original data with analysis results
5. **Google Sheets** - Stores final results

## 📋 Prerequisites

- n8n instance (cloud or self-hosted)
- OpenAI API key
- Google Sheets API access
- Google account with appropriate permissions

  
<img width="1330" height="488" alt="image" src="https://github.com/user-attachments/assets/daefb632-2369-475b-8fe5-70667e984fca" />

## 🔧 Setup Instructions

### 1. Import the Workflow

1. Download the `Sentiment_Analyse.json` file
2. In your n8n instance, go to **Workflows** > **Import**
3. Select the JSON file and import

### 2. Configure API Keys

#### OpenAI Configuration:
1. Go to the **OpenAI Chat Model** node
2. Add your OpenAI API key in the credentials
3. Ensure the model is set to `gpt-4o-mini`

#### Google Sheets Configuration:
1. Go to the **Google Sheets** node
2. Set up Google API credentials
3. Update the `documentId` to your target spreadsheet
4. Configure the sheet name and column mappings

### 3. Form Setup

The form collects:
- **Name**: User's name (required)
- **Review**: User's review text (required, textarea)

### 4. Activate the Workflow

1. Click **Activate** to enable the workflow
2. The webhook URL will be generated for form submissions

## 🔄 How It Works

1. **User submits form** → Form data is captured
2. **Review text extracted** → Sent to OpenAI for analysis
3. **Sentiment determined** → AI returns: Positive, Negative, or Neutral
4. **Data merged** → Original form data + sentiment result
5. **Results stored** → Written to Google Sheets

## 📊 Data Flow

```
Form Submission → Sentiment Analysis → Data Merge → Google Sheets Storage
```

## 🛠️ Customization Options

### Modify Sentiment Categories
Edit the prompt in the **Basic LLM Chain** node to change sentiment categories or add more detailed analysis.

### Add Email Notifications
Extend the workflow by adding email nodes to notify stakeholders of new reviews.

### Database Integration
Replace Google Sheets with other databases like Airtable, PostgreSQL, or MongoDB.

### Advanced Analytics
Add nodes for additional processing like:
- Keyword extraction
- Review scoring
- Trend analysis

## 📈 Use Cases

- **Customer Feedback Analysis**: Automatically process customer reviews
- **Product Feedback**: Analyze product reviews and ratings
- **Survey Processing**: Handle large volumes of survey responses
- **Social Media Monitoring**: Process social media mentions and comments

## 🔒 Security Considerations

- Store API keys securely in n8n credentials
- Use environment variables for sensitive data
- Implement rate limiting for public forms
- Regular backup of workflow configurations

## 📝 Google Sheets Schema

The workflow expects/creates the following columns:
- `Name`: User's name
- `Review`: Original review text
- `Sentiment`: AI-determined sentiment (Positive/Negative/Neutral)

## 🐛 Troubleshooting

### Common Issues:

1. **OpenAI API Errors**:
   - Check API key validity
   - Verify rate limits
   - Ensure sufficient credits

2. **Google Sheets Access**:
   - Verify API permissions
   - Check sheet sharing settings
   - Confirm correct document ID

3. **Form Submission Issues**:
   - Test webhook URL
   - Check form field mappings
   - Verify required fields

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- n8n community for the excellent automation platform
- OpenAI for providing powerful language models
- Google Sheets for reliable data storage

## 📞 Support

For issues or questions:
- Check the n8n documentation
- Review the workflow configuration
- Test individual nodes for debugging

---

**Note**: Remember to keep your API keys secure and never commit them to version control.
