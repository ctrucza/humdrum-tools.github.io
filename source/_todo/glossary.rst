

Glossary of Humdrum Terminology
[ ` A `_ | ` B `_ | ` C `_ | ` D `_ | ` E `_ | ` F `_ | ` G `_ | ` H `_ | ` I
`_ | ` J `_ | ` K `_ | ` L `_ | ` M `_ | ` N `_ | ` O `_ | ` P `_ | ` Q `_ |
` R `_ | ` S `_ | ` T `_ | ` U `_ | ` V `_ | ` W `_ | ` X `_ | ` Y `_ | ` Z
`_ ]

--------

**Comment** Either a `global`_ or `local`_ comment. Any `record`_ beginning
with an exclamation mark (``**!**``). `**Further information.**

**Data record** Any record that is not a `comment`_ or an `interpretation`_.
Must contain the same number of tokens as the number of current `spines`_.
`**Further information.**

**Data token** A "word" of data found in a `data record`_. A token consists
of any sequence of consecutive characters -- with the exception of the tab
character (which is used to separate successive tokens). Another exception is
the isolated period character which indicates a `null token. `**Further
information.**

**Exclusive interpretation** Any record beginning with one or more asterisks
(``*****``), where at least one `spine`_ begins with two asterisks.

**Global comment** Any record beginning with two exclamation marks
(``**!!**``).

**Interpretation** Either an `exclusive`_ or `tandem interpretation`_. Any
record beginning with an asterisk (``*****``). `**Further information.**

**Local comment** Any `record`_ beginning with one and only one exclamation
mark (``**!**``). Every `spine`_ in that record must also begin with an
exclamation mark.

**Null comment** A `comment record`_ containing no commentary; only the
appropriate exclamation mark(s) are present.

**Null data record** A `data record`_ consisting only of `null tokens`_.

**Null interpretation** An `interpretation`_ for a given spine or spines
consisting of just the interpretation signifier (i.e., a single asterisk).

**Null token** The period (``**.**``) either alone on a single record or
separated from other characters by a tab. Appears only in `data records`_.
`**Further information.**

**Path Indicator** One of five special `tandem interpretations`_ **``*+``**,
**``*-``**, **``*v``**, **``*^``**, and **``*x``**, found only in tandem
interpretation records. `**Further information.**

**Record** A line of text in a Humdrum file that ends with the new-line
character.

**Reference Record** A type of `**global comment**`_ that is used to store
formal bibliographic information, such as composer's name, title of work,
opus number, etc. Reference records begin with a three- or four-letter
special code used to indicate the type of information present. For example,
the code !!!AIN: is used to formally define the instrumentation used in the
work. Over 100 reference codes are pre-defined in Humdrum. `**Further
information.** `**Complete listing.**

**Spine** A column-like "path" of information -- including `data records`_,
`local comments`_, and `interpretations`_.

**Spine path indicator** Same as `path indicator`_.

**Tandem interpretation** Any record beginning with a single asterisk
(``*****``) where none of the `spines`_ begin with two asterisks.

**Terminator** One of five `path indicators`_ used to indicate the end of a
`spine`_. Indicated by an asterisk followed by a minus sign (``***-**``).

::






--------

(C) Copyright 1999 David Huron

.. _ A : #A
.. _ B : #B
.. _ C : #C
.. _ D : #D
.. _ E : #E
.. _ F : #F
.. _ G : #G
.. _ H : #H
.. _ I : #I
.. _ J : #J
.. _ K : #K
.. _ L : #L
.. _ M : #M
.. _ N : #N
.. _ O : #O
.. _ P : #P
.. _ Q : #Q
.. _ R : #R
.. _ S : #S
.. _ T : #T
.. _ U : #U
.. _ V : #V
.. _ W : #W
.. _ X : #X
.. _ Y : #Y
.. _ Z : #Z
.. _global: #Global Comment
.. _local: #Local Comment
.. _record: #Record
.. _comment: #Comment
.. _interpretation: #Interpretation
.. _spines: #Spine
.. _data record: #Data
.. _exclusive: #Exclusive Interpretation
.. _tandem interpretation: #Tandem Interpretation
.. _data record: #Data Record
.. _null tokens: #Null Token
.. _data records: #Data
     Record
.. _global comment: #global comment
.. _path indicator: #Path Indicator
