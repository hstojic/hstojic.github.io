---
title:  "Practicalities of reproducible research and computing"
date:   2017-10-23 07:25:29 +0000
categories: Research 
description: "In my research I rely a lot on computing. I have spent quite a bit of time thinking about reproducibility and setting up my workflow to achieve it. I benefited a lot from reading about how other people go about their research and what tools are they using. Here I tried to give back to the community by describing the practices and tools I have picked up along the way."
tags: [Research, Reproducibility, Coding, Linux, Version control]
---

This year's students from my ["Introduction to Computing"](https://github.com/hstojic/BGSE_IntroToComputing) course from [Master of Data Science program at BGSE](http://www.barcelonagse.eu/study/masters-programs/data-science) wanted to know a bit more about my setup for coding, what text editor I use, packages, etc. Initially I meant this to be a description of how to set up the Sublime Text editor for coding, so that I have a resource I can point the students to for all the details. However, whole discussion was actually about adopting practices that would make coding more efficient, so it made sense to write a bit more broadly and mention other things I picked up along the way that facilitated my life in front of the keyboard. 

Taking another step back, my specific goals biased the choice of practices and tools. I'm not a professional programmer, I'm a researcher that relies a lot on computing. My aim was not necessarily to adopt the latest industry standards, but to satisfy my scientific computing needs and ensure that my research results are reproducible. In my opinion reproducibility is a foundation of good research, hence I have focused a lot on discussing practices that facilitate achieving this goal.  


## Develop with Linux

Why Linux? Most important advantage in my opinion is that Linux relies less on graphical user interfaces and induces solving problems programatically, with commands that can be easily placed in a script. In other words, it induces adopting solutions that are **reproducible**. In contrast, Windows excels at point-and-click interfaces, since it is geared for normal users that do not have coding-specific needs and reproducibility goals. It's not like Windows cannot be used for coding and computing, of course it can, but it does make the job a bit harder, making the computing tools less accessible.

Then there are **servers** and clusters that I often rely on for any serious computing task. Servers as a rule run on Linux and my life is much easier if I connect and work with servers from a Linux machine. There is also an added **security** benefit, at least for the time being, while the community is still too small to be an interesting target for cyber-gangs. Last but not the least, I am happy to be part of the **open source** movement!  

Tip: I find it useful to keep track of the programs I'm installing on the machine in a shell script. That way I can easily recreate my operating system, whether on the same computer, or mirroring my setup on another computer (e.g. to keep things equal between my personal and work computer).    


## Choose a text editor and learn it well

