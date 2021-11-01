

Best Practices for PR's
=======================

This document is meant to distill what we think are best practices for PR's. Some of it may be obvious. Some of it consists of very specific proposals.

## 0. Be Nice In PR's

Writing and reviewing code should be fun. Even bike-shedding variable names is fun up to a point. At least, PR's should be treated as a safe place to give and receive input. Code reviews are a venue for giving input. Everyone should feel comfortable doing that, learn to give it properly, and feel comfortable receiving this kind of input.

Be careful not to attack; give people the benefit of the doubt; don't take input personally. Beyond this advice, this document won't address what to do when people cross these lines. Talk to your manager.

## 1. Before you go write a ton of code:

- We want to aim for small PR's for a number of reasons: smaller diffs are easier to reason about, and thus less risky; smaller PR's are easier to review.

- But wait, you say, I have a huge gigantic change? There are several tools and approaches to make small PR's more feasible:
(1) Feature flags
(2) Backward-compatibility, for example, keeping old and new pieces of functionality.
(3) Git branches. In particular, branches off branches. When you have a large change, you can often structure it as a series of PR's: For example, a refactoring PR, followed by a PR that adds an appropriate test, followed by a PR that makes the main change.

One exception to this rule is when you have large mechanical refactorings. Even in those cases, future modularization should be able to bound the size of changes that have to go in one merge.

- Have a functional partner BEFORE you write code. "Functional partner" can mean:
  - person who's familiar with the functionality you're adding
  - pair programming partner
  - person who looks over your shoulder

- If you're making a large change vet an outline or sketch of the direction of your change with some senior engineers.

- One of the goals of a PR is knowledge-sharing in addition to correctness issues and discovering bugs early.

### Other Broad Things To Keep In Mind As We Edit Code
- We want to add tests to the codebase with every PR

- We want to add comments throughout the codebase. A common complaint is that new engineers have a hard time understanding the code. One way to help the situation is to add documentation as we learn new parts of the code.

- Everybody is learning Scala, and some of this happens through PR's. Don't worry if it seems like you're making a lot of novice mistakes. Learning all the Scala and FP idioms is a process :)

## 2. Add internal documentation

We want to generally improve the quality and quantity of our internal documentation. Writing
documentation is an integral part of the development and code-writing process. Our main venues for
internal documentation are Slab docs and Scaladoc. Scaladoc makes sense when you're describing the function of a class or method or parameter.
Slab docs make sense when you need to explain how a service works across multiple components. Most PR's should have at least one of the following newly added or updated:

- Slab doc under the Service Documentation topic
- Explanatory Scaladocs or GQL annotations
- README.md or similar within the repo
- Public-facing docs (e.g. API docs, CS docs, or GQL annotations)
- Other docs (google docs if you must, but please link to it from the code)

## 3. Open the PR

* A PR is opened by the author(s) of the branch using the following format:
    `[ITBL-$JIRA] Succinct description of what the branch solves`
* The PR requester(s) fill out the template for the PR description.

## 4. Before you add Reviewers: Self-Review

Put the PR in WIP. Go through the PR yourself and look over the code as if you were the reviewer. Fix obvious issues - unclear variable names, unneeded imports, running `sbt format`,
missing documentation, etc.

Add narrative comments (either in the PR; or better yet in the code) that walk the reviewer through the changes. Document things like the following:
- Unchanged blocks of code that show up as diffs - this saves the reviewer time
- Subtleties (these are best as code comments)
- Tangential changes like cleanups
- Where the main change lies
- The test that proves your change works

Take it out of WIP only after you've done this. (You can also keep it in WIP and add reviewers while it's WIP - this is a good practice.)

## 5. Add assigned reviewers

Add your functionality partner. There should be one other person who's familiar with both the existing code prior to your PR, and the changes that are being made in your PR, just as a matter of knowledge-sharing. This person can be your reviewer.

You can of course add more people as reviewers. You're strongly encouraged to add a recognized code owner for non-trivial PR's.

Ilya is very knowledgeable about the code base so he reviews a lot of things but he shouldn't need to. Unless Ilya is your functionality partner, don't add him as a reviewer.

