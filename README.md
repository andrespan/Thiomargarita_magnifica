# Searching BGCs of Thiomargarita magnifica

Introduction
 
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
fastq-dump --gzip --skip-technical --readids --dumpbase --split-files --clip SRR18724479
~~~
{: .language-bash}


Then we need to assemble the reads with SPAdes:

spades.py [options] -o <output_dir>

