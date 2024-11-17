
+++
date = '2013-07-13'
title = 'Focusing and Defocusing'
+++

I have been lucky enough to do some on-the-ground coaching with our test staff over the last couple of weeks and I was reminded about the unique issues involved with getting from suspected problems or code smells to isolated and replicable bugs. There are many cases in which we see something a first that appears to be an problem and turns out to be either bigger or smaller than it seemed.

Take one case in which a spending report shows a distinct but nominal difference when comparing year over year figures.
|Target 	| Reference |
|----------|----------|
|2011 	|$16,985,654.53 	|$17,243,742.53|
|2012 	|$23,782,198.21 	|$24,170,161.15|


There is no doubt that there is a difference, but it is in the neighborhood of 1%. If this difference is consistently low at all levels of aggregation it will be of little concern for reporting purposes. So do we ignore it let it be or do we write a bug? And here is where we get to problem isolation: one of the most useful things that we can do in software testing. One of the most useful techniques in this is focusing and defocusing concepts that are used in the practice of Rapid Testing  http://www.developsense.com/courses/RapidSoftwareTesting.pdf

Focusing and defocusing is a way of looking at the situation in front of us and see software in different and useful ways. The idea is very much a metaphor which I find myself describing as: drilling in - stepping back, or details - aggregates, accuracy - reliability, and other terms.

In our business we focus and defocus along lots of vectors including:

>from coarse to fine (aggregation)  
from simple to complex  
from many descriptors (dimensions) to without descriptors  
from technical accuracy to business usefulness  
from tightly structured to loose  

When we look at the systems both in working and breaking scenarios. Here are some of the questions that we ask:

Focusing questions:

>Does the data change in accuracy by applying more dimensions? (finer aggregations)  
Can I look at a smaller slice of time?  
What are my expectations of the accuracy of the data at the source?  
Is the source that I am comparing the same source that the system is consuming?  
Where in the chain of processing am I looking?  
Can I remove measures or facts? Does that change anything?  
How could data be excluded?  
How could data be inflated?  
How does this look  
How would this data look in a table?  
What can be eliminated?  
Is there a hierarchy? how do I get to the bottom?  
and more…  

Defocusing questions:

>Does the data change in accuracy by removing dimensions? (coarser aggregations)  
Can I look at a larger slice of time?  
At what stage of processing am I looking at the data?  
Can I remove measures or facts? Does that change anything on those that remain?  
What are my expectations about the state of processing? Is processing complete, is it incomplete? How can I tell?  
Can the data be off but within tolerance? What informed that tolerance?  
Is the data processed in scheduled jobs or in a continuous flow?  
How long has the data been processing?  
How would this data look graphically?  
How does this look for other categories or clients?  
Is there a hierarchy? how do I get to the top?  
What can I add to this?  
and more…. 

And then some things that fit alongside focus-defocus but not within them:

>If the data looks wrong, what could change to make it look right?  
If the data looks right, what could change to make the data look wrong?  
Do colleagues assert that the data is correct or incorrect? Do I agree?  

Let’s go back to our hypothetical nominal 1% discrepancy. If we focus in by applying a country dimension, we might see something like this:
|Country 	|Target 	|Reference|
|----- | ----- | ----- |
|US 	|$9,593,427.23 	|$9,593,427.23|
|UK 	|$3,395,767.34 	|$3,395,767.34|
|FR 	|$1,342,834.49 	|$1,342,834.49|
|DE 	|$1,638,256.37 	|$1,638,256.37|
|ES 	|$- 	|$258,088.00|
|AU 	|$1,015,369.10 	|$1,015,369.10|
|TOTAL  	|$16,985,654.53 	|$17,243,742.53|


Now this tells a very different story right away. Although the total for the year is within an acceptable margin of error, it is because the value for Spain is missing entirely! Looking from this point of view, there is little question if this is a bug.

So think about these 2 different bug titles:

**1% variance in 2011 spend**

**Spend for Spain is missing entirely from 2011 report**

Which one of these is going to get the attention of our developers and analysts?

*This article was written as part of work I did at the Vivaki Nerve Center, part of the Publicis Groupe. Its original archive can be found at [https://web.archive.org/web/20160624022028/http://www.qathedata.com/blog/2013/07/17/focusing-and-defocusing/](https://web.archive.org/web/20160624022028/http://www.qathedata.com/blog/2013/07/17/focusing-and-defocusing/)*
