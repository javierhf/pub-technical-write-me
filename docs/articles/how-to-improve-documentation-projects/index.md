# Part 1 of 3

## Improving an Existing Developer Documentation (1 of 3)

> **What this article covers**\
> _First steps on how to improve an existing documentation project._\
> **Tools**\
> _Confluence, GitHub web and desktop versions, and MarkdownPad2._

### Overview

**Developer Documentation is a curated set of files** describing all the active _workflows_, _setups_, _tools_, _conventions_, _best practices_, and _How-tos_ of your software development product. Through this article, I will refer to it as "documentation" or "docs".

**Documentation supports your team members in their daily and future developments**. It also helps new joiners to reach cruise speed during the onboarding period. _But to do so, your documentation must be up-to-date and well-structured_.

**Keeping the docs up-to-date and in good shape requires resources and dedicated time**. Yet often our project time or budget constraints prevent us from taking care of our docs properly.

In the following sections, you will find a concise description of the first steps you can take to improve your documentation project.

### Step 1 - Organize Your Improvement Project

**Developer documentation has to be visible** to increase the chances of success, and to find collaborators (to improve it). To do so, keeping a _space_ to visualize, describe, and track your improvement project is a useful idea.

**Use your teams/company collaboration tool** for that purpose. For this article, we'll be using Confluence.

**Space Structure**

**The structure of an improvement project may differ** from one project to another. Take the following _space_ structure as a reference that you can adapt to your needs (_then iterate!_):

<table><thead><tr><th width="214">Space Name</th><th width="148">Page Name</th><th width="187">Child Page</th><th>Description</th></tr></thead><tbody><tr><td><strong>[Your Documentation Project´s Name]</strong></td><td></td><td></td><td>Name of your documentation project.</td></tr><tr><td></td><td><strong>Overview</strong></td><td></td><td>Explain briefly the What, Why and How of the documentation.</td></tr><tr><td></td><td><strong>Dashboard</strong></td><td></td><td>Centralized page to easily access all project pages.</td></tr><tr><td></td><td><strong>Analysis</strong></td><td></td><td>Media and results of documentation analysis.</td></tr><tr><td></td><td><strong>Roadmap</strong></td><td></td><td>Visualization of the estimated dates to implement each improvement.</td></tr><tr><td></td><td><strong>Improvement Project</strong></td><td><em>Communication Grid</em></td><td>Contact person by topic.</td></tr><tr><td></td><td></td><td><em>Improvement Plan</em></td><td>Implementation phases and items.</td></tr><tr><td></td><td></td><td><em>Coordination Meetings</em></td><td>Grid to align with your manager or collaborators (<em>Optional</em>).</td></tr></tbody></table>

**Once your improvement project space is set up,** you are ready to:

* Present it to all your team members, including Product Owners and Scrum Masters.
* Track and show your progress.
* Visualize documentation issues/blocking points.
* Access all your project resources.

{% hint style="info" %}
Explain how documentation issues negatively impact teams´ performance. It will help Product Owners and Scrum Masters to understand and provide your project with the resources you need.
{% endhint %}

### Step 2 - Identify Your Documentation Issues

**Identifying your documentation issues means** spotting all the types of issues living among your docs. Some documentation issues are:

* Grammar, spelling, and syntax errors.
* Confusing/Not logical page structure.
* Unclear/Verbose text.

**For each type of documentation issue**, we can apply a specific fix strategy as shown in the following table:

| Documentation Issue                  | Fix strategy                                                                                                                                                                                                                 |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Grammar, spelling, syntax**        | Use a text checker to support your writing. Some good options are [Grammarly](https://app.grammarly.com/), [Hemingway](https://hemingwayapp.com/) or [QuillBot](https://quillbot.com/grammar-check).                         |
| **Page structure**                   | Review your page structure. It shows the logical flow of the information contained according to the objective of the page, for example: _Introduction_, _Prerequisites_, _First Step_, _Working with.../Available Features_. |
| **Naming**                           | Define a naming strategy for page titles, sections and subsections.                                                                                                                                                          |
| **Page elements**                    | Standardize the use of the following elements: lists, tables, tabs, notes, collapsible elements and images.                                                                                                                  |
| **Text unclear** or **too verbose**  | Be concise.                                                                                                                                                                                                                  |
| **Random text formatting**           | Standardize the use of bold and italics for files, folder names, code snippets and code elements (functions, objects, methods, parameters, API names, etc.).                                                                 |
| **Too many topics on a single page** | Stick to "One topic per page".                                                                                                                                                                                               |
| **Unnecessary screenshots**          | Use screenshots or images _ONLY_ when strictly necessary. If you can explain it briefly, do not use screenshots.                                                                                                             |
| **Type of notes**                    | Standardize each type of use case for notes (Info, Help, Warning, etc.).                                                                                                                                                     |

> **What\`s Next?**\
> _In the next article, we will describe how to run a user survey to gather useful feedback from your users/readers. This invaluable feedback will help us prioritize the documentation issues to fix first._
