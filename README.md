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
At the top of each included `tex` file I've written `\chapter{Chapter Name}`. This will add it to the 
table of contents and number any theorems appropriately (i.e. the first theorem in Chapter 2 will be
labeled **Theorem 2.1**).

To divide content we can use `\section{Section Name}` and `\subsection{Subsection Name}`. This will add
to the table of contents and make things look cleaner. Also it takes up vertical space ;)

### Theorems and Proofs
In the headings file I've included some basic formatting stuff such as 

    Theorem environment:     `\begin{thm} *Theorem stuff* \end{thm}`
    Proof environment:       `\begin{prf} *Proofy stuff* \end{prf}`
    Definition environment:  `\begin{dfn} *Definition stuff* \end{dfn}`
    Blackboard Stuff:        `\R, \Q, \Z, \C, \D, \H, etc

### The Index
I've also included an index. I've shown a basic usage example in `introduction.tex`. It's pretty simple;
if we want to add a term to the index we write after the usage of the term `\index{term-name}`. If more
than one instance of `\index{term-name}` comes up then multiple page numbers will be added if needed.

## Compiling
I'm not sure how to add this project to an environment but it should be pretty straight forward. On 
Linux/Unix environments compiling the tex file is simple.

1. `makeindex Fractals370`
    * This will create an index file for `pdflatex` to incorporate
2. `pdflatex Fractals370.tex`
    * This makes the pdf file.

I have to run these in succession a few times to make the pdf file get an up-to-date table of contents
and index.
