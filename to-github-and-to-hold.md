**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0309: To [Git]hub and to Hold
In this episode, we pivot toward a _major_ command-line program that is used in software development: _git_. Like “Kleenex” is to tissue paper or “Xerox” is to copy machines, _git_ is a specific product in the category of source- or version-control software. This software is responsible for ensuring that we can capture the unique nature of source code as a continuously evolving entity, involving fits and starts and frequently worked on at the same time by multiple parties. As of this writing, _git_ is the most widely-used source-/version-control software out there, and GitHub is one of its most widely-used service providers.

## Preproduction
For this episode, “preproduction” primarily involves practice: the total amount of time for these specific activities is anticipated to be pretty brief. However, because the activities themselves will be new or relatively unfamiliar to many of you, it is recommended that you practice them in their entirety off-camera, so that by the time you record yourself, you will have done these same steps multiple times already, and can show that you can do them on camera with confidence and ease

As such, the following specific steps are recommended:
1. Create a backup copy of your curated image collection from [Episode 0204](./curator-personalis.md) so that you can restore it when needed (e.g., restarting your practice, recovering from mistakes, etc.)
2. Don’t hesitate to create and recreate new GitHub repositories for your practice runs—as has been mentioned before, this course relies on repetition in order for you to get the hang of things!
3. Whenever you start over, make sure to fully delete your practice repositories. This option can be found in the _Settings > General > Danger Zone_ section of your GitHub repository’s website. Yes it’s scary-tinted in red, precisely because it involves permanent loss of data. But those options wouldn’t be there if they didn’t have their [rare] uses. Deleting practice runs is definitely one of them 😊
4. Familiarize yourself with [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) using the GitHub website’s built-in editor. Truth be told, in most cases this is what lots of folks use to edit their Markdown (_.md_) files; in fact, I’m using it now in order to write these instructions. But again, the purpose of this course is to familiarize you with becoming proficient at the command line because that’s where a lot of software development happens, so for this episode, the web-based editor is mainly for getting to know Markdown formatting better. On-camera, you’ll do these edits with a command-line editor

As far what you’ll do on camera…

## On Camera
Once you feel sufficiently comfortable, record yourself according to the following script. Of course, make sure to read this script ahead of time too, so that you know precisely what you should be practicing!

_Note:_ As with the previous episode, to make sure that we aren’t totally lost in the future if we encounter an environment that only has one editor or another, make sure you use your non-favorite editor in this video _at least once_

