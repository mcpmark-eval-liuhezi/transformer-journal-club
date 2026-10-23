# Transformer Training Details — Journal Club Fact Sheet

Paper: "Attention Is All You Need" (Vaswani et al.), arXiv:1706.03762

All facts below are taken directly from the paper's LaTeX source, with section numbers for slide citations.

## 1. Optimizer — Section 5.3 ("Optimizer")

- Optimizer: **Adam**
- $\beta_1 = 0.9$
- $\beta_2 = 0.98$
- $\epsilon = 10^{-9}$

## 2. Learning-Rate Schedule — Section 5.3 ("Optimizer")

$$lrate = d_{\text{model}}^{-0.5} \cdot \min(step\_num^{-0.5},\; step\_num \cdot warmup\_steps^{-1.5})$$

- $warmup\_steps = 4000$
- **During warmup** (first 4,000 training steps): the learning rate increases **linearly**.
- **After warmup**: the learning rate decreases **proportionally to the inverse square root of the step number**.

## 3. Hardware and Schedule — Section 5.2 ("Hardware and Schedule")

- Hardware: one machine with **8 NVIDIA P100 GPUs**.
- **Base model**: each training step took about **0.4 seconds**; trained for a total of **100,000 steps**, or **12 hours**.
- **Big model**: step time **1.0 seconds**; trained for **300,000 steps** (**3.5 days**).

## Cross-check against the public arXiv abstract page (arxiv.org/abs/1706.03762, v7)

- English-to-German BLEU, exactly as shown on the page: *"Our model achieves 28.4 BLEU on the WMT 2014 English-to-German translation task, improving over the existing best results, including ensembles by over 2 BLEU."* The **28.4 BLEU** figure is confirmed on the live page.
- Venue note: the listing's metadata contains **no journal-ref / venue row**. The metadata table reads exactly:
  - Comments: 15 pages, 5 figures
  - Subjects: Computation and Language (cs.CL); Machine Learning (cs.LG)
  - Cite as: arXiv:1706.03762 [cs.CL] (or arXiv:1706.03762v7 [cs.CL] for this version)
  - DOI: https://doi.org/10.48550/arXiv.1706.03762
  - The paper was published at NIPS 2017, but the arXiv listing itself does not state a venue.

## Supplementary training facts (same source, for Q&A)

- **Training data (Section 5.1, "Training Data and Batching")**: WMT 2014 English-German, ~4.5M sentence pairs, byte-pair encoding with a shared source-target vocabulary of ~37,000 tokens. English-French: WMT 2014, 36M sentences, 32,000 word-piece vocabulary. Batches of ~25,000 source and 25,000 target tokens.
- **Regularization (Section 5.4)**: residual dropout $P_{drop} = 0.1$ (base model); label smoothing $\epsilon_{ls} = 0.1$.
