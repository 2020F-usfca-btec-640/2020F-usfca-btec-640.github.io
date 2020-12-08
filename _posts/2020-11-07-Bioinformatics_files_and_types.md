---
layout: post
title:  "Bioinformatic files: types and formats"
date:   2020-11-06 12:54:04 -0700
categories: blogpost
---
# Introduction
In bioinformatics there are many different file types to store information from sequencing and genomics work. The most common file types are generally FASTA and FASTQ. But there are a lot of other semi-common file types as well like SAM, BAM, VCF as well as countless other self made file types for individual purposes.

In this post I will cover four file types that are covered in the BTEC 640 course. The first two are the most common which are FASTA and FASTQ. The second two are slightly less common but still worked with frequently which are SAM and VCF.

# FASTA

FASTA stands for FAST-All. It was built off an earlier FASTP format that was designed around protein sequences and then expanded to encompass any kind of sequence format. Hence why the descriptor "All".  
```
>XR_002086427.1 Candida albicans SC5314 uncharacterized ncRNA (SCR1), ncRNA
TGGCTGTGATGGCTTTTAGCGGAAGCGCGCTGTTCGCGTACCTGCTGTTTGTTGAAAATTTAAGAGCAAAGTGTCCGGCTCGATCCCTGCGAATTGAATTCTGAACGCTAGAGTAATCAGTGTCTTTCAAGTTCTGGTAATGTTTAGCATAACCACTGGAGGGAAGCAATTCAGCACAGTAATGCTAATCGTGGTGGAGGCGAATCCGGATGGCACCTTGTTTGTTGATAAATAGTGCGGTATCTAGTGTTGCAACTCTATTTTT
```

The main format of a FASTA file is first a **comment line** that starts with '>'.
You can put anything in the comment line as you see fit although typically there is there is species and index information.

The second part is the **sequence line** which is a series of letters that represents the sequence of either a DNA strand, RNA strand, peptide strand, or something similar. Any line that starts after a semicolon ';' will be ignored. Also any of the following symbols in the sequence will also be ignored during processing: '(tab)','(space)','(asterisk)'.

# FASTQ
A FASTQ is similar to a FASTA except it also has indicators for quality scores. The quality scores indicate how reliability the read is for that particular part of the sequence. The 'Q' in this case stands for quality
```
@K00188:208:HFLNGBBXX:3:1101:1428:1508 2:N:0:CTTGTA
ATAATAGGATCCCTTTTCCTGGAGCTGCCTTTAGGTAATGTAGTATCTNATNGACTGNCNCCANANGGCTAAAGT
+
AAAFFJJJJJJJJJJJJJJJJJFJJFJJJJJFJJJJJJJJJJJJJJJJ#FJ#JJJJF#F#FJJ#F#JJJFJJJJJ
```
As with the FASTA format the first part is a **comment line** and a **sequence line**. After that is another **comment line**, or sometimes a blank line, that acts as a break between the sequence reads and the quality scores. This break line is followed by a '+' as opposed to a '>' like the first line.

The last line is a **quality score line** and MUST contain the same number of symbols in this line as the **sequence line**. Each sequencing company has its range of symbols to represent Phred quality score readings for that base.

# SAM
The SAM stands for the **Sequence Alignment Map** and is a text format for storing sequence data in a series of tab delimited ASCII columns.

