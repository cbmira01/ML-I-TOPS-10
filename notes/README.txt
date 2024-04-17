
    ML/I -- AN IMPLEMENTATION OF THE ML/I MACRO PROCESSOR FOR TOPS-10
            by Calvin Miracle, Louisville KY

        ML/I is a macro processor. According to the Wiki article, "A macro
        processor is a program that copies a stream of text from one place to
        another, making a systematic set of replacements as it does so. Macro
        processors are often embedded in other programs, such as assemblers and
        compilers. Sometimes they are standalone programs that can be used to
        process any kind of text [GPMP]."

        A macro processor can be used as a program development tool to textually
        "extend" a given programming language. Other examples of macro processing
        can be found in the C preprocessor, in assembler programs, and in free-
        standing tools such as m4 for Unix.

        The ML/I macro processor was first developed by Peter Brown for a doctorate
        dissertation at the University of Cambridge in 1966. In addition, it was
        intended to be an example of the UNCOL concept of software portability.
        Over the years, ML/I was eventually ported to many different platforms.
        ML/I is currently curated by Bob Eager, and much more information about
        ML/I is available at the ML/I website [MWEB].

        This implementation of ML/I on TOPS-10 is based on version AJB, the latest
        LOWL version of ML/I. AJB is not the latest possible version, since
        development of ML/I in recent years has continued in the C language.


    BUILD AND TEST

        Before use, ML/I must be built on your TOPS-10 system. The instructions
        below assume the presence of the Macro-10 assembler and sufficient
        privileges to compile and run programs.

        To build the project, issue the MIC command
                .DO BUILD.MIC

        The main executable resulting will be
                ML1.exe

        which can eventually be migrated to the SYS: directory. Other programs,
        described below, are also built to validate ML/I's machine-dependent
        logic and test the implementation macros.

        To advance further into ML/I, consult [MTUT], [MSIG] and [MMAN],
        located on the ML/I website [MWEB].
   
        A complete test harness for ML/I is available in the build directory.


    NOTES ON THIS IMPLEMENTATION

        ML/I is orignally written in a portable code, LOWL, which can be readily
        converted into PDP-10 code using macro facilities of TOPS-10's MACRO-10
        assembler. 

        Please note that this implementation bears no relation to the ML/I
        implementation for TOPS-10 by John Forecast of the University of Essex. 
        I've searched for publicly-available code of Forecast's ML/I implementation,
        but with no luck. Some of its documentation survives at the ML/I website
        [MWEB], but that documentation is not applicable to this implementation.

        Following are the current implementation decisions [LOWL passim]:
            * Arithmetic, logical and compare ops are all performed as 
                half-word (18-bit).
            * No LOWL operation will clobber LOWL registers as an 
                unintended side effect.
            * Redundant register loads are not performed.
            * Register stores will always preserve the LOWL A register.
            * EQU declarations will always create a new memory location, 
                not reuse an existing one.
            * The LOWL A, B and C registers are implemented as 
                separate machine-dependent registers.
            * The LAA definition covers covers both forms of the LAA operation.
            * LOWL-code locations are not altered in machine-dependent logic 
                (eg, MEVAL in MDCONV).
            * Characters are represented as 7-bit ASCII, right-justified 
                in a 36 bit fullword:
                    0 0000000 0000000 0000000 0000000 xxxxxxx
                    0   NUL     NUL     NUL     NUL     char
            * Character strings are represented as contiguous fullwords.
            * The ML/I hash function used is the 'simple' one 
                mentioned in [LSUP 2.5].


    WORKS CONSULTED

        [GPMP] "General-purpose macro processor."
            Wikipedia, The Free Encyclopedia. Wikimedia Foundation, Inc.
            14 August 2013. Web. 14 September 2013.

        [DMRM] "DECsystem-10 Macro Assembler Reference Manual", DEC part
            number AA-C780C-TB. 1967, 1978 Digital Equipment Corporation.

        [DPRM] "DECsystem-10 Processor Reference Manual", DEC part number
            AA-H391A-TK. 1968, 1971, 1974, 1978, 1982 Digital Equipment
            Corporation.

        Note: many other TOPS-10 manuals can be found at
        http://bitsavers.trailing-edge.com/pdf/dec/pdp10/TOPS10_softwareNotebooks/

        [Gor1] Gorin, R. E. "Introduction to DECsystem-10 Assembly Language
            Programming", Computer Science Department, Stanford University.
            20 July 1985 Ralph E. Gorin.
            http://bitsavers.informatik.uni-stuttgart.de/pdf/stanford/lots/
                Introduction_To_DECSystem-10_Assembly_Lang_Pgmg_Jul85.pdf

        [Gor2] Gorin, R. E. "Introduction to DECSYSTEM–20 Assembly Language
            Programming". 1995, 1999, 2000 Ralph E. Gorin.

        [DaCr] "DECSYSTEM-20 Assembly Language Guide",
            Edited by Frank da Cruz and Chris Ryland,
            Columbia University Center for Computing Activities,
            New York, New York 10027, 3 July 1980.
            ftp://ftp.columbia.edu/kermit/dec20/assembler-guide.txt

        [MWEB] The ML/I website: http://www.ml1.org.uk
            This site is copyright 2011 Bob Eager.
            LOWL implementation manuals and testing code, as well as all ML/I
            manuals and source code, can be found at this site.

        [LOWL] "Implementing software using the LOWL language -- Fourth Edition",
            Copyright 1972,1974,2004 P.J. Brown, R.D. Eager.
            http://www.ml1.org.uk/htmldoc/lowlmap.html
            This manual describes the DLIMP process and core LOWL.

        [LSUP] "Implementing software using the LOWL language
                -- Supplement 3: ML/I -- Second Edition",
            Copyright 1972,2004 P.J. Brown, R.D. Eager.
            http://www.ml1.org.uk/htmldoc/lowlml1.html
            This manual describes specific extensions to core LOWL for ML/I.

        [MTUT] "An ML/I tutorial", Copyright 2004 R.D. Eager.
            http://www.ml1.org.uk/htmldoc/ml1tut.html

        [MSIG] "A simple introductory guide to ML/I",
            Copyright 1970,1982,1998,2004 R.D. Eager, P.J. Brown.
            http://www.ml1.org.uk/htmldoc/ml1sig.html

        [MMAN] "ML/I User's Manual -- Sixth Edition",
            Copyright 1966 thru 2004 P.J. Brown, R.D. Eager.
            http://www.ml1.org.uk/htmldoc/ml1user.html


    RECOGNITION AND THANKS

        Recognition and thanks are due Bob Eager for preserving a part of early
        computing history, ML/I. Please visit his web site at [MWEB].

        Recognition and thanks are due Bob Supnik and his many contributors for
        the historical computer simulator program SIMH, copyright (c) 2001-2008,
        Robert M Supnik, http://simh.trailing-edge.com/

        Recognition and thanks are due Al Kossow and his many contributors for
        the BitSavers trove of historical computer manuals located at
        http://bitsavers.trailing-edge.com/

        Recognition and thanks are due Tim Shoppa and his many contributors for
        the extensive archive of PDP-10 software located at
        http://pdp-10.trailing-edge.com/

