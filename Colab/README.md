# Computational Model of Paid Corrections

Yongzhuo Wu · COMSCI/ECON 206 · Professor Luyao Zhang

Open [Final.ipynb in Colab](https://colab.research.google.com/github/dku-comsci-econ206-Autumn2026/PS2-FP1-Yongzhuo-Wu/blob/main/Colab/Final.ipynb) and select **Runtime → Run all**. The eight code cells contain the complete calculation. Setup requires Python 3.12 or later and internet for the initial dependency installation. The versions in `requirements.txt` run in an isolated environment. No dataset, API key or random seed is needed.

## Model

Two apps simultaneously choose correction H or sycophancy S. Baseline payoffs are HH=(3,3), HS=(1,5), SH=(5,1), SS=(4,4). Each H commits one correction attempt. Three unit-demand users have assumed values (5,4,3) or (3,2,1). At fixed supply, the top k bids win and pay bid k+1; lower user ID breaks ties.

An accepted correction earns payment; delivery cost c is incurred for every attempt. The common acceptance probability q is independent of bids. The funded lottery charges learners zero and pays providers t per accepted correction. Audit and appeal costs have a separate sponsor account.

## Results and checks

- Strong demand with q=1,c=0 gives HH; weak demand gives SS.
- Strong demand with q=1,c=1 leaves every independent pure or mixed pair as an equilibrium.
- At q=.7,c=0, HH and SS coexist with symmetric p(H)=2/3.
- Strict lottery honesty requires qt−c>3. At t=4,q=1,c=0, the reserve is 9.5 and no-appeal spending is 8.5.
- Accepted 102 releases a deposit of 3; disputed 103 holds it until review, then refunds 3. A second review computes its verdict from the answer.

The notebook checks 14,406 finite bid deviations, eight separately entered Nashpy matrices, 121 cost-one mixed pairs, settlement conservation, reserve sufficiency and 24 acceptance/cost scenarios. The last cell displays the execution time, parameters, source fingerprint, environment and sensitivity results, then prints **ALL CHECKS PASS**. These outputs are saved with the notebook.

## Evidence

The October 5 reflection has n=1: A preferred, stated willingness to pay 3 versus 0. Purchases, actual bids, external participants, app choices, delayed learning and live-LLM tests have n=0. Accuracy, liking, hypothetical payment and purchasing are separate outcomes. The arithmetic examples are deterministic rule tests. Demand, acceptance and costs are model inputs; the accuracy–tone and learning studies are research proposals.

References and the literature comparison appear in the paper. The notebook implements the stated model and does not query a language model or process payments.
