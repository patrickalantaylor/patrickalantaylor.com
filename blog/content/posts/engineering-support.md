+++
date = '2023-05-09'
title = 'Is GitHub Copilot Worth It?'
+++
Although there are multiple AI coding assistant plugins in different stages of development right now in the industry, the release of GitHub’s Copilot as a paid product made the biggest splash in the community so far.

AI coding assistance is a very new market and comes with a lot of caveats. This tool is in no danger of replacing anybody’s job in the near future, but it will change the way you write. But will that be for the better or for the worse?

### Things to know about GitHub Copilot:

* What is GitHub Copilot?
* Is GitHub Copilot useful?
* Is GitHub Copilot worth it?
* Is GitHub Copilot suitable for professional development environments?
* The Bottom Line on GitHub Copilot

#### What is GitHub Copilot?

GitHub Copilot is a cloud-based AI coding assistant that provides you with real-time, autocomplete-style coding suggestions based on the code you have already written in your project.

GitHub holds that the biggest share of the market is cloud-hosted source control and is the primary repository for most free and open-source projects and a great many proprietary and corporate codebases. So it is not a big surprise to see that this new tool from GitHub is getting so much attention.
#### Is GitHub Copilot useful?

Overall, the Copilot plugin can save experienced developers time that may be spent looking up code references and saves typing on boilerplate code. But make no mistake, you must know what you are doing. Copilot suggestions are sometimes major time savers, are sometimes nonsense, and are sometimes wrong enough to be dangerous.
##### Case study: In Python, create an SQS queue, add items to it, and receive items

One common way of interacting with Copilot in the IDE is to write up the intention of your code in a comment and then allow Copilot to suggest complete functions that will fulfill the description in the comment.

So you type something like this:

```
connect to AWS and create a queue in SQS
send a message to the queue 
receive a message from the queue
```

And Copilot will create some runnable code like this:

```
import boto3

def create_queue(queue_name): 
    sqs = boto3.client('sqs') 
    response = sqs.create_queue(QueueName=queue_name) 
    print(response['QueueUrl'])  
```
Wow, impressive that Copilot has created a function that does what is asked (and actually works!) from only a description in a code comment.

On one hand, this is a potential time-saver and educational tool, keeping us from having to look up in the AWS reference or Stack Overflow to use the AWS API in Python.

From another point of view, this is an incredibly dangerous suggestion. The code that Copilot has filled in will work in perfect situations, but will be very difficult to debug or operate.

* It has no return value; void functions require implied or shared state which is a rich source of bugs.
* The URL of the queue is printed to the console and is not available to calling objects. Code calling this function to create a queue gets a queue created but will have no way to access it.
* It has no error handling.

The code generated to take messages from the queue is even more concerning:
```
def receive_message(queue_url):
    sqs = boto3.client('sqs') 
    response = sqs.receive_message(QueueUrl=queue_url) 
    print(response['Messages'][0]['Body']) 
    sqs.delete_message(QueueUrl=queue_url, 
ReceiptHandle=response['Messages'][0]['ReceiptHandle'])  
```
This code will take a message from the queue and immediately delete the message. One of the primary values of a queue like SQS is guaranteed message handoff. Queues can allow multiple clients to take messages from the queue and work on those messages.

A client picks a message off the queue and works on that data, and only after work is complete does the client then go back to delete the message to indicate that the work on that message is complete.

If a client fails to complete the task, the queue message will be added back for another client to pick up. This allows the system to guarantee that each message is delivered successfully “at least once.” To take a message from the queue and delete immediately is antithetical to the core offering of message durability.

Any experienced developer that is using a queue will know all of this and would refactor the code that Copilot creates. So, this makes Copilot a good tool for experienced developers, but potentially dangerous for beginners.

Copilot will help with what to type. But it will not help with what to think or what to do. It encourages bad practices in style and will potentially make suggestions that are wrong in just about every case.

The code completion and syntax suggestions from Copilot are potentially able to save a lot of typing but always require expert eyes on it. When GitHub describes Copilot as “Your AI pair programmer,” in my view, this is a misnomer.

A pair programmer will ask interesting questions, will force you to defend your code, and will introduce fresh ideas. Copilot does none of those things effectively.
#### Is GitHub Copilot worth it?

GitHub Copilot is a paid service and costs $19/month. In the overall picture of software development, $19 represents notably less than 15 minutes of developer time, and so any time efficiency gained, even in typing boilerplate code, could offset that $19 cost easily.

There are also multiple competitors in the AI code assist space:

* Tabnine
* AWS Code Whisperer
* Kite
* JetBrains Datalore
* Jedi

And many more. These all have tradeoffs with specialization, maturity, cost, and privacy. The landscape is continually shifting these days, which is a big indicator that this is an exciting and cutting-edge field.

Overall, GitHub Copilot is not as unique in the industry as it may first appear. There are many very mature players in the field that are developing or already have an AI Code assist offering, AWS and JetBrains most notably.

If you find any utility in it, Copilot is likely worth the cost. But it is not the only player in the game, and the field is only getting more competitive.
#### Is GitHub Copilot suitable for professional development environments?

Aside from utility and expense, GitHub Copilot is a third-party plugin that has access to all the code you write. It analyzes the code that you type and may send any amount of telemetry back to GitHub for analysis.

A quick look at network connections for a MacOS computer running PyCharm with GitHub Copilot shows that Copilot opens multiple network connections to the servers at github.com or to IP addresses owned by Microsoft.
The license agreement notes explicitly that Copilot may send telemetry back to GitHub and this network monitoring confirms that that is happening.

GitHub Copilot has used a huge corpus of open source code for its training. There has already been quite a bit of discussion and concerns that GitHub is in a gray area in honoring open source contributors, but it is unlikely that this will have any legal effect on end users.

#### So as a consideration for professional software developers, I would consider the following:

Junior to mid-level software developers should only use AI coding assistance like Copilot on experimental and educational projects. Junior to mid-level devs should not write production code with Copilot.  

Mid-level to senior developers and above could use Copilot to speed code completion and lookups on unfamiliar syntax and libraries. Copilot is of particular interest for senior to principal developers that jump between languages a lot. Trying to remember the nitty-gritty of syntax when jumping between C# / Python / Scala / Java projects can be a pain. Copilot could be a handy way to remind yourself of those differences. But it will take an experienced developer to read and confirm the code that Copilot suggests.  

It is a given, but worth saying explicitly that Copilot is only appropriate for situations in which a developer is implementing without security considerations or proprietary IP. GitHub informed users that data is sent back to their servers and network monitoring confirms that is happening. Even if we could confirm that no sensitive data is transmitted today, there is no way to assure that all future activity would offer the protection necessary for proprietary or highly sensitive projects.

#### The Bottom Line on GitHub Copilot

So there you have it. GitHub Copilot is an exciting development in the software industry and offers some very cool utility. It does not claim to write perfect or even correct code, but that does not get in the way of usefulness in many situations.

Just be sure not to let it do the thinking for you. As a professional software engineer, the responsibility to think is squarely on you.

*This article was written as part of work I do at AIM Consulting, part of the Addison Group. Its original article can be found at https://aimconsulting.com/insights/is-github-copilot-useful/*
