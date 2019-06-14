# Git Commit Messages

A well-written git commit message provides valuable documentation, both now and
in the future. Code reviewers read commit messages to understand our pull
requests, so good messages make their jobs easier and help them provide useful
feedback. Future developers (including, most likely, ourselves) can use our
commit messages to reconstruct our mental state when we made a change, better
understand our choices, and make more intelligent decisions themselves.

So, what does a good commit message look like?

Structurally, we favor the format described by [commit.style][] and [Tim
Pope][]: at most 50 characters of capitalized summary, a blank line, and as many
paragraphs or bullet points of explanation as necessary (hard-wrapped to 72
characters).

Content-wise, we try to keep the length of our commit messages commensurate with
the complexity of our changes. An extremely simple change may only require a
single line, but a more complicated commit might need several paragraphs of
context and explanation, discussion of alternatives, links, or even ASCII
diagrams.

In a commit, we want to explain:

* Why the change is necessary,
* How this change solves the problem, and
* What other side-effects the change might cause.

Here's an example of a good commit message:

```
Reverse polarity of the turboencabulator

We've recently had complaints from customers that the differential
polarity of the turboencabulator induces magnetoreluctance in their
prefabulated semi-boloid marzelvanes.

To avoid that, we chose to reverse polarity instead of realigning the
pentametric fans. Realignment would have required us to swab the tremie
pipes with high-pericosity tetraethyliodohexamine (which we may do in
the future), but we're in a rush. To achieve temporary polarity
reversal, this commit:

* Routes goniometric data into the quasistatic negative-time
  regeneration oscillator,
* Adjusts the annular grillage coefficient, and
* Re-reciprocates the dingle arm.

The parameters of the grillage coefficient are documented in RFC 123ABC.
```

A less-than-ideal version of that commit message might be:

```
fix turboencabulator polarity
```

We discourage the use of `git commit -m` to commit directly on the command line,
since it gives us a poor mindset right at the offset. Instead, we like a plain
`git commit`; we're writing history, and text editors are better for that.

These guidelines apply to commits merged into `master`. In feature branches,
where commits will eventually be squashed and rewritten, we don't worry too much
about message quality and often push "WIP" commits. When squashing and merging
the branch, though, we're careful to take the time to compile a meaningful and
well-formatted message.

Some developers still find it useful to include some context in commits on
feature branches, since that context can jog their memory when they compose
their squashed commit message. That's entirely up to each person, of course.

[commit.style]: https://commit.style/
[Tim Pope]: https://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html
