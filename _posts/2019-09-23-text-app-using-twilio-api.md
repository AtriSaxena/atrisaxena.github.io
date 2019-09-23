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

5. Put your twilio credentials and twilio phone numbers in ‘credentials.py’

{% highlight python %}
account_sid = "Your Account Sid"
auth_token = "Your Auth Token"
my_cell = "+Your Cell Number"
my_twilio = "+Your Twilio Number"


{% endhighlight %}


6. Clone the code from my [GitHub Repository](https://github.com/CoderAtri/Twilio_Sms_Python_App).

7. Open the terminal and install twilio python package:

{% highlight python %}
pip install twilio

{% endhighlight %}

8. Create ‘send_sms.py’ & Run.

{% highlight python %}
from twilio.rest import Client
from credentials import account_sid, auth_token, my_cell, my_twilio
 
client=Client(account_sid,auth_token)
my_msg= "Here goes your message...." #Write your message
message=client.messages.create(to=my_cell, from_ = my_twilio, body=my_msg)

{% endhighlight %}

You just sent your first text through your Python Text App that uses the Twilio API. 

For any problem or issue please comment down. Please review about my post.
