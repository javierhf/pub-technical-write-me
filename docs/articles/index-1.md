---
title: Single-Responsibility Principle for Documentation Projects
---

# Single-Responsibility Principle for Technical Documentation

> **What this article covers**
>
> _A customized application of the single-responsibility for on technical writing._\
> **Tools**
>
> _N/A._

## Overview

**According to Wikipedia, the Single-Responsibility Principle (SRP) is:**


**This term was created by Robert C. Martin** who expresses the principle as:

> "A class should have only one reason to change."

**The word "reason" caused some controversy within the community,** so he had to provide further clarification, saying that the "principle is about people." He also added that the principle's focus is _roles_ or _actors_.

## Roles in a Documentation Project

**Documentation projects may include the following roles:** _collaborators_, _editors_ (reviewers), _technical writers_, _translators,_ and _managers_. Ideally, we'll have a single person for each role.

**Lucky for us, we have technical writers, a role that absorbs many of the previous roles.** Technical writers:

* Edit the collaborations with other team members.
* Manage the documentation project and platform.
* Collaborate with new content actively.

**Having a technical writer allows your collaborators (Subject-matter experts)** to focus where they provide more value:

> While Subject-mmatter experts provide a draft with the right information, the technical writer converts their information drafts into content.

But _how do we apply and support this separation of responsibilities?_

## Single-Responsibility Principle (SRP) for Documentation Projects

**Applying the SRP to documentation projects requires a shift** in the product team's mindset:

* Team members or collaborators provide the information.
* The technical writer creates the content.

### Key Concepts

**Applying the SRP to documentation projects** involves understanding the key concepts described in the following table:

| Concept              | Description                                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Information**      | <p>All pieces of text, screenshots and raw data provided by collaborators. </p><p></p><p>Text includes <em>introduction</em>, process steps, <em>features</em>, and <em>code elements</em> (libraries, parameters, snippets, endpoints).</p><p></p><p>Information is provided as a draft containing the right informative elements, <em>in the right order and</em> <em>in the right context</em>.</p> |
| **Content**          | Information that has been standardized according to the style guide, Information Architecture and technical writing best practices.                                                                                                                                                                                                                                                                    |
| **Shared Ownership** | <p>Documentation is a team effort, with everyone contributing to and owning the final result.<br><br>The visible face of the documentation set is the Technical Writer.</p>                                                                                                                                                                                                                            |

**With these concepts in mind,** we define the following roles and responsibilities:

| Role                  | Responsibility                                                                                                                                                         |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Collaborators**     | <p>Provide information that is:</p><ol><li>Correct</li><li>Presented in the right order</li><li>Embedded in the right context</li></ol>                                |
| **Reviewers**         | Validate the information provided by collaborators when required.                                                                                                      |
| **Technical Writers** | <ol><li>Convert information into content</li><li>Manages the release process</li><li>Creates content from scratch</li><li>Manages documentation as a product</li></ol> |

## Conclusion

**The single-Responsibility Principle is the new mindset of** assigning a limited and specific set of tasks for all the roles participating in the documentation workflow, ensuring everyone adds value according to their expertise, and embracing documentation as a shared ownership to provide documentation we are proud of.&#x20;

**The Single Responsibility Principle (SRP) changes the concept of documentation ownership** from _individual ownership_ to _shared ownership_. Now, all product development roles can contribute to the final product: _we all own the docs!_&#x20;

While this shift to _shared ownership_ may be challenging for some, technical writers can ease the transition with effective communication strategies.
