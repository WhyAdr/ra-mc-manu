# Materials and Methods

## *De Novo* Assembly and Polishing

### Long-Read *De Novo* Assembly and Consensus Generation
Genomic DNA from eight *Mycolicibacterium cosmeticum* isolates (ANT01, ANT06, BODY01, BODY06, BULB01, BULB06, DESC01, and DESC06) was sequenced using Oxford Nanopore Technologies (ONT) [insert flow cell/sequencing platform details, e.g., MinION/GridION, sequencing chemistry]. Raw long-read quality assessment and read filtering were conducted using [insert read QC/filtering software, e.g., NanoPlot / Filtlong, version and filtering thresholds]. 

Long-read *de novo* assembly and consensus generation were performed using the Trycycler pipeline (v[insert version]) [Wick et al., 2021]. Read sets were subsampled into independent subsets and assembled using [insert de novo assemblers used, e.g., Flye, Miniasm/Minipolish, Raven, with versions and parameters]. The resulting contigs were clustered, reconciled, circularized, and partitioned into high-confidence consensus sequences in accordance with the standard Trycycler workflow.

### Short-Read Hybrid Polishing and Genome Reorientation
To correct residual indel errors and base-calling inaccuracies in the long-read consensus assemblies, a two-step short-read error correction pipeline was applied using paired-end Illumina reads, following best-practice polishing recommendations outlined by Ryan Wick (https://rrwick.github.io/2024/06/11/short-read-depth.html) and George Bouras (https://github.com/gbouras13/pypolca). First, paired-end short reads were aligned to the draft Trycycler assemblies using BWA-MEM (v0.7.19-r1273) with the `-a` flag enabled to preserve all alignments in repeat regions. Alignments were filtered with Polypolish `filter` (v0.7.1) and polished using Polypolish `polish` (v0.7.1) with default parameters (`--fraction_invalid 0.2`, `--fraction_valid 0.5`, `--max_errors 10`, `--min_depth 5`) to repair errors across both unique and repetitive sequences.

The Polypolish-corrected assemblies were subsequently polished using Pypolca (v0.4.0) in careful mode (`pypolca run --careful`) to fix remaining base substitutions and short indels. Finally, complete circularized chromosomes and extrachromosomal elements were standardized and reoriented using Dnaapler (v1.3.0) via `dnaapler all` (`--autocomplete nearest`, `-e 1e-10`), reorienting chromosomal contigs to start at the *dnaA* replication initiation gene.
