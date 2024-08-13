---
title: Single-Responsibility Principle for Documentation Projects
---

# Single-Responsibility Principle for Technical Documentation

> **What this article covers**\
> How to apply the _single-responsibility principle for on technical writing projects._\
> **Tools**\
> _N/A._

## Overview

**According to Wikipedia, the Single-Responsibility Principle (SRP) is:**

> a computer programming principle that states that "A module should be responsible to one, and only one, actor."

**This term was created by Robert C. Martin** who expresses the principle as:

> "A class should have only one reason to change."

**The word "reason" caused some controversy within the community,** so he had to provide further clarification, saying that the "principle is about people." He also added that the principle's focus is _roles_ or _actors_.

## Roles in a Documentation Project

**Documentation projects may include the following roles:** _collaborators_, _editors_ (reviewers), _technical writers_, _translators,_ and _managers_. Ideally, we'll have a single person for each role.

**Lucky for us, we have technical writers, a role that absorbs many of the previous roles.** Technical writers:

* Edit the collaborations with other team members
* Manage the documentation project and platform
* Collaborate with new content actively

**Having a technical writer allows your collaborators (Subject-matter experts)** to focus where they provide more value:

> While Subject-mmatter experts provide a draft with the right information, the technical writer converts their information drafts into content.

But _how do we apply and support this separation of responsibilities?_

## Single-Responsibility Principle (SRP) for Documentation Projects

**It seems simple but applying the SRP to documentation projects requires a little change** in the product team's mindset:

* Now they will provide the information
* The technical writer will create the content

### Key Concepts

**Applying the SRP to documentation projects** starts by understanding three key concepts as described in the following table:

| Concept              | Remarks                                                                                                                                                                                                                                              |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Information**      | Information consists of all pieces of text (introduction, process steps, features, and code descriptions), screenshots and raw data provided by collaborators, in the right order, in the right context and containing information which is correct. |
| **Content**          | <p>Content is the information after being standardized. </p><p></p><p>Standardized information reflects the style guide and the technical writing best practices.</p>                                                                                |
| **Shared Ownership** | Every page is the result of cross-team collaboration, so all teams own the documentation and are encourage to provide feedback to improve it.                                                                                                        |

**Keeping these concepts in mind,** we can define the following roles, and their responsibilities:

| Role                 | Responsibility                                                                                                                                                              |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Collaborators**    | <p>Provide a documentation draft with information that:</p><ol><li>is correct,</li><li>is presented in the right order,</li><li>is embedded in the right context.</li></ol> |
| **Reviewers**        | Validate the information provided by collaborators when required.                                                                                                           |
| **Technical Writer** | <ol><li>Converts information into content.</li><li>Manages release process.</li></ol>                                                                                       |

## Conclusion

**Single-Responsibility Principle is the new mindset:** assigning a limited and specific set of tasks for all the roles participating in the documentation workflow, ensuring we all add value where we are experts, and embracing documentation as a shared ownership to provide a documentation we are proud of.&#x20;

**The Single Responsibility Principle (SRP) for documentation projects shifts the concept of documentation ownership** from individual to shared. This shift increases the chances of developing a quality documentation encouraging cross-team collaboration.&#x20;

This idea of shared ownership may be not be easy for everyone to accept, but it impacts the quality of our documentation positively. When we all own the documentation, we all take care of it.
