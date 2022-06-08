# ANSI Color Escape Sequences
### Credit: [Richard Barnes](https://richard.science/)

This repo contains a fantastic Stack Overflow [answer](https://stackoverflow.com/questions/4842424/list-of-ansi-color-escape-sequences) given by Richard Barnes, with the objective of preserving it from Stack Overflow's moderators...

---

The ANSI escape sequences you're looking for are the Select Graphic Rendition subset. All of these have the form

    \033[XXXm

where XXX is a series of semicolon-separated parameters.

To say, make text red, bold, and underlined (we'll discuss many other options below) in C you might write:

    printf("\033[31;1;4mHello\033[0m");

In C++ you'd use

    std::cout<<"\033[31;1;4mHello\033[0m";

In Python3 you'd use

    print("\033[31;1;4mHello\033[0m")

and in Bash you'd use

    echo -e "\033[31;1;4mHello\033[0m"

where the first part makes the text red (31), bold (1), underlined (4) and the last part clears all this (0).

As described in the table below, there are a large number of text properties you can set, such as boldness, font, underlining, &c.

## Font Effects

<table class="s-table">
<thead>
<tr>
<th>Code</th>
<th>Effect</th>
<th>Note</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>Reset / Normal</td>
<td>all attributes off</td>
</tr>
<tr>
<td>1</td>
<td>Bold or increased intensity</td>
<td></td>
</tr>
<tr>
<td>2</td>
<td>Faint (decreased intensity)</td>
<td>Not widely supported.</td>
</tr>
<tr>
<td>3</td>
<td>Italic</td>
<td>Not widely supported. Sometimes treated as inverse.</td>
</tr>
<tr>
<td>4</td>
<td>Underline</td>
<td></td>
</tr>
<tr>
<td>5</td>
<td>Slow Blink</td>
<td>less than 150 per minute</td>
</tr>
<tr>
<td>6</td>
<td>Rapid Blink</td>
<td>MS-DOS ANSI.SYS; 150+ per minute; not widely supported</td>
</tr>
<tr>
<td>7</td>
<td>[[reverse video]]</td>
<td>swap foreground and background colors</td>
</tr>
<tr>
<td>8</td>
<td>Conceal</td>
<td>Not widely supported.</td>
</tr>
<tr>
<td>9</td>
<td>Crossed-out</td>
<td>Characters legible, but marked for deletion.  Not widely supported.</td>
</tr>
<tr>
<td>10</td>
<td>Primary(default) font</td>
<td></td>
</tr>
<tr>
<td>11–19</td>
<td>Alternate font</td>
<td>Select alternate font <code>n-10</code></td>
</tr>
<tr>
<td>20</td>
<td>Fraktur</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>21</td>
<td>Bold off or Double Underline</td>
<td>Bold off not widely supported; double underline hardly ever supported.</td>
</tr>
<tr>
<td>22</td>
<td>Normal color or intensity</td>
<td>Neither bold nor faint</td>
</tr>
<tr>
<td>23</td>
<td>Not italic, not Fraktur</td>
<td></td>
</tr>
<tr>
<td>24</td>
<td>Underline off</td>
<td>Not singly or doubly underlined</td>
</tr>
<tr>
<td>25</td>
<td>Blink off</td>
<td></td>
</tr>
<tr>
<td>27</td>
<td>Inverse off</td>
<td></td>
</tr>
<tr>
<td>28</td>
<td>Reveal</td>
<td>conceal off</td>
</tr>
<tr>
<td>29</td>
<td>Not crossed out</td>
<td></td>
</tr>
<tr>
<td>30–37</td>
<td>Set foreground color</td>
<td>See color table below</td>
</tr>
<tr>
<td>38</td>
<td>Set foreground color</td>
<td>Next arguments are <code>5;&lt;n&gt;</code> or <code>2;&lt;r&gt;;&lt;g&gt;;&lt;b&gt;</code>, see below</td>
</tr>
<tr>
<td>39</td>
<td>Default foreground color</td>
<td>implementation defined (according to standard)</td>
</tr>
<tr>
<td>40–47</td>
<td>Set background color</td>
<td>See color table below</td>
</tr>
<tr>
<td>48</td>
<td>Set background color</td>
<td>Next arguments are <code>5;&lt;n&gt;</code> or <code>2;&lt;r&gt;;&lt;g&gt;;&lt;b&gt;</code>, see below</td>
</tr>
<tr>
<td>49</td>
<td>Default background color</td>
<td>implementation defined (according to standard)</td>
</tr>
<tr>
<td>51</td>
<td>Framed</td>
<td></td>
</tr>
<tr>
<td>52</td>
<td>Encircled</td>
<td></td>
</tr>
<tr>
<td>53</td>
<td>Overlined</td>
<td></td>
</tr>
<tr>
<td>54</td>
<td>Not framed or encircled</td>
<td></td>
</tr>
<tr>
<td>55</td>
<td>Not overlined</td>
<td></td>
</tr>
<tr>
<td>60</td>
<td>ideogram underline</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>61</td>
<td>ideogram double underline</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>62</td>
<td>ideogram overline</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>63</td>
<td>ideogram double overline</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>64</td>
<td>ideogram stress marking</td>
<td>hardly ever supported</td>
</tr>
<tr>
<td>65</td>
<td>ideogram attributes off</td>
<td>reset the effects of all of 60-64</td>
</tr>
<tr>
<td>90–97</td>
<td>Set bright foreground color</td>
<td>aixterm (not in standard)</td>
</tr>
<tr>
<td>100–107</td>
<td>Set bright background color</td>
<td>aixterm (not in standard)</td>
</tr>
</tbody>
</table>

## 2-bit Colours

You've got this already!

## 4-bit Colours

The standards implementing terminal colours began with limited (4-bit) options. The table below lists the RGB values of the background and foreground colours used for these by a variety of terminal emulators:

INSERT IMAGE

Using the above, you can make red text on a green background (but why?) using:

    \033[31;42m

## 11 Colours (An Interlude)

In their book "Basic Color Terms: Their Universality and Evolution", Brent Berlin and Paul Kay used data collected from twenty different languages from a range of language families to identify eleven possible basic color categories: white, black, red, green, yellow, blue, brown, purple, pink, orange, and gray.

Berlin and Kay found that, in languages with fewer than the maximum eleven color categories, the colors followed a specific evolutionary pattern. This pattern is as follows:

1. All languages contain terms for black (cool colours) and white (bright colours).
2. If a language contains three terms, then it contains a term for red.
3. If a language contains four terms, then it contains a term for either green or yellow (but not both).
4. If a language contains five terms, then it contains terms for both green and yellow.
5. If a language contains six terms, then it contains a term for blue.
6. If a language contains seven terms, then it contains a term for brown.
7. If a language contains eight or more terms, then it contains terms for purple, pink, orange or gray.

This may be why story Beowulf only contains the colours black, white, and red. It may also be why the Bible does not contain the colour blue. Homer's Odyssey contains black almost 200 times and white about 100 times. Red appears 15 times, while yellow and green appear only 10 times. ([More information here](https://en.wikipedia.org/wiki/Linguistic_relativity_and_the_color_naming_debate))

Differences between languages are also interesting: note the profusion of distinct colour words used by English vs. Chinese. However, digging deeper into these languages shows that each uses colour in distinct ways. ([More information](http://muyueh.com/greenhoney/))

INSERT IMAGE

Generally speaking, the naming, use, and grouping of colours in human languages is fascinating. Now, back to the show.

## 8-bit (256) colours

Technology advanced, and tables of 256 pre-selected colours became available, as shown below.

INSER IMAGE

Using these above, you can make pink text like so:

    \033[38;5;206m     #That is, \033[38;5;<FG COLOR>m

And make an early-morning blue background using

    \033[48;5;57m      #That is, \033[48;5;<BG COLOR>m

And, of course, you can combine these:

    \033[38;5;206;48;5;57m

The 8-bit colours are arranged like so:

    0x00-0x07:  standard colors (same as the 4-bit colours)
    0x08-0x0F:  high intensity colors
    0x10-0xE7:  6 × 6 × 6 cube (216 colors): 16 + 36 × r + 6 × g + b (0 ≤ r, g, b ≤ 5)
    0xE8-0xFF:  grayscale from black to white in 24 steps

## ALL THE COLOURS

Now we are living in the future, and the full RGB spectrum is available using:

    \033[38;2;<r>;<g>;<b>m     #Select RGB foreground color
    \033[48;2;<r>;<g>;<b>m     #Select RGB background color

So you can put pinkish text on a brownish background using

    \033[38;2;255;82;197;48;2;155;106;0mHello

Support for "true color" terminals is listed [here](https://gist.github.com/XVilka/8346728).

Much of the above is drawn from the Wikipedia page "[ANSI escape code](https://en.wikipedia.org/wiki/ANSI_escape_code)".

## A Handy Script to Remind Yourself

Since I'm often in the position of trying to remember what colours are what, I have a handy script called: `~/bin/ansi_colours`:

    #!/usr/bin/python

    print "\\033[XXm"

    for i in range(30,37+1):
        print "\033[%dm%d\t\t\033[%dm%d" % (i,i,i+60,i+60);

    print "\033[39m\\033[49m - Reset colour"
    print "\\033[2K - Clear Line"
    print "\\033[<L>;<C>H OR \\033[<L>;<C>f puts the cursor at line L and column C."
    print "\\033[<N>A Move the cursor up N lines"
    print "\\033[<N>B Move the cursor down N lines"
    print "\\033[<N>C Move the cursor forward N columns"
    print "\\033[<N>D Move the cursor backward N columns"
    print "\\033[2J Clear the screen, move to (0,0)"
    print "\\033[K Erase to end of line"
    print "\\033[s Save cursor position"
    print "\\033[u Restore cursor position"
    print " "
    print "\\033[4m  Underline on"
    print "\\033[24m Underline off"
    print "\\033[1m  Bold on"
    print "\\033[21m Bold off"

This prints

INSERT IMAGE
