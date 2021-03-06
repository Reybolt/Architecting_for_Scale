Author: Reynaldo Arteaga
Date: Feb 2018

# Part 1 Chapter 1

> Quote: No one cares if your system has great features if they can't use it.

Availability vs. Reliability:

Availability: The ability of your system to be operational when needed in order to perform those operations.

Reliability: The ability for your system to perform the operations it is intended to perform without making a mistake.

> E.g. A system that adds 2 + 3 and gets 6 has poor reliability. A system that adds @ + 3 and never returns a result at all has poor availability.

What Causes Poor Availability:
* Resource Exhaustion: Increase number of users.
* Unplanned load-based changes: Quick last minute changes to handle more users.
* Increased number of moving parts: A larger staff to handle more work.
* Outside dependencies: Dependencies on external applications.
* Technical Debt: Increase to application complexity

> Your company cannot survive long if you constantly have availability problems.

# Chapter 2:

Example: A Simple Icon Failure. Took down the entire page because a third party user-specific icon failed. They assumed it would always work.

We can't test everything but we can deliver with some things in mind:

* Build with failure in mind
* Always think about scaling
* Mitigate risk
* Monitor availability
* Respond to availability issues in a predictable and defined way.

## Focus # 1: Build with failure in mind

> Werner Vogels, CTO of Amazon: "Everything fails all the time." Plan on your applications and services failing. It will happen. Now, deal with it.

* Design:
    * What design patterns will help improve your availability?
    * Simple error catching deep within your application, retry logic etc.
* Dependencies:
    * When a component fails how do you retry? What if the issue is unrecoverable (hard failure) or recoverable (soft failure)?
* Customers:
    * What do you do when a component that is a customer of your system behaves poorly? 
    * Can you throttle excessive traffic?
    * Can you handle excessive load on your system?

## Focus # 2: Always think about scaling

* Idea for SA!: A lot of our algorithms simply go through all sites and then disperse the load, rather than do that, we should break that down into batches. So we always have batches of 100 or 1000 (some efficient/reasonable number).
    * *Possible Solution:*
        select count(*) from sites. then split into N-batches.
        * Need to consider how fast it is to pull out 10000 sites vs. 10 batches of 1000. 

* Is it static or dynamic?
    * Increasing speed can occur when you use CDNs for static content and bundle the dynamic content together.

## Focus # 3: Mitigate risk

When the system fails it often could have been identified through risk management

> Example: T-shirt website. Uses third party search engine. Risk management says it could fail. When it does, load up the most popular t-shirts we have to the list instead. If user can't find what they're looking for, then give them a 10% coupon on the page. Expect failure but handle it when it does.

> SolarAnalytics Workshop: How should we handle the case where users don't have data?

## Focus #4: Monitor Availability

You can't know if there is a problem in your application unless you can see there is a problem.

* Server Monitoring
    * To monitor the health of your servers.
* Configuration change monitoring
    * To monitor your system configuration to identify if and when changes to your infrastructure impact your application.
* Application performance monitoring
    * To look inside your application and services to make sure they are operating as expected.
* Synthetic Testing
    * Examine in real time how yur application is functioning from the perspective of your users
* Alerting
    * Inform appropriate personnel

## Focus # 5: Respond to Availability Issues in a Predictable and Defined Way

* Need to action when alerts are raised.
* Good to have a manual for everyone to follow when a developer sees an issue.
    > SA Dev have done this!!
* Let the corresponding people and teams know what happened since it may affect their responsibilities and services.

# Chapter 3: Measuring Availability

> Site availability percentage: = (total_seconds_in_period - seonds_system_is_down)/ total_seconds_in_period

The Nines

* 2 Nines: 99%: 432 min
* 3 Nines: 99.9%: 43min
* 4 Nines: 99.99%: 4min
* 5 Nines: 99.999%: 26 sec
* 6 Nines: 99.9999%: 2.6 sec

# Chapter 4: Improving your availability when it slips


# Part 1: Risk Management

