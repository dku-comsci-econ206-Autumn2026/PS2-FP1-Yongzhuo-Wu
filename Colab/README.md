# PS2 · How to Make AI Applications Reduce Sycophancy

Yongzhuo Wu · FP1 · Session B · yw650@duke.edu  
COMSCI/ECON 206 · Professor Luyao Zhang

## Reproduce the result

1. Open [PS2.ipynb in Colab](https://colab.research.google.com/github/dku-comsci-econ206-Autumn2026/PS2-FP1-Yongzhuo-Wu/blob/ps2/Colab/PS2.ipynb).
2. Select **Runtime → Run all**. Initial installation requires internet. Python 3.12 or later is required. The first cell prepares a dedicated environment and preserves Colab's loaded NumPy/SciPy. No dataset, API key, or random seed is needed.
3. The eight code cells report auction outcomes, platform payoffs, equilibrium/deviation checks, the cost boundary, and the access comparison. The final output should say **ALL CHECKS PASS** and give the actual execution time and package versions.

`PS2.ipynb` contains my final Colab run from October 6, 2026, 11:08:10 UTC (19:08:10 Beijing time), using Python 3.13.16. All eight code cells passed, including 14,406 bid-deviation checks, four matching Nashpy cases, and 121 cost-boundary mixed-strategy pairs. Its code, execution counts and saved outputs are unchanged from my Colab download. Metadata `ps2_records` contains the execution record, my identification of the run, and the source-hash input. `requirements.txt` lists the six pinned solver dependencies.

The final cell computes SHA-256 from four model-function sources, the matching Nashpy subprocess source, and model parameters. The saved hash input is embedded in notebook metadata; the final cell also exports JSON copies into the runtime. SHA-256 uses UTF-8 JSON with sorted keys and compact separators. The test harness, timestamps, versions and display formatting are outside this scope. Changing a covered function or parameter changes the digest. The notebook runs without external JSON inputs.

## Strategic model

Two profit-maximizing applications choose H (verifiable correction) or S (sycophancy) simultaneously. Baseline payoffs are ordered (A, B).

| A / B | H | S |
|---|---|---|
| H | (3,3) | (1,5) |
| S | (5,1) | (4,4) |

This is a static, complete-information platform game with unobserved concurrent actions. Nash equilibrium is the appropriate concept. S strictly dominates without correction sales. Each H commits one identical slot before bidding. Platforms know the scenario value vector; each of three users has private unit demand, quasilinear utility, and no budget constraint. Verifiable delivery and payment enforcement are assumed.

At fixed supply k, the highest k sealed bids win and pay the highest losing bid. Lower user ID breaks ties; there is one round, no reserve, and no loser payment. Each H application receives one payment minus delivery cost c.

## Expected results

| Case | Pure Nash equilibria | Revenue at equilibrium | Correction surplus W | Access |
|---|---|---|---|---|
| No service | SS | 0 | 0 | 0/3 |
| Strong (5,4,3), c=0 | HH | 6 | 9 | 2/3 |
| Weak (3,2,1), c=0 | SS | 0 | 0 | 0/3 |
| Strong, c=1 | HH, HS, SH, SS | 6, 4, 4, 0 | 7, 4, 4, 0 | 2/3, 1/3, 1/3, 0/3 |

Strong demand gives H-minus-S gain 1−c against either action: unique HH for c<1, unique SS for c>1. At c=1, every independent mixed-strategy pair is also an equilibrium. Equal payoff rows for A and columns for B establish indifference. Nashpy returns the four pure corners and a degeneracy warning; it does not enumerate the continuum. Weak demand gives gain −1−c, hence SS for c≥0.

Four hand-transcribed Nashpy cases match the model with maximum profitable deviation 0 (tolerance 1e-10). Checks include costs 0.5 and 2, 121 mixed pairs, six conditional auction rows, and 14,406 finite bid-deviation comparisons. The finite grid checks implementation; the threshold argument establishes fixed-supply truthfulness under the stated assumptions. General multi-unit demand, common values, budgets, variable quality, collusion, and unenforceable delivery fall outside this claim.

Payments are transfers: buyer utility plus revenue equals allocated value. W is allocated value minus ck, excluding baseline profits and unmodeled harms. At k=2, an equal lottery gives each user access probability 2/3 and expected allocated value 8 (strong) or 4 (weak), versus auction 9 or 5. Lottery financing and its platform equilibrium are unspecified. A synthetic 2–1 vote selects a service goal, not factual truth.

## Behavioral boundary and sources

One retained author reflection preferred correction A for 17×6=112, stated WTP 3 versus 0, and recorded no purchase. It neither estimates population demand nor identifies the vector (5,4,3). Completed preference observations have n=1; actual bids, purchases, platform actions and delayed learning each have n=0. Interface tests do not enlarge the human sample. Studio screenshots and original review records accompany the article source. Tone/order controls and incentivized purchasing remain an unperformed design.

Game theory predicts supply; social choice evaluates correction surplus and access; the auction changes net profit. Sycophancy evidence: [Sharma et al., ICLR 2024](https://openreview.net/forum?id=tvhaxkMKAn) and [Cheng et al., Science 2026](https://doi.org/10.1126/science.aec8352). Closer mechanism precedents reward information and costly effort: [Miller et al. (2005)](https://doi.org/10.1287/mnsc.1050.0379), [Witkowski et al. (2013)](https://doi.org/10.1609/hcomp.v1i1.13089). This application assumes verified quality and connects auction-funded supply with a cost/access challenge. Auction foundation: [Vickrey](https://doi.org/10.1111/j.1540-6261.1961.tb02789.x), [Roughgarden, §3](https://theory.stanford.edu/~tim/w14/l/l21.pdf); solver: [Nashpy](https://nashpy.readthedocs.io/en/stable/).

## Project materials and release

Canonical repository: [https://github.com/dku-comsci-econ206-Autumn2026/PS2-FP1-Yongzhuo-Wu](https://github.com/dku-comsci-econ206-Autumn2026/PS2-FP1-Yongzhuo-Wu), release **ps2**.  
Interactive demonstration: [https://huggingface.co/spaces/dku-comsci-econ206-2026/AI-Sycophancy](https://huggingface.co/spaces/dku-comsci-econ206-2026/AI-Sycophancy).  
The repository contains the proposal PDF, `COMSCI_ECON206_PS2_Overleaf_Student_Template/`, `Colab/`, `Poster/`, and `Hugging Face/`. The paper source includes Figure 1 and supporting records. The A0 PPTX and matching PDF are in `Poster/`.


AI assisted with code and supporting materials; the author's model decisions, checks, and personal Colab execution are documented in Author Notes. Appendix A.1 retains the nine historical disclosures.

## Figure legend

The article, poster and interface use a shared palette. Labels repeat each meaning so interpretation does not depend on color alone. Figure 1 remains readable in grayscale and protanopia/deuteranopia previews.

| Role | Color | Line or label | Purpose |
|---|---|---|---|
| Text | #212A33 | Explicit labels | Dark text on light backgrounds |
| Computed model | #003399 | Solid outlines and scenario labels | Assumed inputs and calculated outcomes |
| Author reflection | #006633 | Solid outlines and observed-record labels | The single completed self-reflection |
| Proposed test | #56616B | Dashed outline and proposed-test label | Distinguishes future research from observations |
| Neutral surface | #F4F6F7 | Shared-question panel | Groups related information |
| Background | #FFFFFF | White | Print readability |
| Divider | #CFD5D9 | Table rules | Separates rows and panels |
| Interface error | #C00000 | Explicit error message | Identifies invalid inputs without relying on color |
