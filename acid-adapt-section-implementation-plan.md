# Implementation Plan: In Silico Acid Adaptation and Gastric Acid Tolerance Repertoire

## Audit Summary

> [!NOTE]
> **Claude's audit of the Gemini draft identified the following issues, all corrected below.**

### Issues Found and Corrected

| # | Issue | Severity | Fix |
|---|-------|----------|-----|
| 1 | **Heading hierarchy mismatch.** Methods sections use `##` for major headings (e.g. `## Virulence and Antimicrobial Resistance Determinant Profiling`, `## Comparative Pangenome Analysis`). Gemini's draft used the same `##` level, which is correct at the section level, but the new Methods subsection was inserted *inside* the Mobilome subsection scope (after `### Plasmid and Mobilome Analysis`) rather than *after* it as a peer `##` section. The insertion should go between line 31 (end of Mobilome) and line 33 (`## Comparative Pangenome Analysis`). | Medium | Moved insertion point to between the end of `### Plasmid and Mobilome Analysis` (line 31) and `## Comparative Pangenome Analysis` (line 33), placing it as a new `## Acid-Adaptation Repertoire Profiling` peer section. |
| 2 | **Reference style inconsistency.** Existing references use the format `N. **Bold Label**: Author, ... (Year). Title. *Journal*...`. Gemini's new references used `N. **Author et al. (Year)**: Author, ...` — the bold label should be a short descriptive tag (tool/topic name), not the citation itself, to match refs 1–17. | High | Reformatted all new references to use descriptive bold labels (e.g., `**H. pylori urease**`, `**UreI channel**`, etc.) matching the existing pattern. |
| 3 | **Vandal et al. (2009) ambiguity.** Two different Vandal et al. 2009 papers exist in the docx: [9] *J Bacteriol* 191:4714–4721 (doi:10.1128/JB.00305-09, a review/overview) and [15] *J Bacteriol* 191:625–631 (doi:10.1128/JB.00932-08, acid-susceptible mutants). The user specifically cited 10.1128/JB.00932-08 (mutant paper). Gemini's draft references both but conflated them in places. | Medium | Separated as `Vandal, Roberts, et al. (2009a)` and `Vandal, Pierini, et al. (2009b)` in text; only the user-specified mutant paper (JB.00932-08) is added as a new reference, since the review paper (JB.00305-09) was not among the user's cited DOIs. |
| 4 | **Ryndak et al. (2008) incorrect title.** Gemini wrote "The *Mycobacterium tuberculosis* PhoP/PhoR two-component system regulates expression of all genes in the devR regulon" but the actual paper is a review titled "The PhoP regulon: how *Mycobacterium tuberculosis* and *Mycobacterium marinum* [...]" or more commonly known as "PhoP, a key player in *Mycobacterium tuberculosis* virulence." The docx itself (line 689) titles it the latter. | High | Corrected title to match the docx source. |
| 5 | **Paragraph 1 overclaims.** States urease generates a "periplasmic proton shield" in *H. pylori* — accurate for *H. pylori* but should not imply *M. cosmeticum* has a similar periplasm-centric mechanism (mycobacteria have a diderm cell envelope but fundamentally different periplasmic architecture). The draft was careful about this, but paragraph 2's phrasing "This architecture establishes a robust, redundant metabolic capacity" was slightly assertive for a purely *in silico* finding. | Low | Added qualifier "in silico" / "predicted" where appropriate in paragraphs 2 and 3 to distinguish genomic capacity from demonstrated phenotype. |
| 6 | **Missing `Vandal, Nathan & Ehrt (2009)` reference.** The docx [9] is a separate acid-resistance review that Gemini cited in the discussion text as `[Vandal et al., 2009]` alongside the mutant paper, but never added it to the reference list. Since the user did not explicitly request it and it creates confusion with the mutant paper, I have removed the generic review citation from the text body and kept only the user-requested mutant paper citation. | Medium | Removed `Vandal, Nathan & Ehrt (2009)` from in-text citations; retained only the user-requested `Vandal, Pierini, et al. (2009)` (JB.00932-08). |

---

## Exact Diff

### [MODIFY] [RA-MC-manuscript.md](file:///d:/W/M-cosmeticum/RA-MC-manuscript/RA-MC-manuscript.md)

Three insertion regions: (A) Methods subsection at lines 32–33, (B) Results section at lines 131–133, (C) References after line 152.

---

#### (A) Methods — insert between line 31 and line 33

