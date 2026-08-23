# Materials and Methods

## *De Novo* Assembly and Polishing

### Long-Read *De Novo* Assembly and Consensus Generation
Genomic DNA from eight *Mycolicibacterium cosmeticum* isolates (ANT01, ANT06, BODY01, BODY06, BULB01, BULB06, DESC01, and DESC06) was sequenced using Oxford Nanopore Technologies (ONT) MinION platform [insert flow cell/sequencing platform details, e.g., MinION/GridION, sequencing chemistry].
Prior to loading into the MinION flow cell, the gDNAs are prepared into a sequencing library using .... kit. Raw long-read quality assessment and read filtering were conducted using [what QC tool is used? NanoPlot?? The filtering thresholds??, mention the tool and filtering thresholds]. 

Long-read *de novo* assembly and consensus generation were performed using the Trycycler pipeline (which version??) [Wick et al., 2021]. Read sets were subsampled into independent subsets and assembled using [mention the assemblers used to feed into Trycycler, along with versions and run parameters]. The resulting contigs were clustered, reconciled, circularized, and partitioned into high-confidence consensus sequences in accordance with the standard Trycycler workflow.

### Short-Read Polishing and Genome Reorientation
To correct residual indel and substitution errors in the long-read consensus assemblies, a two-step short-read polishing pipeline was applied using paired-end Illumina reads, following best-practice polishing recommendations outlined by Ryan Wick (https://rrwick.github.io/2024/06/11/short-read-depth.html) and George Bouras (https://github.com/gbouras13/pypolca). First, paired-end short reads were aligned to the draft Trycycler assemblies using BWA-MEM (v0.7.19-r1273) with the `-a` flag enabled to preserve all alignments in repeat regions. Alignments were filtered with Polypolish `filter` (v0.7.1) and polished using Polypolish `polish` (v0.7.1) with default parameters (`--fraction_invalid 0.2`, `--fraction_valid 0.5`, `--max_errors 10`, `--min_depth 5`) to repair errors across both unique and repetitive sequences.
The Polypolish-corrected assemblies were subsequently polished using Pypolca (v0.4.0) in careful mode (`pypolca run --careful`) to fix remaining base inaccuracies. Finally, complete circularized chromosomes and extrachromosomal elements were reoriented using dnaapler (v1.3.0) via `dnaapler all` (`--autocomplete nearest`, `-e 1e-10`), reorienting chromosomal contigs to start at the *dnaA* gene, while extrachromosomal contigs were reoriented to start at either *repA* or *terL* gene

# References
1. **Trycycler**: Wick, R. R., Judd, L. M., Cerdeira, L. T., Hawkey, J., Méric, G., Vezina, B., Wyres, K. L., & Holt, K. E. (2021). Trycycler: consensus assembly of bacterial genomes from multiple long-read assemblies. *Genome Biology*, 22(1), 256. https://doi.org/10.1186/s13059-021-02483-3
2. **BWA-MEM**: Li, H. (2013). Aligning sequence reads, clone sequences and assembly contigs with BWA-MEM. *arXiv preprint*, arXiv:1303.3997. https://doi.org/10.48550/arXiv.1303.3997
3. **Polypolish**: Wick, R. R., & Holt, K. E. (2022). Polypolish: Short-read polishing of long-read bacterial genome assemblies. *PLOS Computational Biology*, 18(1), e1009804. https://doi.org/10.1371/journal.pcbi.1009804
4. **Pypolca / POLCA**: 
   - Bouras, G. (2024). *pypolca: Standalone Python implementation of the POLCA polisher from MaSuRCA* (v0.4.0). GitHub. https://github.com/gbouras13/pypolca
   - Zimin, A. V., & Salzberg, S. L. (2020). POLCA: rapid and accurate error correction for genome assemblies. *Bioinformatics*, 36(9), 2877–2879. https://doi.org/10.1093/bioinformatics/btaa080
5. **Dnaapler**: Bouras, G., Mallawaarachchi, S., Papudeshi, B., Roach, M. J., & Edwards, R. A. (2024). Dnaapler: reorienting microbial genomes to a designated starting gene. *Microbial Genomics*, 10(11), 001306. https://doi.org/10.1099/mgen.0.001306
6. **Short-Read Depth Recommendation**: Wick, R. R. (2024). *How much short-read depth do you need for hybrid polishing?* Ryan Wick's Bioinformatics Blog. https://rrwick.github.io/2024/06/11/short-read-depth.html

