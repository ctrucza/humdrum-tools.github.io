================================
Command: solfa
================================

--------------

COMMAND
~~~~~~~

**solfa** -- translate selected Humdrum pitch-related representations to
tonic solfa syllables (``**solfa``)

--------------

SYNOPSIS
~~~~~~~~

`` solfa  [-tx]  [inputfile ...]  [> outputfile.sol]``

--------------

DESCRIPTION
~~~~~~~~~~~

The **solfa** command transforms various pitch-related inputs to the
corresponding tonic solfa syllables. The command outputs one or more
Humdrum ``**solfa`` spines -- where pitches are designated by the
syllables *do, re, mi, fa, so, la,* and *ti* -- or their chromatic
alterations: *di, da, ri, ra,* etc. (see below). Tonic solfa syllables
can be determined only with reference to some prevailing key. For
example, the pitch C is the tonic (``do``) in the key of C major, but
the mediant (``mi``) in the key of A-flat major. The **solfa** command
expects a tandem interpretation indicating the key of the input passage;
**solfa** will adapt to specified changes of key within an input stream.
If no key information is provided prior to the first pitch-related data,
**solfa** issues an error message and terminates.

There are various systems for extending the tonic solfa syllables in
order to representing chromatic alterations. The system used by
**solfa** is tabulated below. (Pronunciations are indicated in
parentheses.)

    basic
    raised
    **lowered**
    do (*doe*)
    di (*dee*)
    de (*day*)
    re (*ray*)
    ri (*ree*)
    ra (*raw*)
    mi (*me*)
    my (*my*)
    me (*may*)
    fa (*fah*)
    fi (*fee*)
    fe (*fay*)
    so (*so*)
    si (*see*)
    se (*say*)
    la (*la*)
    li (*lee*)
    le (*lay*)
    ti (*tee*)
    ty (*tie*)
    te (*tay*)

*Summary of **solfa** Signifiers*

The **solfa** command differs from the `**deg** <deg.html>`__ and
`**degree** <degree.html>`__ commands in that pitches are represented
without regard to major or minor *mode.* For example, in the key of C
major, **deg** and **degree** will characterize A-flat as a lowered
sixth scale degree, whereas the same pitch will be a normal sixth scale
degree in the key of C minor. In the case of **solfa,** the A-flat will
be characterized as ``le`` -- whether or not the key is C major or C
minor. As in the case of **deg** and **degree**, the amount of chromatic
alteration is not represented; once a pitch is "raised," raising it
further will not change the output representation. For example, where
the tonic pitch is B-flat, both B-natural and B-sharp are represented by
``di``.

The **solfa** command is able to translate any of the pitch-related
representations listed below. For descriptions of the various input
representations (including ``**solfa``) refer to Section 2
*(Representation Reference)* of this reference manual.