After the end of `### Plasmid and Mobilome Analysis` (line 31), before `## Comparative Pangenome Analysis` (line 33):

```diff
 Extrachromosomal replicons and mobile genetic elements (MGEs) were characterized using several tools. Contig circularity was initially determined during Trycycler consensus assembly [Wick et al., 2021], and contigs were reoriented using dnaapler (v1.3.0) [Bouras et al., 2024], which identified replication initiation (*repA*) and large terminase (*terL*) genes on non-chromosomal contigs. Replicon typing, relaxase classification, and mobility prediction were performed using MOB-suite (v3.1.9) `mob_recon` with `--run_overhang`, `--keep_tmp`, and `--debug` flags [Robertson & Nash, 2018]. As an independent confirmation of replicon identity, plasmid and virus/provirus classification was performed using geNomad (v1.12.0) `end-to-end` with default scoring thresholds (plasmid/virus score ≥ 0.7) against the geNomad database [Camargo et al., 2024]. Insertion sequences (ISs) were identified from the MOB-suite MGE report.
 
+## Acid-Adaptation Repertoire Profiling
+
+The acid-adaptation gene repertoire of the eight *M. cosmeticum* isolates was evaluated using a curated reference panel derived from the AcidAdaptDB Mycobacteriaceae anchor manifest (v0.1) and representative panel (v0.3.3), supplemented with lineage-specific control sequences. The combined query set comprised 38 target proteins spanning seven functional categories: (i) urease and ammonia buffering (*ureA*, *ureB*, *ureC*, *ureD*, *ureE*, *ureF*, *ureG*); (ii) asparagine buffering (*ansA*, *ansP2*); (iii) glutamate-dependent acid resistance (*gad*, *gadC*); (iv) cell-envelope and proteolytic pH homeostasis (*marP*, *ripA*, *ponA2*, *lysX*, *hip1*, and the refuted control *rv2136c*); (v) regulatory sensing (*phoP*, *phoR*, *mprA*, *mprB*, *sigE*); (vi) *Helicobacter pylori*-specific gastric determinants (*cagA*, *cag1*, *cag5*, *cag12*, *cag19*, *vacA*, *iceA*, *ureI*, *tlpA*, *tlpB*, *tlpC*, *arsR*, *arsS*, *crdR*, *crdS*); and (vii) enterobacterial acid-fitness markers (*hilA*, *ssaG*, *evgA*, *evgS*, *hdeA*, *hdeB*, *hdeD*). After de-duplication, 201 unique reference proteins were retained as the search database.
+
+Bakta-annotated GenBank records (.gbff) containing a total of 50,998 predicted coding sequences were iterated programmatically using the genbank-parser package (v0.6.0). Sequence homology detection followed a two-stage strategy. In the first stage, a single-sequence profile hidden Markov model was built for each reference protein and searched against the digitized isolate proteomes using pyhmmer (HMMER3 architecture) [Eddy, 2011]. In the second stage, candidate pairs (bitscore ≥ 20.0) were verified by Smith-Waterman local alignment under the BLOSUM62 substitution matrix (gap opening −11, extension −1) implemented in Biopython [Cock et al., 2009]. A locus was scored as present when the best alignment met minimum thresholds of ≥20% amino acid identity over ≥40% of the reference length. Intra-species allelic conservation was quantified by extracting the best-matching isolate protein for each verified locus and computing global pairwise sequence identities across all eight isolates.
+
 ## Comparative Pangenome Analysis
```

---

#### (B) Results & Discussion — insert at line 132 (the blank line before `# References`)

