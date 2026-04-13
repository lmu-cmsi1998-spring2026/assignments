**CMSI 1998** Special Studies: Software Carpentry, Spring 2026\*

\*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0427: Welcome to the Multiverse
In this episode, we take _git_’s ability to facilitate concurrent, distribute software development to its logical extreme: multiple _branches_. So like before, this episode needs to be done in pairs

As a side trip, due to the amount of starter code involved, we will use GitHub Classroom to set up this assignment. Make sure to use the supplied links in the course website to set up your repositories!

## Preproduction
Preproduction is once again about straight-up practicing of the script, although this time the practice and final repositories are acquired via GitHub Classroom rather than being manually created by me. Take advantage of the practice phase to familiarize yourselves with this episode’s [MacGuffin](https://en.wikipedia.org/wiki/MacGuffin): a calculator function with a modular design for supporting different mathematical operations

The episode script involves common activities that are accomplished using _git_ command sequences. They are described here, and can be practiced in isolation (i.e., you can do these activities in ways that are different from how they are specified in the script). However, it does make sense to eventually practice them exactly described in the script once you feel that you’re ready

### Creating branches
1. Use `git switch` to ensure that you are on the branch that will serve as the basis of the new branch (the base branch is always `main` in the script, but in practice it can be any branch at all)
2. Invoke `git switch -c <new-branch-name>`: the `-c` option tells `git switch` that you would like to create a new branch. Note that _git_ branch names may not contain spaces
3. You can now work as usual: create/edit files, `add`/`commit` them, rinse and repeat
4. At this point, the branch is on your local repository only. To send it to the server, invoke `git push -u origin <new-branch-name>`

### Merging branches
1. Make sure that you have committed any work that you have been doing
2. Use `git pull` or `git fetch` to grab the latest code from the GitHub server
3. Use `git switch <branch-to-merge>` to reference the remote branch locally
4. Try out the branch to get to know what has changed and/or to test for regressions
5. Use `git switch` to return to the branch into which you will be merging the new work (this is always `main` in the script, but in practice it can be any branch)
6. Invoke `git merge <branch-to-merge>`
7. _Test the program_ once more to make sure that everything is OK
8. Whenever you are ready, use `git push` to send the updated base branch to the server

### Stashing uncommitted work
If you need to merge a branch before you reach a viable commit point in your own workflow, you can use `git stash`:
1. Invoke `git stash push` to set aside revised files (note that this does not affect new, untracked files—in practice, such files are not yet referenced by any committed code so _git_ leaves them there)
2. With your code stashed, you should be able to follow the steps above for merging branches
3. Once the merge is complete, invoke `git stash pop` to bring the stashed code back
4. If the merged branch contained modifications to your stashed files, conflicts may arise. Such conflicts can be resolved in the same way as in the previous episode
5. _Test the program_ after merging to make sure that everything is OK

### Resolving conflicts
Conflict resolution was covered in the prior episode, so this should mostly be a review:
1. Use a code editor to comparing current vs. incoming changes, and edit the code to reflect whatever combination of these changes constitutes the correct version of the code
2. If you are resolving conflicts due to a branch merge, make sure to `git add` the reconciled files then invoke `git commit` (no message) to conclude the merge
3. If you are resolving conflicts from a `git stash pop`, you may wait to perform the `add`/`commit` sequence until your own work-in-progress has reached a committable state
4. _Test the program_ after all conflicts are resolved to make sure that everything is OK

When the script mentions any of these activities, that means you will want to perform the corresponding command sequence, customized according to the specific branch(es) involved

As you can see above, you must _always_, _always_ test the final result of your merges to make sure that the code still works as intended and does not experience any regressions. In repositories with robust _continuous integration_ setups, missing a regression may be caught automatically and _everyone will know_ that you’re the one who broke the build 😬

## On Camera
Once you are ready to record, use GitHub Classroom once again to acquire the final repository for the episode. The final repository will have the same starter content as the practice repository so make sure to keep track of which folder you’re doing your work!

### This Episode’s [MacGuffin](https://en.wikipedia.org/wiki/MacGuffin): A calculator program that can be extended in a modular way
The _calc_ program in the starter repositories provides the foundation for a command-line program that can perform various operations, which each operation being supplied as a separate _module_ in its own Python file. This allows modules to first be developed on their own, without having to change the central _calc.py_ file. When a module is finished, it can then be “installed” into _calc.py_ with just a few lines of code

A module consists of two (2) functions:
* The _operator_ function performs the calculation itself: it is expected to accept a single `list[float]` argument (representing its operands) and returns a `float` representing the result of performing the operation on those operands. For example, the _add_ module’s operator function is defined like this:

      add(addends: list[float]) -> float
* The _describer_ function returns a string that describes the operation. The _calc_ program uses this function to display help messages for the user. It takes no arguments and returns a `str`, like this:

      describe_add() -> str

The modules do not need to have any knowledge of the _calc.py_ program, and can be developed as standalone programs (see the `if __name__ == '__main__':` block of _add.py_ for an example)—perfect for doing concurrent work! When a module is ready for use by _calc_, _calc.py_ can be revised as follows:
1. Import the operator and describer functions into _calc.py_
2. Add an entry to the `CALC_MODULES` dictionary, as follows:
   * The _key_ of the entry is the command-line identifier of the operator
   * The _value_ of the entry is itself a dictionary with two keys/values: `operator` references the operator function, and `describer` references the describer function

You can look at the existing entry in `CALC_MODULES` for a concrete example of these specifications

As with previous “MacGuffins,” the exact behavior, robustness, and correctness of the program itself isn’t the focus of the episode; it is mainly there to give you a concrete target around which to show your _git_ knowledge and skills. However, you are strongly encouraged to work out at least an MVP (minimum viable product) for the program, just for your own personal satisfaction and to match up with future real-world scenarios as accurately as possible

### Scene One: A Bug’s Life
The starter code is buggy as-is! It doesn’t gracefully handle the case where an unsupported operator (i.e., an operator without an entry in `CALC_MODULES`) is given by the user. For this scene, one team member should create a bugfix branch that uses a `try`/`except KeyError` block to handle this situation by reminding the user which operators are available while the other team member continues to enhance the program by implementing a new module of their choice, performing their work on another branch

On-camera, the scene should start with the following:
1. The bug-fixing team member should show themselves creating a bug-fix branch and pushing it to `origin`
2. The module-creating team member should show themselves creating a branch for the new module and pushing it `origin`

Off-camera, both team members should do their work, committing as frequently as necessary. Once the work is finished, the team goes back on camera to show the following:
1. Both team members take turns using `git log` to show the work that they have done on their respective branches, then push their branch to `origin` so that the GitHub server is fully updated
2. One of the team members then goes to _Insights > Network_ on their repository’s GitHub website to show how all three branches (`main`, the bug-fix branch, and the new-module branch) are visualized by the website
3. The bug-fixing team member merges the bug-fix branch into `main`, demonstrating how `main` now handles an unsupported operator gracefully. `main` is then pushed to the server
4. The new-module team member switches to `main`, invokes `git pull`, then merges `main` into the new-module branch. After the merge, the new-module branch should now handle unsupported operators gracefully as well, _and_ also support the new operation implemented by the module. Once everything is working, the merged branch should be pushed to the server
5. The new-module team member merges the new-module branch into `main` and pushes this to the server as well
6. Finally, the bug-fixing team member pulls `main`, showing that they too now have both the fixed program and the newly-implemented operator

This scene models how bug-fixing and new-feature development can take place on a software product at the same time 🪲

### Scene Two: Finding New Operators
It’s time to focus on new features! For this scene, both team members each implement new operators and their describer functions. They each work on their own branches, then merge and test when done. One team member merges before the other member commits, thus requiring the use of `git stash` in order not to lose their work-in-progress

On-camera, the scene should start with each team member creating a branch for their new operator then pushing it to `origin`. The action then goes off-camera as each team member implements their respective new operators. One team member commits as frequently as necessary, while the other member does _not_ commit their work 

Once the committing member’s work is done, the team returns to the camera to merge their work. After each merge, the program should be tested to ensure that the new operator has been integrated correctly. _calc.py_ should also be run without arguments to make sure that the describer functions are correctly invoked as well:
1. The committing team member pulls `main` then merges their branch into `main`, doing the aforementioned tests before pushing
2. The non-committing team member uses `git stash push` to set their work-in-progress aside temporarily, then pulls `main` to verify that the new operator is now on their copy and works as expected
3. That team member then switches back to their branch, invokes `git stash pop`, then commits to their branch, merges into `main`, and verifies _their_ work on `main` before pushing
4. If a merge results in a conflict, both team members should look at the conflicting code and figure out how to resolve it together. After that, the usual merge conflict resolution sequence should be performed
5. Once both new operators have been successfully merged into `main`, one team member performs a cumulative demo showing how their version of _calc.py_ now supports four (4) operators overall: the original `add` operator, the operator added in Scene One, and the two operators added in Scene Two
6. After the demo, the other team member then shows GitHub’s _Insights > Network_ view to review the overall history of their code up to this point

This scene models how multiple new features can be developed concurrently, then merged into a new version of the software product once the features are done 🚀

### Scene Three: Coco-operators
Scene Three is structurally the same as Scene Two, except the roles should be switched so that the other team member now shows their ability to `git stash` their work. Come up with two more new operators to implement (if you run out of ideas, let me know!) and follow the Scene Two sequence again, except switch roles for the team member who does not commit their work and must use `git stash` in order to pull `main`

## Operational Notes
* Just as with the previous episode, this episode essentially consists of the same activity, but with slight variations per scene. Scenes Two and Three are identical but with role reversals for the team member who stashes their work. As always, this is intentional and is meant to provide multiple opportunities for practicing the creation, maintenance, and merging of branches
* However, the activities themselves consist of multiple actions and so practice off-camera is also very important. The number of actions involved do reflect real-world processes so it’s important to get to know them well and correctly. Please don’t hesitate to ask the instructor for clarification if a sequence doesn’t seem to go as expected or if any confusion arises

## How to Turn it In
Upload the final video file to the corresponding assignment slot in Brightspace. If the file is too large, find an alternative way to host the file then link to it in your Brightspace submission. Ideally this won’t be necessary

We expect to see the `practice-0427` and `episode-0427` repositories as well—as before, we will be reviewing them too

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 90 points total |
| • Concurrent branch work and merging on a bug fix and _calc_ module | 30 points |
| • Concurrent branch work on distinct _calc_ modules with stashing | 30 points |
| • Another scenario as above but with switched roles | 30 points |
| Proficiencies to demonstrate | 110 points total |
| • _git_ branch creation and pushing by both team members | 25 points |
| • Merging non-conflicting branches by both team members | 20 points |
| • Resolving branch merge conflicts by both team members | 20 points |
| • Pushing and popping unfinished, uncommitted code to/from the _git_ stash | 25 points |
| • Using commands and techniques from prior episodes (_git_ commands covered so far, `cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 20 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **200** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
