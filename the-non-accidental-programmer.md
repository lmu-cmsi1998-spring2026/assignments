**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0323: The Non-Accidental Programmer
With this episode, we fully pivot into the _software_ part of “software carpentry:” we’ll go from zero to program end-to-end, with all _git_ activity taking place on the command line! Per the overall spirit of this course, the attention will not be as much about the code but on the _process_ and _tool usage_ that helps bring this code to life

## Preproduction
This episode seeks to strike a tricky balance: we want to retain our focus on improving proficiency with software development tools, especially _git_, but we also need to do this in a situation that faithfully reflects real-world software development workflows. The program to be written should be understood well enough so that it isn’t a distraction from learning the “carpentry” of it all, but it also shouldn’t be rote-memorized, because of course that isn’t how we develop software

We can only do so much within the instructions to ensure this balance; the rest will be up to you and your commitment (pun intended heh) to learning the material in a way that benefits you on the long term. Here is the general approach:

1. Follow the code-along in class
2. Get to know the program well enough to re-code it on your own _without copy-pasting_
3. As before, if you feel you need to practice off-camera beforehand, do so as much as you need to, including invocation of the requisite _git_ commands
4. Use the GitHub red zone as well as the `ls -a`, `rm`, and `rmdir` commands as needed whenever you need to start over

## On Camera
We iterate again the delicate balance that we’re aiming for, which is to emphasize tool usage while keeping things real. Please always be mindful of this as our overarching goal…

### Scene One: Repository-Side Story
Record yourself creating and initializing the repository from scratch. The process is largely the same as the prior episode (private repository, no further add-ons), except that you won’t have any immediate files to add and commit right away. As such, you can largely follow the command sequence that GitHub provides under the **create a new repository on the command line** heading

Use a similar naming schema as before: `episode-0323-<your GitHub username>`

* Make sure to first create the directory for your local repository and `cd` into that before following GitHub’s instructions
* After creating and initializing the repository, reload the GitHub website for it in order to show that it has been fully initialized
* Feel free to invoke `git status` whenever needed, in order to get an up-to-date, accurate understanding of your repository’s status

### Scene Two: A Few Good Commits
In this course, we seek to instill not only proficiency with the tools involved in software development, but with best practices in the software development process itself. As such, we are specifying _which_ commits you should make and _how_ to accomplish them

#### General process for each commit
Because we are seeking to mimic actual software development more accurately, please feel free to use any editor of your choice (probably not command line, heh) for writing your code. This episode shows where command-line editors play a role in the process
1. Perform your edits off-camera using the editor of your choice
2. Make sure your code is in a working state after each milestone
3. When you start recording, state the work that you have just finished and say that you are about to commit your work
4. Use `git status` to show what files were changed
5. Use `git diff` to show the changes that were made
6. Use `git add <filename>` to stage your changes
7. Use `git status` to show that the files are now staged
8. Use `git diff --staged` to show that you can still examine the changes you made
9. Finally, use `git commit -m "<message>"` to commit your work—remember to make the commit message specific and descrirptive!
10. Pause recording at this point and move on to the next commit when ready
11. Take note that for two (2) of these commits, you will do a cut-scene (see below) where you use `git commit --amend`

#### Make five (5) commits, doing three (3) on camera
Phase your work according to the following five (5) units of work, each concluding in a commit. For three (3) of them, record yourself following the process above:
1. Edit the _README.md_ file to describe the program more thoroughly
2. Make the program read the command-line arguments as intended (including setting defaults when an expected argument is omitted)
3. Implement the main loop, ensuring that it runs the desired number of times
4. Generate the random coordinates within the loop, tallying up the ones inside the unit circle
5. Make the program compute and display the final result

These five (5) commits are _in addition to_ the first commit done during repository initialization. So in the end, you should have a total of six (6) or more commits in your repository when you’re done

Note that we are expressly _not_ pushing our work to the GitHub servers until Scene Five

Once more, you are _not_ expected to record yourself doing the actual edits. Just record yourself when the coding work is done and you are ready to commit your work. And you only need to record yourself for three (3) of the commits; do the others off-camera

### Scene Three (actually cut-scenes within Scene Two): Terms of Amendment
For _two_ (2) of the recorded commits in Scene Two, perform an additional step: revising your commit message after having already made the commit. This is done with `git commit --amend`

Yes this is a little contrived but it would otherwise be difficult to do this fully organically 😅

Feel free to concoct whatever reasons you like for motivating an after-commit message revision. Maybe you had a typo; maybe you wanted to rephrase something; maybe you wanted to add another detail. There are lots of real-world reasons for us to revise our commit message after the fact

These two cut-scenes should proceed as follows:
1. Invoke `git commit --amend` to—here it is!—bring up the command-line editor. Note how your most recent commit message appears at the top
2. Edit the message as desired
3. Save and quit
4. Invoke `git log` to show that your commit message has indeed been changed!

