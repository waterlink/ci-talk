Hello.

This is TDD screencast #6. Today we are going to talk about Continuous Integration Training.

I'm Oleksii Fedorov. I'm Software Craftsperson.

Let's start with the outline.

First, we will talk about Continuous Integration. What it is and what it isn't.

Second, we will take a close look at Check-Out/Check-In cycle.

Then, we will take a look into the training Kata with restrictions.

Then, we will do some live coding on that Kata.

Finally, we will draw a bottom line.

Shall we get started?

Jenkins server, Travis server, TeamCity server, and others are not Continuous Integration.

They are just Build-Servers.

Continuous Integration means to integrate our changes back to the upstream very often.

In terms of `git`, that would mean doing `git push origin master` every few minutes.

The reason for doing that is to avoid long-running branches and painful merges and to enable continuous delivery.

So how often should we integrate if we were to do continuous integration?

According to Extreme Programming, we should integrate every TDD Red-Green-Refactor cycle.

Meaning that, we check out the latest changes from the version control system, we apply one Red-Green-Refactor cycle and we check in our changes back.

For `git` it would mean:

- do pull-rebase from the upstream
- do one cycle of Red-Green-Refactor
- commit our changes
- do another pull-rebase from the upstream
- fix any conflicts
- and push everything back to the upstream

Such a cycle would be 3-5 minutes on the average

At first, Continuous Integration is really hard to do

Although, it is a trainable skill

We train it by applying "Discard on RED" restriction to any TDD Kata.

- We set up a timer to ring every 2 minutes
- Every time it rings, we run tests
- When tests are green, we proceed as nothing happened
- And when tests are red, we discard any pending changes
- We are allowed to commit the changes only when in green state, at any point of time

We will need a way to discard the changes and make the commit quickly. Maybe IDE shortcuts or aliases on the command line. Here is what I usually use:

- `red` command that discards any pending changes
- and `green` that commits all pending changes with supplied commit message

Let's take a look at our Kata, that we will be doing today:

It is called "Matches 3 Kata"

There is a field with gems of different colors.
When player swaps neighboring gems:

- 3 or more gems of the same color in row or column are to be destroyed
- or, when there are no such gems, swap is to be rejected

There is an additional concept of gravity:

- when gems are destroyed, the gems placed on top of them are to be moved down to fill empty cells of the field
- as you might guess, this may result in more gems to be destroyed

Let's take a look at the example:

- Every rectangle here represents concrete state of the field
- R means gem of Red color
- G means gem of Green color
- B means gem of Blue color

- First, we can see that player swaps two neighboring gems
- They are getting swapped
  - and there is a row of 3 gems of blue color
  - they are getting destroyed here
- Then gravity gets applied:
  - and gems on the top of empty cells get moved down

That is it with the example. Shall we begin with live coding?


## Bottomline

Today we have learned that Continuous Integration and Build Servers are not the same thing.

Additionally we learned that length of TDD Red-Green-Refactor cycle might be just perfect fit for Check-Out/Check-In cycle.

Finally we have taken a look into the TDD Kata restriction, that allows us to train Continuous Integration skills.

From demo, it was clearly seen that the restriction punishes us every time we do too big step and it forces us to find smaller incremental steps instead.

That is it for today. Thank you for watching. Until next time!
