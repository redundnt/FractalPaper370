# README 
## Fractal Paper for Math 370

Hey Guys, I'm setting up this repo so that we can easily work on the final paper and 
merge the results. The basic layout is as follows.

## Outline

```sh
Fractals370.tex     # This is just a wrapper. It includes some files, such as a headings file
                    # and each chapter

headings.tex        # This contains all the packages, etc. This should have everything we need
                    # but if not let me know

tex/                # This is the directory where you will be working. Don't mess w/ anything else.
                    # If you do need to change something in headings.tex, let me know and I'll update
                    # the file. This is to keep us from trying to merge multiple changes to the file
                    # simultaneously
                    
    introduction.tex    # An introductory chapter explaining what fractals are -- basically a stronger 
                        # abstract
    nature.tex          # This will include the fractals in nature portion of the paper
    sierpinski.tex      # This is the Sierpinski's Triangle portion of the paper. This can be split 
                        # into two files if it's easier to work that way. Just create files 
                        #   - sierpinski1.tex
                        #   - sierpinski2.tex
                        # and write \include{sierpinski1.tex} and \include{sierpinski2.tex} in the body
                        # of sierpinski.tex
    measuretheory.tex   # Measure theory and fractional dimension (maybe some talk of dimensionality in
                        # the Sierpinksi chapter. Scott will elaborate on this
    complexdynamics.tex # Working with Julia, Mandelbrot sets and Newton Fractals.
    appendix.tex        # Maybe if anyone has anything extra to add that doesn't fit in the flow

img/                # Directory for image files. Maybe prepend section name to images to avoid naming
                    # conficts. For example, I would add an image like 'cd_julia01.jpg' since I'm
                    # working on complex dynamics
```

## Adding to files

### Dividing Content

At the top of each included `tex` file I've written `\chapter{Chapter Name}`. This will add it to the  table of contents and number any theorems appropriately (i.e. the first theorem in Chapter 2 will be labeled **Theorem 2.1**).

To divide content we can use `\section{Section Name}` and `\subsection{Subsection Name}`. This will add to the table of contents and make things look cleaner. Also it takes up vertical space ;)

### Theorems and Proofs
In the headings file I've included some basic formatting stuff such as 

    Theorem environment:     \begin{thm} *Theorem stuff* \end{thm}
    Proof environment:       \begin{prf} *Proofy stuff* \end{prf}
    Definition environment:  \begin{dfn} *Definition stuff* \end{dfn}
    Blackboard Stuff:        \R, \Q, \Z, \C, \D, \H, etc

### The Index
I've also included an index. I've shown a basic usage example in `introduction.tex`. It's pretty simple; if we want to add a term to the index we write after the usage of the term `\index{term-name}`. If more than one instance of `\index{term-name}` comes up then multiple page numbers will be added if needed.

## Compiling
I'm not sure how to add this project to an environment but it should be pretty straight forward. On Linux/Unix environments compiling the tex file is simple.

1. `makeindex Fractals370`
    * This will create an index file for `pdflatex` to incorporate
2. `pdflatex Fractals370.tex`
    * This makes the pdf file.

I have to run these in succession a few times to make the pdf file get an up-to-date table of contents and index.

## Working with git
### Setup
Figure out where you want the project to live. If I'm keeping it on desktop I navigate to my Desktop directory:
```sh
cd ~/Desktop
```
and then issue the command:
```sh
git clone https://github.com/redundnt/FractalPaper370.git
```
This puts the entire latex project (described above) in your Desktop directory. I can now edit it to my hearts content,
save changes, compile, etc without changing anything anyone else is working on.
### Stay Up To Date
I recommend regularly issuing the command
```sh
git pull origin master
```
This pulls down any changes made by people in our group onto your computer. To make sure that we avoid conflicts I STRONGLY RECOMMEND that nobody work on files that aren't theirs to work on. I will stick to the introduction.tex and complexdynamics.tex files, for example.

### Adding and Commiting
After I've done some editing and I want to wrap up I have to add the changes I've done to git. This is easy. From the 
home folder of the project I enter:
```sh
git add .
```
followed by
```sh
git commit -m "A message detailing what was done. Typically short like `Added some definitions`"
```
My local git repository is now ready to be pushed to github!

### Pushing to Repository
If you make any changes nobody will be able to see them until you put them back on github (and is downloaded by others).
To do this, issue the command
```sh 
git push origin master
```
Github will then ask for your credentials. When I update my `bfg` repository it looks like this
```git
ben@bbeonx:~/Code/Sandbox/gitcollab/bfg$ git push origin master
Username for 'https://github.com': bkushigian
Password for 'https://bkushigian@github.com': 
```
Notice that the password doesn't appear (this is for security reasons, so don't freak out if you can't see the letters you're typing. If you screw up, just hold backspace down for a second or two to clear what you've entered).

### Normal Git Workflow
So when I start working on a project I will first `pull` to see if anything new is on the repository. I'll then work for a while and once I've finished for the day I will again `git add .` and `git commit -m "some message"`. Finally, once this is done, I issue the `git pull origin master` to see if anything has been added by others (if anyone has added something github won't let me push until I've pulled). Finally, once I'm up to date with everything on the repo I issue the 
`git push origin master` and enter my credentials.
So to clarify

1. `git pull origin master`         # Get up to date with repo
2. Edit some files. Save changes.
3. `git add .`                      # Add my new work to the repository
4. `git commit -m "message!"`       # Commit my messages to git (this includes all added changes)
5. `git pull origin master`         # Double check to see if anyone has added something new
6. `git push origin master`         # Push your changes to the repo!
7. `git drunk`                      # You're done! Go party
