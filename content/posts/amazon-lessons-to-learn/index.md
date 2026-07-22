---
title: "Amazon Lessons to Learn"
date: 2026-07-21
description: "Amazon development concepts"
tags: ["basics", "knowledge", "snippets", "Amazon", "2019"]
author: "Dusan B. Jovanovic"
---
### Original date: 2019-05-15

> DBJ Comment -- This describes managing the high pressure environment. On lower levels this probably works. But , there are serious issues with the wider picture of this. Primarily value of Architecture is neglected. Architects are called "Bar Raisers" etc. Mountain of Technical Debt is raising at Amazon. ROI and "Time to Market" are two key drivers at AMZN 2019. The likely outcome will be AMZN dropping into the hot mess of legacy systems and technical debt. Same as MSFT was in, starting with "Longhorn" disastrous attempt to combat the huge technical debt. It took MSFT 10+ years of the survival boot-camp to somehow overcome that potentialy fatal disaster.


**[Source](https://www.theregister.co.uk/2019/05/14/amazons_away_teams/?page=2) article**

### The principles of Amazon service-oriented collaboration

Here's how Amazon's service-oriented collaboration works based on our research:

1.  Team structure
    -   Each of the groups that owns a service has a set of goals and possibly a P&L that represents success. A roadmap is generally in place to meet those goals.
    -   The teams are ostensibly autonomous and can make any important decision needed to meet their goals.
    -   The "value to the customer" is part of the mission for each team. This codified using content such as mock press releases to ensure developers keep end user needs in mind.
    -   As much as possible, teams are kept small, adhering to the two-pizza rule, meaning about six people.
    -   Services can be refactored or new services can be spun out to new teams. Teams that don't work are shut down and the technology they created is distributed to other teams or discarded.
    -   New teams often are created to solve urgent, end-to-end problems.
2.  Development process
    -   Teams use a shared set of development tools for source code and managing the development pipeline, some offered as shared services. There are many tools and services that are commonly or universally used, but no hard requirements. Every team can do what makes sense to get the job done fast. While this is true, at some point you may have to show with data why you deviated.
    -   The DevOps model is fully embraced. Each team performs operational support for its service.
    -   Access to most source code is not hard to get. One group can usually quite easily take a look at the source code of another without prior restraint. There are some exceptions.
    -   A/B testing and detailed monitoring is widespread and used for almost every aspect of the site and infrastructure. The testing is based on the WebLab service, supported by a team that trains staff on how to make testing statistically significant.
    -   Teams do not generally have to worry about the rates of internal use of resources. There is no internal currency changing hands for tracking such usage. Rates of usage internally across services are allocated as part of the budget process and monitored by finance teams who meet periodically with teams to discuss any unusual growth in services and encourage optimization.
    -   Decreasing technical debt is not considered a good reason to do anything unless it has an impact on reaching the goals of the team.
3.  Collaboration practices
    -   Changes to one team's service may be implemented by another team who needs the enhanced capability by what is called an Away Team. This team works on the Home Team's code to add what it needs according to established engineering standards and then leaves that code in good order to be maintained by the Home Team who owns the service, with help when needed.
    -   When an Away Team is not an option because the requestor doesn't have the ability to implement improvements to the service, this does lead to a management discussion about how to optimize the big picture roadmap. Usually roadmaps are bursting, so accommodating a new request means reshuffling the existing roadmap.
    -   If extending a service using an Away Team doesn't work out for some reason, it is perfectly fine to duplicate and create whatever you need to accelerate your progress. There is no concern about duplication across the platform as long as you have a need that will help you move forward.
    -   A team creating a service is given credit when they do something that has a positive downstream impact on other services. Management recognizes contributions to the big picture, usually on the P&L of the higher entity.
    -   "Bar raisers", Amazon staff who act as independent experts who approve key decisions, often who work on other teams, are used not only for hiring, for which they are widely known, but for high impact decisions for design, customer experience, architecture, and A/B testing. It is possible to go against the recommendation of a bar raiser, but such a move is noted and made visible to higher levels of management.

These principles operate somewhat differently based on the part of Amazon that is using them.

The oldest, original set of technology that morphed into services is generally called legacy. There is an internal platform called MAWS, which is an internal platform of services that are not public. The public form of AWS is the latest. There may be others we have not heard about.

For example, older products such as Amazon.com or Kindle may use services from all three of these layers. Newer products like the Alexa and Echo tend to use more of the public services on AWS.

There have been many generations of evolution from legacy to MAWS to AWS and also with respect to development tools. All of these changes happen in waves that may take years to complete.

The teams outside AWS proper are less likely to have a P&L at the service or team level. In general, AWS teams are known for having the most methodological purity, a state in which the service, team, and P&L have the same boundary.

Keep in mind this picture was assembled from talking to many people with different perspectives at different levels of the organization. It would be wonderful to make it sharper. But finding someone who knows the whole picture and detailed history is not easy. Amazon PR staff take note: we are always ready to sit down with Werner Vogels, Amazon CTO, and go over the details.

#### How [Kurzweil](https://en.wikipedia.org/wiki/Ray_Kurzweil) and [Von Hippel](https://en.wikipedia.org/wiki/Eric_von_Hippel) explain the power of service-oriented collaboration

Amazon's model encourages direct team-to-team, service-to-service collaboration, providing principles for collaboration so that as much progress as possible can take place based on each team optimizing the services it needs directly.

As your correspondent came to understand Amazon's model, I realized that the structure of service-oriented collaboration used levers for acceleration that have been documented by two celebrated researchers who have studied how technology development can be optimized.

MIT professor Eric Von Hippel's research into user-driven innovation shows that when the user is given direct access to the means for creating a solution, potentially at least, tremendous innovation can result. The "[sticky information](https://evhippel.mit.edu/papers/section-2/)" that otherwise must be rendered into requirements documents or transferred from user to builder is difficult and never complete. When this step doesn't have to take place because user and builder are the same person or same team, the outcome is much better. Amazon's Away Team model embraces this concept and allows teams to create building blocks that have ideal fit to purpose.

![for aws teams feature](https://regmedia.co.uk/2019/05/08/graph1.jpg?x=442&y=293&infer_y=1 "for aws teams feature")

Ray Kurzweil's analysis of the exponential pace of technology development provides another lens through which the power of Amazon's model can be explained. Your correspondent has summarised Kurzweil's model in [Research Mission on Technology Leverage](https://earlyadopter.com/2018/03/09/technology-leverage/), but his thesis is as follows:

-   At first, progress in any area of technology seems slow because basic services are being developed.
-   But then, more complex services are built out of the simpler ones, and so on, accelerating the pace of development.
-   At the same time, funding goes to improving services that are most impactful.
-   As the services are used more, the fit to purpose improves.

Kurzweil's research shows how in many different areas of technology, this pattern has held throughout history. At Amazon, my view is that we are still in the early stages of this exponential curve, which is being driven by use of services both inside and outside of Amazon.

Amazon's model wouldn't work without data from usage driving funding and optimization. End-to-end teams and Away Teams play a crucial role in identifying new services and improving the fit of existing services.

![for aws teams feature](https://regmedia.co.uk/2019/05/08/graph2.jpg?x=442&y=293&infer_y=1 "for aws teams feature")

Right now, AWS has focused on creating general purpose higher level services that all fit into a generic platform for software development. The highest level services are being created on top of the platform by Amazon itself (Amazon.com, Alexa, Kindle, etc) and by AWS customers who are building all sorts of products and IT infrastructure.