When I was taking my first steps in programming I was relying on language specific integrated development environments (i.e. IDE's). Matlab, the first serious language I started using (I don't count STATA, beloved tool of economists), comes with a great IDE. It was a great experience using it, but the issue has arisen when I started learning R and Python. I used a different IDE for each one of these, [Rstudio](https://www.rstudio.com/) for R and [Spyder](https://github.com/spyder-ide/spyder) for Python, each coming with a different set of shortcuts and their own idiosyncratic interfaces. It's easy to see that this was not an efficient setup.

Somewhere along the way I have read about a solution for this inefficiency - find a powerful text editor and use it for everything! One of the best advices I have attended to. This way I ended up learning one editor well, avoided mental load associated with switching between editors and gained in productivity immensely. 

There are quite a few good text editors that are versatile enough to be able to use them for any task. Fans swear by [Vi](https://vim.sourceforge.io/download.php) and [Emacs](https://www.gnu.org/software/emacs/), and it's fun to read fiery discussions about which one is better on Reddit and elsewhere. I find them a bit arcane and somewhat unfriendly, but it's worth checking them out. I opted for [Sublime text 3](http://www.sublimetext.com/). I use it for every text-based task, for programming in languages like R, Python, C, or JavaScript, and for writing scientific articles, i.e. pretty much everything I do on a computer except for browsing the Internet. Note that it is not a free software. You can use the full version but every once in a while a pop-up window will appear asking you to buy a licence ($80). You can safely ignore it though. After some time, out of gratitude for improving my work life considerably, I did buy the licence.

![Sublime text 3 editor interface](/posts_files/2017-10-23-reproducible-research/sublimeText.png)


### Setting up the Sublime Text 

In its basic form, Sublime text is a good, cool looking text editor. It has quite a few features I cannot work without any more. For example, in auto-completion of words or whenever doing some search (in its menus, within text etc), it uses **fuzzy search**, i.e. you don't have to type the exact phrase to find a piece of code or text. Another feature I like is **multiple selection**, you select a piece of text, press `CTTRL+D` and Sublime will select the nest instance of that text. 

Arguably the best aspect of Sublime is that it comes with a sizeable ecology of packages. These packages make my life much easier. To access all these packages, what you will need to do first is to install the [package manager](https://packagecontrol.io/installation). Once that is done, press `CTRL+SHFT+P` and start typing `install packages`, a corresponding option will appear and press `ENTER`. This will open a list of all packages that you can install. Here is the list of packages I use on pretty much every day basis.  

- [SublimeREPL](https://github.com/wuub/SublimeREPL) allows you to open a console - whatever is available on your system: Python, R, C, shell, and so on - in another window inside the editor and send arbitrary amount of code from a script from another window for an execution (e.g. `CTRL+,+S` will send selected piece of code). When coding I like to interact with the output and this feature for me is extremely valuable. SublimeREPL might not catch paths to executable files for some consoles, so you might need to specify the paths in SublimeREPL settings. It's worth noting that you can open python virtual environments as well. There are some other alternatives that I don't have much experience with, like [TerminalView](https://github.com/Wramberg/TerminalView).     
- [R-Box](https://github.com/randy3k/R-Box) provides additional support for coding in R. This includes pop-up hints for commands, more advanced syntax highlighting, support for other formats of coding in R, like Rmarkdown, Rsweawe, Rcpp etc.  
- [SendCode](https://github.com/randy3k/SendCode) allows you to send code for execution to external applications, like terminal, screen, tmux etc.   
- [GitGutter](https://github.com/jisaacks/GitGutter) is a subtle indicator of which line has changed with respect to the previous version of the file. It will automatically pick up the version control files if you keep the project under Git version control. There are various other packages that facilitate using Git, like `Sublimerge` but I haven't used them much.  
- [Latexing](http://www.latexing.com/) - provides additional support for writing in LaTeX, from better syntax highlighting to pulling up citation keys from my BibTex file.  
- [WordCount](https://github.com/titoBouzout/WordCount) provides a simple counter of number of words in a document; strangely, it doesn't come by default in the Sublime text.  
- [SublimeWritingStyle](https://github.com/thedataking/SublimeWritingStyle) is a neat package that indicates poor writing style, following some sensible rules for good writing, such as "avoid using passive voice". You can add additional words you want it to mark for you and I find this quite useful. [Deirdre McCloskey's book](https://www.amazon.com/Economical-Writing-Deirdre-McCloskey/dp/1577660633/ref=la_B001ITVIAI_1_1?s=books&ie=UTF8&qid=1508745325&sr=1-1) on writing mentions words indicative of poor style and I use this option to highlight them in the text.  
- [Markdown Extended](https://github.com/jonschlinkert/sublime-markdown-extended) provides additional support for writing in [markdown](https://daringfireball.net/projects/markdown/).  
- [SideBarEnhancements](https://github.com/titoBouzout/SideBarEnhancements) gives more options when side bar is opened with project files view.    
- [AllAutocomplete](https://github.com/alienhard/SublimeAllAutocomplete) provides autocomplete options based on all files in the project, not only the current file. Comes with a unique licence :)   
- [ColorPicker](https://weslly.github.io/ColorPicker/) provides a neat pop-up colour map to get an RGN or HEX code for any colour.  
- [Terminal](https://github.com/wbond/sublime_terminal) launches a terminal in the folder containing the currently edited file, I use it often.     


## Enter version control 

Have you ever had situation like this?

![](/posts_files/2017-10-23-reproducible-research/final.gif)

Version control to the rescue! There are several version control softwares, but I have tried only `git`, which has served me well so far. Linus Torvalds has initially developed Git for collaborative effort of developing the Linux kernel - it allows multiple users to work simultaneously on the code of the same software project. It is also the software underlying the [GitHub](http://www.github.com), a popular public software repository.

Most of the time I am using git locally and I am a single person developing the code for my research projects. Even though this usage mode exploits only a fraction of git's capacity, there are many benefits that made it worthwhile paying the cost of adopting it into my everyday work. 

1. **No more clutter.** I got rid of situations from the comic, now I have a single file and with each version there is also a message that describes the change, making it much easier to find a version I want to go back to.  
2. **Break the code.** Once I have a working version of the code, I can easily create a new "branch" (essentially a copy of the whole project) where I am tinkering with a new feature or optimizing certain parts (in multiple files potentially). This compartmentalisation means I can safely experiment, knowing that the working version is safe and I can easily revert to it. I use the same git feature to create a cleaned-up version of the project files that I make available publicly (e.g. analysis code and data I have used in the papers), and I can still get my development version with all the files with a single command.  
3. **Publishing code on GitHub.** When I want it, I can still associate the local git repository with a GitHub repository and share the code publicly. For example, I have shared teaching materials with students for the courses I have recently taught ([Introduction to Computing](https://github.com/hstojic/BGSE_IntroToComputing) and [Bayesian Optimization](https://github.com/hstojic/BGSE_BayesOptim)).

As with any tool there is some cost to pay. Git takes a bit of time to learn and getting used to it. Git works well with plain text files - files with code are fine, but MS Office type of documents are not. Many researchers are still heavily relying on MS Word, so this might be a no go for them.

I won't go into any details on how to use Git, there are enough tutorials on the Internet - for example, check the official website ([git-scm.com](https://git-scm.com/)), it has good explanations and useful examples. I'll give two tips though. 

1. I use Git from a terminal and `.gitconfig` file makes such usage much easier. There are plenty of GUI's, but I have never really tried any of them. They might be useful for people that are not on friendly terms with terminal or for bigger collaborative effort with dozens of branches, which was not the case for me. In Git config file you can, for example, set aliases for commands you use often, e.g. `git cm` instead of `git commit -m`. Time spent typing git commands will decrease a lot. You can check my config files [here](https://github.com/hstojic/config).  
2. [Meld](http://meldmerge.org/) is a small tool related to version control that I use often. It provides a simple interface for examining the differences between text files, including different versions of the same file that are under version control. It comes handy when there are a lot of changes, for example, I use it a lot for writing papers - when I get a new version of the manuscript from a collaborator, I use it to examine the changes and merge them into a master manuscript.


## GNU Make to automatise everything

Command line is great because I can combine a series of tools to create a single analysis pipeline script (e.g. Bash script). For example, I can download the data from some URL with `wget`, call Python to do some data cleaning or text processing, then call R that will generate some good-looking figures and finally compile the manuscript written in LaTeX. This greatly improves reproducibility as all the steps in the project automated scripted and ideally I can reproduce whole pipeline by executing a single script. Having notes on what you do in each step is fine (e.g. a Readme file), but documentation is sometimes not updated, while a script should be correct.

Instead of a bash script, what is usually used for these purposes is a command line tool called [GNU Make](). It is essentially a Bash script with slightly different syntax, where some additional checks are performed to make the computation more efficient. I can specify dependencies between the files and script will re-run the code that has been changed, not everything, as would be the case in a simple Bash script.

Below is a simplified example of a `makefile` file that I have in every project directory where my manuscript sits. For example, if I would change the code for the figure, next time I execute the makefile (simple `make` in the command line in this directory would do the trick), make would realize the figure script has changed and would first update the dependency. I would have a similar `makefile` on the top level that connects all the steps of the analysis pipeline.

```bash
# this command specifies how to compile a pdf of the manuscript, given 
# the dependencies 
manuscript.pdf: references.bib manuscript.tex ../rFigs/fig_blah.pdf 
	pdflatex manuscript
	bibtex manuscript
	pdflatex manuscript
	pdflatex manuscript

# this command specifies how to generate the required figure that is
# expected to be in rFigs directory while the code that generates it
# is in the cFigs directory
../rFigs/fig_blah.pdf: ../cFigs/fig_blah.R
	cd ../cFigs && R CMD BATCH fig_blah.R fig_blah.Rout
```


## Use the same project file organization throughout

At some point I ran into an excellent course by Karl Broman on ["Tools for reproducible research"](http://kbroman.org/Tools4RR/). He had a really good advice on organizing files on a hard disk - choose a scheme for organizing all files related to a project and apply it consistently for every project. His argument was that you should reduce the time spent on searching for files. 
Having adopted such standardized approach to project management I have to say that indeed those savings accumulate.

![Project files](/posts_files/2017-10-23-reproducible-research/files.png)

This is how I organize my project files. All materials relevant for a project is in a single directory/folder on my harddrive in `projects/` directory. 

- First, project is under version control with Git. I usually keep everything under version control except the data (kept in data repositories, like [OSF](https://osf.io) or [figshare](https://figshare.com)) and outputs that can be reproduced by executing some code (e.g. figures or simulations).  
- Directories with `d` prefix contain data. I keep raw data separate from processed data, I never edit the data manually, instead I keep a record of all manipulations in a script and place processed/cleaned data in a different directory.   
- As you might have guessed, I keep all the code in directories with `c` prefix. I find it useful to separate code I use for simpler analysis (`cAnalysis` directory), computational modelling (`cModeling` directory), running behavioural experiments (`cExp` directory) etc.  
- I keep results, output from analysis scripts in separate directories with prefix `r`. For example, code in `cFigs` produces figures I would use in an article and I place these in `rFigs` directory.  
- Directories with `p` prefix contain project output. For example, `pManuscript` contains an article (LaTeX) that I would submit to a journal once finished, while `pTalk` contains slides for a talk on this topic. `pNotes` is a bit different, here I keep all the notes related to the project - `meetings.md` with summaries from the meetings, `literature.md` with notes on the most relevant articles etc.  
- There is a `LICENSE` file as well, stipulating how the code and outputs can be used. I plan for making project files publicly available (e.g. on [OSF](https://osf.io)) when the project is done. Licence is essential as without it no one knows how the project files can legally be used.  
- Finally, I have a `README.md` file that briefly introduces the project and explains what is where and what is it doing, and a `makefile` that connects all the steps of the analysis. Each directory has its own `README.md` and `makefile` if needed. For example, my top `makefile` will typically first download the raw data from an online repository, place it in `dRaw` then call the makefiles in each directory in an appropriate order and finish with compiling the manuscript. The goal is to be able to reproduce all the analysis with a single command.   

I don't keep all of my projects in the parent `projects/` directory. To reduce the clutter I place retired projects (compressed) into an `projects/archive` directory and half-baked ideas into `projects/play` directory. 

Organisation is somewhat different than Broman's, but what matters is having *some* system that is applied consistently. Version control helps a lot. For example, I usually need slightly different figures for talks or posters and then I can easily create new branches of the repository where `cFigs` code is appropriately adapted, and same goes for creating different journal submissions, public version of project files etc.

How we do science is changing and increasing number of reviewers and journals are requiring authors to publish all the files relevant for the project - analysis code, code for generating the figures, raw data etc. This is a good thing. Article published in a journal is not the only research output. Other people can reuse the code and data for different purposes, extending the impact and making science as a whole more efficient. I know that I would had been grateful for having access to such material, my learning curve during the PhD would have been much different with it. With a standardised project organisation and planning to open the files from the outset it will be far easier to make it happen.


## Use meaningful file and directory names

Smart usage of directory and file names can reduce search time further for yourself, and especially your collaborators or users.  

- I try to use meaningful names and avoid abbreviating too much. From the directory/file name I should approximately know what the content is.    
- When using dates in file names and text, I use the following format: **year-month-day**, e.g. 2017-10-03. Using a clear separator like hyphens makes it easier to search for with `grep`-like tools, and the order facilitates sorting.   
- I tend to repeat the file names across projects if the file is doing the same thing, e.g. in every `pManuscript` folder I always have `manuscript.tex` and `references.bib` file. That way I can reuse makefiles and some code snippets.  


## To do list

- Container technology seems like a promising way to enhance reproducibility, by making operating system and software dependencies clearer and easier to execute. For example, with [Docker](https://www.docker.com/) another researcher needs only docker installation (available for all platforms) and can easily launch a Docker image where whole analysis pipeline is implemented. I haven't incorporated it yet in my workflow, but it's on the top of my todo list and I'll try to implement it in one of my next projects.   
- I write articles in LaTeX. LaTeX is a plain text so it plays well with the version control system, but I have to admit it's syntax heavy. I'm fine with that, but collaborators might not be. So far I've been lucky(?) and they've been happy with that format. Collaborative writing was greatly facilitated by [Overleaf](https://www.overleaf.com/) platform. The problem is that there is still a bit of copy-pasting going around, and that is not good for reproducibility. Ideally, I should integrate the text with the code producing figures and statistical results. I have been looking at [Rmarkdown](http://rmarkdown.rstudio.com/) for a while now for solving this issue. If I worked alone I probably would have tried it already with articles, but for collaborative writing there is no platform that would execute R code. This one will be a tough one to resolve.  
