- Introduction
- Background
- Model Architecture
- Why Self-Attention
- Training
- Results
- Conclusion
- Attention Visualizations

# Journal Club Recap: "Attention Is All You Need" (arXiv 1706.03762)

This journal club briefing covers "Attention Is All You Need" (Vaswani et al., 2017), the paper that introduced the Transformer. The dominant sequence transduction models of the day were built on complex recurrent or convolutional neural networks, with an encoder and decoder connected through attention. The Transformer proposes a new, simple architecture based solely on attention mechanisms, dispensing with recurrence and convolutions entirely. It keeps the classic encoder-decoder shape — six identical layers stacked on each side, built from multi-head self-attention and point-wise feed-forward networks. The results are striking. On WMT 2014 English-to-German, the big model reaches 28.4 BLEU, improving on the existing best results, including ensembles, by more than 2 BLEU. On WMT 2014 English-to-French, it sets a new single-model state of the art of 41.8 BLEU. Training took 3.5 days on eight GPUs, a small fraction of the training cost of the best models from the literature.

## Comprehension Quiz

Attendees can take the quiz here:
https://docs.google.com/forms/d/e/1FAIpQLSe3ii4OQOu8C8GjevZZmpAYz4BKfDzNej0fhr-FzQniMBBzkQ/viewform