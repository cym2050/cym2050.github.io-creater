---
title: "How the Internet Works"
date: 2020-07-31T22:11:54+08:00
draft: true
---


That was a little bit excessive but I'm very very excited to start the course.
So in this section we're going to be talking about browsing the web it's the first part in the How the Internet Works section,and some of you are thinking right now.Whoa, whoa, whoa Andrei,come on.I know how the Internet works.Let's get to the heavy, you know, technical stuff.But this is something that actually
took me quite a few years to learn.And I see a lot of people just skimming the surface of
this stuff without fully understanding how everything works together, without having those foundations it's
actually very, very difficult to think about performance,optimizing your sites and so on and so on.
So we're going to start off very, very basic and we're going to learn something
that took me many years to to learn and once I figured this out everything clicked so just hang in there
trust me, I promise you you'll learn something new in this section and we're going to be talking about
browsing the web.We have over here a laptop and we have our browser let's say Google Chrome and we typically like
to say, go to Google and we're going to visit Google so we type in Google.com Well what happens
technically when we do that? When we enter Google.com we press enter on our keyboard.We ask a question who's
this Google.com fellow? And that question gets asked all the way down to our ISP.
ISP is Internet Service Provider and I put a dollar sign up here just so you know those are
the people that you pay so you can have Internet.So if you're in the states that's Cogiko, Verizon.
If you're in Canada that'll be Bell or Rogers or you know, depending on your country you have your big big
companies that make a lot of money from Internet usage. So they get that request and they send that off
to something called the DNS server so Domain Name Servers and we'll get into that later on in the course.
So don't worry too much about it. But essentially it's a phone book - a phone
book that has the list of all these URLs like Google.com and it has the addresses
of them, so exactly like a phone book. They know where Google.com is so they say,
"Hey you know, I don't know Mr. Google.com personally, but I do know his address.
So you should go check him out."So they send off that request back through the ISP
and the website or the web browser, Google Chrome in this case gets "172.217.7.23" alright,
cool, but nothing is showing up yet.There's no there's no Google.com,
I can't do any searches yet. OK we receive - it's what
we call an IP address. So think of this as something that every single computer
has one, anything that's connected to the Internet has its own address so the laptop that I'm working
on right now an IP address, your laptop or computer has an IP address.
So this IP address allows the Internet to work essentially, it knows our location our address.
So what we do now with Google.com we know this IP address - the browser sends off another request
to the Google servers and it knows where the Google servers are because, well because we have this address
so we go seek it out and you can think of servers as computers essentially.
My laptop could be a server your computer could be a server.
Servers are essentially computers that are sometimes in basements or in huge server farms
and they have a piece of software running that just like at a restaurant where a server brings you food.
It knows how to send you files when you request for them.
So we send this off and the Google servers say oh yeah no problem,
let me give you my HTML CSS and Javascript and we'll get into what those are
later on in the course, but think of them as just text files. They are text files that Google is going to send
to the browser so we can have Google working. So let me just minimize this
and show you what it's doing. So we're copying these files and Google server's
saying yeah no problem thanks for asking for Google. Here it is.
And the web browser receives the HTML, CSS,and javascript.
So if we go to the next section boom we have google.com and everything's working.
Now that sounded like a whole bunch of stuff that happened in between and when we're on the internet
everything is quite fast but yet underneath the hood all of that is happening and it's crazy to think
how fast everything works.
Don't take my word for it.
Let's just check this process that
I'm not just making stuff up for you.
If what we learned was correct,
technically we can skip this process right.
I mean if we know the address of Google can we just,
you know, go into this directly and just instead
of putting Google.com, just put in this in our search
bar and it automatically goes to the Google servers.
Well let's try it out.
Let's let's open up Google here.
And ooh, what a pretty picture.
All right.
So we go to Google.com, nothing crazy here and
that's great but, what if instead of that I put in
the IP address so 172, there's no way I could
remember this address, so I've done this before
and I press Enter look at that, Google.com.
So as you can see, I'm not lying.
It's what's happening. The IP address gets sent to
the Google servers - Google servers sends us a few
files so that we can finally load Google.com. In
the next section we're going to do something fun.
We're going to break a bit of Google and - and toy
around with the webite again to show you how cool
all of this technology is.