---
title: "Python Text APP using Twilio API"
categories:
  - Projects
tags:
  - projects
  - python
  - programming
  - learning
---

![](https://www.fullstackpython.com/img/160511-send-sms-python/header.jpg)


## Twilio: 
Twilio allows software developers to programmatically make and receive phone calls and send and receive text messages(SMS) using its web service APIs. Twilio’s services are accessed over HTTP and are billed based on usage.

## Target:
Our Target is to make a python program to use Twilio API and send a SMS to a phone.

### Following are the Steps:

1. Create an account on [Twilio](https://twilio.com/).
2. Verify a Phone number on Twilio [from here](https://www.twilio.com/console/phone-numbers/verified). That you would like to SMS.
3. Get Twilio Credentials from [here](https://www.twilio.com/console) : 
    - Get Account SID
    - Get Auth Token

4. Get Phone Number:
    - Your Twilio Phone number is [here](https://www.twilio.com/console/phone-numbers/incoming)
    - Verified Cell Phone Number You Want To Text by clicking [here](https://www.twilio.com/console/phone-numbers/verified)

5. Put your twilio credentials and twilio phone numbers in ‘credentials.py’.
<script src="https://gist.github.com/AtriSaxena/2ce7e5fec837bb87bcb9af83b2c662c5.js"></script>
6. Clone the code from my [GitHub Repository](https://github.com/CoderAtri/Twilio_Sms_Python_App).

7. Open the terminal and install twilio python package:

<script src="https://gist.github.com/AtriSaxena/11a6138135595cf07456905c2b34811d.js"></script>

8. Create ‘send_sms.py’ & Run.

<script src="https://gist.github.com/AtriSaxena/c84dfddc930fbf416ee4d25950c8d66a.js"></script>

You just sent your first text through your Python Text App that uses the Twilio API. 

For any problem or issue please comment down. Please review about my post.
