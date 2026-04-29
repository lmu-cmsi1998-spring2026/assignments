**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0511: Use the Force You Should Not
We wrap up our introduction to software “carpentry” with a suite of less-frequently used _git_ commands, typically not used everyday and meant for very specific situations. Outside of such situations, these commands may be easily misused and can create more problems than they solve. Ergo, the title of this episode

## Preproduction
Unlike prior episodes, the proficiencies to demonstrate in this one are as much about knowing _when_ to use these _git_ commands as they are about simply using them. As such, consider yourself to be a “co-writer” of this episode: as part of preproduction, make sure that you have clearly planned out situations where each command is justifiably called for. Examples of these situations have been described and demonstrated in class—pattern your scenes alongside them, using your own code or past work and providing your own creative details

With the situations planned out, the rest of preproduction is once again a matter of practice. We are back to working solo here, so please do create practice repositories as needed (our sneaky way of making you review past material 😁). Always start your practice repository names with `practice-0511` and include your GitHub username after that, so that it’s immediately clear whose repository is which

## On Camera
Whenever you’re ready with each scene, go ahead and record yourself. Each scene should follow the same general structure:
1. _Before recording_, set up your repository with any pre-existing commits or branches that are needed in order to demonstrate the corresponding command effectively
2. _Upon recording_, describe how the situation starts. What’s in the repository? What activities are you about to do?
3. Do whatever you feel is needed on camera to lead up to the use of the command for the scene
4. Before performing the command(s), use the right combination of `git status`, `git log`, or any other _git_ commands, plus the more visual displays of your repository’s GitHub website, to illustrate the “before” state of your repository
5. Perform the commands themselves. Talk through why these commands comprise the appropriate way to resolve the situation
6. Once the commands are done (committing and pushing as necessary), review the “after” state of your repository, pointing out how your commands have addressed the original problematic situation
7. As much as possible, use realistic code and files to demonstrate your situations. Feel free to pick and choose work from previous episodes, or come up with your own. Code from other classes you’re currently taking can apply too!

Remember that for the command examples in the scenes below, the angle brackets `<>` represent placeholders for actual information that you’ll supply, and the `<>` characters themselves should _not_ be included

### Scene One: `restore` of the Jedi
Enact a situation that calls for an appropriate use of the `git restore` command, which discards current uncommitted changes to files and takes them back to their last committed versions:

    git restore <files/folders>
    git restore --staged <files/folders>

Make sure to also include the case of files that have _never_ been committed, and how `git restore` behaves differently with those files (as seen in class)

### Scene Two: `revert` of the Sith
Enact a situation that calls for an appropriate use of the `git revert` command, which undoes a commit and commits this reversal:

    git revert <commit ID>

### Scene Three: `reset` of Skywalker
Enact a situation that calls for an appropriate use of the `git reset` command, which undoes one or more commits _without leaving a record_ of the reversals. Because this rewrites pre-existing history, updating GitHub will require a `push --force`:

    git reset <commit ID or HEAD expression>

The `HEAD expression` variant is optional but can sometimes be convenient and more intuitive; feel free to look it up if you want to use that

### Scene Four: The Phantom `rebase`
Enact a situation that calls for an appropriate use of the `git rebase` command, which “resequences” a branch so that its changes take place entirely after another one:

    git switch <branch to resequence>
    git rebase <branch upon which to resequence>

Because this rewrites pre-existing history, updating GitHub will require a `push --force`

### Scene Five: The `rebase --interactive` Holiday Special
Enact a situation that calls for an appropriate use of the `git rebase --interactive` command, which provides broad, history-changing capabilities across multiple commits:

    git rebase --interactive <commit ID or HEAD expression>

Yes, this will also require that you “use the `--force`” 🧐 In addition, as seen in class this command makes heavy use of the default command-line editor, so if desired feel free to customize your `EDITOR` environment variable as you please

### Scene Six: Attack of the `cherry-pick`
Enact a situation that calls for an appropriate use of the `git cherry-pick` command, which applies a single commit from anywhere else in the repository to any selected branch in that repository:

    git cherry-pick <commit ID>

This counts as a new commit, and therefore does not require “the `--force`”

## Operational Notes
* Remember again that, as not-everyday-use commands, an important takeaway of this episode isn’t just _how_ to use these commands well, but also _when_ (as discussed in class). It may in fact take more time to fashion a compelling situation than it will to perform the commands that resolve this situation, so plan accordingly
* It’s OK to work with classmates in brainstorming situations that motivate these commands; this can save you time and generate viable ideas more quickly. If you do work with someone else in coming up with setups for the scenes, restrict the collaboration to the _idea_ or _concept_—make sure to set up files and repositories individually

## How to Turn it In
Upload the final video file to the corresponding assignment slot in Brightspace. If the file is too large, find an alternative way to host the file then link to it in your Brightspace submission. Ideally this won’t be necessary

Leave any repositories used in the video on the class’s [GitHub organization](https://github.com/lmu-cmsi1998-spring2026). Make sure they are named clearly; at the very least, include your GitHub username in the repository’s name. Ideally, the repository name also identifies that it is part of this episode: `episode-0511`

We expect to see the `practice-0511` and `episode-0511` repositories as well—as before, we will be reviewing them too

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 30 points total |
| • Scenario for `git restore` | 5 points |
| • Scenario for `git revert` | 5 points |
| • Scenario for `git reset` | 5 points |
| • Scenario for `git rebase` | 5 points |
| • Scenario for `git rebase --interactive` | 5 points |
| • Scenario for `git cherry-pick` | 5 points |
| Proficiencies to demonstrate | 70 points total |
| • Sensible situation for and effective usage of `git restore` | 10 points |
| • Sensible situation for and effective usage of `git revert` | 10 points |
| • Sensible situation for and effective usage of `git reset` | 10 points |
| • Sensible situation for and effective usage of `git rebase` | 10 points |
| • Sensible situation for and effective usage of `git rebase --interactive` | 10 points |
| • Sensible situation for and effective usage of `git cherry-pick` | 10 points |
| • Using commands and techniques from prior episodes (_git_ commands covered so far, `cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 10 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
