================================
Command: synco
================================

--------------

COMMAND
~~~~~~~

**synco** -- measure degree of metric syncopation for Humdrum input

--------------

SYNOPSIS
~~~~~~~~

`` synco  [-e]  [inputfile ...]  [ > outputfile.syn]``

--------------

DESCRIPTION
~~~~~~~~~~~

The **synco** command characterizes the degree of metric syncopation
evident at successive moments in a passage. It outputs a single Humdrum
spine (``**synco``) containing numerical values representing the
instantaneous level of syncopation.

The **synco** command requires at least two spines of input data -- one
of which must be `` **metpos.`` (The ``**metpos`` representation encodes
the position in the metric hierarchy for each data record in the input.)
The other input spine(s) must contain information that explicitly or
implicitly encodes the occurrence of note onsets. Appropriate inputs to
**synco** include the pitch-related representations listed below. For
descriptions of the various input representations refer to Section 2
*(Representation Reference)* of this reference manual.

    +----------------+----------------------------------------------------------------------+
    | ``**cbr``      | critical band rate (in equivalent rectangular bandwidths)            |
    +----------------+----------------------------------------------------------------------+
    | ``**cents``    | hundredths of a semitone with respect to middle C=0                  |
    +----------------+----------------------------------------------------------------------+
    | ``**cocho``    | cochlear coordinates (in millimeters)                                |
    +----------------+----------------------------------------------------------------------+
    | ``**deg``      | key-related relative scale degree                                    |
    +----------------+----------------------------------------------------------------------+
    | ``**degree``   | key-related absolute scale degree                                    |
    +----------------+----------------------------------------------------------------------+
    | ``**freq``     | fundamental frequency (in hertz)                                     |
    +----------------+----------------------------------------------------------------------+
    | ``**fret``     | fretted-instrument pitch tablature                                   |
    +----------------+----------------------------------------------------------------------+
    | ``**kern``     | core pitch/duration representation                                   |
    +----------------+----------------------------------------------------------------------+
    | ``**MIDI``     | Music Instrument Digital Interface tablature                         |
    +----------------+----------------------------------------------------------------------+
    | ``**pc``       | pitch class                                                          |
    +----------------+----------------------------------------------------------------------+
    | ``**pitch``    | American National Standards Institute pitch notation (e.g. "A#4")    |
    +----------------+----------------------------------------------------------------------+
    | ``**semits``   | equal-tempered semitones with respect to middle C=0 (e.g. 12 = C5)   |
    +----------------+----------------------------------------------------------------------+
    | ``**solfa``    | tonic solfa syllables                                                |
    +----------------+----------------------------------------------------------------------+
    | ``**solfg``    | French solfège system (fixed \`doh')                                 |
    +----------------+----------------------------------------------------------------------+
    | ``**specC``    | spectral centroid (in hertz)                                         |
    +----------------+----------------------------------------------------------------------+
    | ``**Tonh``     | German pitch system                                                  |
    +----------------+----------------------------------------------------------------------+

*Input representations processed by **synco**.*

The resulting ``**synco`` spine contains numerical values, where zero
represents no metric syncopation and successively increasing values
represent increasing amounts of metric syncopation.

The **synco** command implements a definition of metric syncopation
inspired by the work of Lee and Longuet-Higgins (see
`REFERENCES <#REFERENCES>`__). In brief, metric syncopation may be
defined as a moment where an expected metric stress is absent. More
specifically, a metrically syncopated moment is defined as occurring
when no note-onset happens at a moment whose metric position is more
important than that of the most recent note onset. For example, where a
note onset occurs on the second beat of a quadruple meter, and is not
followed by a note onset on the third beat, the third beat is deemed
metrically syncopated because it occupies a higher metric position than
the previous onset.

The numerical output values generated by **synco** are calculated as the
logarithm of the metric position of the previous onset minus the
logarithm of the metric position of the current moment -- where the
current moment has no note onset, and coincides with a higher metric
position than the previous onset. The use of the logarithmic difference
weights the output values so that missing downbeats at the beginning of
a measure produce a greater metric syncopation value than lesser beats
or sub-beats in the measure. In addition, metric syncopation is greater
when the difference in metric position between the previous onset and
the current moment is greatest. (See `EXAMPLES <#EXAMPLES>`__.)

If more than one musical part is given as input, **synco** responds to
the *aggregate* rhythmic structure -- as though all of the parts were
amalgamated into a single rhythmic stream. By itself, a single musical
part may evoke considerable metric syncopation, but in combination with
other parts, metrically syncopated moments are typically fewer. In
short, running **synco** on a multi-part score normally produces
different results from running **synco** on each part individually.

**synco** monitors the input in order to determine the Humdrum
*time-base* -- if encoded. Specifically, **synco** checks to ensure that
the time-base is not excessively short. It is possible to have time-base
values that exceed the temporal resolving power of human listeners. For
example, if an onset appears a thirty-second duration prior to an
expected down-beat, listeners are apt to hear the displaced onset as
occurring **on** the beat rather than being a very short syncopation.
"Excessively short" is operationally defined as a time-base resolution
shorter than a sixteenth note. In such cases, **synco** issues a
warning, noting that the time-base may be too short.

Note that only one metrically syncopated moment can happen following a
given note onset; subsequent syncopated moments require the intervention
of another note onset. By way of example, a note occurring immediately
prior to an absent major downbeat, will not also cause syncopated
moments to arise for other beats within a measure containing only rests.
In short, two metrically syncopated moments can't occur without some
note onset intervening.

It is recommended that output files produced using the **synco** command
should be given names with the distinguishing \`.syn' extension.

--------------

OPTIONS
~~~~~~~

The **synco** command provides the following options:

    +----------+---------------------------------------------------------+
    | **-e**   | echo the input in the output                            |
    +----------+---------------------------------------------------------+
    | **-h**   | displays a help screen summarizing the command syntax   |
    +----------+---------------------------------------------------------+

Options are specified in the command line.

If the **-e** option is invoked, the output will echo all of the input
spines along with the ``**synco`` output.

--------------

EXAMPLES
~~~~~~~~

The following two examples illustrate the use of **synco.** In both
examples, the left-most spines represent the input, and the right-most
spine (labelled ``**synco``) represents the corresponding output.

The first example shows the minimum input of a single ``**pitch`` input
plus the metric position information (``**metpos``). The meter signature
is 2/4 and the time-base is an eighth duration. (See the `**timebase
(4)** command.) Hence there are 4 data records per measure. The first
beat in each measure is assigned the metric position "1"; the second
beat is assigned the metric position "2"; and the second half of each
beat is assigned the metric position "3". Zero values in the ``**synco``
spine indicate the absence of any syncopation. In measure 3, a single
syncopated moment happens at beat 2. The output was produced using the
simple command: ``synco inputfile``. ```` <timebase.html>`__

    !! Example #1
    \*\*pitch
    \*\*metpos
    \*\*synco
    \*M2/4
    \*M2/4
    \*
    \*tb8
    \*tb8
    \*tb8
    =1
    =1
    =1
    r
    1
    0
    .
    3
    0
    r
    2
    0
    A4
    3
    0
    =2
    =2
    =2
    G4
    1
    0
    .
    3
    0
    B4
    2
    0
    r
    3
    0
    =3
    =3
    =3
    C5
    1
    0
    C5
    3
    0
    .
    2
    0.41
    B4
    3
    0
    =4
    =4
    =4
    \*-
    \*-
    \*-

In the following example, two metrically syncopated moments are evident.
Notice that the rhythmic information for the two ``**kern`` spines is
amalgamated, and that the non-pitch spine (``**foo``) has no affect on
the processing. ````

    !! Example #2
    \*\*foo
    \*\*kern
    \*\*metpos
    \*\*kern
    \*\*synco
    \*
    \*M2/4
    \*M2/4
    \*M2/4
    \*
    \*
    \*tb8
    \*tb8
    \*tb8
    \*tb8
    A
    =1
    =1
    =1
    =1
    A
    4r
    1
    4r
    0
    A
    .
    4
    .
    0
    A
    .
    3
    .
    0
    A
    .
    4
    .
    0
    A
    8r
    2
    8r
    0
    A
    .
    4
    .
    0
    A
    [8a
    3
    [8a
    0
    A
    .
    4
    .
    0
    A
    =2
    =2
    =2
    =2
    A
    4a]
    1
    8a]
    1.10
    A
    .
    4
    .
    0
    A
    .
    3
    8a
    0
    A
    .
    4
    .
    0
    A
    8b
    2
    8r
    0
    A
    .
    4
    .
    0
    A
    8r
    3
    8b
    0
    A
    .
    4
    .
    0
    A
    =3
    =3
    =3
    =3
    A
    8cc
    1
    8cc
    0
    A
    .
    4
    .
    0
    A
    4.cc
    3
    4cc
    0
    A
    .
    4
    .
    0
    A
    .
    2
    .
    0.41
    A
    .
    4
    .
    0
    A
    .
    3
    8b
    0
    A
    .
    4
    .
    0
    A
    =4
    =4
    =4
    =4
    \*-
    \*-
    \*-
    \*-
    \*-

--------------

PORTABILITY
~~~~~~~~~~~

DOS 2.0 and up, with the MKS Toolkit. OS/2 with the MKS Toolkit. UNIX
systems supporting the *Korn* shell or *Bourne* shell command
interpreters, and revised *awk* (1985).

--------------

SEE ALSO
~~~~~~~~

``  metpos (4), **synco (2),  timebase (4),  urrhythm (4)``

--------------

REFERENCES
~~~~~~~~~~

Longuet-Higgins, H. C., & Lee, C. S. "The perception of musical
rhythms," *Perception,* Vol. 11 (1982) pp. 115-128.

--------------

| 

-  `**Pertinent description in the Humdrum User
   Guide** <../guide23.html#Synco>`__
-  `**Index to Humdrum Commands** <../commands.toc.html>`__
-  `**Table for Contents for Humdrum User Guide** <../guide.toc.html>`__

| 

.. | | image:: /Humdrum/HumdrumIcon.gif
.. |Humdrum | image:: /Humdrum/HumdrumHeader.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
.. | | image:: /Humdrum/HumdrumIcon.gif
.. | | image:: /Humdrum/HumdrumSpacer.gif