#### The editor adjustment bureau
Observe that _git_ will bring up a default command-line editor when performing `git commit --amend`—and this editor might not be your editor of choice. For one (1) of your two (2) commits, show that you know how to set the `EDITOR` environment variable to change this up!
1. `echo $EDITOR` to show its current value (it may be blank, indicating that _git_ will choose a default)
2. `export EDITOR=<path to editor>` to set the editor (use `which` to determine the path)
    * Though less precise, some setups might have a path that has spaces in it—if this affects you, just naming the editor should suffice: `export EDITOR=<editor executable name>`
    * To clear the value of `EDITOR` without having to close/open a new command line window, you can do `unset EDITOR`
4. Do `git commit --amend` as described above

If _git_ **does** default to your editor of choice, turnabout is fair play! Still pick a commit where you perform the above steps, but for the command-line editor that is _not_ your favorite. You can always set it back afterward

As such, _everyone_ should end up with commit amendment footage that:
* Uses your command-line editor of choice
* Uses the _other_ command-line editor
* Shows that you know how to set the `EDITOR` environment variable

And yes, you can make this permanent. We’ll leave this for you to figure out, because not everyone will need to do so. _Hint:_ The previous episode showed you how

### Scene Four: A Multi-run π
With everything done, capture some footage of yourself running the program with different numbers of darts, and share your answer to this question:
> What is the smallest number of “darts” to throw in order to guarantee a π estimate that is accurate to at least 3.14?

### Scene Five: You Git Served
1. Use `git log` to review all the commits that you have made. Remember that if `git log`’s output exceeds the size of your command-line window, you can scroll through it with exactly the same controls as `more`/`less`
2. Use `git push` to send your commits to the GitHub server
3. Reload/refresh the GitHub website for your repository, showing that your work and commit history are now accurately reflected there

## Operational Notes
* Yes, many steps and commands are involved here, but they should all take very little time to actually perform! As such, we expect the final videos to be relatively short
* As before, practice as much as you need off-camera. But always make sure to clear things out before each run, to ensure that you are starting from scratch
* Fun bit: the title of each scene (and one of the sub-scenes) is derived from an old movie. Can you name them all?

(the next section is the same as before, but included here for easy reference)

> ## Video Specifications
> To make sure that we get the key information that we need from your video, all non-interstitial segments (i.e., the parts where you’re showing your command-line skillz) should be formatted as follows:
> * The contents of your command line window should be easily readable, including commands that you are in the middle of typing
> * You must be visible live onscreen (thumbnail, overlay, etc.), and what you say should be sync-ed up with the audio and what you’re typing
> In other words, it must be clear that what’s happening on the command-line screenshare is going on live with your in-person spoken commentary. Any evidence to the contrary will have…undesirable consequences
>
> > Although no particular video software is prescribed for the course, note that the above requirements are easily met by using Zoom. Start a new “meeting” that includes yourself, turn on your camera, share your window or screen, and record. That should pretty much do it
>
> Mistakes are perfectly OK! No need to re-record yourself if you mistype something. In fact, showing how you recover from mistakes live is a good way to reinforce your skills, because such mistakes _will_ happen in real life. If your command has a typo or somehow fails, just try it again and keep going
>
> That said, it’s also perfectly OK to “practice” beforehand. Navigate through the folders and look at files on your own first, before recording the video. That will give you a sense of what you’ll see, such that when you do it with the camera/mic on, you’ll be generally prepared. Casual mistakes will also be easier to recover from if you practice beforehand

## How to Turn it In
Upload the final video file to the corresponding assignment slot in Brightspace. If the file is too large, find an alternative way to host the file then link to it in your Brightspace submission. Ideally this won’t be necessary

In addition, don’t delete the final version of your `episode-0323` GitHub repository. We will be reviewing that as well

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 30 points total |
| • Live creation and initialization of your `episode-0323` GitHub repository | 5 points |
| • Live footage of the specified commits | 5 points |
| • `git commit --amend` scenes for selected commits | 5 points |
| • Setting of `EDITOR` environment variable | 5 points |
| • Multiple runs of the final program in order to answer the question | 5 points |
| • Final `log` and `push`, with exploration of updated GitHub website | 5 points |
| Proficiencies to demonstrate | 70 points total |
| • Initializing and populating a _git_ repository from scratch | 5 points |
| • Making incremental commits as you work, according to the given steps and procedures (this involves both your recorded episode and the state of your GitHub repository) | 20 points |
| • Checking the status of a _git_ repository | 5 points |
| • Examining file differences from the prior commit (unstaged and staged) | 10 points |
| • Reviewing the commit log | 5 points |
| • Amending a commit message | 10 points |
| • Customizing the editor that _git_ uses | 10 points |
| • Using commands and techniques from prior episodes (`cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 5 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
