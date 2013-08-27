---
layout: posts
title: "Learning to code on a low end graphical calculator"
categories: [coding]
---

This is how I first started to program, in 1997 to be exact. It was the year I entered high school. Every students was required to have a [TI80](http://en.wikipedia.org/wiki/TI80) or higher, an entry level programmable graphical calculator. This marvelous little machine cost 100 French Francs at the time, roughly $20 USD or 15 Euros.

<img src="/assets/TI80.jpg" alt="TI80" style="float: left; margin-right: 40px;" />

I started programming withit as soon as one of my friends showed me how he had created a rock-paper-scissors program on his TI80, and I could never program enough. I programmed before, during and after class - much to the irritation of my teachers (using a calculator in French class is somewhat conspicuous). Like many people who ended up being programmers, I had just found something I loved. My TI80 is dead now, I tore it apart to try and put it back together as soon as I upgraded, the next year.

Programming on the TI80 was, in retrospect, a peculiar experience. The language was TI-BASIC, which was a quirky language to say the least especially, in its TI80 form:
- the keyboard was calculator style, with the letters ordered alphabetically
- you didn't type the program text but inputted [lexemes](http://en.wikipedia.org/wiki/Lexical_analysis) directly. For example, to use a for loop, you didn't type the letter F, O and R, but you went in the "Program" menu, and chose the seventh item from the list. In your program code, the "FOR(" would be then be displayed and you could input your parameters.
- there was no way to comment your code
- variable names were all exactly one letter long and always in caps (in fact everything was always in caps); and variables could only hold a float value. Some of these variables could be overwritten by the system. X and Y notably got set to coordinates chosen on the screen, so you could never use these variables in any program with graphical capabilities. This meant that you could use at most 25 variables (the greek letter theta &theta; was also available) in a program, all with nondescript names. All these variables were system-wide global variables.
- variables only held floating point values, no strings, objects, arrays...
- you couldn't create macros or functions in a program. You could call a program from another program, but there was no direct way to pass data from one program to the other, you used the variables as they were all global
- the only data model available were arrays, called lists. There were only 6 lists available, with a max size of 99 items, and of course they could only store floats.
- there was no way to get data from the user during the program run apart from a prompt. This meant there was no way for the calculator to tell which key was being pressed, so any real time interaction was out of the question
- storing data in variables was done in the opposite way to the standard. Instead of typing: A = 1, you typed: 1->A
- goto were available, but you were limited to 36 goto destinations.

Of course, there were also strong limitations with the hardware.
there was only 7Kb of RAM on the calculator and no ROM, so you checked every byte to make sure your program would fit, and could run without hitting "ERR: MEMORY".

The screen was 2-colors, of course, and a very small screen (76 by 80 if I remember correctly).

There was no data input port. This meant you were limited to TI-BASIC and couldn't use any Assembly, like other TIs could. This also meant that if you wanted to use a program a friend had or that you found on the Internet, the only way to get it was to retype it entirely.

This led to a number of hacks to get the code running. I wouldn't put closing parenthesis at the end of my FOR loop definition because the interpreter would add it implicitely. That way I'd gain one byte of memory. 

Two dimensionnal matrixes were handled by putting the array\[n\]\[m\] data at the n\*\(array_size\)+m position in the one dimensionnal list. 

Often, I'd go at great length coming up with clever mathematical formulas that today I would do in a separate function, with a bunch of if/else. That would save me a few lines of code as well as making the program flow a little clearer. 

When I wanted the program flow to wait a few seconds, I'd make the calculator calculate the hardest operation it could without running out of memory: 69\!. If it tried to compute 70\!, it crashed.

At the time of course, I didn't realise that was weird in any way. It was just how you programmed.

Here is an example of a program I wrote. In this programe you would, play a game similar to Invaders, except turn based instead of real time. Enemies would appear randomly at the top, and go down every turn. The player would try to kill them off one by one at each of his turn. Enemies would be one step closer everytime. I advise you not to try to understand this code...

{% highlight ruby %}

:PLOTSOFF 
:FNOFF
:CLRLIST L1,L2,L3,L4
:1->XMIN
:63->XMAX
:0->XSCL
:1->YMIN
:47->YMAX
:0->YSCL
:CLRDRAW
:CLRHOME
:DISP "INVADERS
:PAUSE
:CLRHOME
:DISP "","","INITIALIZATION
:69!
:69!
:69!
:DISP "ENEMIES TO","DESTROY","SIZE?
:LBL F
:INPUT "(0<X<95)",W
:IF W>94
:GOTO F
:IF W<0
:GOTO F
:INPUT "LEVEL?",V
:PLOT1(**,L3,L4,°) (**= STAT PLOT, TYPE, 1)
:5->DIM L3
:5->DIM L4
:FOR(A,1,5
:RANDINT(1,53->L3(A)
:47->L4(A)
:END
:LBL 1
:IF DIM L3=W+5
:GOTO 6
:CLRDRAW
:FOR(A,1,DIM L3
:PT-ON(L3(A),L4(A)
:END
:IF MIN(L4)<=10
:GOTO 9
:TRACE
:LINE(1,1,X,10
:LINE(11,1,X,10
:LINE(21,1,X,10 
:LINE(33,1,X,10
:LINE(43,1,X,10
:LINE(53,1,X,10
:LINE(63,1,X,10
:FOR(A,10,50,5
:LINE(X,10,X,A
:END
:FOR(A,1,DIM L3
:IF X=L3(A
:GOTO 7
:END
:L4-RANDINT(1,V)->L4
:GOTO 1
:LBL 7
:L4-RANDINT(1,V)->L4
:RANDINT(1,53->L3(A)
:47->L4(A)
:RANDINT(1,53->L3(DIM L3+1
:47->L4(DIM L4+1)
:GOTO 1
:LBL 6
:FOR(A,1,DIM L3
:LINE(L3(A),10,L3(A),47
:END
:PAUSE
:CLRHOME
:DISP "WON!
:PAUSE
:CLRLIST L1,L2,L3,L4
:CLRHOME
:STOP
:LBL 9
:FOR(A,10,47
:HORIZONTAL A
:END
:CLRDRAW
:PAUSE
:CLRHOME
:DISP "GAME OVER
:PAUSE
:CLRHOME
:CLRLIST L1,L2,L3,L4
:PLOTSOFF

{% endhighlight %}

[Edsger W. Dijkstra](http://en.wikipedia.org/wiki/Edsger_W._Dijkstra) famously said that those that start to learn programming with Basic become brain damaged. With the hindsight, I can see what he means. Good coding practices were few and far between in the TI-BASIC world. I'm glad to report, though, there seems to be few lasting repercussions on my programming style. At least, I don't think it is, you'd have to ask the people who maintain my code.

What I mainly programmed was games. I started with some glorified rock-paper-scissors, and went on to more advanced territory. The one I liked the most was Minesweeper. Programming has always seemed more fun to me than actually playing the games I developed, but Minesweeper was one the few games I wrote that I actually used more than a few times. 

After that, I tried to do even more advanced games, but the wall that I hit was the calculator's inability to allow real time interaction. This limited me to turn based games, which often (in my opinion) are no fun. Especially with a low-level game designer like I am. I tried strategy games, but couldn't come up with a sufficiently advanced AI to make the game any fun to play.

That's when I tried something else: I actually developed [my own version of Sim-City for the TI80](https://github.com/yannickmahe/ti80-simcity). It was very limited, both graphically and in functionality, but it was pretty fun to play. I was somewhat proud of myself for that one.

A friend of mine had started his own website, on a Geocities type service provided by his ISP. He asked me if he could put my programs on his website. I, of course, was okay with it. So he typed the whole source code manually on his computer and put it on his website. In essence, before I had any real idea was open source was, I had released my first open source software.

A few years later, I randomly googled "TI80 games" and found on a website I had never heard of, a list of a few games. (the website is still online today: [http://www.ti80.online.fr/jeux.php3](http://www.ti80.online.fr/jeux.php3) - in french) The last one of the list was Sim-City. The one I had programmed. Apparently, someone had stumbled onto my friend's page, and copied the game on their calculator, played it, and found it good enough to put on their website. The only part that was slightly annoying was that they had removed my name from the program (pretty easy to do: remove DISP "BY YANNICK" from the code).

I guess I got "pirated" but it was a pretty awesome feeling: somebody, somewhere, was actually playing a game I had created! But the best part was when I found somebody had used the game and liked it so much... *they wrote a strategy guide*.

**Further discussion**

Reddit discussion on [/r/coding](http://www.reddit.com/r/coding): [link](http://www.reddit.com/r/coding/comments/1l3ql1/learning_to_code_on_a_low_end_graphical_calculator/)
