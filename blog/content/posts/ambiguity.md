+++
date = '2012-12-13'
title = 'Embracing Ambiguity'
+++

What we are here to do in QA is to help the team to develop the highest quality product inside the shortest possible time with the lowest possible cost. We test software, not to prove its fitness or to pass or fail test cases. We test software to avoid the pain and cost of delivering a product that is too expensive to maintain, or too unstable to provide utility to our users.

It is natural to take these rather ambiguous goals and to unpack them into more concrete and verifiable terms; but it is important to remember that the thing that we are aiming for at the end of the launch is inherently ambigious.

We recently had a project in which we knew that data had to be delivered within an acceptable time window and that the volume and the complexity of the data was prone to vary wildly.

The script for the original conversations with our users were essentially like this:

ANALYST. 
So when do you need the figures from last night to be available in your report?  
USER. 
Well, as soon as you can get it!  
ANALYST. 
Yes, but it might take a year to build the system to have it ready by 3:00 AM, and then you don’t really need it until you come in at 9.  
USER. 
A year?  
ANALYST. 
Yeah, maybe it depends on too much that we just don’t know yet about the feed.  
USER. 
Well I need it before 9.  
ANALYST. 
OK good, how much before?  
USER. 
Well many of us actually get into the office at 8 and we really need to get cracking, and on some days, we have a meetings at 9 that take a lot of prep. And Susan sometimes gets in at 7. but I don’t know how much analysis she does at that hour…. 
ANALYST  
So how about we say that we will have the data by 8 and we see how that works for you over the first quarter after deployment.  
USER  
Ok sure  

And that is how most of the analysis in defining a product is done. It is as much psychology and negotiation as it is documentation. And with full knowledge of how this conversation went, I would not start squawking too loudly when data is coming in at 8:05 unless that started climbing.

What is required in systems like this, is more than the ability to read and understand a software requirement document or a story’s acceptance criteria. It is the ability of a tester to know the system, and understand the user. There are ranges of acceptable behavior, the boundaries of which are fuzzy. Even more, there are tradeoffs in what is right. I bet that user would be fine with getting the data at 9:00 if it was there every single morning and it only took 10 seconds to cut and paste into a report. So consistency, ease of use and query time is going to be a factor in delivery time.

This is not an instruction to cut corners, this is an attempt to gain the understanding that a system does not necessarily succeed at 7:59 and fail at 8:01. The definitions of our success are qualitative. Often in the interests of doing that which is doable, we will put quantitative criteria on our goals. But those goals are often a proxy.

For that matter, it is Quality Assurance; not Quantity Assurance.

*This article was written as part of work I did at the Vivaki Nerve Center, part of the Publicis Groupe. Its original archive can be found at [https://web.archive.org/web/20160623201606/http://www.qathedata.com/blog/2012/12/13/embracing-ambiguity/](https://web.archive.org/web/20160623201606/http://www.qathedata.com/blog/2012/12/13/embracing-ambiguity/)*
