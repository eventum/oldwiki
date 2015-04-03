---
title: Eventum:Setting up email routing with qmail
permalink: /Eventum:Setting_up_email_routing_with_qmail/
---

== Quick Notes ==

When you're setting up Eventum's [Email Routing Interface](/Eventum:Email_Routing_Interface "wikilink") for qmail, use these options in the Administration -\> General Setup area:

`Email Routing Interface: Enabled`
`Recipient Type Flag: [doesn't matter, choose any]`
`Email Address Prefix: issue-`
`Address Hostname: [the domain name of the email address issues should be sent to]`
`Warn Users Whether They Can Send Emails to Issue: [doesn't matter, choose any]`

In your /var/qmail/control/virtualdomains, add the line:

`yourdomain.com:eventum`

Then reload your qmail (as root):

`# svc -t /service/qmail-send`

NB: The reload procedure may vary depending on your qmail installation.

That directs all of the incoming emails for issue-xyz@yourdomain.com to the unix account called "eventum" on the mail server.

### \~/.qmail files

for mails being pushed to eventum you need to create \~/.qmail-\* files:

`.qmail-issue-default - handles issue-XXX@yourdomain.com mails`
`.qmail-note-default - handles note-XXX@yourdomain.com mails`
`.qmail-draft-default - handles draft-XXX@yourdomain.com mails`
`.qmail-default - catchall address for @yourdomain.com mails`

the files contents should in general invoke route_TYPE.php file from Eventum installation. For example \~/.qmail-issue-default:

`cd /usr/share/eventum && /usr/bin/php route_issues.php`

You may use [<http://cvs.pld-linux.org/cgi-bin/cvsweb.cgi/SOURCES/eventum-router-qmail.sh> this](/http://cvs.pld-linux.org/cgi-bin/cvsweb.cgi/SOURCES/eventum-router-qmail.sh_this "wikilink") script from [<http://www.pld-linux.org/> PLD Linux](/http://www.pld-linux.org/_PLD_Linux "wikilink") to do so. Additionally to invoking the PHP scripts that script maps the postfix style exit codes to qmail exit codes.