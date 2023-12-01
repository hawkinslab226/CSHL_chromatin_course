# CSHL_course

## CSHL Fall 2023 Computational Genomics Course
Welcome! This is the material and tutorials for the Chromatin Workshop.
The database adopted in this course is under the reference: "Enhancer Chromatin and 3D Genome Architecture Changes from Naive to Primed Human Embryonic Stem Cell States".
https://www.cell.com/stem-cell-reports/pdfExtended/S2213-6711(19)30126

## Data info:
- **Cell Type**: Naïve cells
- **Histone modification**: H3K4me3: Promoters & H3K27ac: Promoters and Enhancers
- **Library info**: **1)** SE-fastq files; **2)** 3 M rads
- **Data File**: Total 6 files (2 for each histone modification & 2 input files)

### 1) Quality Control of Sequencing using FastQC/MultiQC
- **Documentation**: *FastQC*: https://www.bioinformatics.babraham.ac.uk/projects/fastqc/ & *MultiQC*: https://multiqc.info/
- FastQC: ~3 -4 min <br /> 
`fastqc *.fastq`
- MultiQC: ~ 1 min <br />
`multiqc *.zip`

### 2) Processing data & Genome Mapping
**Chromap** for aligning and preprocessing high throughput chromatin profiles (*ATAC-seq & ChIP-seq*); **1)** Trimm the low-quality reads and adaptors; **2)** Remove duplicated reads; **3)** Perform the mapping. https://github.com/haowenz/chromap

- Build the indexed genome (available !!!) ~ 1 min
` chromap -i -r genome.fa -o index`
- Flags:
**-i**: indexing genome flag 
**-r**: reference genome
**-o**: output name

### 2.1) Reference Genome
- Genome assembly: GRCh38.p14 <br />
&#x1F538; **Only the chromosome 22 human genome** (*only because it is one of the smallest!!*)
- Chromosome 22 info : https://useast.ensembl.org/Homo_sapiens/Location/Chromosome?r=22 <br />

### 2.2) Processing & mapping data 
- Chromap: *~35 sec*
`chromap --preset chip -x index_chrm22 -r Homo_sapiens.GRCh38.dna.chromosome.22.fa -q 20 --min-read-length 10   -1 SRR5063143_naive_H3K27ac_PE.fastq  -o  SRR5063143_naive_H3K27ac_chromap.bed` <br />
- Flags:
**--preset chip**:Mapping chip reads
**-x**:index 
**-r**:reference genome 
**-q**:Min MAPQ (*Quality*)
**--min-read-length**:min length read
**-1**:Single-end (*if use paired-end also included -2*) 
**-o**: output file
*--trim-adapters(not used)*





  





