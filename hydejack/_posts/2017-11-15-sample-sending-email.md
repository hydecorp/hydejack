---
id: 73
title: 'Example: Sending Email'
date: 2017-11-15T09:03:53+00:00
author: Lucas
layout: post
guid: http://www.lucas-liu.com/?p=73
permalink: /2017/11/15/sample-sending-email/
categories:
  - Java
---
This is a sample template with the method of sending email.

[Github Link](https://github.com/Lucas12138/Sending-Email)

_Prerequisite: JavaMail_

<pre class="brush: java; title: ; notranslate" title="">import java.util.Properties;
import javax.mail.Message;
import javax.mail.MessagingException;
import javax.mail.PasswordAuthentication;
import javax.mail.Session;
import javax.mail.Transport;
import javax.mail.internet.InternetAddress;
import javax.mail.internet.MimeMessage;

public class SampleSendingEmail {

public static void sendMail() {
 final String username = "--from@gmail.com--";
 final String password = "--password--";

Properties props = new Properties();
 props.put("mail.smtp.starttls.enable", "true");
 props.put("mail.smtp.auth", "true");
 props.put("mail.smtp.host", "smtp.gmail.com");
 props.put("mail.smtp.port", "587");

Session session = Session.getInstance(props,
 new javax.mail.Authenticator() {
 protected PasswordAuthentication getPasswordAuthentication() {
 return new PasswordAuthentication(username, password);
 }
 });

try {

Message message = new MimeMessage(session);
 message.setFrom(new InternetAddress("--from@gmail.com--"));
 message.setRecipients(Message.RecipientType.TO,
 InternetAddress.parse("--to@gmail.com--"));
 message.setSubject("Hello World");
 message.setText("Test");

Transport.send(message);

System.out.println("Done");

} catch (MessagingException e) {
 throw new RuntimeException(e);
 }
 }

public static void main(String[] args) {
 sendMail();

 }
}

</pre>