The primary function of a SAM is to map sequence reads to a reference sequence. It has a **header** and a **body**. The **header** starts with '@' and holds generic information about the SAM file (version information, if the file is sorted or not, information on reference sequences, etc).
```
1:497:R:-272+13M17D24M	113	1	497	37	37M	15	100338662	0	CGGGTCTGACCTGAGGAGAACTGTGCTCCGCCTTCAG	0;==-==9;>>>>>=>>>>>>>>>>>=>>>>>>>>>>	XT:A:U	NM:i:0	SM:i:37	AM:i:0	X0:i:1	X1:i:0	XM:i:0	XO:i:0	XG:i:0	MD:Z:37
19:20389:F:275+18M2D19M	99	1	17644	0	37M	=	17919	314	TATGACTGCTAATAATACCTACACATGTTAGAACCAT	>>>>>>>>>>>>>>>>>>>><<>>><<>>4::>>:<9	RG:Z:UM0098:1	XT:A:R	NM:i:0	SM:i:0	AM:i:0	X0:i:4	X1:i:0	XM:i:0	XO:i:0	XG:i:0	MD:Z:37
19:20389:F:275+18M2D19M	147	1	17919	0	18M2D19M	=	17644	-314	GTAGTACCAACTGTAAGTCCTTATCTTCATACTTTGT	;44999;499<8<8<<<8<<><<<<><7<;<<<>><<	XT:A:R	NM:i:2	SM:i:0	AM:i:0	X0:i:4	X1:i:0	XM:i:0	XO:i:1	XG:i:2	MD:Z:18^CA19
9:21597+10M2I25M:R:-209	83	1	21678	0	8M2I27M	=	21469	-244	CACCACATCACATATACCAAGCCTGGCTGTGTCTTCT	<;9<<5><<<<><<<>><<><>><9>><>>>9>>><>	XT:A:R	NM:i:2	SM:i:0	AM:i:0	X0:i:5	X1:i:0	XM:i:0	XO:i:1	XG:i:2	MD:Z:35
```
The **body** consists of alignment reads which each have 11 parts. Some terminology to also keep in mind is:

**Template**: The DNA fragment that was measured

**Reads**: A template may produce one or more reads. These reads may cover just a subsection of the template.

**Segments**: Each read may produce one or more alignments that will have aligned regions called segments.

