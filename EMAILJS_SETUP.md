# EmailJS Setup Instructions

This project uses EmailJS to send contact form emails directly from the frontend. Follow these steps to set it up:

## Step 1: Create an EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Sign up for a free account (free tier includes 200 emails/month)

## Step 2: Create an Email Service

1. In the EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail, Outlook, etc.)
4. Follow the setup instructions for your provider
5. Note down your **Service ID**

## Step 3: Create an Email Template

1. Go to **Email Templates** in the dashboard
2. Click **Create New Template**
3. Use the following template structure:

**Subject:** New Contact Form Submission from {{from_name}}

**Content:**
```
Hello,

You have received a new message from your website contact form:

Name: {{from_name}}
Email: {{from_email}}
Company: {{company}}
Message: {{message}}

---
This email was sent from your website contact form.
```

4. Set the **To Email** field to: `hamad.sipra@inferatech.net`
5. Set the **From Name** field to: `{{from_name}}`
6. Set the **Reply To** field to: `{{from_email}}`
7. Save the template and note down your **Template ID**

## Step 4: Get Your Public Key

1. Go to **Account** → **General**
2. Find your **Public Key** in the API Keys section
3. Copy the public key

## Step 5: Configure Environment Variables

1. Create a `.env` file in the root of your project (copy from `.env.example`)
2. Add your EmailJS credentials:

```env
VITE_EMAILJS_SERVICE_ID=your_service_id_here
VITE_EMAILJS_TEMPLATE_ID=your_template_id_here
VITE_EMAILJS_PUBLIC_KEY=your_public_key_here
```

3. Replace the placeholder values with your actual credentials

## Step 6: Restart Your Development Server

After adding the `.env` file, restart your development server:

```bash
npm run dev
```

## Testing

1. Fill out the contact form on your website
2. Submit the form
3. Check your email (hamad.sipra@inferatech.net) for the message
4. You should receive an email with all the form details

## Troubleshooting

- **"Configuration Error"**: Make sure all three environment variables are set in your `.env` file
- **Emails not sending**: Check the browser console for error messages
- **Template variables not working**: Make sure your template uses the exact variable names: `{{from_name}}`, `{{from_email}}`, `{{company}}`, `{{message}}`
- **Rate limiting**: The free tier has a limit of 200 emails/month. Upgrade if you need more.

## Security Notes

- The `.env` file should be added to `.gitignore` to keep your credentials secure
- Never commit your `.env` file to version control
- The public key is safe to use in the frontend, but keep your service and template IDs private in production

