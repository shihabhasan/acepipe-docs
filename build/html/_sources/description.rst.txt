============
Description
============

The `ACE`_ pipeline (ACEPipe) currently works with the following genes - SSU (16S/18S) rRNA and fungal ITS.
It consists of a quality control module, amplicon clustering with `QIIME2`_, and taxonomy assignment on representative
OTU sequences using `BLAST`_. The pipeline can run both on the forward (R1) reads and both (R1 & R2) reads.

.. _ACE: http://ecogenomic.org
.. _QIIME2: http://qiime2.org
.. _BLAST: http://blast.ncbi.nlm.nih.gov/Blast.cgi



Quality Control
^^^^^^^^^^^^^^^

All fastq files are processed with `fastqc`_ and the reports made available.
All fastq files are then trimmed to remove primer sequence with `Cutadapt`_,
and quality trimmed to remove poor quality sequence using a sliding window
of 4 bases with an average base quality above 15 using the software `Trimmomatic`_.
All reads are then hard trimmed to 250 bases, and any with less than 250 bases excluded.


.. _fastqc: http://www.bioinformatics.babraham.ac.uk/projects/fastqc/
.. _Cutadapt: http://cutadapt.readthedocs.io/en/stable/index.html
.. _Trimmomatic: http://www.usadellab.org/cms/?page=trimmomatic|Trimmomatic



Taxonomy
^^^^^^^^

Fasta files are processed using `QIIME2`_'s workflow with default parameters and taxonomy assignment.
Representative features (OTU) sequences are then BLASTed against the reference database (`Silva`_ and `UNITE`_).
The main analysis output is an OTU table comprising the taxonomic classification of the best database match
and a representative sequence for each OTU.

.. _QIIME2: http://qiime2.org
.. _Silva: http://www.arb-silva.de
.. _UNITE: http://unite.ut.ee


Result
^^^^^^

We provide the fastqc reports, OTU tables (QIIME2 BIOM file, a filtered raw count table,
and a filtered fraction table), processing statistics file and associated bar plot, and
a file listing software versions from the QIIME2 pipeline.

Kind Regards, The ACE Team