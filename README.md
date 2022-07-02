# Searching BGCs of Thiomargarita magnifica

Introduction

Candidatus Thiomargarita Magnifica has recently been described as the world's largest bacterium with an average length of one centimeter and being visible to the naked eye leads us to rethink everything we thought we knew about bacteria.

Genetic analysis of Ca. T. magnifica reveals high levels of elongation genes that together with the loss of key genes in cell division may explain its length.
 
 _FIXME_
 
Obtaining genomic Data

We download reads of Candidatus Theomargarita magnifica from the article:

https://www.science.org/doi/10.1126/science.abb3634

Accesion numbers from SRA files
~~~
 SRR18724479
 SRR18723883
 SRR18723969
 SRR18723970 
 SRR18725150
 ~~~
 {: .source}

We choose one and use SRAtoolkit for download the SRA file:

~~~
srapath SRR18724479
~~~
{: .language-bash}

~~~
https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18724479/SRR18724479
~~~
{: .output}

~~~
wget -P Data https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18724479/SRR18724479
~~~
{: .language-bash}

~~~
--2022-07-01 13:09:20--  https://sra-pub-run-odp.s3.amazonaws.com/sra/SRR18724479/SRR18724479
Resolving sra-pub-run-odp.s3.amazonaws.com (sra-pub-run-odp.s3.amazonaws.com)... 54.231.128.233
Connecting to sra-pub-run-odp.s3.amazonaws.com (sra-pub-run-odp.s3.amazonaws.com)|54.231.128.233|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1059211832 (1010M) [binary/octet-stream]
Saving to: ‘Data/SRR18724479’

SRR18724479                                100%[========================================================================================>]   1010M  8.35MB/s    in 85s

2022-07-01 13:10:46 (11.9 MB/s) - ‘Data/SRR18724479’ saved [1059211832/1059211832]
~~~
{: .output}

Then we depackage the fastq files with fastq-dump:

~~~
cd Data
fastq-dump --gzip --skip-technical --readids --dumpbase --split-files --clip SRR18724479
~~~
{: .language-bash}

~~~
ls 
SRR18724479_1.fastq  SRR18724479_2.fastq
~~~
{: .output}

_1.fastq contains all forward reads and _2.fastq contains all reverse reads in a fastq file.

Then we need to assemble the reads with SPAdes:

spades.py [options] -o <output_dir>

Then we use our assembly for search the BGCs on antiSMASH:

https://antismash.secondarymetabolites.org/#!/start

We use the default parameters on the online platform







