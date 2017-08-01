|CyVerse logo|_

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_

Filter and Trim High-throughput Sequencing Reads with Trimmomatic
==================================================================

Goal
-----

A high-throughput sequencing run generates large files containing perhaps as many
as several 10's of millions of individual sequencing reads. After assessment of
sequencing quality using a software such as `FastQC <https://cyverse-fastqc-quickstart.readthedocs-hosted.com/en/latest/>`_,
filtering and trimming steps can remove populations of low quality reads, remove
sequenicng adaptors, and trim low-quality regions of individual reads. `Trimmomatic <http://www.usadellab.org/cms/?page=trimmomatic>`_
is a popular software that perform several manipulations to prepare reads for
downstream analysis.

----

Prerequisites
-------------

Downloads, access, and services
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

*In order to complete this tutorial you will need access to the following services/software*

..
	#### Comment: Modify the table below as needed ####

.. list-table::
    :header-rows: 1

    * - Prerequisite
      - Preparation/Notes
      - Link/Download
    * - CyVerse account
      - You will need a CyVerse account to complete this exercise
      - `Register <https://user.cyverse.org/>`_

Platform(s)
~~~~~~~~~~~

*We will use the following CyVerse platform(s):*

..
	#### Comment: Modify the table below as needed ####

.. list-table::
    :header-rows: 1

    * - Platform
      - Interface
      - Link
      - Platform Documentation
      - Learning Center Documentation
    * - Discovery Environment
      - Web/Point-and-click
      - `Discovery Environment <https://de.cyverse.org/de/>`_
      - `DE Manual <https://wiki.cyverse.org/wiki/display/DEmanual/Table+of+Contents>`_
      - `Guide <https://learning.cyverse.org/projects/discovery-environment-guide/en/latest/>`__

Input and example data
~~~~~~~~~~~~~~~~~~~~~~

*In order to complete this quickstart you will need to have the following inputs prepared*

.. list-table::
    :header-rows: 1

    * - Input File(s)
      - Format
      - Preparation/Notes
      - Example Data
    * - High-throughput sequencing reads
      - compressed FASTQ (.fq.gz or .fastq.gz - compressed)
      - No pre-processing of these reads is necessary.
      - See `Trimmomatic inputs <http://datacommons.cyverse.org/browse/iplant/home/shared/cyverse_training/quickstarts/trimmomatic/00_input>`_

------

*Get started: Filter, Trim, and Process High-throughput Sequenicng Reads with Trimmomatic*
-------------------------------------------------------------------------------------------

Several of the most popular options for Trimmomatic will be shown here. For all
of the options, and additional details including the ordering of cleaning/
filtering steps, see the `full Trimmomatic documentation <http://www.usadellab.org/cms/?page=trimmomatic>`_.

  1. Login to the `Discovery Environment`_
  2. Click on the 'Data' panel. In the desired directory, click the 'File' menu,
     select 'Create' and then 'New Plain Text File'. Create a **Trimmomatic Settings**
     file by entering the desired Trimmomatic functions (one per line) to set the
     options used by the Trimmomatic program. Click 'Save' and save the file with
     a '.txt' extenstion in the desired directory. See an `example Trimmomatic Settings <http://datacommons.cyverse.org/browse/iplant/home/shared/cyverse_training/quickstarts/trimmomatic/00_input>`_
     file.

	 .. hint::

		 Trimmomatic has several individual functions (see `full Trimmomatic documentation`_).
		 To specifiy a function and its parameters, you will usually give the function name, followed
		 by a colon separated set of parameters. Commonly used functions include:

            - **"SLIDINGWINDOW:<windowSize>:<requiredQuality>"**: Perform a sliding window trimming, cutting once
              the average quality within the window falls below a threshold
            - **"LEADING:<quality>"**:Cut bases off the start of a read, if below a threshold
              quality
            - **"TRAILING:<quality>"**: Cut bases off the end of a read, if below a threshold
              quality
            - **"MINLEN:<length>"**: Drop the read if it is below a specified length


            Additionally, you can provide Trimmomatic with a file containing a list
            of adaptor sequences to be trimmed.


            - **"ILLUMINACLIP:<fastaWithAdaptersEtc>:<seed mismatches>:<palindrome clip threshold>:<simple clip threshold>"**
              : Cut adapter and other illumina-specific sequences from the read.

  3. Click 'Apps' and open the Trimmomatic App `Trimmomatic-programmable-0.33 <https://de.cyverse.org/de/?type=apps&app-id=4c5c7480-4b0b-11e7-9b36-008cfa5ae621&system-id=de>`_.
     Name your analysis, and if desired enter commands and select or adjust the
     output folder.
  4. Under settings, select 'paaired-ended' or 'single-ended'. Under 'Enter a
     folder of sequencing files:' select a folder containing one or more sequencing
     files (.fq.gz or .fastq.gz).
  5. Under 'Trimmer settings file in text format' browse to the location of the
     Trimmomatic settings file you created in step 2.
  6. If you are using the 'ILLUMINACLIP' function, browse to the location of the
     fasta file containing Illumina adaptor sequences. (You may find some
     relavant Illumina adaptors `here <https://github.com/timflutre/trimmomatic/tree/master/adapters>`_ ).
  7. Click 'Launch Analysis' to launch the analysis. Click the 'Analysis' button
     to view job status and obtain results.

----

*Summary*
~~~~~~~~~~~

Once completed, the Discovery Environment Trimmomatic App will return the trimmed
reads:

**Paired End Outputs - 4 outputs for each pair (R1/R2) of reads:**

.. list-table::
    :header-rows: 1

    * - Output
      - Description
      - Example
    * - - trmPr_readname_R1.fq/.fastq (output_forward_paired)
        - trmPr_readname_R2.fq/.fastq (output_reverse_paired)
        - trmS_readname_R1.fq/.fastq (output_forward_unpaired)
        - trmS_readname_R2.fq/.fastq (output_reverse_unpaired)
      - Every pair of sequence reads will generate a set of paired reads that
        have been trimmed according to the functions specified in the provided
        trimmomatics settings file.
      - See `Example outputs <http://datacommons.cyverse.org/browse/iplant/home/shared/cyverse_training/quickstarts/trimmomatic/01_output>`_

**Single End Outputs - 2 outputs for each pair (R1/R2) of reads:**

.. list-table::
    :header-rows: 1

    * - Output
      - Description
      - Example
    * - trimreadname_R1.fq/.fastq
      - Every sequence will generate a trimmed file as well as a file of the
      - None provided.
..
    Summary

**Next Steps:**

To confirm that Trimmomatic processing has achived the desired results, you may
wish to evaluate the reads using `FastQC`_.


-----

Additional information, help
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

..
    Short description and links to any reading materials

Search for an answer: `CyVerse Learning Center <http://learning.cyverse.org>`_ or `CyVerse Wiki <https://wiki.cyverse.org>`_

Post your question to the user forum:
`Ask CyVerse <http://ask.iplantcollaborative.org/questions>`_

----

**Fix or improve this documentation**

- On Github: `Repo link <https://github.com/CyVerse-learning-materials/trimmomatic_quickstart>`_
- Send feedback: `Tutorials@CyVerse.org <Tutorials@CyVerse.org>`_

----

|Home_Icon|_
`Learning Center Home <http://learning.cyverse.org/>`_

.. |CyVerse logo| image:: ./img/cyverse_rgb.png
    :width: 500
    :height: 100
.. _CyVerse logo: http://learning.cyverse.org/
.. |Home_Icon| image:: ./img/homeicon.png
    :width: 25
    :height: 25
.. _Home_Icon: http://learning.cyverse.org/
