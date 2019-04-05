# Git Merge Conflicts

## Learning Goals

- Identify merge conflicts
- Recognize resolving merge conflicts
- Recognize reverting merges

## Introduction

When working on our own on utilizing a standard git workflow a project, chances
are we may not encounter clashing code when merging between branches. However,
in a collaborative environment, things can get a little messy.

Don't let it cause alarm! With a little bit of context, time, and patience, we
can often step through merge conflicts and "resolve" them one by one, ending up
with a single functional working branch when it's all done. Remember, Git
provides us a number of tools that help keep our work safe, so don't get scared
if you see a conflict, or even make some mistakes along the way. You can always
cancel or undo changes and start again if necessary.

## Identify Merge Conflicts

How does this happen? Let's take a simple scenario: We were very careful to pull
down a working branch and made several commits documenting our progress.
However, when we are ready to "push" our changes back up to the remote branch or
"merge" them into another branch such as `master`, we get got an error from Git
along the lines of:

```bash
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
```

Git merge conflicts occur when competing changes are made to the same line of a
file, or when one person edits a file and another person deletes the same file.
Usually, Git is able to easily merge multiple changes by different people
without issue, but a change like reordering a couple blocks of code or text or
even a small change like adding or removing code from the same line can
create a merge conflict.

## Recognize Resolving Merge Conflicts

In Git, "merging" is the act of integrating another branch into your current
working branch. You're taking changes from another context and combining them
with your current working files.

If you open the offending file in a text editor, you’ll find an indication of
the bits that are different, something like this:

```bash
<<<<<<< HEAD
The line I changed in this file.
=======
The line someone else changed in this file.
>>>>>>> 031389f2cd2acde08e32f0beb084b2f7c3257fff # (this can be a commit number or a branch name)
```

The contents after the first markers are from your current working branch. After
the angle brackets, Git tells us where (from which branch or commit) the changes
came from. The line with `=======` separates the two conflicting changes.

You will have to resolve the conflict manually. Edit the content between the
`<<<<<<<` and `>>>>>>>` angle brackets to get the file where it needs to be.

After cleaning up the file with the final contents, all that is left is to save
it. When you're done with that file, you mark the file as resolved by executing
`git add <filename>`.

Finally, a merge conflict situation needs to be concluded by a regular commit
with a commit message noting the conflict resolution.

## Recognize Reverting Merges

Keep in mind that you can return to the state before you started the merge at
any time. This should give you the confidence that you can't break anything. On
the command line, you can use `git merge --abort` to do this for you.

In case you've made a mistake while resolving a conflict and realize this only
after completing the merge, you can still easily undo it: You can revert back to
the commit before the merge happened by viewing the log with `git log` and reset
it with `git reset --hard <commit number>` to start over again.

## Conclusion

Merge conflicts can seem like a scary task. Developers fear that they may lose
important data in the act of combining content from other commits. However, a
merge conflict is not something to be feared! It will not bring you or your team
to a halt or cripple your central repository. Git merge conflicts can only occur
on a developer's local machine&mdash;and not on the server. This allows us to
assess each change one by one, and bring the files together safely. Git gives us
clear indicators where each conflict lies and the tools to correct them. Git
also gives us tools to undo changes that were made in the merge conflict, in
case in mistakes were made and noticed after the fact. This feature allows
branching to be additionally useful when it comes to having a sandbox to test
out new code.

## Resources
[Dealing with Merge Conflicts](https://www.git-tower.com/learn/git/ebook/en/command-line/advanced-topics/merge-conflicts)
[Resolving a merge conflict using the command line](https://help.github.com/en/articles/resolving-a-merge-conflict-using-the-command-line)
[Git merge conflicts](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts)