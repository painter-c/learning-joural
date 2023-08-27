## Terms and Definitions
*Mail Server* - Handles sending, receiving and storing of email messages


## Notes
- **Simple Mail Transfer Protocol (SMTP)** is used for sending messages to a mail server
- **Mail servers** handle sending, recieving, and storing of email messages
- While SMTP is used for outgoing emails, **Post Office Protocol Version 3 (POP3)** and **Internet Message Access Protocol (IMAP)** are used for incoming messages
- A mail server has three major components, an **incoming** component, an **outgoing** component, and a **storage** component
- Email clients communicate with emails stored on a mail server through outgoing email protocols such as POP3 and IMAP
- One reason to send emails using an email service provider is because they have good IP reputation
- Sending an email through SMTP directly to a recipient mail server risks being marked as spam or IP blacklisted
- Email service providers manage authentication to ensure the legitimacy of senders
- A **DNS MX Record** directs emails sent to a particular domain to a particular mail server
- A DNS MX Record is typically registered through a dns provider such as GoDaddy or Cloudflare

## SMTP
- Facilitates the transmission of emails between a client and server
- In this case, the client is the sending email server, and the server is the receiving email server
- A functioning SMTP server should have both client and server functionality
- Doesn't specify how emails are queued or stored on the receiving server
- SMTP servers typically use port 25 or 587
- SMTP servers are responsible for filtering spam and blacklisting certain senders
- An email client must have the domain name or ip address of an SMTP server

## Reputation
- Domain reputation is based on how other email providers have interacted with your email domain (@domain.xyz)
- IP reputation is based on how other email providers have interacted with the sender IP address
- End users will typically use an email service provider because the provider will take on the responsibility of maintaining domain and ip reputation, so the users emails do not get blocked

## Spoofing and Countermeasures
- The sender of email addresses can be easily spoofed by modifying the "From" field of an email header
- SMTP provides no method to validate the authenticity of an email's sender