# AI Prompt & Email Template Guide

## AI Prompt for Email Templates

**Effective Prompt Structure:**
```
Please enhance the design and styling of the email template to match the attached design exactly. 
Ensure that all elements are consistent with the provided layout. 
I need a clean, fully HTML email template with no external frameworks—pure HTML and inline CSS only. 
Provide the complete, ready-to-use output.
```

## Key Prompt Requirements
- **Specificity:** Match design exactly
- **Constraints:** Pure HTML + inline CSS only
- **Output:** Complete, ready-to-use template
- **No frameworks:** Avoid Bootstrap, Tailwind, etc.

## Email Template Best Practices

### Technical Requirements
- **Inline CSS:** All styles must be inline for email client compatibility
- **Table-based layout:** Use `<table>` for structure (not div/flexbox)
- **Image optimization:** Include alt text and fallbacks
- **Mobile responsive:** Use media queries sparingly

### Essential Elements
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Email Template</title>
</head>
<body style="margin:0; padding:0; background-color:#f4f4f4;">
  <table width="100%" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="padding: 20px;">
        <table width="600" cellpadding="0" cellspacing="0" style="background-color: #ffffff; border-radius: 8px;">
          <tr>
            <td style="padding: 40px; text-align: center;">
              <h1 style="color: #333; font-family: Arial, sans-serif; margin: 0 0 20px 0;">Welcome!</h1>
              <p style="color: #666; font-family: Arial, sans-serif; font-size: 16px; line-height: 24px; margin: 0 0 30px 0;">Thank you for joining us. We're excited to have you on board.</p>
              <a href="#" style="background-color: #007bff; color: #ffffff; text-decoration: none; padding: 12px 30px; border-radius: 5px; font-family: Arial, sans-serif; font-weight: bold; display: inline-block;">Get Started</a>
            </td>
          </tr>
        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

### Email Client Compatibility
- **Outlook:** Requires table-based layouts
- **Gmail:** Limited CSS support
- **Mobile:** Test on iOS/Android mail apps
- **Web clients:** Yahoo, Hotmail variations

## Summary
Email templates need pure HTML with inline CSS, table-based layouts, and extensive testing across email clients. AI prompts should specify exact design matching and technical constraints.