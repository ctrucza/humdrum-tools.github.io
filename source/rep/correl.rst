================================
Representation: \*\*correl
================================

| 

Humdrum Representation for Statistical Correlations
===================================================

REPRESENTATION
~~~~~~~~~~~~~~

    **\*\*correl** -- statistical correlation representation

DESCRIPTION
~~~~~~~~~~~

    The **\*\*correl** representation is used to characterize the degree
    of statistical correlation for successive moments. Data tokens for
    **\*\*correl** decimal values ranging between -1 (perfect negative
    correlation) and 1 (perfect positive correlation).

FILE TYPE
~~~~~~~~~

    It is recommended that files containing predominantly ``**correl``
    data should be given names with the distinguishing \`.cor'
    extension.

SIGNIFIERS
~~~~~~~~~~

    The following table summarizes the **\*\*correl** mappings of
    signifiers and signifieds.

        +-------+---------------------------------------------------------+
        | 0-9   | correlation values specified as integer or real value   |
        +-------+---------------------------------------------------------+
        | .     | decimal point; null token                               |
        +-------+---------------------------------------------------------+
        | +     | plus sign (optional)                                    |
        +-------+---------------------------------------------------------+
        | -     | minus sign                                              |
        +-------+---------------------------------------------------------+

        *Summary of **\*\*correl** Signifiers*

EXAMPLES
~~~~~~~~

    A sample document is given below:

        ````
        +--------------+
        | \*\*correl   |
        +--------------+
        | \*C:         |
        +--------------+
        | \*M4/4       |
        +--------------+
        | .            |
        +--------------+
        | 0.0          |
        +--------------+
        | +0.3037      |
        +--------------+
        | +.52         |
        +--------------+
        | 0.6          |
        +--------------+
        | 0.211        |
        +--------------+
        | .            |
        +--------------+
        | -.241        |
        +--------------+
        | -0.17        |
        +--------------+
        | -1           |
        +--------------+
        | 0.221        |
        +--------------+
        | .            |
        +--------------+
        | \*-          |
        +--------------+

    Notice that melodic accent values can be either real or integer
    values. Rests are represented by the single letter \`r'.

PERTINENT COMMANDS
~~~~~~~~~~~~~~~~~~

    The following Humdrum command produces **\*\*correl** data as
    output:
    `**correl** <../commands/correl.html>`__
    calculate numerical correlation between two spines

TANDEM INTERPRETATIONS
~~~~~~~~~~~~~~~~~~~~~~

    The following tandem interpretations can be used in conjunction with
    **\*\*correl:**

        +--------------------+----------------+
        | meter signatures   | ``*M6/8``      |
        +--------------------+----------------+
        | key signatures     | ``*k[f#c#]``   |
        +--------------------+----------------+
        | key                | ``*c#:``       |
        +--------------------+----------------+

        *Tandem interpretations for **\*\*correl***

SEE ALSO
~~~~~~~~

    `` barlines, correl, **simil, simil``

--------------

| 

-  `**Pertinent description in the Humdrum User
   Guide** <../guide25.html#The_correl_Command>`__