![SAM alignment parts](https://bioinformatics.uconn.edu/wp-content/uploads/sites/15/2017/01/format2.png)

1. *QNAME*: Query template NAME. Reads/segments having identical QNAME are regarded to come from the same template. A QNAME ‘*’ indicates the information is unavailable.
2. *FLAG*: Combination of bitwise FLAGs (more information below).
3. *RNAME*: Name of reference sequence. It generally refers to chromosome number.
4. *POS*: Leftmost mapping position of the first matching base in read. It has 1-based indexing. If pos is set as 0, it represents a unmapped read.
5. *MAPQ*: MAPping Quality. It equals −10 log10 Pr{mapping position is wrong}, rounded to the nearest integer. A value 255 indicates that the mapping quality is not available.
6. *CIGAR*: Concise Idiosyncratic Gapped Alignment Report (CIGAR) string. It describes alignment characteristics.
7. *RNEXT*: RNEXT is the name of the chromosome or contig to which the next template in a pair aligns. RNEXT of value ‘=‘ means align to same reference and ‘*’ represent no information available (single end sequencing)
8. *PNEXT*: Position of the primary alignment of the NEXT read in the template. Set as 0 when the information is unavailable. This field equals POS at the primary line of the next read.
9. *TLEN*: Template LENgth. It is set as 0 for single-segment template or when the information is unavailable.
10. *SEQ*: segment SEQuence.
11. *QUAL*: PHRED score values of read. If ‘*’ no values are stored.

# VCF
Variant Calling Format/File. It is a text file that contains a **header** and data lines that constitue a **body**. It stores gene sequence variations.
```
##fileformat=VCFv4.2
##fileDate=20090805
##source=myImputationProgramV3.1
##reference=file:///seq/references/1000GenomesPilot-NCBI36.fasta
##contig=<ID=20,length=62435964,assembly=B36,md5=f126cdf8a6e0c7f379d618ff66beb2da,species="Homo sapiens",taxonomy=x>
##phasing=partial
##INFO=<ID=NS,Number=1,Type=Integer,Description="Number of Samples With Data">
##INFO=<ID=DP,Number=1,Type=Integer,Description="Total Depth">
##INFO=<ID=AF,Number=A,Type=Float,Description="Allele Frequency">
##INFO=<ID=AA,Number=1,Type=String,Description="Ancestral Allele">
##INFO=<ID=DB,Number=0,Type=Flag,Description="dbSNP membership, build 129">
##INFO=<ID=H2,Number=0,Type=Flag,Description="HapMap2 membership">
##FILTER=<ID=q10,Description="Quality below 10">
##FILTER=<ID=s50,Description="Less than 50% of samples have data">
##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">
##FORMAT=<ID=GQ,Number=1,Type=Integer,Description="Genotype Quality">
##FORMAT=<ID=DP,Number=1,Type=Integer,Description="Read Depth">
##FORMAT=<ID=HQ,Number=2,Type=Integer,Description="Haplotype Quality">
#CHROM POS ID REF ALT QUAL FILTER INFO FORMAT NA00001 NA00002 NA00003
20 14370 rs6054257 G A 29 PASS NS=3;DP=14;AF=0.5;DB;H2 GT:GQ:DP:HQ 0|0:48:1:51,51 1|0:48:8:51,51 1/1:43:5:.,.
20 17330 . T A 3 q10 NS=3;DP=11;AF=0.017 GT:GQ:DP:HQ 0|0:49:3:58,50 0|1:3:5:65,3 0/0:41:3
20 1110696 rs6040355 A G,T 67 PASS NS=2;DP=10;AF=0.333,0.667;AA=T;DB GT:GQ:DP:HQ 1|2:21:6:23,27 2|1:2:0:18,2 2/2:35:4
20 1230237 . T . 47 PASS NS=3;DP=13;AA=T GT:GQ:DP:HQ 0|0:54:7:56,60 0|0:48:4:51,51 0/0:61:2
20 1234567 microsat1 GTC G,GTCT 50 PASS NS=3;DP=9;AA=G GT:GQ:DP 0/1:35:4 0/2:17:2 1/1:40:3
```
The **header** lines start after '#'. Words that start after '##' are keywords.
The **body** has various lines each with eight columns of information. This is similar to the SAM where each line had 11 columns. The columns are:
1. *CHROM*: The name of the sequence (typically a chromosome) on which the variation is being called.
2. *POS*: The position of the variation. (1-N where N is the length of the chromosome)
3. *ID*: Semi-colon separated list of unique identifiers where available. The identify the kind of variation such as SNP or deletion.
4. *REF*: The reference base (or bases in the case of an indel) at the given position on the given reference sequence.
5. *ALT*: The list of alternative alleles at this position.
6. *QUAL*: A quality score associated with the inference of the given alleles.
7. *FILTER*: A flag indicating which of a given set of filters the variation has passed.
8. *INFO*: additional information about the variation. Descriptors are usually one of the following:

  • AA : ancestral allele

  • AC : allele count.

  • AF : allele frequency.

  • AN : total number of alleles in called genotypes

  • BQ : RMS base quality at this position

  • CIGAR : cigar string describing how to align an alternate allele to the reference allele

  • DB : dbSNP membership

  • DP : combined depth across samples, e.g. DP=154

  • END : end position of the variant.

  • H2 : membership in hapmap2

  • H3 : membership in hapmap3

  • MQ : RMS mapping quality, e.g. MQ=52

  • MQ0 : Number of MAPQ == 0 reads covering this record

  • NS : Number of samples.

  • SB : strand bias.

  • SOMATIC :somatic mutation

  • VALIDATED : validated by follow-up experiment

  • 1000G : membership in 1000 Genomes

9. (optional) *FORMAT*: An extensible list of fields for describing the samples.
10. (+) (optional) *#SAMPLEs*: For each sample described in the file, values are given for the fields listed in *FORMAT*.

## Resources
1. https://bioinformatics.uconn.edu/resources-and-events/tutorials-2/file-formats-tutorial/#
2. https://en.wikipedia.org/wiki/Variant_Call_Format
3. https://en.wikipedia.org/wiki/SAM_(file_format)#cite_note-spec-3
4. https://en.wikipedia.org/wiki/FASTQ_format
5. https://en.wikipedia.org/wiki/FASTA_format
