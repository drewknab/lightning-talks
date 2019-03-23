%title: Customizing Bash Prompts
%author: Drew Knab
%date: TBD

-> Customizing Bash Prompts <-
==============================
------------------------------

-> # Basic Terminal Info <-
*\\u* = username
*\\h* = hostname
*\\H* = fully qualified domain name
*\\w* = path to current directory
*\\W* = current directory
*\\d* = current date DDD MMM ddd
*\\@* = time hh:mm AM/PM
*\\n* = New Line

-------------------------------------------------

-> # Colors <-

(Pretty much) any modern terminal running bash has 16
colors available by escape characters.
  
They correspond to the absolute barest of
bones configurations.

Most terminal emulator themes only really adjust a small
subset of these colors

Many terminal emulators also support a 256 color mode.
That's not necessarily useful in a prompt, because
you've more than likely chosen to use an 8 - 16 color
theme in your terminal emulator.

-------------------------------------------------

-> # ANSI Escape Sequence <-

First you start with an escape character:
*\\e*
*\\033*
*\\x1b*

We'll use *\e* because it's the most convenient

All of these get you to the same place.

If you want to test at the command line you can type:
*echo -e "\\e[31mHello \\e[0mWorld"*

You can also mix and match colors and text effects
with ; delimited list.
If we wanted to make a bold, underlined 'yellow'
text we could do i.e. *echo -e "\\e[1;4;33mHi\\e[0m there"*

-------------------------------------------------

| _Text Effect_        | _Set_ | _Reset_ |
| ------------------ | --- | ----- |
| Bold               | 1   | 21    |
| Dim                | 2   | 22    |
| Underlined         | 4   | 24    |
| Blink              | 5   | 25    |
| Reverse            | 7   | 27    |
| Hidden             | 8   | 28    |
| Reset Text Effects | -   | 0     |

-------------------------------------------------


| _Color_          | _Foreground_ | _Background_ |
| -------------- | ---------- | ---------- |
| Default        | 39         | 49         |
| Black          | 30         | 40         |
| Red            | 31         | 41         |
| Green          | 32         | 42         |
| Yellow         | 33         | 43         |
| Blue           | 34         | 44         |
| Magenta        | 35         | 45         |
| Cyan           | 36         | 46         |
| Light Gray     | 37         | 47         |
| Dark Gray      | 90         | 100        |
| Light Red      | 91         | 101        |
| Light Green    | 92         | 102        |
| Light Yellow   | 93         | 103        |
| Light Blue     | 94         | 104        |
| Light Magenta  | 95         | 105        |
| Light Cyan     | 96         | 106        |
| White          | 97         | 107        |

-------------------------------------------------


-> # Unicode <-

Bash > 4.1
Beginning with 4.2 you can use a unicode
character by placing four hexidecimal digits
in a $'' string
\u2771

Prior to 4.2 you would have to use a different byte encoding
\xE2\x9D\xB1

-------------------------------------------------

-> # Strategies to Maintain a Clean Prompt <-
Warning Opinions Ahoy
Put any unicode/text into a variable
Use += to concat the string into managable bits
rather than one long single line
