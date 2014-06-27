================================
Representation: \*\*diss
================================

| 

Humdrum Representation for Dissonance
=====================================

REPRESENTATION
~~~~~~~~~~~~~~

    **\*\*diss** -- sensory dissonance representation

DESCRIPTION
~~~~~~~~~~~

    The **\*\*diss** representation is used to characterize the degree
    of sensory dissonance for successive acoustic moments. Two types of
    tokens are recognized by **\*\*diss:** dissonance-tokens and
    barlines. Dissonance-tokens encode integer values greater than or
    equal to zero. Larger values represent higher sensory dissonance.
    Dissonance values reflect the measurement method devised by Kameoka
    and Kuriyagawa (see `**REFERENCES** <#REFERENCES>`__).
    Barlines are represented using the "common system" for barlines --
    see `**barlines** <barlines.rep.html>`__.

FILE TYPE
~~~~~~~~~

    It is recommended that files containing predominantly ``**diss``
    data should be given names with the distinguishing \`.dis'
    extension.

SIGNIFIERS
~~~~~~~~~~

    The following table summarizes the **\*\*diss** mappings of
    signifiers and signifieds.

        +-------+--------------------------------------------+
        | 0-9   | dissonance values specified as integers;   |
        +-------+--------------------------------------------+
        |       | measure numbers                            |
        +-------+--------------------------------------------+
        | =     | barline                                    |
        +-------+--------------------------------------------+
        | ==    | double barline                             |
        +-------+--------------------------------------------+
        | =;    | barline with pause sign                    |
        +-------+--------------------------------------------+

        *Summary of **\*\*diss** Signifiers*

EXAMPLES
~~~~~~~~

    A sample document is given below:

        ````
        +------------+
        | \*\*diss   |
        +------------+
        | \*C:       |
        +------------+
        | \*M4/4     |
        +------------+
        | =1         |
        +------------+
        | 65         |
        +------------+
        | 84         |
        +------------+
        | 152        |
        +------------+
        | 160        |
        +------------+
        | =2         |
        +------------+
        | 211        |
        +------------+
        | 1017       |
        +------------+
        | 841        |
        +------------+
        | 1221       |
        +------------+
        | =3         |
        +------------+
        | \*-        |
        +------------+

    Note that rests are not represented in the **\*\*diss** scheme.

PERTINENT COMMANDS
~~~~~~~~~~~~~~~~~~

    The following Humdrum command produces **\*\*diss** data as output:

        `**diss** <../commands/diss.html>`__
        calculate the degree of sensory dissonance for successive
        spectra

TANDEM INTERPRETATIONS
~~~~~~~~~~~~~~~~~~~~~~

    The following tandem interpretations can be used in conjunction with
    **\*\*diss**:

        +--------------------+----------------+
        | meter signatures   | ``*M6/8``      |
        +--------------------+----------------+
        | key signatures     | ``*k[f#c#]``   |
        +--------------------+----------------+
        | key                | ``*c#:``       |
        +--------------------+----------------+

        *Tandem interpretations for **\*\*diss***

SEE ALSO
~~~~~~~~

    `` barlines, diss, **spect, spect``

REFERENCES
~~~~~~~~~~

    Kameoka, A. & Kuriyagawa, M. "Consonance theory, part I: Consonance
    of dyads." *Journal of the Acoustical Society of America,* Vol. 45,
    No. 6 (1969a) pp.1451-1459.
    Kameoka, A. & Kuriyagawa, M. "Consonance theory, part II: Consonance
    of complex tones and its calculation method." *Journal of the
    Acoustical Society of America,* Vol. 45, No. 6 (1969b) pp.1460-1469.

--------------

