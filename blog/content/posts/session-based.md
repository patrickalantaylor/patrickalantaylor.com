+++
date = '2012-07-14'
title = 'A Journey Into Session Based Test Management'
+++

**Installment 1: On Test Cases**
One of the core values of our QA practice at the Vivaki Nerve Center is Intellectual Honesty. It is an aesthetic that we strive for truthfulness in our work and our communications and give the most accurate, least obfuscated information possible even when it is the harder thing to do.

With that I have been driven to rethink our practice of test documentation and test cases. One of the most common questions from partners and leadership is what percentage of test cases are complete and what percentage of test cases are passing? On the surface this seems to be a reasonable metric for progress and results of test activity on a project. At least until we start to notice:

* When running a test we often find bugs that are unrelated to the thing that we were looking for.
* A test case could represent anywhere from 60 seconds to 60 days worth of work.
* If testing every permutation of a product is impossible, documenting every permutation is impossible-squared.

Once upon a time, I wrote test cases like this

>[title]  
Confirm that doing a thing brings a specific condition  
[steps]  
1 do something  
2 do something  
3 do something  
[expected result]  
Expect something  

If you don’t get what you expected, you have a bug. Go ahead and copy those steps into a bug.

All of the thought and insight was supposed to go into test documentation. Test execution was expected to be a mechanical process. But that comes with some problems (see above)

These days we write test cases that read more like this

>[title] 
Verify “functional area”  
[body]  
confirm that feature or function is congruent with functional and non-functional requirements published in spec document or acceptance criteria.  

This style of documentation is less overhead; but I have come to realize that these are not even really test cases. There is no traceable pass or fail criteria; there is no expected result; there are no concrete instructions. And for good reason, for test cases don’t really make sense (see above above)

With that in mind, we are experimenting with the use of test charters rather than test cases. In Session Based Test Management, the test charter is one of the core artifacts of test planning and sets the goal or agenda for an exploratory test session. With the language of a charter we are able to have much more freedom to speak directly to what types of testing will be done and to what depth we will be doing it. Our team is highly entrepreneurial, and has a strong practice of exploratory testing in our applications. We know that most of the bugs that we find are the result of tester intuition and expertise rather than scripted, blind action and that we do many different kinds of testing simultaneously.

Here are some of our first examples

> Explore processing of data from source to target with small data sets with normal business data
Explore processing of data sets from source to target with large data sets in normally sized text files, with normal business data
Explore processing of data from source to target with normally sized data sets with very large files
Explore processing of data sets from source to target with small data sets in normally sized text files, with abnormal and boundary business data

Even in the first test planning meeting when we came up with these, a few differences became immediately apparent.

It was easier to write a test charter than a test case because it more naturally describes what we actually plan to do.
There was much less boilerplate and fluff in the charters we were writing.
The discussions that arose from the writing these charters were about testing. Instead of talking on verbiage, semantics or standards; we talked about functional boundaries, equivalency classing, and risk areas.

We are tremendously excited about the potential of this technique. As we continue to explore and refine our implementation of it here, we will keep posting our experience on the strengths weaknesses, pitfalls and pratfalls. so stay tuned… [EDIT] Now posted! Installment 2: [Test Charters in Practice](../charters/)

*This article was written as part of work I did at the Vivaki Nerve Center, part of the Publicis Groupe. Its original archive can be found at [https://web.archive.org/web/20160624051900/http://www.qathedata.com/blog/2012/06/14/on-test-cases/](https://web.archive.org/web/20160624051900/http://www.qathedata.com/blog/2012/06/14/on-test-cases/)*
