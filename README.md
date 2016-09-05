# Docs Like Code

## Us...

I've been using "docs like code" techniques for multiple projects in
multiple contexts from open source software docs to blog posts to
enterprise documentation sites.

## You...
I know you. You want to learn and experiment with improving documentation by
changing the way you think about docs? Then here is your opportunity to
prove you can moderinize your docs.

You need to know about docs like code, what is it? Why would you apply the
techniques behind docs like code? You need a tutorial and a quick set
of wins to prove to yourself and your team that your docs are ready
for a new mindset, a new toolset, and a new docset. Let's go.

## Notes

To Setup a custom domain for a gh-pages Project Pages repo that handles www.yourdomain.com and yourdomain.com (assumes you already have a gh-pages branch on your repo):

From your project repo, gh-pages branch. Create a CNAME file with the contents yourdomain.com. Commit then push.
In your DNS manager, setup two cname records. One for the root apex (@) and one for www. Both point to YOURusername.github.io. If your DNS provider does NOT support ALIAS records on the root apex (@), simply create A records that point to 192.30.252.153 and 192.30.252.154
Wait til your name servers update:

dig yourdomain.com +nostats +nocomments +nocmd

## Theme Colophon
Theme courtesy of https://mmistakes.github.io/so-simple-theme/