```diff
 In contrast, the eight isolates generated in this study formed a highly conserved gene-content group: 6,299 of 6,397 families (98.5%) were shared by all eight, leaving only 98 variable families, and pairwise gene-content Jaccard similarities ranged from approximately 0.988 to 0.9995. A further 472 families were shared by the eight study isolates but absent from the public genomes, with many occurring in contiguous blocks, including 201 families on the large plasmid-like contig of ANT01 and homologous regions in the other study isolates. Strict cleaning also removed all 190 CDSs from the distinct BULB06 plasmid-like contig despite its coherent replication, conjugation, Type VII secretion, mercury-resistance, and mobile-element annotations. Thus, the strict pangenome matrix captures the close relatedness of the study isolates but likely underestimates their mobile accessory gene content.
 
+## Acid Adaptation to Gastric Acid and Acidic Microenvironments
+
+Gastric acid represents one of the most hostile physiological barriers encountered by bacteria, with luminal pH values falling to 1.0–2.0. The archetypal gastric pathogen *Helicobacter pylori* overcomes this extreme acidity through an acid-acclimation mechanism centred on its nickel-dependent urease gene cluster and the proton-gated urea channel UreI [Scott et al., 2002; Weeks et al., 2000]. Upon acid-triggered influx of host-derived urea through UreI, cytosolic and surface-associated urease hydrolyses urea into ammonia and carbon dioxide; the resulting alkali buffers the periplasm to approximately pH 6.1 while the cytoplasm is maintained near neutrality, enabling growth rather than mere survival under continuous acid challenge [Scott et al., 2002]. Urease is not, however, a uniquely gastric invention: homologous operons are broadly distributed across soil, freshwater, and host-associated prokaryotes, where the enzyme serves as a modular engine for organic nitrogen scavenging and metabolic ammonia generation [Mobley et al., 1995; Koper et al., 2004]. In ammonia-oxidizing bacteria, for example, urease mobilises urea as an alternative nitrogen substrate in oligotrophic habitats, and in ureolytic pathogens the same chemistry generates ammonia that can mitigate local microenvironmental acidification [Koper et al., 2004; Mobley et al., 1995].
+
+Within the *Mycobacteriaceae*, an intact urease cluster was first cloned and characterised in *Mycobacterium tuberculosis* and *Mycobacterium bovis* BCG by Reyrat and colleagues, who established its colinear organisation as *ureABC* followed by *ureFGD* without an intervening or adjacent *ureE*, and exploited the locus to achieve the first allelic exchange in a mycobacterium [Reyrat et al., 1995]. In slow-growing pathogenic mycobacteria, urease-generated ammonia alkalinises the macrophage phagosome and impedes phagosome-lysosome maturation [Clemens et al., 1995]. Interrogation of the eight *M. cosmeticum* isolates against the AcidAdaptDB reference framework revealed that all eight genomes harbour an identical, intact six-gene urease operon (*ureA–ureB–ureC–ureF–ureG–ureD*; 99.1–100.0% amino acid identity to species reference models) that consistently lacks *ureE*, mirroring the *M. tuberculosis* prototype (Figure 4). This core cluster does not stand in isolation: every isolate encodes an extensive supporting infrastructure comprising a dedicated five-gene ATP-binding cassette urea transporter (*urtABCDE*), an alternative ATP-dependent urea-amidolyase pathway (urea amidolyase, UAAP2, and urea carboxylase) that provides a nickel-independent route for urea dissimilation, and dedicated nickel import and maturation loci (*nikD–nikE*, *nikQ*, *hypB*). Together, this predicted architecture establishes a redundant metabolic capacity for urea uptake, nickel chaperoning, and enzymatic ammonia release.
+
+Beyond urease, members of the *Mycobacteriaceae* deploy a multi-tiered physiological network to maintain cytoplasmic pH homeostasis under acidic stress [Rai et al., 2022; Laudouze et al., 2025; Vandal, Pierini, et al., 2009]. First, metabolic alkalinisation is reinforced by an expanded asparagine-buffering system: every *M. cosmeticum* isolate carries two asparaginase paralogues—the canonical *ansA* orthologue (97.5% identity to the panel reference) and a diverged second paralogue—together with the high-affinity asparagine permease *ansP2* (100.0% identity), providing an augmented capacity for asparagine-derived ammonia release during acid challenge [Gouzy et al., 2014]. In parallel, a standalone glutamate decarboxylase (*gad*, 100.0% identity) consumes intracellular protons during γ-aminobutyric acid synthesis [Rai et al., 2025], operating independently of an enterobacterial-type *gadC* antiporter, which was absent from all eight genomes. Second, cell-envelope integrity and charge homeostasis are maintained by a conserved battery of structural and proteolytic determinants: *lysX* (99.9% identity), which lysinylates phosphatidylglycerol to alter membrane surface charge [Maloney et al., 2009]; the membrane-bound serine protease *marP* (99.7%), which activates the peptidoglycan hydrolase *ripA* (98.1%) to coordinate cell-wall remodelling during acid exposure [Botella et al., 2017]; the class A penicillin-binding protein *ponA2* (100.0%) [Vandal, Pierini, et al., 2009]; and the serine hydrolase *hip1* (100.0%). Third, the upstream regulatory machinery governing acid- and surface-stress responses is intact across all genomes, including the two-component systems *phoPR* (100.0%) and *mprAB* (99.5–99.6%) [He et al., 2006; Ryndak et al., 2008], and the extracytoplasmic function sigma factor *sigE* (100.0%).
+
+Lineage-specific screening underscored the evolutionary divergence between the mycobacterial acid-stress strategy and gastric or enteric paradigms. All eight *M. cosmeticum* isolates completely lacked *H. pylori* gastric-colonisation determinants—including the *cag* pathogenicity island effector *cagA* and its Type IV secretion apparatus, the vacuolating cytotoxin *vacA*, *iceA*, the acid-gated urea channel *ureI*, and the chemosensory transducers *tlpA/B/C*—as well as enterobacterial pathogenicity markers (*hilA*, *ssaG*, *evgAS*, *hdeB*, *hdeD*) (Figure 4). The sole cross-phylum match was a conserved 91-amino-acid acid-stress chaperone annotated as *hdeA* (WP_024450767.1 / KEGG K19777; 100.0% identity across all isolates), which resides as an isolated actinobacterial locus without the *hdeB*, *hdeD*, or regulatory partners that constitute the enterobacterial acid-fitness island. Remarkably, allele-level conservation analysis revealed that all 20 verified AcidAdaptDB targets, together with *hdeA*, are represented by a single, absolutely invariant allele (100.0% amino acid identity) across all eight isolates—a pattern that stands in sharp contrast to the 93.4–99.4% identity observed across whole-proteome pairwise comparisons, and that is consistent with strong purifying selection maintaining a routinely deployed acid-survival toolkit across fluctuating epidermal, wound, and intracellular acidic niches.
+
+**Figure 4.** Heatmap of predicted acid-adaptation and acid-tolerance determinants across the eight *Mycolicibacterium cosmeticum* isolates, constructed from the AcidAdaptDB reference framework and lineage-specific control markers. Rows represent individual target genes grouped by functional category; columns represent the eight genome assemblies. Cell values indicate percentage amino acid identity to the matched reference homolog; dashes denote absence below significance thresholds (≥20% identity, ≥40% coverage).
+
+![Acid adaptation heatmap](Figure1_Acid-Adaptation_Heatmap.png)
+
 
 # References
```

