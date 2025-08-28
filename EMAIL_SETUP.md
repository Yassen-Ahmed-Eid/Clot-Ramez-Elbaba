# Email Setup for ClotCare Emergency System

## Overview
The ClotCare system now automatically sends emergency email alerts when someone accesses the curing system page. This indicates a potential pulmonary embolism emergency.

## Setup Instructions

### 1. Gmail Account Setup
You need a Gmail account to send emails. If you don't have one, create one at [gmail.com](https://gmail.com).

### 2. Enable 2-Step Verification
1. Go to your Google Account settings: https://myaccount.google.com/
2. Click on "Security" in the left sidebar
3. Find "2-Step Verification" and click "Get started"
4. Follow the setup process to enable 2-Step Verification

### 3. Generate App Password
1. In your Google Account Security settings, find "App passwords"
2. Click on "App passwords"
3. Select "Mail" as the app and "Other" as the device
4. Click "Generate"
5. Copy the 16-character password that appears (it will look like: `abcd efgh ijkl mnop`)

### 4. Configure Email Settings
1. Open the `email_config.py` file
2. Replace the placeholder values with your actual information:

```python
# Your Gmail address (the one sending emails)
EMAIL_SENDER = "your-actual-email@gmail.com"

# Your Gmail app password (the 16-character password from step 3)
EMAIL_PASSWORD = "abcd efgh ijkl mnop"

# Email address to receive emergency alerts
EMAIL_RECIPIENT = "your-actual-email@gmail.com"

# Optional: Add additional recipients (uncomment and add email addresses)
ADDITIONAL_RECIPIENTS = [
    # "doctor@hospital.com",
    # "emergency@clinic.com"
]
```

### 5. Test the Email Function
1. Deploy your updated code to Railway
2. Visit the curing system page: `https://your-app.railway.app/frontend/curing.html`
3. Check your email for the emergency alert

## How It Works

1. **Automatic Trigger**: When someone visits the curing system page, it automatically sends an email
2. **Email Content**: The email includes:
   - Emergency alert subject line
   - Timestamp of when the system was activated
   - Clear indication of a potential PE emergency
   - Instructions to check the system

3. **Multiple Recipients**: You can configure multiple email addresses to receive alerts

## Security Notes

- **Never commit your email credentials to version control**
- The `email_config.py` file should be added to `.gitignore`
- Use app passwords, not your regular Gmail password
- The app password is specific to this application and can be revoked if needed

## Troubleshooting

### Email Not Sending
1. Check that 2-Step Verification is enabled
2. Verify the app password is correct (16 characters, no spaces)
3. Ensure your Gmail account allows "less secure app access" or use app passwords
4. Check the server logs for error messages

### Gmail Security Warnings
- If you get security warnings, check your Google Account activity
- You may need to approve the app password usage
- Consider using a dedicated Gmail account for this system

## Example Email Alert

```
Subject: 🚨 EMERGENCY: ClotCare Curing System Activated

🚨 EMERGENCY ALERT 🚨

The ClotCare Curing System has been activated!

Time: 2025-01-15 14:30:25

This indicates a potential pulmonary embolism emergency.

Please check the system immediately and take appropriate action.

---
ClotCare Emergency Response System
Automated Alert
``` 