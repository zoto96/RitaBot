---
title: "How to Update to 1.1.7 and Above"
permalink: /update/
excerpt: "How to Update."
last_modified_at: 2020-05-05T14:00:00+01:00   #Please Update, The +00:00 is the Time Zone difference
redirect_from:
  - /theme-setup/
toc: true

# Date formatting & Date Parsing - Let formatting and parsing date expressed in ISO8601 format.
# Can be obtained from https://dencode.com/en/date
# ---- Defined ----
# YYYY-MM-DD'T'hh:mm:ssTZD (e.g. 2015-12-11T20:28:30+01:00)
# YYYY = four-digit year
# MM = two-digit month (01=January, etc.)
# DD = two-digit day of month (01 through 31)
# hh = two digits of hour (00 through 23) (am/pm NOT allowed)
# mm = two digits of minute (00 through 59)
# ss = two digits of second (00 through 59)
# TZD = time zone designator (Z or +hh:mm or -hh:mm)
---

## How to Update to 1.1.7 and Above
#### 1. Checklist
* You must have a bot already running on your server, if not then refer to [Setting up a New Bot](#new-bot)

#### 2. Fork this Repo
* Complete a Pull Request from the master Branch of ZyC0R3/Rita to your master branch.
* Detailed instructions with example can be found here: https://www.sitepoint.com/quick-tip-sync-your-fork-with-the-original-without-the-cli/

#### 3. Deploy Update in Heroku
* Log in to your Heroku account.
* Select the bot you made in step 3 of [Setting up a New Bot](#new-bot)
* Under **Deployment Method** Scroll down to the manual deploy section, and select the **Master** branch. Click deploy branch, and wait for the successfully deployed message.
