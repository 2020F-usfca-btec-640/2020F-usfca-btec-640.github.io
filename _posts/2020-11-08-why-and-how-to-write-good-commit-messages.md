---
layout: post
title:  "How to and Why Write Good Commit Messages"
date:   2020-11-08 12:54:04 -0700
categories: commit messages overview
---
## The Purpose of Commit Messages

When you want to save a snippet of code to your Git repository, a commit command is used. This will tell whatever program you're using to take a snapshot of your work so it can be referred to at a later time. Committing your work documents your progress as you work through and perfect your code. A caption is necessary for each of these snapshots so you know what was changed and why certain decisions were made. This is the purpose of a commit message. *A commit message is a concise statement detailing how and why changes were made in your code.*

## The Importance of Writing Good Commit Messages

#### A well written commit message is the best way to communicate changes in your code.

###### This includes communicating to:
  1. Yourself
    * The way you write messages can help you remember what you did when you go back to look at them weeks or months later.
  2. Your collaborators
    *  Being as descriptive as possible in just a few words can help others understand the progress of your work without confusing them.

Writing concise commit messages will make the log of your Git repository easier to navigate and the flow of a project comprehensible. Uncomplicated messages are crucial for teams to effectively collaborate in GitHub.

#### Things to keep in mind when creating a Git commit message
  1. Specify the type of commit. Examples of commit types includes a fix, a  feature or style update, a test, documentation, etc.
  2. Always use the imperative tense, **not past tense!**
  3. Use a capital letter in the first word of the subject line.
  4. Subject and body of a commit need to be separate - use a blank line.
  5. The subject line should not exceed 50 characters.
  6. Wrap text of body manually at 72 characters.
  7. If you have a hard time keeping it brief, you're probably trying to commit too many changes at once. Commit frequently to avoid this.
  8. Aim to explain why and what you did, not how you did it.
  9. Do not end your commit message with a period.

## How to write a commit message

#### A commit message should always be able to fill in the blank part of this sentence:
This commit will *fill in the blank*

###### For example:
This commit will *fix problem x*

###### This sounds a lot better than:

This commit will *fixed problem x*

See why using the imperative tense is important? Commit messages should sound like you are commanding someone to do something.

#### Subject and body of a commit message

Many times commit messages will not warrant much explanation and a simple message will suffice. A common example is when you find a typo.

```
Remove extra character
```
In this situation, you can simply look and see that an extra character was removed from your code. This is a simple typo, so no extra explaining is necessary.

However when one 50 character line isn't enough to explain, you'll need to add a body. This would look something like:

```
Add subject here and do not exceed 50 characters

Add body here and separate with a blank line.
Wrap text so body does not exceed 72 characters.
```
#### The easiest and fastest way to add and commit your work is to use command line arguments.

  This process would look something like this:
  ```bash
  $ git add my_script.sh
  $ git commit -m "Fix problem x"
  ```
  Then, after you've finished working and committed everything you can push to your GitHub repository.

  ```bash
  $ git push origin my-branch
  ```
  **Note:** if your commit message requires a body, you can use -m multiple times in the command line separated by a blank to create a new paragraph.

  ```bash
  $ git commit -m "Subject" -m "Body"
  ```
You can read more about writing commit messages [here](https://chris.beams.io/posts/git-commit/)
