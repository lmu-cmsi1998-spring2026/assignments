**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0408: Dynamic Duo
We expand our _git_ horizons further by playing to one of its greatest strengths: concurrent, distributed development. As such, this episode will be done in pairs, with co-hosts taking turns showing off their _git_ skills 💯

## Preproduction
Preproduction, as with the previous episode, is pretty much multiple practice runs of the script. That way, you can experience multiple repetitions of commits, pulls, merges, and merge-conflict resolution. This will also allow you to get to know the [MacGuffin](https://en.wikipedia.org/wiki/MacGuffin) program for the script, _day_counter_

### Practice Repository
One difference is that because it will be less practical here to keep creating, setting up, then deleting a new repository every time, we will establish a practice repository for all of the pairs, `practice-0408-<team name>`. You can keep using that repository throughout your practice runs; because you need to “reset” things every time, you will want to learn the _git_ command for removing a file from the repository:

    git rm <file/folder>

This works just like `git add` except that it notifies _git_ that you want to _remove_ files/folders from the repository (i.e., _git_ will stop tracking them). Finishing the sequence is the same as before: once your staged files are showing exactly the actions that you want, you can `git commit` then eventually `git push` to update GitHub’s remote copy. Of course, as you perform each command, feel free to invoke `git status` to get to know how your repository’s state changes from one command to the next

To document that you actually _did_ practice the script 😅 we will review your practice repository before creating the final repository that you will use on camera. A fresh repository will be created so that it will have a clean history without lingering practice commits in it

### Practice Onscreen Collaboration
Because the script calls for taking turns with screensharing, your team may find it worthwhile to also spend some time with practicing that. In particular, get the hang of taking turns with sharing windows or screens, so that you can smoothly transition to each other as called for by the script. The more practiced you are with this, the smoother it will be to tap in and out on camera

## On Camera
Once you are ready to record, notify the instructor that you are ready and we will create a fresh repository for your team, with the name `episode-0408-<team name>`, already set up to include you as collaborators. We will take a quick look at `practice-0408-<team name>` to ensure that you have indeed put in some preproduction time before recording. Once the final repository has been created, you may then clone it and follow the script for real, on camera 🎥

### The [MacGuffin](https://en.wikipedia.org/wiki/MacGuffin): A program that counts the days between two dates
To provide a sufficiently realistic scenario for performing the version control operations in this script, your team will implement _day_counter_, a program that accepts two dates expressed as three integers apiece for year, month, and day, then computes the number of days between them

As seen in class, implementing this program cleanly requires three “support” functions:
* `is_valid_date(year: int, month: int, day: int) -> bool` returns `True` if the given `year`, `month`, and `day` comprise a valid date and `False` if not. For example, June 19. 1992 is a valid date; June 31, 1992 is not. February 29, 2024 is a valid date; February 29, 2025 is not
* `days_in_month(year: int, month: int) -> int` returns the number of days in the given `month` for the given `year`. The `year` parameter is necessary because leap years affect the number of days in February. It’s true that all other months have the same number of days regardless of the year, but for generality, even a single edge case necessitates knowing the year
* `is_leap_year(year: int) -> bool` returns whether the given `year` is a leap year. This function should accurately follow the [leap year rules for the Gregorian calendar](https://en.wikipedia.org/wiki/Leap_year#Gregorian_calendar)

To encounter the expected merge situations in the script, make sure to implement each function _in its own separate file_. This also gives you practice with writing multi-module programs, which is almost always the case for most code these days

You will then have a final file, _day_counter.py_, which houses the `day_counter` function itself. The file should be executable from the command line as follows:

    python3 day_counter.py <year1> <month1> <day1> <year2> <month2> <day2>

The `day_counter` function itself should have this signature:

    day_counter(year1: int, month1: int, day1: int, year2: int, month2: int, day2: int) -> int

The return value should be the number of days between the two dates

Note that, as a “MacGuffin,” the exact behavior, robustness, and correctness of the program itself isn’t the focus of the episode; it is mainly there to give you a concrete target around which to show your _git_ knowledge and skills. However, you are strongly encouraged to work out at least an MVP (minimum viable product) for the program, just for your own personal satisfaction and to match up with future real-world scenarios as accurately as possible

### Scene One: Holy Leaping Years, Batman!
Before recording this scene, do the following:
* One team member should implement the `is_leap_year` function in its own file
* The other team member should edit _README.md_ with some descriptive Markdown for the _day_counter_ program

Now _on camera_, do the following, switching screenshares as needed:
* Both team members should commit their work using the established routine from the previous episode: `git diff`, `git add`, `git diff --staged`, `git commit -m`, with `git status` invoked as frequently as needed
* One team member should push first (`git push`). You may also show the GitHub website to show that the push has landed on GitHub’s servers
* The other team member should then do a `git pull`. This should result in a merge that does not have any conflicts because you edited different files. This pulling team member should show that they can successfully complete the merge operation
* **Test the merge:** Make sure that the merged version of the code still works as expected
* Once the merge is done and tested, the pulling team member can now invoke `git push`
* Finally, the first team member does a `git pull`, resulting in everyone now being in-sync
* And…cut!

### Scene Two: Riddle Me the Days in this Month, Batman!
Before recording this scene, do the following:
* One team member should do some light edits on the `is_leap_year` file—you can make improvements, add comments, or anything that looks right.
* The other team member should implement the `days_in_month` function in a new, different file from `is_leap_year` (so you will need to import that function because `days_in_month` needs `is_leap_year`)

Now _on camera_, do the following, switching screenshares as needed. Importantly, the merging team member should switch—if you merged in Scene One, then your teammate should be the one merging in Scene Two:
* Both team members should commit their work using the established routine from the previous episode: `git diff`, `git add`, `git diff --staged`, `git commit -m`, with `git status` invoked as frequently as needed
* The team member who didn’t push first previously should push first now (`git push`). You may also show the GitHub website to show that the push has landed on GitHub’s servers
* The other team member should then do a `git pull`. This should result in a merge that does not have any conflicts because you edited different files. This pulling team member should show that they can successfully complete the merge operation
* **Test the merge:** Make sure that the merged version of the code still works as expected
* Once the merge is done and tested, the pulling team member can now invoke `git push`
* Finally, the first team member does a `git pull`, resulting in everyone now being in-sync
* And…cut!

### Scene Three: Same Valid Bat-Date, Same Valid Bat-Channel!
Before recording this scene, do the following:
* _Both team members_ should implement their version of `is_valid_date`—make sure to use the exact same filename!
* This time, the commits can happen off-camera. Do that locally, _without_ pushing yet

Now _on camera_, do the following, switching screenshares as needed:
* One team member pushes their work first
* The other team member then pulls, and this should result in a merge conflict because you both created the exact same file
* Both team members should then work to resolve the conflict; show yourselves looking at the two alternative versions of `is_valid_date` and deciding together which lines to keep or omit
* The pulling team member resolves the conflict (`git add`)
* **Test the resolved merge conflict:** Make sure that the merged version of the code still works as expected
* Once the resolved merge conflict is done and tested, complete the operation for _git_ (`git add`, `git commit`), then `git push`
* Finally, the first team member does a `git pull`, resulting in everyone now being in-sync
* The first team member should also test this latest version, to ensure that things are also still working on their side
* And…cut!

### Scene Four: Bam! Pow! Count! Days!
Before recording this scene, do the following:
* _Both team members_ should implement their version of `day_counter`—make sure to use the exact same filename!
* As with the earlier scene, the commits can happen off-camera now too. Do this locally, _without_ pushing yet

Now _on camera_, do the following, switching screenshares as needed:
* Are you sensing a pattern yet? 😁 Despite the length of each scene, note that they essentially play out the same scenarios, giving each team member a turn on each side of the workflow
* So the on-camera activities for Scene Four are the same as for Scene Three, except that the team members should switch roles this time 

### Cut-Scene: Bat File Repellent (_.gitignore_)
Somewhere between Scenes One and Four, a folder called _\_\_pycache\_\__ will appear in your respective repositories. This is what is called a _build product_—a file created by technology platform that is derived from the code and therefore does not need to be committed because it gets generated automatically as needed. One can just manually avoid doing `git add` on this file, but that can be error-prone. Instead, _git_ has a file for that!

The moment one of you sees _\_\_pycache\_\__ show up, don’t include it in any `git add`s. Instead, it’s time to create a file called _.gitignore_. This file should be at the top of the repository folder and should just contain that folder’s name:

    __pycache__

_On camera_, one team member should create this file and then:
* Creating this file should now _omit_ _\_\_pycache\_\__ from `git status`
* Use `ls` to show that the folder is still there; it is simply just ignored now by _git_
* Once this is verified to work as expected, that team member should `add`, `commit`, and `push` this latest change
* _Before pulling_, the other team member should then show _\_\_pycache\_\__ appearing in `git status`
* As always, commit any work in progress before pulling
* The team member then performs a `git pull` (with merge if needed)
* The pulling/merging team member should then re-invoke `git status` to show that _\_\_pycache\_\__ is no longer listed, despite `ls` showing that it is still present

## Operational Notes
* As indicated, the script is lengthy due to the amount of detail, but it really just repeats the same pattern. The detail is provided to ensure that each student shows the intended experience on camera, but ultimately, it’s the same flow for each scene. Hope that makes things more manageable
* Note also that each scene can take place with time-jumps in between. Please leverage that characteristic to make it easier to plan and coordinate recording sessions. The important condition is that you _both give yourselves enough time_ to do this, rather than cramming everything too near the due date
* Depending on how _git_ is configured on your machine, one or both of you may encounter an initial message upon your first `git pull`. It will start like this, usually in a different text color:

        hint: You have divergent branches and need to specify how to reconcile them.
        hint: You can do so by running one of the following commands sometime before
        hint: your next pull:

  If you see this, choose the first command option shown, `git config pull.rebase false` (as you learn more about _git_, you might prefer one of the other options in the future, but for now go with that first one)

  After running that command, doing `git pull` a second time should proceed without incident. No worries if you encounter this off-camera; just set things up and proceed as planned. Same if it happens while on-camera—that’s all good, just act accordingly and move right along

  This configuration should happen at most only once for every repository clone. If it appears to happen repeatedly, let me know and we will try to diagnose why the setting does not appear to stick on your setup

## How to Turn it In
Upload the final video file to the corresponding assignment slot in Brightspace. If the file is too large, find an alternative way to host the file then link to it in your Brightspace submission. Ideally this won’t be necessary

We expect to see the `practice-0408` and `episode-0408` repositories as well—as before, we will be reviewing them too

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 80 points total |
| • Conflict-free committing and merging of `is_leap_year` and _README.md_ | 16 points |
| • Conflict-free committing and merging of `is_leap_year` and `days_in_month` | 16 points |
| • Merge conflict resolution of `is_valid_date` | 16 points |
| • Merge conflict resolution of `day_counter` | 16 points |
| • Appearance of _\_\_pycache\_\__ and omission via _.gitignore_ | 16 points |
| Proficiencies to demonstrate | 120 points total |
| • Good commit habits by both team members (`git status`, `git diff`, etc.) | 20 points |
| • Merging non-conflicting pulls by both team members | 30 points |
| • Resolving merge conflicts by both team members | 30 points |
| • Telling _git_ to ignore files that should not be committed via _.gitignore_ | 20 points |
| • Using commands and techniques from prior episodes (_git_ commands covered so far, `cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 20 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **200** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
