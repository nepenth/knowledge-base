**Source:** [https://twitter.com/i/web/status/1868949757646774395](https://twitter.com/i/web/status/1868949757646774395)
**Original Post Date:** 2025-07-15 11:53:21

# Sending Emails with Python: Best Practices Using smtplib

## Introduction
Email marketing is a powerful tool for engaging customers and promoting products or services. In this article, we'll explore how to send emails programmatically using Python's `smtplib` module. We'll cover the essential components of sending an email, including SMTP server configuration, email headers, and body construction. By following best practices, you can ensure reliable email delivery and maintainability in your codebase.

## Importing Required Modules

To send emails using Python, we need to import the `smtplib` module. This module provides an interface to the Simple Mail Transfer Protocol (SMTP), which is used for sending emails across the internet.

_The `smtplib` module is imported to access SMTP functionality for sending emails._

```python
import smtplib
```

## Configuring Email Parameters

Before sending an email, we need to configure the necessary parameters such as the SMTP server address, subject line, sender and recipient email addresses, and the email body. These parameters are typically stored in variables for easy modification and reusability.

_Variables are defined for the SMTP server address, subject line, recipient and sender email addresses, and the email body._

```python
HOST = "smtp.mydomain.com"
SUBJECT = "Test email from Python"
TO = "mike@mydomain.com"
FROM = "python@mydomain.com"
text = "blah blah blah blah"
```

## Constructing the Email Body

The email body is constructed using a multi-line string that includes standard headers such as `From`, `To`, and `Subject`. The headers are separated from the email body by a blank line. This ensures proper formatting and readability of the email content.

_The email body is constructed as a multi-line string with proper headers and formatting._

```python
BODY = "\r\n".join((f"From: {FROM}", f"To: {TO}", f"Subject: {SUBJECT}", "", text))
```

## Connecting to the SMTP Server

To send an email, we need to establish a connection to the SMTP server. This is done using the `smtplib.SMTP()` constructor, which takes the SMTP server address as an argument.

_An SMTP server object is created to establish a connection to the SMTP server._

```python
server = smtplib.SMTP(HOST)
```

## Sending the Email

Once the connection to the SMTP server is established, we can send the email using the `sendmail()` method. This method takes the sender's email address, a list of recipient email addresses, and the email body as arguments.

_The `sendmail()` method is used to send the email with the specified sender, recipient, and body._

```python
server.sendmail(FROM, [TO], BODY)
```

## Closing the Connection

After sending the email, it's important to close the connection to the SMTP server. This is done using the `quit()` method, which ensures that resources are properly released and the connection is terminated gracefully.

_The `quit()` method closes the SMTP server connection._

```python
server.quit()
```

## Best Practices for Email Marketing with Python

When implementing email marketing campaigns using Python, it's essential to follow best practices to ensure reliable delivery and maintainability. This includes using environment variables or configuration files for sensitive information like SMTP server credentials, validating email addresses before sending, and handling exceptions gracefully to manage potential errors during the email sending process.

- Use environment variables or configuration files for SMTP server credentials.
- Validate email addresses before sending to avoid bounce backs.
- Handle exceptions gracefully to manage errors during the email sending process.
- Consider using libraries like `email` for more complex email formatting and attachments.

> **Note/Tip:** Always test your email sending functionality with a small batch of recipients before deploying to a larger audience.

> **Note/Tip:** Monitor the performance and delivery rates of your emails to ensure optimal results.

> **Note/Tip:** Comply with anti-spam regulations and provide an unsubscribe option in your marketing emails.

## Key Takeaways

- The `smtplib` module is essential for sending emails programmatically in Python.
- Properly configuring email parameters ensures accurate and reliable delivery.
- Constructing the email body with proper headers and formatting enhances readability.
- Establishing and managing SMTP server connections is crucial for successful email sending.
- Following best practices, such as using environment variables and handling exceptions, improves maintainability and reliability.

## Conclusion
In this article, we've explored how to send emails programmatically in Python using the `smtplib` module. By following best practices for email configuration, headers, and SMTP server management, you can ensure reliable email delivery and maintainability in your codebase. Implementing these techniques will help you create effective email marketing campaigns that engage customers and promote your products or services.

## External References

- [Python Documentation: smtplib](https://docs.python.org/3/library/smtplib.html)
- [Email Marketing Best Practices](https://www.emailmarketingbestpractices.com/)


## Media

**Image Description:** The image is a screenshot of a code snippet demonstrating how to send an email using Python. The title at the top of the image reads:

**"HOW TO SEND AN EMAIL WITH PYTHON"**

Below the title, there is a subtitle in parentheses:

**(UNDER 20 LINES OF CODE)**

The code is displayed in a terminal-like interface with a dark background and syntax-highlighted text. Here is a detailed breakdown of the code:

### **Code Breakdown:**

#### **1. Import Statement**
```python
import smtplib
```
- The `smtplib` module is imported. This module provides an interface to the Simple Mail Transfer Protocol (SMTP), which is used for sending emails.

#### **2. Variables for Email Configuration**
```python
HOST = "smtp.mydomain.com"
SUBJECT = "Test email from Python"
TO = "mike@mydomain.com"
FROM = "python@mydomain.com"
text = "blah blah blah blah"
```
- **HOST**: The SMTP server address (e.g., `smtp.mydomain.com`).
- **SUBJECT**: The subject line of the email.
- **TO**: The recipient's email address.
- **FROM**: The sender's email address.
- **text**: The body of the email.

#### **3. Constructing the Email Body**
```python
BODY = "\r\n".join((
    f"From: {FROM}",
    f"To: {TO}",
    f"Subject: {SUBJECT}",
    "",
    text
))
```
- The email body is constructed as a multi-line string using the `join()` method.
- The body includes:
  - `From:` header with the sender's email.
  - `To:` header with the recipient's email.
  - `Subject:` header with the email subject.
  - A blank line separating the headers from the body.
  - The actual text of the email.

#### **4. Connecting to the SMTP Server**
```python
server = smtplib.SMTP(HOST)
```
- An SMTP server object is created using the `smtplib.SMTP()` constructor, passing the SMTP server address (`HOST`).

#### **5. Sending the Email**
```python
server.sendmail(FROM, [TO], BODY)
```
- The `sendmail()` method is used to send the email.
  - **FROM**: The sender's email address.
  - **TO**: A list containing the recipient's email address.
  - **BODY**: The constructed email body.

#### **6. Closing the Connection**
```python
server.quit()
```
- The `quit()` method is called to close the connection to the SMTP server.

### **Visual Details:**
- The code is displayed in a terminal-like interface with a dark background.
- Syntax highlighting is used:
  - Strings are highlighted in yellow.
  - Keywords (e.g., `import`, `join`, `fro`, `to`, `subject`) are highlighted in green.
  - Variables and function names are in white.
- The top of the terminal interface shows macOS-style window control buttons (red, yellow, and green).

### **Purpose:**
The code demonstrates a simple way to send an email using Python's `smtplib` module. It is concise and adheres to the title's claim of being under 20 lines of code. The example is generic and uses placeholder values for the SMTP server, sender, recipient, and email content.

### **Key Technical Details:**
- **SMTP**: The Simple Mail Transfer Protocol is used for sending emails.
- **Headers**: The email includes standard headers (`From`, `To`, `Subject`).
- **Multi-line String**: The email body is constructed using a multi-line string with proper formatting.
- **Connection Management**: The SMTP server connection is properly opened and closed.

This code serves as a basic template for sending emails programmatically in Python.
![The image is a screenshot of a code snippet demonstrating how to send an email using Python. The tit...](./media/image_1.jpg)