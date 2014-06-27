================================
Command: num
================================

--------------

COMMAND
~~~~~~~

**num** -- number selected Humdrum records according to user-defined
criteria

--------------

SYNOPSIS
~~~~~~~~

`` num [-efT] [-a **interp] [-i n] [-n regexp] [-o n] [-O n] [-p regexp] [-P regexp] [-r regexp] [-R regexp] [-s regexp] [-S regexp] [-x regexp] [-z regexp] [-Z regexp] [inputfile ...]``

--------------

DESCRIPTION
~~~~~~~~~~~

The **num** command produces sequential numerical output according to
user-defined numbering criteria. In its default operation, **num**
simply inserts numbers at the beginning of each data record -- beginning
with the value 1, and increasing by 1 for successive data records.
However, **num** provides various options that allow the user to specify
more precisely the kinds of data and conditions under which numbering
occurs.

Numbers may be inserted prior to data tokens, appended following data
tokens, or inserted in the middle of data tokens. Numbers may be output
only for the first input spine, or for all input spines. Alternatively,
numbers may be output in a separate output spine specified by the user.
Numbers may be assigned only to those data records matching a given
regular expression, or may be assigned to all records *other* than those
matching a regular expression. Numerical counts may begin at any real or
integer value and may be incremented or decremented by any real or
integer value. Numbering may restart at some defined value whenever a
certain regular expression is matched in the input. Numbers may be
output only when certain conditions are met; for example, although
counting may continue, outputting of numbers may be suspended or resumed
when the input data match user-specified regular expressions.

By way of example, the **num** command might be used to number measures,
phrases, chords, notes, rests, or other musically-pertinent features.
(See `EXAMPLES <#EXAMPLES>`__ below.)

--------------

OPTIONS
~~~~~~~

The **num** command provides the following options:

    +-------------------+----------------------------------------------------------------------+
    | -a *\*\*interp*   | append a new spine (*\*\*interp*) containing the output numbers      |
    +-------------------+----------------------------------------------------------------------+
    | **-e**            | place numbers at end of data tokens (rather than at the beginning)   |
    +-------------------+----------------------------------------------------------------------+
    | **-f**            | number all spines (all fields) in the input                          |
    +-------------------+----------------------------------------------------------------------+
    | **-h**            | displays a help screen summarizing the command syntax                |
    +-------------------+----------------------------------------------------------------------+
    | -i *n*            | set increment value to *n* (defaults to 1)                           |
    +-------------------+----------------------------------------------------------------------+
    | -n *regexp*       | number only those records matching *regexp*                          |
    +-------------------+----------------------------------------------------------------------+
    | -o *n*            | set initial offset value to *n* (defaults to 1)                      |
    +-------------------+----------------------------------------------------------------------+
    | -O *n*            | set offset value to *n* after a reset                                |
    +-------------------+----------------------------------------------------------------------+
    | -p *regexp*       | horizontally position the output number immediately following the    |
    +-------------------+----------------------------------------------------------------------+
    |                   | first occurrence of *regexp* on the line                             |
    +-------------------+----------------------------------------------------------------------+
    | -P *regexp*       | horizontally position the output number immediately prior to the     |
    +-------------------+----------------------------------------------------------------------+
    |                   | first occurrence of *regexp* on the line                             |
    +-------------------+----------------------------------------------------------------------+
    | -r *regexp*       | resume numbering records when *regexp* is matched                    |
    +-------------------+----------------------------------------------------------------------+
    | -R *regexp*       | resume numbering records after *regexp* is matched                   |
    +-------------------+----------------------------------------------------------------------+
    | -s *regexp*       | suspend numbering records when *regexp* is matched                   |
    +-------------------+----------------------------------------------------------------------+
    | -S *regexp*       | suspend numbering records after *regexp* is matched                  |
    +-------------------+----------------------------------------------------------------------+
    | **-T**            | reset counter when all spines have exclusive interpretations         |
    +-------------------+----------------------------------------------------------------------+
    | -x *regexp*       | exclude numbering those records matching *regexp*                    |
    +-------------------+----------------------------------------------------------------------+
    | -z *regexp*       | reset counter when record matches *regexp*                           |
    +-------------------+----------------------------------------------------------------------+
    | -Z *regexp*       | reset counter after record matches *regexp*                          |
    +-------------------+----------------------------------------------------------------------+