It is recommended that output files produced by the **solfa** command
should be given names with the distinguishing .sol extension.

    +---------------+---------------------------------------------------------------------+
    | ``**kern``    | core pitch/duration representation                                  |
    +---------------+---------------------------------------------------------------------+
    | ``**pitch``   | American National Standards Institute pitch notation (e.g. "A#4")   |
    +---------------+---------------------------------------------------------------------+
    | ``**solfg``   | French solfège system (fixed \`doh')                                |
    +---------------+---------------------------------------------------------------------+
    | ``**Tonh``    | German pitch system                                                 |
    +---------------+---------------------------------------------------------------------+

*Input representations processed by **solfa**.*

--------------

OPTIONS
~~~~~~~

The **solfa**

command provides the following options:

    **-h**

    displays a help screen summarizing the command syntax

    **-t**

    suppresses printing of all but the first note of a group of tied
    notes

    **-x**

    suppresses printing of
    non-``**solfa signifiers  Options are specified in the command line. ``

    The **-t** option ensures that only a single output value is given
    for tied notes; the output coincides with the first note of the tie.

    In the default operation, **solfa** outputs non-pitch-related
    signifiers in addition to the degree value. For example, in the key
    of D, the ``**kern`` token "4Gz" will result in the output "4faz" --
    that is, after translating G to fa, the "4...z" signifiers are
    retained in the output. For some applications, echoing
    non-pitch-related signifiers in the output is useful. However, in
    other situations, the result can prove confusing. The **-x** option
    is useful for eliminating non-pitch-related signifiers from the
    output.

    --------------

    EXAMPLES
    ~~~~~~~~

    The following example illustrates the use of **solfa.** The input
    contains four pitch-related spines -- one of which (``**MIDI``)
    cannot be processed by **solfa.** In addition, there is one
    non-pitch-related spines (``**embell``). ````

        !! \`solfa' example.
        \*\*kern
        \*\*Tonh
        \*\*MIDI
        \*\*solfg
        \*\*pitch
        \*\*embell
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*C:
        \*d:
        \*G#:
        \*a:
        \*F:
        \*F:
        =1
        =1
        =1
        =1
        =1
        =1
        8ee-
        Gis2
        /60/
        do3
        F4foo
        ct
        .
        .
        /-60/
        .
        .
        .
        8f
        H2
        /62/
        fa3
        G4bar
        upt
        .
        .
        /-62/
        .
        .
        .
        8dd-
        B2
        /70/
        mi3
        E4
        ct
        .
        .
        /-70/
        .
        .
        .
        8d--
        Cis4
        /61/
        r
        F4
        sus
        .
        .
        /-61/
        .
        .
        .
        =2
        =2
        =2
        =2
        =2
        =2
        [4a-
        r
        .
        mi\_b3
        F4 A4
        .
        .
        Heses2
        .
        re3
        G4 Bb4
        ct
        4a-]
        C3
        /48/ /52/
        do3
        E4 C5
        ct
        .
        .
        /-48/
        .
        .
        .
        .
        H2 E3
        /-52/
        la3
        G4
        ct
        =3
        =3
        =3
        =3
        =3
        =3
        r
        A2 F3
        .
        r
        F4
        .
        ==
        ==
        ==
        ==
        ==
        ==
        \*-
        \*-
        \*-
        \*-
        \*-
        \*-

    Executing the command:

        `` solfa -tx input > output``

    produces the following result: ````

        !! \`solfa' example.
        \*\*solfa
        \*\*solfa
        \*\*MIDI
        \*\*solfa
        \*\*solfa
        \*\*embell
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*M2/4
        \*C:
        \*d:
        \*G#:
        \*a:
        \*F:
        \*F:
        =1
        =1
        =1
        =1
        =1
        =1
        me
        fi
        /60/
        me
        do
        ct
        .
        .
        /-60/
        .
        .
        .
        fa
        la
        /62/
        le
        r
        upt
        .
        .
        /-62/
        .
        .
        .
        ra
        le
        /70/
        so
        ti
        ct
        .
        .
        /-70/
        .
        .
        .
        ra
        ti
        /61/
        r
        do
        sus
        .
        .
        /-61/
        .
        .
        .
        =2
        =2
        =2
        =2
        =2
        =2
        le
        r
        .
        so
        do mi
        .
        .
        le
        .
        fa
        re fa
        ct
        .
        te
        /48/ /52/
        me
        ti so
        ct
        .
        .
        /-48/
        .
        .
        .
        .
        la re
        /-52/
        do
        re
        ct
        =3
        =3
        =3
        =3
        =3
        =3
        r
        so me
        .
        r
        do
        .
        ==
        ==
        ==
        ==
        ==
        ==
        \*-
        \*-
        \*-
        \*-
        \*-
        \*-

    Both processed and unprocessed spines are output. Notice that the
    tied note at the beginning of measure 2 in the ``**kern`` spine has
    been rendered as a single note rather than as two notes (due to the
    **-t** option). Also notice that the non-pitch-related signifiers
    (e.g. foo) in the first notes of the ``**pitch`` spine have been
    stripped away (due to the **-x** option).

    --------------

    FILES
    ~~~~~

    The file ``x_option.awk`` is used by this program when the **-x**
    option is invoked.

    --------------

    PORTABILITY
    ~~~~~~~~~~~

    DOS 2.0 and up, with the MKS Toolkit. OS/2 with the MKS Toolkit.
    UNIX systems supporting the *Korn* shell or *Bourne* shell command
    interpreters, and revised *awk* (1985).

    --------------

    SEE ALSO
    ~~~~~~~~

    `` **deg (2),  deg (4), **degree (2),  degree (4), **kern (2),  kern (4), **pitch (2),  pitch (4), **solfa (2), **solfg (2),  solfg (4), **Tonh (2),  tonh (4)``

    --------------

    | 

    -  `**Pertinent description in the Humdrum User
       Guide** <../guide04.html#Scale_Degree>`__
    -  `**Index to Humdrum Commands** <../commands.toc.html>`__
    -  `**Table for Contents for Humdrum User
       Guide** <../guide.toc.html>`__

    | 

.. | | image:: /Humdrum/HumdrumIcon.gif
.. |Humdrum | image:: /Humdrum/HumdrumHeader.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
.. | | image:: /Humdrum/HumdrumIcon.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
