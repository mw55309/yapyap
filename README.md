# yapyap
YapYap: pedantic classification of read fates in BWA MEM

Read alignment is far more complicated than you might think and quite frankly samtools flagstat doesn't cut it.

Stream the SAM output of bwa mem directly through yapyap to create a report, written to STDERR, that shows in great detail how many reads fall in each of ~50 categories of read fates.

Think about it, each read in a pair can have:

* 0 alignments
* 1 global alignment
* 1 split alignment
* Multiple alignments all global
* Multiple alignments, mixed global and split 
* Multiple alignments, all split

Mix in whether the alignments are flagged as primary and properly paired or not, and you can see that every fragment has 100s of possible fates.

## Usage

### With bwa 

STDOUT will be unaltered SAM, STDERR will be yapyap report
```bash
bwa mem -M reference.fa reads_1.fq reads_2.fq | yapyap 
```

### With samtools
STDOUT will be unaltered SAM, STDERR will be yapyap report
```bash
samtools view aligned.bam | yapyap
```

