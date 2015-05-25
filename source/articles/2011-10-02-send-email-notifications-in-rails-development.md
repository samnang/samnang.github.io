---
title: Send Email Notifications in Rails Development
date: 2011/10/02
tags: Rails, MailCatcher, Letter Opener, letter_opener, MockSMTP
description: When there are features in your application that deal with sending email to users(eg. account activation, forget password). When you would like to test those features in your Rails development environment, then you probably go to running server's log to copy generated links in the sending email. Would you ever though any easier solution?
layout: post
---

When there are features in your application that deal with sending email to users(eg. account activation, forget password). When you would like to test those features in your Rails development environment, then you probably go to running server's log to copy generated links in the sending email, and how about when your managers would like to test them as well, then do they know how to go to the log to copy the links? And some other people use their real email addresses(eg. gmail) to receive the emails. Would you ever though any easier solution?

## 1. [MailCatcher](https://github.com/sj26/mailcatcher)
MailCatcher is a Ruby gem from Samuel Cochran. MailCatcher runs a super simple SMTP server which catches any message sent to it to display in a web interface.

### How    
    $ gem install mailcatcher
    $ mailcatcher -f
    Starting MailCatcher
	==> smtp://127.0.0.1:1025
	==> http://127.0.0.1:1080

Then set the delivery method in `config/environments/development.rb`

    config.action_mailer.delivery_method = :smtp
    config.action_mailer.smtp_settings = { :host => "localhost", :port => 1025 }

## 2. [Letter Opener](https://github.com/ryanb/letter_opener)
Letter Opener is a Ruby gem from Ryan Bates who run the awesome railscasts. Letter Opener previews emails in the browser instead of sending it.

### How
First add the gem to your development environment and run the bundle command to install it.

    gem "letter_opener", :group => :development

Then set the delivery method in `config/environments/development.rb`

    config.action_mailer.delivery_method = :letter_opener

**Note:** While I write this article, there are some people face an issue with nothing happen when sending email out. I found the problem because of Launchy dependency gem version. Because @ryanb hasn't specified version of Launchy dependency gem in gemspec file, then it won't install the new Launchy version if there is any old versions in local gems. I already sent a pull request, and hope it will fix soon.

## 3. [MockSMTP](http://mocksmtpapp.com/)
The third option that I haven't tried myself either is MockSMTP. MockSMTP is a native Mac application that embeds its own SMTP server.

### HOW
There is [a help page](http://mocksmtpapp.com/help) to tell you how to could configure your Rails applications to use with MockSMTP.

## UPDATE
[Dushyanth Maguluru](http://twitter.com/dushyanth_m) has added in his comment a couple of other ways by using ActionMailer interceptor or by writing your own mail delivery classes:

<http://asciicasts.com/episodes/206-action-mailer-in-rails-3>
<https://github.com/DushyanthMaguluru/custom_mail_delivery>
