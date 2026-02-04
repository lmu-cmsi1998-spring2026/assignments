**CMSI 1998** Special Studies: Software Carpentry, Spring 2026*

*_The phrase “software carpentry” was coined by Greg Wilson and Brent Gorda in 1998:
https://software-carpentry.org/_

# Episode 0218: Edits, Envs, & Execution
We’ll delve into the next level of command-line proficiency by way of an activity that we enjoy from time to time, and sometimes may be a necessity: customization. By putting up an episode where we craft a simple “bespoke” command line for ourselves, we’ll give ourselves some exposure to the three “E”s in the title: editing, environment variables, and execution on the command line

## Preproduction
1. Think of two (2) hypothetical “commands” that you think you’ll find fun or useful on the command line. Maybe a simple joke teller? A tip calculator? Some combination of other commands that you seem to always run consecutively? One of these programs should be implementable on the shell; the other should be something you can do in Python (if you prefer another language, let me know and we’ll see if it can work)

    Keep in mind that modern shells can handle conditions and loops—you don’t have to get too fancy, but in case you want your shell script to be a tad more sophisticated, look at [this tutorial](https://www.geeksforgeeks.org/bash-scripting-if-statement/) as well as [this one](https://www.geeksforgeeks.org/looping-statements-shell-script/)

    While writing things up, you can use the `source` command to test your shell script and `python` itself to test your Python program (or another language of choice, if prearranged with and approved by the instructor)

    Don’t make these very long, because you’ll be typing them live on video!

3. Think about how you would like to personalize your command prompt. As you have seen, the prompt itself is easy to change: set the `PS1` environment variable (there are others of course but let’s stay with `PS1` for this assignment). It’s the options that can be mind-boggling…so you can use these websites to see what’s available:
   * https://zsh-prompt-generator.site (for _zsh_ users)
   * https://bash-prompt-generator.org (for _bash_ users)
  
   Come up with three (3) different ones, and take note of their final values. Make sure you understand what the parts mean, because you’ll _type them yourself_ in the video (devs have secret bags of tricks too!). The _bash_ prompt generator, in particular, has _lots_ of bells and whistles. If you generate something that does more than modify `PS1`, back off for now 😅

   The _zsh_ generator assigns to the `PROMPT` variable, but for consistency those work with `PS1` too. But its unique `RPROMPT`/`RPS1` variables are straightforward enough, so _zsh_ users can set that too if it helps to keep things interesting or fun

4. Make a backup of your shell configuration file (typically _~/.bashrc_ for _bash_ and _~/.zshrc_ for _zsh_) so that you can restore it in case things go wrong…and now practice by setting the `PATH` and `PS1` variables there in order to make your customizations stick. Restore the originals so that you can do this live on video later

Whenever you’re happy with these, you’re ready to roll…after the usual practice runs of course, which at this point we will take for granted as part of your preproduction routine 🧐

## On Camera
With the prep in your pocket, here’s the actual script to follow on camera. Scenes One and Two are pretty independent of each other, so you might want to consider recording them separately. Make sure you do Scene Three last because it will use what you do in the earlier scenes

_Note:_ We acknowledge that we may all have a favorite when it comes to a command-line editor, but to make sure we aren’t totally lost in the future if we encounter an environment that only has one editor or another, make sure you use your non-favorite editor in this video _at least once_

### Scene One: Bespoke Commands
1. Use the command-line editor of your choice (`vi`, `nano`, `pico`…probably not `ed` 😬) to write the two (2) short, simple scripts mentioned above. You can have the code offscreen somewhere if you aren’t comfortable rewriting them from scratch, but make sure that you show yourself typing things out on video! The point here, after all, is to show that you know your way around a command-line editor
2. Show that those programs work via `source` or `python` (or other appropriate language)
3. Use `which` onscreen to show the viewer where your shell and Python (or other language) are located
4. Re-edit the programs on the command line and add the correct _shbang_ (`#!`) prefix to each of them
    * Specific to _Git Bash_ users, you will want to perform this step _after_ the next one, in lieu of `chmod u+x`. This is due to a _Git Bash_-specific functionality where the executability of a script/program is determined by the presence of the _shbang_ line rather than manual execution of `chmod u+x`
5. Use `ls -l` or `ls -F` to show that your files are not yet marked as executable
6. Use the `chmod u+x` command to make them executable
7. Use `ls -l` or `ls -F` again to show that they are now executable
8. Actually run them by prefixing them with `./`
9. Use the `mv` command to remove any file extensions—they are very close to acting exactly like standard commands now!
10. Modify your `PATH` variable (don’t forget you can use `echo` and `$` to avoid typos) so that `PATH` now includes the location of your newly-created commands
11. Show that they are actual commands now, capable of executing from any folder (`cd` elsewhere to prove it!)
12. Remember that your `PATH` change is temporary when modifying it dynamically—in Scene Three, you’ll show that you can make it permanent

### Scene Two: Bespoke Prompt
1. Show that you can change `PS1` at will in order to customize your shell prompt
2. As you type each prompt value, make sure to _explain them_ as you go! (i.e., say what each placeholder will do; indicate which parts are just custom text). Of course we all know that the prompt generator website helped, but the viewer doesn’t need to know that 🤫
3. Show the viewer the value of your `LANG` or `LC_CTYPE` environment variable to indicate whether your prompt can include emoji
   * …and make sure to prove it by showing at least one prompt with such an emoji
   * if your system doesn’t allow direct typing of emoji, it’s OK to copy-paste it from a website or other source
4. Do this three (3) times, once for each prompt that you invented
5. Again these changes are temporary—until Scene Three

### Scene Three: Bespoke Be-Permanent
1. Record yourself on a fresh command line window, and show how the prompt is the current (boring!) default and your commands don’t work
2. Edit the appropriate configuration file for your shell on the command line (typically _~/.bashrc_ for _bash_ and _~/.zshrc_ for _zsh_)
3. Set your custom `PATH` and `PS1` variables (remember you can use `$` to reuse the existing `PATH`, if your file already has that)
   * You can only have one `PS1` so pick a favorite custom prompt as the one that will stick
4. Use the `source` command to “reload” the configuration file and show that your custom prompt and commands are now available
5. Open a new command line window and show that your custom prompt and commands are now available automatically

And that’s a wrap! You should now have a video episode showing that you know how to customize your command line 💪🏼

## Operational Notes
* As you can see, there’s a bit more prep here than before (especially the programming), but remember that these are just vehicles for you to exercise the _actual_ skills that we want, which are editing on the command line, facility with modifying environment variables, and getting a little bit more insight into what makes something “executable” on the command line. So don’t feel like your mini-scripts have to be amazing or super powerful; just keep them short and sweet
* Same goes for the prompt—that’s why you’re allowed to use those prompt generator websites after all. The key takeaway is that the command prompt is “just another variable” in the system, albeit a variable that has very high visibility
* Another reason to keep the lengths reasonable is because you’ll be typing them onscreen. The shorter your scripts and prompts, the shorter your video 😊 But don’t make them nonsense scripts and prompts either. Strike a balance between something you find genuinely interesting and keeping things at an appropriate length

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
| Expected content | 30 points total |
| • Live creation/editing then execution of two (2) scripts, one for the shell and another on a programming language | 10 points |
| • Live setting of three (3) custom prompts | 10 points |
| • Live editing of shell configuration file to make these “stick” | 10 points |
| Proficiencies to demonstrate | 70 points total |
| • Ability to edit files on the command line with **both** _vi_ and _nano_/_pico_ | 20 points |
| • Usage of `echo` and `$` to inspect the values of environment variables | 10 points |
| • Ability to modify `PATH` and `PS1` variables to customize one’s command line | 20 points |
| • Usage of shbang (`#!`), `ls -l` or `ls -F`, and `chmod u+x` to see and set the executability of a file | 10 points |
| • Using commands and techniques from prior episodes (`cd`, `ls`, `more`/`less`, tab autocomplete, command history/search, command editing, `mv`, etc.) | 10 points |
| Fun factor (counted only if content and proficiencies are complete) | extra credit |
| Sus footage | deduction only |
| Punctuality | deduction only |
| **Total** | **100** |

Regarding the fun factor extra credit, as noted in the syllabus, entertainment value makes informative videos better but it does not redeem uninformative ones. Make sure that your episode has the requested content and you show the desired proficiencies first before spending time on sprucing things up. Otherwise, extra credit will not be included

Graders reserve the right to impose additional overall deductions if anything that seriously detracts from effective fulfillment of the assignment’s objectives is noted, even if it does not match any specific category above
