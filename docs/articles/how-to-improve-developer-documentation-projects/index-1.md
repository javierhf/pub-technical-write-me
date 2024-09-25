---
title: Improving an Existing Developer Documentation (2 of 3)
---

# Part 2 of 3

> **What this article covers**\
> _First steps on how to improve your developer documentation project._\
> **Tools**\
> _Confluence, GitHub (web and desktop versions), and MarkdownPad2._

## Getting Feedback from Your Users

**You've created your documentation, and you have users actively working with your product. But what's next?** Understanding how your users interact with and perceive your content is crucial. They work with your documentation firsthand, so they have valuable insights that can help you refine and enhance your documentation. Ignoring their feedback is like shooting yourself in the foot.

_But, how do we gather feedback from our users?_

**User surveys are an effective method to gather feedback**. Surveys allow us to gain _insights into how users perceive and utilize your documentation_, _identify their current need_s, _and uncover any pain points_ they may have. With this information in our hands, we can make informed decisions on:

* _What needs to be improved_
* _Which areas to prioritize_

Read the following steps to know how to prepare your user survey.

### Step 1 - Design a User Survey

**To design a user survey,** **we need to know what to ask and how to ask it**. But language is tricky, so even if we are technical writers, we should double-check the survey's questions with another colleague (and a UX researcher, if possible).

**Check out the following questions of a real user survey** for a developer documentation**.**Take them as a reference to create your survey:

1. Which product/platform do you use?
2. What is your role?
3. How (un)familiar are you with the \[Write your documentation name here] documentation?

* [ ] Not at all familiar
* [ ] Slightly familiar
* [ ] Somewhat familiar
* [ ] Moderately familiar
* [ ] Extremely familiar

3. How often do you read the \[Write your documentation name here] documentation?

* [ ] Never
* [ ] From time to time
* [ ] A few times a month
* [ ] Monthly
* [ ] Weekly
* [ ] I don't even close that tab

4. Which topics are you looking for in the \[Write your documentation name here]?
5. How (un)satisfied are you with the \[Write your documentation name here] documentation?

* [ ] Very unsatisfied
* [ ] Unsatisfied
* [ ] Neutral
* [ ] Satisfied
* [ ] Very satisfied

6. Please explain briefly why you are (un)satisfied with the \[Write your documentation name here] documentation.
7. How (un)useful do you find the \[Write your documentation name here] documentation?

* [ ] Not useful at all
* [ ] Not useful
* [ ] Neutral
* [ ] Useful
* [ ] Very useful

8. Explain briefly why you consider the \[Write your documentation name here] documentation (un)useful.
9. Do you bookmark the \[Write your documentation name here] pages you need?

* [ ] Never
* [ ] I only bookmark the topics I need
* [ ] I bookmark \[Write your documentation name here] main topics only
* [ ] I bookmark the \[Write your documentation name here] home page only
* [ ] Always

10. When I need to find some information on a page, I make CTRL+F:

* [ ] &#x20;Never
* [ ] Rarely
* [ ] Sometimes
* [ ] Often
* [ ] Always

11. When I need to find some information on the \[Write your documentation name here] pages, I scroll:

* [ ] &#x20;Never
* [ ] Rarely
* [ ] Sometimes
* [ ] Often
* [ ] Always

12. How often do you use the \[Write your documentation name here] page's _Search_ box:

* [ ] &#x20;Never
* [ ] Rarely
* [ ] Sometimes
* [ ] Often
* [ ] Always

13. Regarding the content of a page, what do you prefer?

* [ ] &#x20;A plain content structure - No tabs, no accordions. All the information is shown at once
* [ ] A plain content structure containing some visual elements and disclosing content progressively

14. Which topics would like to find in the \[Write your documentation name here]?
15. If you were to make one suggestion for improving the \[Write your documentation name here] pages, what would it be?

* [ ] Better visual design
* [ ] Content should be more comprehensible
* [ ] Content should be easier to find
* [ ] Others (Develop your answer)

{% hint style="success" %}
_**Acknowledgments**_

