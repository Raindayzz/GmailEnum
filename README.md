# GmailEnum
This is a tool I created based on a recent penetration test where the client enumerations had some ip lockouts and I didn't want to proxy a bunch of requests.

This was inspired and only created due to : https://blog.0day.rocks/abusing-gmail-to-get-previously-unlisted-e-mail-addresses-41544b62b2

This was something that @x0rz discovered and google wrote it off as normal so we must abuse lol.

Remember this is a Google Suite Account Enumeration Tool using magic 

This is a fundamental abuse of a non rate-limited enpoint https://mail.google.com/mail/gxlu. We can fuzz a load of usernames and if a cookie is returned, the account is valid.


This program needs the three following:
 - -f = inputFilename (this can be usernames or emails)
 - -d = domain of email (ie: gmail.com or company.com)
 - -o = output of the valid accounts will be written to file

In regards to the input file, it has some logic that can detect if it's just usernames and add the domain or you can provide the emial list instead. Either way, make sure they are normalized.  


Examples:
`python3 gmailEnum.py -f users.txt -d gmail.com -o ValidAccount.txt`