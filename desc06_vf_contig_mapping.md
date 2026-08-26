# DESC06 Virulence Factor Gene → Contig Mapping

## Summary

DESC06 has 87 VF gene hits total. Cross-referencing coordinates from [DESC06-reoriented_best_hits.tsv](file:///d:/W/M-cosmeticum/VF_results-RA-mycolicibacterium/DESC06-reoriented/DESC06-reoriented_best_hits.tsv) against the Bakta contig boundaries:

- **contig_1** (5,252,470 bp, main chromosome): 53 hits
- **contig_2** (1,069,271 bp, disputed fragment): 34 hits
- **contig_3–5**: 0 hits

## Contig_2 VF genes — classified as Core vs. DESC06-unique

### Core genes displaced onto contig_2 (also present in ANT01 on its cluster_001)

These genes are part of the conserved core repertoire shared by all 8 isolates. In the other 7 isolates, they reside on the single main chromosome. In DESC06, they were placed on contig_2 because Trycycler split the chromosome.

| Gene | DESC06 contig_2 coords | ANT01 cluster_001 coords | Identity % | Category |
|---|---|---|---|---|
| *mbtE* | 263,281–268,425 | 2,206,222–2,211,366 | 78.4% | Mycobactin |
| *mbtC* | 258,963–260,242 | 2,201,904–2,203,183 | 79.5% | Mycobactin |
| *glnA1* | 475,566–477,002 | 2,418,507–2,419,943 | 92.6% | Glutamine synthesis |
| *kasB* | 417,955–419,205 | 2,360,896–2,362,146 | 83.7% | FAS-II |
| *caeA* | 461,613–463,094 | 2,404,554–2,406,035 | 80.5% | Carboxylesterase |
| *trpD* | 508,546–509,546 | 2,451,487–2,452,487 | 84.0% | Tryptophan synthesis |

> [!IMPORTANT]
> These 6 genes are NOT new to DESC06. They are part of the conserved core but were mapped to contig_2 because the ~1 Mbp fragment is a displaced piece of the chromosome. They should not be counted among DESC06-unique VF genes.

### DESC06-unique genes on contig_2

These genes have 0% identity in all other 7 isolates — genuinely specific to DESC06:

| Gene | Coords on contig_2 | Identity % | Category |
|---|---|---|---|
| *mbtA* | 252,952–254,520 | 78.1% | Mycobactin |
| *mbtB* | 254,976–258,182 | 75.8% | Mycobactin |
| *mbtD* | 262,524–262,726 | 76.7% | Mycobactin |
| *mbtF* | 268,588–272,901 | 76.0% | Mycobactin |
| *mbtG* | 272,917–274,144 | 79.5% | Mycobactin |
| *mbtH* | 274,213–274,385 | 89.1% | Mycobactin |
| *mbtI* | 252,100–252,914 | 76.9% | Mycobactin |
| *nuoG* (2nd copy) | 134,144–135,675 | 75.3% | Immune modulation |
| *ndk* | 51,063–51,467 | 87.7% | Immune modulation |
| *ptpA* | 440,812–441,277 | 79.2% | Immune modulation |
| *mptC* | 520,362–521,522 | 78.4% | LAM |
| *capA* | 655,565–657,008 | 74.0% | LAM |
| *mmpL4a* | 376,417–379,082 | 70.8% | GPL locus |
| *mmpL4b* | 872,759–873,557 | 73.5% | GPL locus |
| *mps1* | 803,742–804,415 | 71.7% | GPL locus |
| *mps2* (2nd copy) | 265,576–265,803 | 77.4% | GPL locus |
| *fbpA* | 802,557–803,190 | 76.1% | Adherence |
| *fbpB* | 802,571–803,195 | 76.2%* | Adherence |
| *fbpC* (2nd copy) | 802,556–803,217 | 78.4% | Adherence |
| *sypC* | 265,003–265,049 | 95.7% | Exotoxin |
| *pvdI* | 265,564–265,804 | 76.3% | Pyoverdine |
| *pvdL* | 265,639–265,803 | 76.5% | Pyoverdine |
| *mce7D* | 911,604–912,873 | 79.0% | Mce7 |
| *mce7F* | 914,275–915,450 | 73.3% | Mce7 |
| *mce8A* | 908,284–909,389 | 72.7% | Mce8 |
| *mce8D* | 911,617–912,585 | 73.7% | Mce8 |
| *mce8E* | 913,017–913,569 | 75.1% | Mce8 |
| *mce8F* | 914,275–915,426 | 71.9% | Mce8 |

> [!NOTE]
> *fbpA*, *fbpB*, and the 2nd *fbpC* all map to overlapping coordinates (~802,556–803,217), suggesting a single locus matching multiple VFDB references. Similarly, *sypC*, *pvdI*, and *pvdL* overlap at ~265,003–265,804 within the mycobactin biosynthesis region — these are likely cross-hits from the nonribosomal peptide synthetase (NRPS) domains of the *mbt* cluster rather than genuine phytotoxin/pyoverdine genes.

## Contig_1 DESC06-unique genes

These DESC06-unique genes reside on the main chromosome:

| Gene | Coords on contig_1 | Identity % | Category |
|---|---|---|---|
| *mce1D* | 4,872,255–4,873,893 | 81.1% | Mce1 |
| *mce3C* | 1,236,207–1,237,529 | 78.7% | Mce3 |
| *mce4E* | 627,929–629,043 | 80.6% | Mce4 |
| *fbpA* | 3,303,551–3,304,421 | 84.6% | Adherence (fbpB hit) |
| *fbpB* | 3,303,551–3,304,421 | 84.6% | Adherence |
| *phoP* | 648,939–649,658 | 88.2% | Regulation |
| *phoR* | 649,733–651,124 | 78.4% | Regulation |
| *regX3* | 4,155,106–4,155,790 | 88.6% | Regulation |

## Key Conclusions

1. **contig_2 is a displaced chromosomal fragment**, not a plasmid or foreign element — proven by the presence of 6 conserved core genes (*mbtE*, *mbtC*, *glnA1*, *kasB*, *caeA*, *trpD*) that are on the main chromosome in all other isolates.

2. **The d4 dDDH of 84.6%** for contig_2 alone (vs. *M. cosmeticum* DSM 44829) further confirms same-species origin.

3. **The DESC06-unique genes on contig_2** cluster into two main genomic regions:
   - **~250–275 kb region**: Extended mycobactin biosynthesis cluster (*mbtA–I*), with NRPS domains also hitting *sypC*/*pvdI*/*pvdL* as cross-matches
   - **~800–915 kb region**: Adherence (*fbp* paralogs), GPL (*mmpL4b*, *mps1*), and MCE transporters (*mce7*, *mce8*)

4. **Some "unique" hits are artifacts**: *sypC* (95.7% to a *Pseudomonas* phytotoxin) and *pvdI*/*pvdL* (pyoverdine siderophore) are almost certainly NRPS domain cross-hits from the mycobactin cluster, not genuine exotoxin/pyoverdine genes.