Our practice is generally not to dump a PR link into #engineering to put things up for review other than in exceptional, trivial cases. If you have a very small review, adding "this is a one-liner" lets people know they can do it quickly in advance.

Try to avoid globbing up the entire team if your first reviewer doesn't review immediately. Instead, prod your functionality partner. Don't be shy about pinging your assigned reviewer: Slack them, DM them, ping them in person. Everyone knows it's important and that they're supposed to make time for it; don't feel like you're bothering any one just because you're prodding them for a code review.

### Consider in-person or video reviews

In the time before Github, many code reviews were done in person. Github reviews - which are asynchronous, online, and text-only - work really well for modest changes. But once your review gets to a certain level of complexity, it may be easier to walk someone through the review in person.

As @jochia mentions, "especially for younger engineers, this is extremely helpful. Just reading other people's code is a skill to be developed, and is much better use of everyone's time to just sit down and hash out the details of a PR in person (or video). For the author of the PR, you get your reviews done faster, for the reviewer, you spend less time reading and rereading for just understanding."

### Consider WIP reviews.

Sometimes you might want to open up a pull request for the purpose of getting
tests run on CircleCI. To indicate that it is a Work In Progress and is not
ready for review, prepend the PR title with `WIP`. If you do want review from
someone even though it's a Work In Progress, let them know over Slack.

When you're learning Scala, which many of us are, you may expect a good number of style comments. Add reviewers while the PR is WIP to get early feedback.

## 6. Reviewing code

When reviewing code, follow these guidelines:

* Does the change have tests? Do the tests cover all necessary cases?
* Are there code style issues that should be addressed?
* Discuss trade-offs and aim to come to resolution quickly. Don't let open
  questions in PR discussions remain unanswered.
* Ask questions rather than making demands. Seek to understand first: `could you do this differently?` `why did you delete this?` `what happens if xxx?` etc. A question is more useful than an assertion e.g. `this is wrong` because it grants the author the benefit of the doubt.
* Always be nice in your comments. Don't be too terse, as this may leave
  intent or tone open to interpretation. You are reviewing someone's hard work!
* Take it to synchronous communication (Slack, call, Hangout) if there's too
  much back and forth going on. If this is the case, leave a comment with the
  result of those discussions for others to see and for archival.

### PR comment priorities

PR comments can range from stylistic issues to correctness, bugs, and even design issues. Hopefully not the last or something has gone wrong.

Sometimes when someone makes a PR comment it's unclear how much one cares about the issue being raised. Some people may indicate certain issues as "not a big a deal" or a "nitpick" or "idc". But nobody does this consistently for all their comments, which leaves lingering doubt in a number of cases. We propose the following framework to make this clearer.

- P1: MUST do before merging
- P2: Should do before merging
- P3: Could defer

For example, it would be rare for a style issue to be a P1. Most style issues should be P3. However style issues are generally easy to fix so P2 is OK.


## 7. How to respond to PR comments

Personally, my bias is to try to implement every suggestion. If nothing else, it's easier to just implement simple suggestions than argue about them.

Besides that the common options are:
- Add a comment in the code to clarify things. If a reviewer commented on it in the PR
- Comment back within the PR
- Redesign things
- Defer them to a subsequent PR
- Defer them with a JIRA (somewhat discouraged)
- Defer them them with a TODO in the code (strongly discouraged)

If the reviewer marks something as a P2 or P1 you should definitely try to do it.

## 8. Merging and deploying the PR

* PR approvals are required before merge in the main repo.
* After a reviewer approves a PR, the requester is responsible for merging it
  and deploying to production.
* Delete the branch after merging

Merging a PR means the change is ready to go to production. Typically the workflow is to merge then deploy immediately, i.e. merge just before you're ready to deploy. It's not recommended to merge such that it eventually goes out with the next deploy.

During a deploy freeze, don't merge until after the freeze is lifted. Otherwise the first deploy after the freeze will end up with many incidental changes that won't be monitored by the authors.

It's not recommended for non-authors to merge a PR. Once something is merged to master, it may be deployed at any time. There are a number of reasons why an author may not want their PR to be immediately deploy. For example, they may want to monitor their deployment, they may have additional edits they want to make before merging, etc.

Deployment:

* Announce your deploy on Slack's #deploytrain channel.
