**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0204: Curator Personalis
You may have noticed that the previous episode consisted solely of _reading_ or _viewing_ existing files and folders—we weren’t making any changes. We make that leap with this episode! We’ll continue to practice using `cd`, `ls`, and `more`/`less` along with the range of shortcuts and techniques for speeding up command entry. But now we’ll also add new operations that _change_ files and folders…so make sure to take the mindfulness and care up a notch 👀

Still, to add a certain layer of safety, we will perform our operations on a totally new set of files and folders where errors won’t have critical stakes. Read on to see…

## Preproduction

1. Pick a general “theme” or subject area that you find personally interesting, and download multiple images which fit that theme to the standard downloads folder on your computer. You will _curate_ these images into an organized collection by way of files and folders 🧐
    * To ensure that you have enough variety to work with, download at least 10 such images (plan to have some that you will eventually delete; see below)
    * Because you’ll be moving files around, make a backup copy (no need to use the command line here) and set it aside so that you can restore/re-copy your files after practicing
2. Practice the “On Camera” script as needed, deleting your practice files and restoring them from your backup copy with each repetition so that you can start fresh

## On Camera

### Scene One: Veni
1. Start your episode by talking briefly about your chosen theme and why you picked it
2. Also start the episode with the images in your downloads folder, as if you had just downloaded them
3. Show your downloads folder in its initial state on the command line (`cd`, `ls` with wildcard), with all 10 images in there as a flat list

### Scene Two: Vidi
1. Using _only_ the command line, create a top-level “collection” folder with at least two (2) levels of categories underneath (i.e., _Collection_ > _Category_ > _Subcategory_). Name the collection and category folders as you please
    * Use `mkdir` to create the folders; use `mkdir -p` to create multiple levels at once!
    * You may put the top-level collection folder anywhere you want, and can name it anything you want. You’re the curator!
    * With the minimum two levels, you will have paths of up to _collection/category/subcategory_
    * Feel free to think aloud/on your feet so that you rename/delete/recreate folders as needed (`rm`, `rmdir`, `mv`, `mkdir`)
2. Each folder should have a _README.txt_ describing each category
    * Use the `cat >` command for this (remember that <kbd>control</kbd>-<kbd>d</kbd> on a new blank line terminates your input)
    * Yes you can’t edit them on the command line (yet). That’s on purpose! If you make a mistake, just `cat >` again—that’s perfectly OK and part of the practice, so you realize that this command _replaces_ existing files completely
    * Because you can’t edit (yet), keep the descriptions short. The focus is on the commands, and not the content. But don’t go `asdfasdf` either
    * Remember you can use `more`/`less` to review a file’s content after creating it with `cat >`—do this onscreen as well to reinforce that skill from the prior episode
3. Use the `mv` command to place your downloaded images in the corresponding categories/subcategories
    * Have at least 1–2 images that are either completely general or don’t have a second-level subcategory (i.e., they don’t have a category/subcategory and rightly belong right at the top of collection or within the first-level category). In other words, the subcategory folders shouldn’t be the only ones that contain image files
    * Remember that `mv` is synonymous with renaming! Rename at least a few downloaded image files as you `mv` them (since they may have non-user-friendly or overly long names) to something that fits your organizational scheme better or is simply more readable
    * Make sure to retain file extensions like _.jpg_, _.png_, _.gif_, etc. when renaming
    * Remember that tab autocomplete and `..` work with `mv` too!
4. Name at least one file and folder each with multiple words (or name all of them that way!). Don’t let the command line’s special treatment of spaces stop you, because commands _can_ handle file and folder names with spaces as long as you use `"`, `'`, or `\` correctly

### Scene Three: Vici
1. Use the `rm` command to change your mind about certain images and not include them in your curated collection after all (yes this might be a contrived condition, but it’s still a plausible scenario for curation)
    * Remember that `rm` on the command line is permanent—no Trash Can or Recycle Bin here! That’s why we’re practicing on these images only, so that the consequences of a mistake aren’t dire
    * Still, take extra care with `rm`—allow yourself a moment of mindfulness before pressing that <kbd>Return</kbd>/<kbd>Enter</kbd> key
2. Perform all of the operations on the command line, but you can keep a desktop window open to check your work. Make sure that both windows are shared and recorded on the video; you can either share your entire desktop or share multiple windows—pick whatever works best for you
3. When you’re done, “show off” your fully-curated image collection by navigating through them on your desktop with the standard graphical user interface, showing how you were able to construct and organize these images fully via the command line 🤩

## Operational Notes
This video episode is a lot more open-ended than before, so we have some general notes to mention:
* You may perform the above operations with each scene in any order. What matters is that (a) you show that you do them all, and (b) your end result is an organized image collection the way that you want it
* No need to re-record when you make a mistake! Mistakes are simply more opportunities to practice—if you make a mistake, just type another command that rectifies the error:
  * Invoke `mv` again until the file is where you want it
  * If you mistakenly `rmdir`, then `mkdir` it again
  * If you mistakenly `rm` a file, then re-download it (and this part of course doesn’t need to be done on the command line)
  * If you type the wrong thing with `cat >`, just retype it
* Note that these commands can also be used while you’re practicing, in order to start over cleanly and/or reset things
* Reinforce the commands from the previous episode to move around freely within your collection and review your _README.txt_ files
* Use history and command-editing shortcuts freely and as needed

Importantly: _**Keep this folder**_ after you are done—you will use it in a future assignment!

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

## Specific Point Allocations
For this particular episode, graded categories are as follows:

| Category | Points |
| -------- | -----: |
| Expected content | 20 points total |
| • Brief description of your collection’s theme | 5 points |
| • Creation and organization of the collection | 10 points |
| • Walkthrough of the full final version on the graphical file interface | 5 points |
| Proficiencies to demonstrate | 80 points total |
| • Creating folders, including multiple levels at once (`mkdir`, `mkdir -p`) | 15 points |
| • Creating short text files (_README.txt_ via `cat >` + <kbd>control</kbd>-<kbd>d</kbd>) | 15 points |
| • Placing files in the right folders your category scheme, including files that don’t have a subcategory or category (`mv`) | 15 points |
| • Specifying folder and file names that have spaces in them via `"`, `'`, or `\` | 10 points |
| • Making adjustments as needed, whether to fix errors or due to changing your mind (`rmdir`, `rm`, `mv`, `mkdir`, `mkdir -p`, `cat >`) | 10 points |
| • Using commands and techniques from the prior episode (`cd`, `ls`, `more`/`less`, command history, command editing) | 15 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