Options are specified in the command line.

Normally, the effect of **num** is to add numbers to data tokens already
in the input. With the **-a** option, **num** creates a new spine which
is appended to the right of the input stream. The numerical outputs of
**num** become data records in this new output spine. The user can
specify the name of the output interpretation via the command line
parameter *\*\*interp*. The **-a** option cannot be used with the **-p**
or **-P** options.

The **-e** option causes numbers generated by **num** to be append to
the end of each appropriate data token rather than the (default)
beginning of each data token. The **-e** and **-a** options are mutually
exclusive. In addition, the **-e** option cannot be used with the **-p**
or **-P** options.

The **-f** option causes all spines (all fields) in the input to be
numbered rather than the (default) first (left-most) spine. The **-f**
option is mutually exclusive with the **-a** option. In addition, the
**-f** option cannot be used with the **-p** or **-P** options.

The **-i** option allows the user to set the increment value for
successive numbers. The default value is 1 -- meaning that successive
numerical outputs are 1 greater than the previous value. Negative
increment values are also permissible. For example, the user might
define an initial value beginning at 100, and decrement by 5 with each
successive value.

The **-n** option causes **num** to output numerical values, only when
the current data record matches a specified regular expression.

The **-o** option is used to define an initial (offset) value from which
subsequent numbers are calculated. If no offset is defined, the default
value is 1.

The **-O** option defines an offset value to which the counter will be
returned each time a *reset* action occurs. The **-O** option should be
used in conjunction with one of either the **-T**, **-z** or **-Z**
options.

The **-p** and **-P** options allow the user to place any output
numerical value in a particular (horizontal) place in the output line.
In the case of **-p** the output number is positioned immediately
following the first (left-most) string matching the specified regular
expression. With the **-P** option, the output number is positioned
immediately prior to the first string matching the specified regular
expression. The **-p** and **-P** options cannot be used with either the
**-a**, **-e** or **-f** options.

The **-r** option defines a condition under which the outputting of
numbers will resume. Specifically, the user defines a regular expression
with the **-r** option that, when matched, causes the immediate
resumption of printing.

The **-R** option is similar to the **-r** option, with the exception
that outputting of numbers is resumed *after* any record matching the
specified regular expression.

The **-s** option causes the outputting of numbers to be suspended when
an input record matches a specified regular expression. Although the
numerical values are not outputted, the numerical values continue to be
incremented in accordance with the defined counting conditions.

The **-S** option is similar to the **-s** option, with the exception
that the outputting of numbers is suspended *after* any record matching
the specified regular expression.

The **-T** option causes the counter to be reset (to the value specified
by **-O**) whenever exclusive interpretations are encountered in all of
the input spines. If no initial offset has been specified via the **-O**
option, then the counter is reset to the value 1.

The **-x** option causes records matching a given regular expression to
be excluded from the counting; no output is generated for such records.
Note that when used in conjunction with the **-n** option, both the
*match* and *don't match* criteria must be fulfilled in order for the
current record to participate in the counting.

The **-z** option causes the counter to be reset (to the value specified
by **-O**) whenever a data record matches a specified regular
expression. If no initial offset has been specified via the **-O**
option, then the counter is reset to the value 1.

The **-Z** option is similar to the **-z** option, with the exception
that the counter is reset *after* any record matching the specified
regular expression.

--------------

EXAMPLES
~~~~~~~~

