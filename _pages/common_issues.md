---
title: "Common Issues"
permalink: /common-issues/
excerpt: "Common Issues with Rita"
last_modified_at: 2021-02-01T14:00:00+01:00   
redirect_from:
  - /errors/
toc: true


---

## __**Common Issues**__

Common issues found with Rita and solutions


# `!t embed` command must be sent daily to continue translations 
     * A. **How to fix** - Run these commands in order:
`!t settings dbfix`
`!t settings updatedb`
`!t embed` with parameter of on or off (`!t embed off` , `!t embed on` 


# Bot is unresponsive (does not send response at all) and shows as online
     *  A. **How to fix** - Deploy your Bot again in Heroku from your github branch (if you dont have a branch then fork the repo and connect it to your Heroku Deploy Method). Bot will then function and begin responding


# Bot only repeats ***Bot Restarted*** message when sending commands 
     * **How to fix** - Run the command `!t embed on` or `!t embed off` (they are two different styles, try both out! You can change the style at any time

If you require more assistance join our [Discord Server](https://discord.gg/mgNR64R)
