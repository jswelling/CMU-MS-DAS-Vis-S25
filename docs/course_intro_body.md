# Welcome to 38612 #
## Information Visualization for Data Scientists ##



## Instructor: ##
Joel Welling
welling@psc.edu

Office hours are by appointment for now, by Zoom or in person (here in 300 SC room 394).


### Some important things about me ###

* I have reduced red-green color vision, like a lot of males.
* My hearing isn't great either, so if I say "What? What?" a lot, that's why.
I apologize in advance.



## Equipment ##
Do you have a laptop or equivalent?
* Linux?
* Windows?
* Mac?

Can you write code on it?

It is entirely appropriate to use your laptop for any assignment for this class.
Most of the assignments I give can also be done using your Bridges2 account, but
there will be exceptions.


(I'll re-activate your Bridges account if necessary).



## Reality Checks ##
I'm assuming that:
* Everyone can write and run Python 3
* Everyone can fire up a Jupyter Notebook, and modify it if
necessary.
* Everyone can run a Python program *outside* a Jupiter
Notebook, like on a command line.
* Everyone can edit files.

If you are not comfortable doing any of these things, contact me after
class and we will fix it.


## Another Reality Check ##
* Can you download data from Github?
* Can you clone a Github repository and run the code in it?
* Can  you build a Conda or Pip environment from a requirements.txt file?
* Have you ever reviewed and merged a PR?

We will be doing a day on GitHub-based collaboration, because it's standard
in the industry.


## Other Experience ##

What kinds of data visualization have you done in the past?

What kinds have you seen elsewhere that you were impressed by?

Have you ever written a Flask application, or other server-side web code?  Do you
know Javascript?

How much statistics do you know?  Linear regression? Logistic regression? LOESS?



## Data, Idioms, and Manifolds ##

Visualization techniques mostly consist of collections of *idioms* for
mapping data to visual representations.

Any given visualization is built by combining idioms.

Idioms are only applicable to data of particular types.  For example,
a spreadsheet and a fluid dynamics simulation require very different
idioms.  Data exists on *manifolds*, and each idiom is only suitable
for one or a few different manifolds.



## Getting The Data Into The User's Brain ##

Obviously, the best choice of visualization depends on the viewer.
Consider color-blind viewers, for example.

Experience also matters.  Almost everyone can read a bar chart, but
highly skilled users can become proficient with some very complex
idioms.


<span class=tinytext>Brain connectivity, from LaPlante et al. 2014, "The ConnectomeVisualization 
Utility: Software for Visualization of Human Brain Networks"</span>
<span class='image60'>
![Part of Fig. 5 of doi:10.1371/journal.pone.0113838.g005](images/10.1371_journal.pone.0113838_fig_5.png)
</span>



## Course Plan In A Nutshell ##

We will:
* Talk about the various manifolds on which data can exist
* Look at idioms for each manifold
* ...and tools that can be used to create them
* Do some programming exercises with those tools
* Work with some large interactive visualization tools

This is not intended to be an ordered list.


## "Large interactive software tools"

We'll spend a few days on <a href="https://www.tableau.com/products/tableau">Tableau</a>...

...and try out <a href="https://visit-dav.github.io/visit-website/index.html">VisIt</a>, a tool for very large scale
scientific visualization.



## Mechanics ##

We have a <a href="https://canvas.cmu.edu/courses/44862/pages/course-intro-and-mechanics?module_item_id=6003745" target="_blank">Canvas page</a> for:
* scheduling
* assignments
* homework hand-in, unless otherwise specified

...and a <a href="https://github.com/jswelling/CMU-MS-DAS-Vis-S25" target="_blank">Github page</a> for:
* the lectures (including this one), via <a href="https://jswelling.github.io/CMU-MS-DAS-Vis-S25/" target="_blank">"github pages"</a>
* source code and data
* maybe group projects


## If you know how, clone that GitHub repo now!



## Homework Policy ##

Let's take a moment to look at the [syllabus](https://canvas.cmu.edu/courses/44862/assignments/syllabus) sections on Evaluation and Late Homework.



## Grading ##

There will be roughly one homework assignment per week, typically due the following week.
These assignments are meant to be submitted through Canvas.  They will all have comparable
weight; there is no special "final project".


In addition, each student is expected to do a very brief in-class presentation about some interesting visualization they saw in the
outside world, with a brief description of why they thought it was well done or poorly done.  The goal here is to learn to observe
and evaluate real-world visualizations.


Scoring for this presentation is boolean- you either do it or you
don't.  It will be worth the same number of points as a homework
assignment.  If for any reason you feel you cannot do this assignment,
please contact me and we will find an appropriate alternative.



## ChatGPT And All That ##

Yes, you could ask some LLM to write your homework code. Please just ask me for
help instead.  I actually enjoy helping students, and you'll learn more.