_Thanks to_ [_Daniela Diener_](https://www.linkedin.com/in/daniela-diener-515588109/) _and_ [_Roksana Skryzcka_](https://www.linkedin.com/in/roksana-skrzycka-b3542b124/) _for reviewing the initial survey_.
{% endhint %}

***

#### Why These Questions?

**Design your questions according to the topic you want feedback about,** for example: _user browsing behavior_, _page layout preferences_, _missing topics_, etc.

**To know which type of feedback we are addressing** with the sample survey of this page, read the following table:

<table><thead><tr><th width="204">Type of Feedback</th><th width="164">Question Number</th><th>Explanation</th></tr></thead><tbody><tr><td><strong>Your users (role, team/product)</strong></td><td>1, 2</td><td><p>Knowing the role, team or product of our users, helps us to identify:</p><ul><li>Our audience.</li><li>Which role/teams are reading our docs the most.</li></ul><p><br>This information can lead us to develop role or team/product focused documentation, or address specific issues or lack of interest impacting the documentation.</p></td></tr><tr><td><strong>Awareness by role, and team/product</strong></td><td>3, 4</td><td>If our platform, toolset, product or project has a lot of people using it, checking the awareness level is a must to double check that our people know where to find the documentation they need, and what we have prepared for them.</td></tr><tr><td><strong>Frequency of use</strong></td><td>3</td><td><p>Answers to this question will tell us if our documentation is being used and how much. </p><p>Knowing this, we can take further actions to deepen the engagement or reinforce it if the docs are not being checked frequently.</p></td></tr><tr><td><strong>Topics of interest</strong></td><td>4</td><td><p>Too many times we create the docs that <em>we think</em> would be of use for our users. </p><p></p><p>This question will tell us if we are right, and which topics need to be revamped (or removed).</p></td></tr><tr><td><strong>Level of (dis)satisfaction</strong></td><td>5, 6</td><td><p>A satisfied user is another word for useful docs (and product!). </p><p></p><p>A low level of satisfaction gives us the chance to ask <em>Why?</em>, and find the source of that dissatisfaction.</p></td></tr><tr><td><strong>Usefulness perception</strong></td><td>7, 8</td><td>We can think that our documentation is useful but, again, our users will either confirm it or deny it. <em>Another opportunity to improve</em>.</td></tr><tr><td><strong>Access point to our documentation</strong></td><td>9</td><td><p>Sometimes we think that our users access directly our documentation typing the URL in the browser. </p><p></p><p>This question will tell us about the <em>bookmarking</em> habits of our users' bookmark. With that in mind, we will have a better idea of the impacts of changing any page or section name that could probably be bookmarked. </p><p></p><p>Here, an effective and reliable communication strategy for changes is key.</p></td></tr><tr><td><strong>Browsing and search behavior</strong></td><td>10, 11</td><td>Browsing and search behavior have a decisive impact on how we will design our pages, and which visual elements can be used.<br><br>For example, using collapsible elements may cause troubles to <em>CTRL+F</em> users that, for example, work with Chrome.</td></tr><tr><td><strong>Reading behavior</strong></td><td>10, 11, 12</td><td>Same as previous topic.</td></tr><tr><td><strong>Direct Improvements</strong></td><td>13, 14</td><td>This is the open-air gold mine. Users will tell you what they want and see as a positive impact for the docs.</td></tr></tbody></table>

#### MS Forms

**Use any survey creation tool** **that fits your needs**. I used MS Forms because it was available and provided an easy way to:

* Visualize the number of participants.
* Provide different kinds of diagrams to visualize the results of the questions.
* Download the results in a consumable Excel format.
* Easily share the survey.

### Step 2 - Schedule the Survey

**Scheduling the survey at the right time is as important as the survey itself.** We are all focused on providing value to our projects and don't want to get distracted. So check in advance with the leading roles the best date and time to run the survey.

If your users are not your teammates, ask Customer Support or an equivalent department for help.

**When discussing the time for the survey,** remember to:

1. Communicate the objectives of the survey.
2. Specify a timeframe for completing the survey.
3. Highlight the importance and benefits of their participation.
4. Encourage team-wide participation.
5. Minimize disruptions to their workflow.

{% hint style="info" %}
In Agile product development teams, the daily meetings of a certain week and the retrospective meeting seem a good place to share the survey
{% endhint %}

### Step 3 - Survey Time

**During the survey meeting,** remember to introduce yourself and:

1. Present the documentation: _What_, _Why,_ and _How._
2. Explain the importance of improving the docs.
3. Explain the structure of the survey.
4. _Release the survey!_

> **What's Next?**&#x20;
>
> _The next article will analyze the results of the survey, and identify the most important ones._
