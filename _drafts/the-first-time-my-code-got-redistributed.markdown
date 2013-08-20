---
layout: posts
title: "The first time a program I wrote got redistributed (without my knowledge)"
categories: [coding]
---

This is a story from way back when I first started to program, in 1997 to be exact. It was the year I entered high school. Every students was required to have a [TI-80](http://en.wikipedia.org/wiki/TI-80) or higher, an entry level programmable graphical calculator. 

![TI-80](/assets/TI80.jpg "TI-80") I started programming as soon as one of my friends showed me how he had created a rock-paper-scissors program on his TI-80, and could never program enough. I programmed before, during and after class - much to the irritation of my teachers (using a calculator in French class is somewhat conspicuous). Like many people who ended up being programmers, I had just found something I loved. My TI-80 is dead now, I tore it apart to try and put it back together as soon as I upgraded, the next year.

Programming on the TI-80 was, in retrospect, a peculiar experience. The language was TI-BASIC, which was a quirky language to say the least especially, in its TI-80 form:
- the keyboard was calculator style, with the letters ordered alphabetically
- you didn't type the program text but inputted [lexemes](http://en.wikipedia.org/wiki/Lexical_analysis) directly. For example, to use a for loop, you didn't type the letter F, O and R, but you went in the "Program" menu, and chose the seventh item from the list. In your program code, the "FOR(" would be then be displayed and you could input your parameters.
- there was no way to comment your code
- variable names were all exactly one letter long and always in caps (in fact everything was always in caps); and variables could only hold a float value. Some of these variables could be overwritten by the system. X and Y notably got set to coordinates chosen on the screen, so you could never use these variables in any program with graphical capabilities. This meant that you could use at most 25 variables (the greek letter theta was also available) in a program, all with nondescript names. All these variables were system-wide global variables.
- you couldn't create macros or functions in a program. You could call a program from another program, but there was no direct way to pass results from one program to the other.
- the only data model available were arrays, called lists. There were only 6 lists available, with a max size of 99 items, and of course they could only store floats.
- there was no way to get data from the user during the program run apart from a prompt. This meant there was no way for the calculator to tell which key was being pressed, so any real time interaction was out of the question
- storing data in variables was done in the opposite way to the standard. Instead of typing: A = 1, you typed: 1->A

Of course, there were also strong limitations with the hardware.
there was only 7Kb of RAM on the calculator and no ROM, so you checked every byte to make sure your program would fit, and could run without hitting "ERR: MEMORY"
the screen was 2-colors, of course, and a very small screen (76 by 80 if I remember correctly)
there was no data input port. This meant you were limited to TI-BASIC and couldn't use any Assembly, like other TIs could. This also meant that if you wanted to use a program a friend had had or that you found on the Internet, the only way to get it was to retype it entirely.

At the time though, I didn't realise that was weird in any way. It was just how you programmed.

[Edsger W. Dijkstra](http://en.wikipedia.org/wiki/Edsger_W._Dijkstra) famously said that those that start to learn programming with Basic become brain damaged. I'm glad to report, there seems to be few lasting repercussions on my programming style. At least, I don't think it is.

What I mainly programmed was games. I started with some glorified rock-paper-scissors, and went on to more advanced territory. The one I liked the most was Minesweeper. Programming has always seemed more fun to me than actually playing the games I developed, but Minesweeper was one the few games I wrote that I actually used more than a few times. 

After that, I tried to do even more advanced games, but the wall that I hit was the calculator's inability to allow real time interaction. This limited me to turn based games, which often (in my opinion) are no fun. Especially with a low-level game designer like I am. I tried strategy games, but couldn't come up with a sufficiently advanced AI to make the game any fun to play.

That's when I tried something else: I actually developed my own version of Sim-City for the TI-80. It was very limited, both graphically and in functionality, but it was pretty fun to play. I was somewhat proud of myself for that one.

A friend of mine had started his own website, on a Geocities type service provided by his ISP. He asked me if he could put my programs on his website. I, of course, was okay with it. So he typed the whole source code manually on his computer and put it on his website. In essence, before I had any real idea was Open Source was, I had released my first open source software.

A few years later, I randomly googled "TI-80 games" and found on a website I had never heard of, a list of a few games. (the website is still online today: [http://www.ti80.online.fr/jeux.php3](http://www.ti80.online.fr/jeux.php3) - in french) The last one of the list was Sim-City. The one I had programmed. Apparently, someone had stumbled onto my friend's page, and copied the game on their calculator, played it, and found it good enough to put on their website. The only part that was slightly annoying was that they had removed my name from the program (pretty easy to do: remove DISP "BY YANNICK" from the code).

I guess I got "pirated" but it was a pretty awesome feeling: somebody, somewhere, was actually playing a game I had created! But the best part was when I found somebody had used the game and liked it so much... they wrote a strategy guide.
