+++
date = '2012-05-07'
title = 'Finishing Well'
+++

There are a lot of shops these days doing some cutting edge lifecycle management techniques like continuous deployment, A/B testing on the live site, deploying to prod at the end of every scrum and other new and exciting ideas. These techniques work well for very high volume sites that serve a large number of users, but we at the Vivaki Nerve Center are focused on delivering very high value to a very low number of users, at least relative to Google and Facebook. Our deployment cycle is bound to major milestones and negotiated features, and we sometimes find ourselves wanting to get features out in front of users first and then address cost of ownership and the burden on the production team in subsequent hotfixes or launches.

We are focused first on the value proposition, next on cost of ownership, and then on polish, maintainability, et cetera. This philosophy often has us making some tough choices to get a product into production and in the hands of our users while much of the quality control, monitoring, and other non user facing features are still being worked on. In a terrific lot of cases it makes sense to get something out and running before the entire system has been completed but we have to be even more careful than we would in a world with locked in scope and a checklist of acceptance criteria.

Issues I consider on a go-nogo decision include:

* What can we demonstrate about the stability of data delivery. If the QC or the monitors are not built, how will we detect problems? How will the production team be able to react to problems?
* What has been the error rate in our pre production or test environment? For how much time have we been able to run without tweaking the system.
* Without automated insight into the system, can the monitoring of this system be done without the aid of our expert production staff? What is the near term availability of our production experts?

* Will the lack of monitoring and automation simply affect the near term staff required to operate the system, or does this run the risk of delivering data that is late, or worse: incorrect?

It is one thing to require more staff or our more experienced production people to be on hand during a transitional phase, but getting the data wrong is a non starter. That is a situation up with which we will not put.

Once we do agree that moving forward is the right thing, and we get that juicy new data into prod, we are in a whole new risk situation: appearing to be finished when in fact there is much more to do. This requires new focus, and new level of maturity in people and processes. There are a significant number of issues to watch out for as the focus of our enterprise begins to shift toward the next big thing.

* What are the problems in front of us today? Are we going to need a hotfix right away?
* What are the sprint stories that we will complete before this project is done? What is their stack rank?
* How long do we think this transition period will need to last? Weeks? Months?
What is our plan for maintaining or retiring pre production test and dev environments?
    * Do we have good reason to run these systems after we complete transition?
    * When we do shut them down, what is our plan to stand them back up? How about in the context of an ememrgency hotfix?
* Does our leadership know that we are not done? We probably sent out a launch message, without any further communication, it might look like there is nothing more to do.

The opportunity to get features out before we otherwise would is of tremendous advantage. It helps us to foster the relationship we keep with our users and in some cases, allows revenue to start flowing earlier. We make sure that we follow up on the operational elements of our systems at the appropriate time and with appropriate focus. This allows us to watch total cost of ownership and the bottom line, and keeps well the important relationship we have with our colleagues on the production team.