### Scene One: Let There Be Repository
1. Create a new _git_ repository under [this course’s GitHub organization](https://github.com/lmu-cmsi1998-spring2026). To avoid overlapping or conflicting names, name your repository according to this format (don’t include the `<>` when you substitute your GitHub username):

       episode-0309-<your GitHub username>

   Make the repository _Private_ and do **_not_** add anything further to it (i.e., no README file, no _.gitignore_, no license). The intent is for you to know how to initialize a _git_ repository from scratch
2. On your command line, create a new folder (`mkdir`) that will house your repository’s file
3. `cd` to that folder
4. While `cd`-ed in that folder, invoke:

       git init

    * This script asks you to do a variant of GitHub’s instructions labeled “**…or create a new repository on the command line**”
    * During practice, consider following those commands exactly at first, just so you get the hang of it
5. Use the command line to move (`mv`) your curated image collection folder from [Episode 0204](./curator-personalis.md) into this brand-new _git_ repository
6. Invoke `git status` to show that _git_ now lists this folder in the “Untracked files” section
7. Now that the files are there, you can proceed with the following commands. Note that they correspond to the instructions given in “**…or create a new repository on the command line**,” but we did `git init` first and we now include your curated image collection folder:

       echo "# <your image collection title>" >> README.md
       git status
       git add README.md
       git status
       git add <your image collection folder name>
       git status
       git commit -m "<message for your first commit>"
       git status
       git branch -M main
       git remote add origin <the SSH URL of your repository>
       git push -u origin main
       git status

    * We have added `git status` here and there so that you can see how _git_ updates your repository as you invoke certain commands
    * Some commands need customization, as indicated by the `<>` placeholders
    * Speaking of which, that last `<>` substitution matters! —it _must_ be the SSH URL of your repository, and not HTTPS. This will indicate that you have successfully set up SSH key authentication
9. Once the `push` completes, go to the GitHub website for your repository, and show your viewers that your curated image collection is now on the Internet under version control!
    * Due to the file sizes of your images, make sure to perform the `push` in an environment with a solid Internet connection
    * You can stop recording and invoke `git push` in a new clip if you need to relocate—the fresh new repository will wait for you just fine 😊 Observe how `git push` is the only command that requires being online

### Scene Two: Up[grade] to [Mark]down
Before hopping into this scene, during preproduction identify three (3) subfolders for which you can add more commentary to their _README.txt_ files. Scene Two involves converting them to Markdown, adding some content, committing these changes to the repository, and pushing them to GitHub

Remember to use both command-line editors in some way throughout this scene

For each selected subfolder, do the following:
1. `cd` to that folder
2. Tell _git_ that you want to rename the file:

        git mv README.txt README.md

3. Invoke `git status` to show how _git_ handled that command
4. Use a command-line editor to revise the now-renamed _README.md_ with additional information about that chosen category
5. Show your Markdown proficiency by including at least the following in _one_ of the _README.md_ files: pick the category where you feel you have the most to say
    * One or more headings (`#`, `##`, `###`, etc.)
    * Bold (`**`) and italic (`_`) text
    * Website links (`[]()` notation)
    * A list (`*` or `1.`)

   Need more examples in addition to the [official documentation](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)? Just switch to <kbd>Code</kbd> while reading this file 😁
    * For the other two files, it suffices to have a heading and brief body text
7. After you finish editing, make sure you are `cd`ed to the location of the just-edited file then do:

        git status # See how git handled the edit that you just made.
        git add README.md
        git status # Make sure README.md is back under “Changes to be committed.”
        git commit -m "<message for your README.md revision>"
        git status

After all three (3) _README.md_ files have been committed, send them to GitHub’s servers:
```
git status
git push
git status
```

Finally, visit the GitHub repository’s website and show your viewers the results of your edit, as rendered by GitHub with Markdown’s clean, crisp formatting 🤌🏽

## Operational Notes
* Note that, perhaps more than previous episodes, the requested on-camera activities can be done over multiple sittings. If it makes things easier, record things over multiple sessions, using a simple video editor to string all of the clips together
* As long as you maintain a backup copy of your curated image collection, it should be pretty safe to delete things and start over. Deleting your repository on GitHub has already mentioned; similarly, you can delete any local repository-in-progress if needed. Just make sure that you always have that pristine backup handy 💡
* Remember that once more, the activities here are meant to be vehicles for practicing the knowledge and skills used during software development. Thus, don’t worry too much about the content of your _README.md_ files: as long as they are within reason and demonstrate the requested proficiencies, all will be well
* Remember also that _only one_ of the _README.md_ files needs to have enough content to show the requested formatting. The other two can be much simpler and shorter with just a heading and brief body text (which can itself be the same text that you wrote previously)

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

In addition, don’t delete the final version of your `episode-0309` GitHub repository. We will be reviewing that as well

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 30 points total |
| • Live creation and initialization of your `episode-0309` GitHub repository | 10 points |
| • Live conversion of _README.txt_ files to _README.md_ | 10 points |
| • Live content expansion of one _README.md_ file to include full range of Markdown formats | 10 points |
| Proficiencies to demonstrate | 70 points total |
| • Initializing and populating a _git_ repository from scratch | 15 points |
| • Checking the status of a _git_ repository  | 10 points |
| • Renaming, editing, committing, and pushing files from the command line | 20 points |
| • Formatting original content with requested Markdown styles | 15 points |
| • Using commands and techniques from prior episodes (`cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 10 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