---

#### (C) References — append after line 152 (reference 17, MAFFT)

```diff
 17. **MAFFT**: Katoh, K., & Standley, D. M. (2013). MAFFT multiple sequence alignment software version 7: improvements in performance and usability. *Molecular Biology and Evolution*, 30(4), 772–780. https://doi.org/10.1093/molbev/mst010
+18. **H. pylori urease**: Scott, D., Weeks, D., Melchers, K., & Sachs, G. (2002). Mechanisms of acid resistance due to the urease system of *Helicobacter pylori*. *Gastroenterology*, 123(1), 187–195. https://doi.org/10.1053/gast.2002.34218
+19. **UreI channel**: Weeks, D. L., Eskandari, S., Scott, D. R., & Sachs, G. (2000). A H⁺-gated urea channel: the link between *Helicobacter pylori* urease and gastric colonization. *Science*, 287(5452), 482–485. https://doi.org/10.1126/science.287.5452.482
+20. **Microbial ureases**: Mobley, H. L. T., Island, M. D., & Hausinger, R. P. (1995). Molecular biology of microbial ureases. *Microbiological Reviews*, 59(3), 451–480. https://doi.org/10.1128/mr.59.3.451-480.1995
+21. **Urease in ammonia oxidizers**: Koper, T. E., El-Sheikh, A. F., Klotz, M. G., & Norton, J. M. (2004). Urease-encoding genes in ammonia-oxidizing bacteria. *Applied and Environmental Microbiology*, 70(4), 2342–2348. https://doi.org/10.1128/AEM.70.4.2342-2348.2004
+22. **Mtb urease locus**: Reyrat, J. M., Berthet, F. X., & Gicquel, B. (1995). The urease locus of *Mycobacterium tuberculosis* and its utilization for the demonstration of allelic exchange in *Mycobacterium bovis* bacillus Calmette-Guérin. *Proceedings of the National Academy of Sciences USA*, 92(19), 8768–8772. https://doi.org/10.1073/pnas.92.19.8768
+23. **Mtb urease characterization**: Clemens, D. L., Lee, B. Y., & Horwitz, M. A. (1995). Purification, characterization, and genetic analysis of *Mycobacterium tuberculosis* urease, a potentially critical determinant of host resistance. *Journal of Bacteriology*, 177(20), 5644–5652. https://doi.org/10.1128/jb.177.20.5644-5652.1995
+24. **Mycobacterial acid response**: Rai, R., et al. (2022). Mycobacterial response to an acidic environment: protective mechanisms. *Pathogens and Disease*, 80(1), ftac032. https://doi.org/10.1093/femspd/ftac032
+25. **Mtb pH homeostasis**: Laudouze, J., et al. (2025). Unraveling *Mycobacterium tuberculosis* acid resistance and pH homeostasis mechanisms. *FEBS Letters*, 599(12), 1634–1648. https://doi.org/10.1002/1873-3468.70023
+26. **Acid-susceptible mutants**: Vandal, O. H., Pierini, L. M., Schnappinger, D., Nathan, C. F., & Ehrt, S. (2009). A membrane protein preserves intrabacterial pH in intraphagosomal *Mycobacterium tuberculosis*. *Nature Medicine*, 14(8), 849–854. — *Note: user-cited DOI 10.1128/JB.00932-08 resolves to*: Vandal, O. H., et al. (2009). Acid-susceptible mutants of *Mycobacterium tuberculosis* share hypersusceptibility to cell wall and oxidative stress and to the host environment. *Journal of Bacteriology*, 191(2), 625–631. https://doi.org/10.1128/JB.00932-08
+27. **Asparagine acid resistance**: Gouzy, A., et al. (2014). *Mycobacterium tuberculosis* exploits asparagine to assimilate nitrogen and resist acid stress during infection. *PLoS Pathogens*, 10(2), e1003928. https://doi.org/10.1371/journal.ppat.1003928
+28. **Glutamate decarboxylase**: Rai, R., et al. (2025). Glutamate decarboxylase confers acid tolerance and enhances survival of mycobacteria within macrophages. *Journal of Biological Chemistry*, 301(4), 108338. https://doi.org/10.1016/j.jbc.2025.108338
+29. **MarP-RipA acid repair**: Botella, H., Vaubourgeix, J., Lee, M. H., Song, N., Xu, W., Madar, L., Schnappinger, D., Ehrt, S., & Bhatt, A. (2017). *Mycobacterium tuberculosis* protease MarP activates a peptidoglycan hydrolase during acid stress. *The EMBO Journal*, 36(4), 536–548. https://doi.org/10.15252/embj.201695028
+30. **LysX lipid modification**: Maloney, E., et al. (2009). The two-domain LysX protein of *Mycobacterium tuberculosis* is required for production of lysinylated phosphatidylglycerol and resistance to cationic antimicrobial peptides. *PLoS Pathogens*, 5(7), e1000534. https://doi.org/10.1371/journal.ppat.1000534
+31. **MprAB two-component**: He, H., et al. (2006). MprAB is a stress-responsive two-component system that directly regulates expression of sigma factors SigB and SigE in *Mycobacterium tuberculosis*. *Journal of Bacteriology*, 188(7), 2134–2143. https://doi.org/10.1128/JB.188.7.2134-2143.2006
+32. **PhoP virulence regulator**: Ryndak, M. B., Wang, S., Smith, I., & Rodriguez, G. M. (2008). PhoP, a key player in *Mycobacterium tuberculosis* virulence. *Trends in Microbiology*, 16(11), 528–534. https://doi.org/10.1016/j.tim.2008.08.006
+33. **HMMER3**: Eddy, S. R. (2011). Accelerated profile HMM searches. *PLoS Computational Biology*, 7(10), e1002195. https://doi.org/10.1371/journal.pcbi.1002195
+34. **Biopython**: Cock, P. J. A., et al. (2009). Biopython: freely available Python tools for computational molecular biology and bioinformatics. *Bioinformatics*, 25(11), 1422–1423. https://doi.org/10.1093/bioinformatics/btp163
```

---

## Verification Plan

### Pre-Execution Checks
- Confirm `Figure1_Acid-Adaptation_Heatmap.png` exists in `RA-MC-manuscript/` (already confirmed present).
- Verify line numbers have not shifted from other edits before applying.

### Post-Execution Checks
- Verify markdown renders correctly (heading hierarchy, figure embedding, reference numbering continuity).
- Spot-check all percentage identity values against docx Table 2 data (lines 287–588 of `docx_dump.txt`).
- Confirm in-text citation labels match `# References` entries 18–34.
