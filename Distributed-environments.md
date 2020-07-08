# A note

It's almost impossible to not find yourself operating in some type of distributed environment in 
most of today's (2020) SaaS sites. Even the simple relationship between your JavaScript client and
your backend servers introduces two systems operating independently, but who rely on some pre-arranged
schema.

# Deployment

1. Never assume that you can control the deployed version of your system in lock step
1. Plan for inconsistency in the versions you have deployed

Some strategies to mitigate the above,

1. Deploy backend changes before frontend changes, with backward compatible support
1. Dark launch your frontend to use the new backend to validate its working
1. Design your frontend to be forward compatible and not break if it gets something it doesn't understand
1. Design your backend likewise 
1. Monitor your deployed versions and alert when inconsistencies exceed a threshold
