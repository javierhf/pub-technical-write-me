# Part 3 of 3

## Improving an Existing Documentation Project (3 of 3)

> **What this article covers**\
> &#xNAN;_&#x41;nalysis of the results of the survey and the derived improvement actions_.\
> **Tools**\
> &#xNAN;_&#x4D;S Forms and Excel_.

### Actioning Your Users' Feedback

**Now that we know the current status of our documentation better** (_See_ [_part 1_](https://javierhf.github.io/technical-write-me/improving-documentation-projects/improving-documentation-project-1/)) and we have gathered feedback from our users (_See_ [_part 2_](https://javierhf.github.io/technical-write-me/improving-documentation-projects/improving-documentation-projects-3/)), it is time to analyze the results of our survey. Based on that, we should then find out which improvement actions we can extract from it.

For this article, I'm providing some screenshots of the results of a real developer documentation survey.

_Let the fun begin!_

### Analyzing the Results

**To analyze the results of our survey,** we will group the questions under the following categories:

* Awareness - Are your users aware of your documentation?
* Frequency of use
* Search and page access behavior - How our users search and access our documentation pages
* Page design - Does our page design meet the needs of our users?
* Next steps (According to our users)
* General perception
* Other comments

**Grouping our questions helps us to identify the type of issues** impacting our documentation and the domain of the solution to implement.

### Results Categories

**The following table shows the screenshots of the survey results,** for each category, and some quick thoughts about them:

| Category                                                                | Results                                                                                               | Quick Thoughts                                                                                                                                                                                  |
| ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Awareness**                                                           | ![Awareness](../improving-documentation-projects-3/images/awareness.png)                              | Our documentation is known but there is still space to reach more readers/users.                                                                                                                |
| **Frequency of use**                                                    | ![Frequency of use](../improving-documentation-projects-3/images/frequency-use.png)                   | Our documentation is being used. Yay!                                                                                                                                                           |
| **Search and page access behavior**                                     | ![search and page access behaviour](../improving-documentation-projects-3/images/search-behavior.png) | If a great number of users do _CTRL+F_ to find content on a page, we should review our page design to ensure we are supporting that behaviour.                                                  |
| **Page design**                                                         | ![Page design](../improving-documentation-projects-3/images/how-content-is-shown.png)                 | <p>Even if the majority of our users prefer the content being gradually revealed, a great deal of our users prefer the content being shown all at once. </p><p></p><p>Let's find a balance!</p> |
| <p><strong>Next steps</strong><br>(<em>According to our users</em>)</p> | ![Next steps](../improving-documentation-projects-3/images/next-steps.png)                            | Keeping our documentation up-to-date requires finding a cross-team collaboration strategy to involve all the required Subject Matter Experts (SME).                                             |
| **General perception**                                                  | ![General perception](../improving-documentation-projects-3/images/general-perception.png)            | Our documentation is perceive as useful. What about opening the door more more content?                                                                                                         |

### What to Do Next?

**To decide what to do next,** keep in mind _the current state_ and _the needs (priorities)_ of our users. From this perspective, you can identify which improvement actions will have the highest impact on your users more accurately.

Once you have done that, plan accordingly.

**When evaluating the current state of our documentation**, you may target some _hot potatoes_. In this case, do some firefighting first and reduce the biggest pain.

**If we don't have any firefighting to do**, talk to your manager roles (Product Owner, Scrum Master, Lead Link, etc.) or your customer/user insights roles/team to:

* Share the survey results.
* Explain and discuss your ideas.
* Know their thoughts and perspectives.

**Involving management and customer/user insights roles** increases the awareness of your documentation project, and reinforces the following idea:

> _Improving product documentation impacts the adoption and ease of use and success of our product._

### Planning the Improvement Actions

**There is no magic formula** **to design an improvement plan**. The following table provides, for each user survey topic group, some remarks to think about and a basic reference plan of action:

<table><thead><tr><th width="235">Topic</th><th>Remarks</th><th>Reference Plan</th></tr></thead><tbody><tr><td><strong>Awareness and Frequency of Use</strong></td><td>Increase the awareness on your documentation project and collaterally the frequency of use, requires involving management roles of different levels, either to enforce the awareness or to act as radiators of information.</td><td><ol><li>Identify your main communication channels.</li><li>Identify your contact person (Product Owners, Product Managers, Lead Links, CEO, CTO, Scrum Masters).</li><li>Inform them about the need to increase the documentation awareness.</li><li>Design the layout for your different communication topics, for example: <em>updates</em>, <em>warnings</em>, <em>issues</em>. Be simple and direct.</li><li>Schedule those communication that can be schedule.</li><li>Start communicating. Be consistent.</li></ol></td></tr><tr><td><strong>Search Behavior and Page Design</strong></td><td>Once we know our users' behavior when reading our documentation, we can support that behavior and implement some changes to help them take the most of their time using our documentation.<br><br>Both <em>search behavior</em> and <em>page design</em> benefits from having a <em>text formatting</em>, <em>page layout</em> and <em>visual elements</em> guidelines. Having templates for each type of page also helps.</td><td><ol><li>Design you style guidelines: <em>text formatting</em>, <em>header/section</em> strategy and naming, use of visual elements.</li><li>Identify which type of pages are you using: <em>Overview</em>, <em>Getting Started</em>, <em>API Reference Guide</em>, <em>Tutorials</em>, <em>FAQ</em>.</li><li>A Google search or your preferred conversational LLM (Large Language Models) can help you here!</li><li>Apply your templates to all your documentation pages. Start with the most used pages. <em>Iterate!</em></li><li>Be consistent.</li></ol></td></tr><tr><td><strong>Keeping Our Documentation Up-to-Date</strong></td><td><p>Keeping our documentation up to date is a tough and cross-teams task. </p><p></p><p>Again, involving the management roles of your company is of great help.</p></td><td><ol><li>Identify the Subject Matter Expert (SME) for each of the topics of your documentation.</li><li>Agree with them to schedule and set up regular documentation reviews.</li><li>Implement a reminder for you to follow up this task.</li><li>Create a checklist for the SME to perform their reviews.</li><li>Keep simple and effective. Check <em>prerequisites</em>, <em>processes</em> or <em>tasks</em>, <em>tools versions</em> and <em>code examples</em>.</li></ol></td></tr><tr><td><strong>General Perception</strong></td><td><p>General perception depends on many topics. Some we can handle (transparency, support, content quality, etc), some we just can't (users not happy with their jobs, users prefer to use a different tool but are not allows, or just bad working habits).</p><p><br>Remember to focus in those issues you can fixed.</p></td><td><ul><li>Keep a fluent and frequent communication with your users.</li><li>Make them feel part of an active and helpful community.</li></ul></td></tr></tbody></table>

### The End?

Documentation projects are, in most cases, living organisms. They are born, they grow, interact with their environment, and adapt to new _surroundings_ and _demands_.&#x20;

To keep our documentation alive and kicking (and our users satisfied!) communication is key.

_Now iterate!_
