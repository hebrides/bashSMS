bashSMS
=======

This is a simple bash script for sending SMS texts. You'll need sendmail. The providers listed are for the US. 
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

