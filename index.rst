==============================================
Oyster River Protocol For Transcriptome Assembly
==============================================

0. Description:

    The OR Protocol descripton goes here...

### Contact Information for Professor Matthew MacManes

    - Email (preferred): Matthew.MacManes@unh.edu
    - Twitter (preferred): @macmanes
    - Phone (discouraged): 603-862-4052
    - Office (I'm hiding under my desk): 189 Rudman Hall

### AWS Setup Instructions: :doc:`aws_setup`

2. Archive Reads

::

  gzip *fastq

3. Initial Quality Check

::

  SolexaQA.pl ../right.fq
  

4. Error Correct

::

  perl run_rcorrector.pl -k 31 -t 30 \
  -1 ../reads/file_1.fastq \
  -2 ../reads/file_2.fastq

5. Assemble

::

  Trinity --seqType fq --max_memory 40G --trimmomatic --CPU 30\
  --left ../reads/file_1.cor.fastq --right ../reads/file_1.cor.fastq \
  --quality_trimming_params "ILLUMINACLIP:/home/ubuntu/trinityrnaseq/trinity-plugins/Trimmomatic/adapters/TruSeq3-PE-2.fa:2:40:15 LEADING:2   TRAILING:2 MINLEN:25"

6. Quality Check

7. Filter

8. Report

