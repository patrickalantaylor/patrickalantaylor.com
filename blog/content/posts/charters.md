+++
date = '2012-08-27'
title = 'A Journey Into Session Based Test Management: Test Charters'
+++
### Installment 2: Test Charters in Practice

In our initial installment of SBTM posts I discussed the problems that I see with the classic test case approach. Test cases end up being a deluge of detail and are tedious to follow and document. Even in an ideal setting where we are able to specify exactly what will be done and do exactly what we specify, the picture will always be incomplete.
Consider this story: A tester is executing a case for a new feature. This feature takes two values from a source database, sums them and writes the result to a target data warehouse. A test case is written that instructs the tester to query the source, manually add up the values, and then look at the target to see that the calculated and recorded value is correct. If the tester can confirm that the value is correct. A simple examination says that the case passes and the tester can move on. But the value can be correct and still not be valid. There could be problems that show up in all kinds of ways that this case does not address:

* Wrong precision
* Data in the target is a week behind the data in the source
* Some values work, other values will be incorrect
* Some values work, other values will cause a crash
* Some fields will work for some values but other fields will break on the same values
* Updates to the source do not trigger updates to the target

In this particular case, we can certainly take all of the scenarios that we were able to imagine when writing the test case and write new cases to account for them. Now instead of one case we have something north of a dozen, and much of the text in these cases will be redundant. Further, our experience in testing says that there are always things about an application that we are unable to consider until we see the application itself. Those unknown-unknowns that trip things up as we go are the most difficult to account for.

When a professional software tester sees a problem when running a case she will most certainly write up a bug for what she saw, but if that bug is not related to what the case was looking for, does that case pass or fail? Should we write up another case that we can mark as failed if the original case is marked as passed? Or should we accept the possibility of 100% of cases passing while there are open bugs in the system? With the constant pressure in today’s business to do more with less, it seems foolish to spend more time doing paperwork and less time testing, but if we have the expectation that every possible bug has a pass or fail check documented in a test case, we are going to do a lot of paperwork. To combat this dilemma, We are adapting practices of session based testing as outlined by Jonathan and James Bach.
[Wikipedia article on SBTM](https://web.archive.org/web/20160623235057/http://en.wikipedia.org/wiki/Session-based_testing)
[Jonathan Bach’s original article on the subject](http://www.satisfice.com/articles/sbtm.pdf)

The central planning artifact of the session based approach is the Test Charter. A test charter sets the scope and goals of a test session. We write up the charters we see as early in the project as we can so that we can get a sense of the total coverage that we will manage. While the scope or granularity of a charter is not strictly defined, we attempt to have a single charter represent 60-120 minutes of focused, uninterrupted test activity.

When list them out, we try to have the charters directly describe what the tester will be doing, and what conditions we are looking for. Here are some examples for an ETL/data warehousing project we are currently running:

>supply a jagged dataset at the source (uneven number of columns per row)
supply delimiters inside text fields
supply mismatched data for the datatypes (text in numeric fields, numbers in boolean fields, etc.)
supply bad or missing data headers
supply sources in different character encodings (ANSI, UTF-8, Latin-1 or others)
supply maximum values for each datatype (2147483647 for ints, max length on all strings)
supply dimensions that do not have facts and facts that do not have dimensions
supply files that have a high degree of duplication


In the body of a charter we will also put any known prerequisites to beginning a session to cover that charter and other considerations that will be of interest to the tester that will be executing a session based on that charter. When is becomes time to run, a tester then picks up a charter, does the necessary prep, blocks time without meetings or distractions and begins work. In using this technique for just a bit more than a month, we are finding that this approach gave a number of benefits right out of the gate:

* Reduced paperwork
* Stakeholders better understand the details of the test planning and intent
* We talk in terms of risk rather than percentage complete
* Important features or inputs get appropriate visibility
* Focusing time to do nothing but testing is not only more productive, but more satisfying.

And perhaps the most useful thing about using charters is that it allows us to roll up to detailed and honest reports that can give every stakeholder from individual contributors to executives a a direct and accurate view on progress and risk.

Part 3: The SBTM Dashboard


*This article was written as part of work I did at the Vivaki Nerve Center, part of the Publicis Groupe. Its original archive can be found at [https://web.archive.org/web/20160623235057/http://www.qathedata.com/blog/2012/08/27/test-charters-in-practice/](https://web.archive.org/web/20160623235057/http://www.qathedata.com/blog/2012/08/27/test-charters-in-practice/)*
