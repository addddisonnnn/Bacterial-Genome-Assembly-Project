# Genome Assembly Project & Pipeline
Through this Genome Assembly Project, a pipeline was created to assemble a bacterial genome and assess and analyze the result of this assembly.

Here lies the result of establishing a nextflow pipeline capable of assembling the genome of a bacteria as well as analyzing the consequences and output of said assembly.

### Methods

The bacterial genome of Alteromonas mecleodii was assembled through a pipeline and analyzed.

This pipeline started off with getting the reads and quality control. Long and short reads were acquired and initial quality control was performed using FastQC v0.12.1 (on default parameters) [1] was run on the short reads. Filtlong v0.3.0 (minimum length at 500 and 90% kept) [2] was run on the long reads for quality control. Flye v2.9.6 (on parameters set to correct nanopore reads) [3] was run on the filtered long reads for assembly.

After assembly, create an index of the assembly, align the short reads to the assembly, and sort and index the alignments with Bowtie2 v2.5.4 [4] and samtools v1.22.1 (on default parameters) [5]. Using the alignments, short-read polish with Pilon v1.24 (with default parameters) [6].

Annotate the polished assembly with Prokka v1.14.6 (on default parameters) [7]. Run BUSCO v6.0.0 (set to the alteromonas_odb12 lineage) [8] on the polished assembly to evaluate completeness. After downloading the canoical reference genome from NCBI RefSeq assembly (GCF_000172635.2) with NCBI-datasets-cli tool v18.6.0 (on default parameters) [9], run QUAST v5.3.0 (on default parameters) [10] twice comparing the final assembly with the reference genome as well as the unpolished assembly.
