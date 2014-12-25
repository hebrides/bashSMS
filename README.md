bashSMS
=======

This is a simple linux shell script for sending SMS texts at regular intervals. To use it, you'll need the *sendmail* command: 
```
sudo apt-get install sendmail
```
Script is below. The providers listed are for the US. (The script tries every provider.)
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

Make sure to set permissions for executing the script:
```
chmod u+x sendSMS.sh
```

And use it like this:
```
./sendSMS.sh 5555555555 < message.txt
```
where *5555555555* is the phone number of the person to whom you're sending the text. *message.txt* contains your message. Format *message.txt* without a `subject:` line.
```
from: hebrides@smgmobile.com
Hi, this is a text message, just for you :-).
.
```

For scheduling, do:
```
crontab -e
```
And add:
```
55 20 * * 2,4 /path/to/script/sendSMS.sh 5555555555 < /path/to/message/message.txt >> /dev/null 2>&1
```
This will send the message every Tuesday and Thursday at 8:55 p.m. See the comments in your crontab file for scheduling syntax.
The `/dev/null 2>&1` prevents cron from sending an email if the text bounces.