The following examples illustrate how **num** may be used. Consider the
following input (left spine) and corresponding **num** output (right
spine). ````

    +------------+---------------+
    | \*\*kern   | \*\*plength   |
    +------------+---------------+
    | =23        | .             |
    +------------+---------------+
    | {8a        | .             |
    +------------+---------------+
    | .          | .             |
    +------------+---------------+
    | 8cc        | .             |
    +------------+---------------+
    | }8ee       | 3             |
    +------------+---------------+
    | {8g#       | .             |
    +------------+---------------+
    | =24        | .             |
    +------------+---------------+
    | 8dd        | .             |
    +------------+---------------+
    | 8ee        | .             |
    +------------+---------------+
    | }8ff       | 4             |
    +------------+---------------+
    | 8r         | .             |
    +------------+---------------+
    | .          | .             |
    +------------+---------------+
    | =25        | .             |
    +------------+---------------+
    | {8gn       | .             |
    +------------+---------------+
    | 8cc        | .             |
    +------------+---------------+
    | }8ee       | 3             |
    +------------+---------------+
    | {8f#       | .             |
    +------------+---------------+
    | =26        | .             |
    +------------+---------------+
    | 8cc        | .             |
    +------------+---------------+
    | 8dd        | .             |
    +------------+---------------+
    | }8ee-      | 4             |
    +------------+---------------+
    | \*-        | \*-           |
    +------------+---------------+

The ``**plength`` output indicates the number of notes in each phrase
for the corresponding ``**kern`` spine. The output was generated using
the following command:

    `` num -a '**plength' -z '{' -x '[.r=]' -s '{' -r '}' -S '}'``

The **-x** option excludes ``**kern`` rests, barlines, and null tokens
from the counting. The **-z** option causes the counter to be reset to 1
whenever a begin-phrase signifier (\`{') is encountered. The **-s**
option causes suspension of output numbers to occur at the beginning of
each phrase, and the **-r** option causes output numbers to be resumed
at the end of each phrase (hence, only the phrase-end signifiers are
given numbered output). The **-S** option ensures that numbers are not
printed for notes outside of phrases; that is, it suspends outputting
numbers following the end of a phrase.§ .FS § Note that this command
will still fail to suppress the numbering of notes occuring prior to the
first phrase. .FE The **-a** option causes the numbers to be output as a
separate spine labelled ``**plength``.

The command

    `` num -a '**ordo' koto``

outputs a new spine labelled ``**ordo`` containing successive integers
beginning at 1 for each data record in the input.

    `` num -n '^=' -x '==' -p '=' -o 108 sarod``

numbers all "common system" barlines in the file ``sarod``, beginning
with measure 108. Double barlines are not numbered (due to the **-x**
option) and numbers are positioned directly following the equals sign
(due to the **-p** option). The **-p** option ensures that the number
precedes pause markings and other possible barline signifiers. Note that
if measure numbers already exist for a file, the measures can be
renumbered by first removing the existing measure numbers using
**humsed**.

The command

    `` num -a '**phrase#' -n '{' -T rebec``

outputs a spine containing numbers that number the beginning of each
``**kern`` phrase for the file ``rebec``; if any exclusive
interpretation is encountered, the phrase numbering is restarted at 1.

The command

    `` num -x '^='``

numbers all data records other than common system barlines.

    `` num -x '^=' -Z '='``

numbers all data records within each common system measure -- starting
at the value 1 with each new measure.

--------------

PORTABILITY
~~~~~~~~~~~

DOS 2.0 and up, with the MKS Toolkit. OS/2 with the MKS Toolkit. UNIX
systems supporting the *Korn* shell or *Bourne* shell command
interpreters, and revised *awk* (1985).

--------------

SEE ALSO
~~~~~~~~

**nl** (UNIX), **\*\*ordo** (2), `**regexp** <regexp.html>`__ (4),
**regexp** (6), `**rend** <rend.html>`__ (4)

--------------

NOTES
~~~~~

The **-O** option should be used in conjunction with one of either the
**-T**, **-z** or **-Z** options.

--------------

| 

-  `**Index to Humdrum Commands** <../commands.toc.html>`__
-  `**Table for Contents for Humdrum User Guide** <../guide.toc.html>`__

| 

.. | | image:: /Humdrum/HumdrumIcon.gif
.. |Humdrum | image:: /Humdrum/HumdrumHeader.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
.. | | image:: /Humdrum/HumdrumIcon.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
