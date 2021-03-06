# Disclaimer

This is not an official Google product. This is work-in-progess research code
and is completely unsupported and may even be unfinished.

# Models for extractive summarization

Inference, learning, and evaluation code for extractive summarization.

Models currently have 2 main components -- Extractors and Losses.

Main model is *CompressiveSummarizerModel*.

1. Extracts RNN embeddings and scores for each token in an input article using
   *ModelInputs* and *SummarizerFeatures* classes.
1. Scores are ingested by *Extractor* to compute extractions and likelihoods,
   samples, marginals.
1. *ExtractorLoss* provides gradients to the *Extractor* and
   *SummarizerFeatures* models from supervision.

*Extractor* implementations:

* *IndependentCardinalityPotentialsExtractor*: uses k-constrained inference to
  extract summaries.
* *TreeConstrainedExtractor*: uses k- and discourse-parse constrained 
  inference to extract summaries.

*ExtractorLoss* implementations:

* *OracleXentExtractorLoss*: learn to extract summaries using supervised
  labels.
* *ROUGEReinforceExtractorLoss*: learn to extract summaries using ROUGE-1
  recall with the ground truth summary and REINFORCE algorithm.
