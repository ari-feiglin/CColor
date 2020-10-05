# <ins>**CCOLOR LIBRARY**</ins>

The CColor Library is a library I wrote for easily formatting and printing colored (and emphasized) text in C. It utilizes ANSI color sequences, and its usage is quite simple. It has one main function, and several other (less appealing and useful) alternatives.

**The main function:**
```c
int print_color(char * format, ...)
```
print_color gets a string that uses the characters ~ and \` in order to print a colored/emphasized string. ~ are for defined constants, and \` is for printing RGB colors. Here's an example:

```c
print_color("~~~HELLO WORLD!~\n", BG_WHITE, BLACK, BOLD, RESET);
```
prints the string "HELLO WORLD!" with a background color of white, a text color of black, and emphasized bold. Afterwards it resets the colors to default and prints a newline character. (BG_WHITE, BLACK, BOLD, and RESET are all defined constants) <br />
The issue here is that the BOLD constant also desaturates the color of the text, so th text's color will be grey, not black. We can override this with and RGB color:

```c
print_color("~`~HELLO WORLD!~\n", BG_WHITE, FG,0,0,0, BOLD, RESET);
```
Here, FG denotes that it is a foreground (or text) color as opposed to a BG (background) color. In order to make it more readble, I do not put spaces between the layer, R, G, or B when printing.

**About defined constants:**
Defined constants are split into four groups with their respective subgroups:
* **Reset** - resets the color and emphasis to default. (RESET)
* **Emphasis** - emphasizes the text (BOLD, ITALIC, UNDERLINE)
* **Defined colors** 
    * [color] - sets the text's color to [color]
    * B_[color] - sets the text's color to the brighter version of [color]
    * BG_[color] - sets the beackground/highlight of the text to [color]
    * BG_B_[color] - sets the beackground/highlight of the text to the brighter version of [color]
* **RGB** - the syntax for RGB is different \` requires four input values: layer, red amount, green amount, and blue amount. Layers are:
    * FG - foreground (for text color)
    * BG - background (for highlight color)

**The other functions:**
All other functions are unnecessary. 
* CLEAR_FORMAT - clears format
* NCLEAR_FORMAT - clears format and prints newline
* BIU - emphasis
* COLOR - text color (defined constant)
* BG_COLOR - background/highlight color (defined constant)
* RGB - text color (RGB)
* BG_RGB - background/highlight color (RGB)

BIU, COLOR, and BG_COLOR are all technically the same function, and doing: <br />
BIU(BOLD) is equivalent to COLOR(BOLD) or BG_COLOR(BOLD), for example. <br />
CLEAR_FORMAT is equivalent to BIU(RESET) or COLOR(RESET) or BG_COLOR(RESET)
