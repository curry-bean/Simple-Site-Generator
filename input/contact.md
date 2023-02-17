# Contact Us

If you have any questions or comments, please feel free to contact us using the form below.

[insert contact form here]

# Contact Us

If you have any questions or comments, please feel free to contact us using the form below.

```csharp
using System;
using System.Net.Mail;

string senderEmail = "your-email@your-domain.com";
string recipientEmail = "admin@your-domain.com";
string subject = "Contact Form Submission";
string body = "Name: John Doe\r\nEmail: john.doe@example.com\r\nMessage: Hello!";

MailMessage message = new MailMessage(senderEmail, recipientEmail, subject, body);
SmtpClient client = new SmtpClient("smtp.your-domain.com", 587);
client.Credentials = new System.Net.NetworkCredential("username", "password");
client.EnableSsl = true;

try
{
    client.Send(message);
    Console.WriteLine("Message sent successfully.");
}
catch (Exception ex)
{
    Console.WriteLine("Error sending message: " + ex.Message);
}
