bashSMS
=======

This is a simple bash script for sending SMS texts. You'll need sendmail: 
```
sudo apt-get install sendmail
```
Use it like this:
```
./sendSMS.sh 5555555555 < message.txt
```
5555555555 is the phone number to which you're texting. message.txt contains your message. See the file for formatting.

Script is below. The providers listed are for the US. The script tries every provider. 
```
#!/bin/bash
providers="@email.uscc.net
@message.alltel.com
@messaging.sprintpcs.com
@mobile.celloneusa.com
@msg.telus.com
@paging.acswireless.com
@pcs.rogers.com
@qwestmp.com
@sms.mycricket.com
@tmomail.net
@txt.att.net
@txt.windmobile.ca
@vtext.com"

for provider in $providers
do
  sendmail "$1$provider" < message.txt
done
```

