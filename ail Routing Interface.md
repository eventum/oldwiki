Overview
--------

Starting with Eventum 1.5.2, the email routing interface is a new (optional) way to automatically associate emails, notes and drafts with an Eventum issue. By setting up the mail server (MTA) to pipe emails sent to a specific address (usually issue+<number>@<domain>, note+<number>@<domain> and draft+<number>@<domain>) into PHP scripts, users are able to use their email clients to reply to emails coming from Eventum, and those replies will be automatically associated with the issue and broadcast to the issue's notification list.

The scripts automatically save a copy of the message for archival purposes in a separate directory, so you would never lose the emails. Create a 'routed_emails' subdirectory under /path-to-eventum/misc/ and setup the proper permission bits on it.

Setup
-----

These pages contain information on setting up the email routing interface:

-   [Doing a fresh install](Eventum:Doing a fresh install "wikilink")
-   [Setting up email routing with Sendmail](Eventum:Setting up email routing with Sendmail "wikilink")
-   [Setting up email routing with qmail](Eventum:Setting up email routing with qmail "wikilink")
-   [Setting up email routing with postfix](Eventum:Setting up email routing with postfix "wikilink")
-   [Setting up email routing with exim](Eventum:Setting up email routing with exim "wikilink")
-   [Setting up email routing with 1 email account for multiple projects](Eventum:Setting up email routing with 1 email account for multiple projects "wikilink")
