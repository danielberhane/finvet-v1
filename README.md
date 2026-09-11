# FinVet v1

Financial misinformation detection with retrieval-augmented generation and external
fact-checking. This is the reference implementation for the paper below.

> **Superseded.** FinVet v2 replaces this design with a multi-agent pipeline and a
> deterministic verdict comparator: [danielberhane/finvet](https://github.com/danielberhane/finvet).
> This repository is kept as the published artifact and is not maintained.

## Paper

Daniel Berhane Araya and Duoduo Liao. *FinVet: A Collaborative Framework of RAG and External
Fact-Checking Agents for Financial Misinformation Detection.*
2025 IEEE International Conference on Big Data (BigData), Macau SAR, China, December 2025.
[IEEE Xplore](https://ieeexplore.ieee.org/document/11400848) · [arXiv:2510.11654](https://arxiv.org/abs/2510.11654)

```bibtex
@inproceedings{araya2025finvet,
  author    = {Berhane Araya, Daniel and Liao, Duoduo},
  title     = {FinVet: A Collaborative Framework of RAG and External Fact-Checking
               Agents for Financial Misinformation Detection},
  booktitle = {2025 IEEE International Conference on Big Data (BigData)},
  year      = {2025},
  month     = dec,
  address   = {Macau SAR, China},
  publisher = {IEEE},
  isbn      = {979-8-3315-9447-3},
  issn      = {2573-2978},
  url       = {https://ieeexplore.ieee.org/document/11400848}
}
```

## What it does

A claim is checked along two retrieval pipelines and against the Google Fact Check API, and
the verdict is decided by confidence-weighted voting across those pathways. Three tiers of
processing adjust the verification strategy according to retrieval confidence, and the output
carries source attribution and an explicit uncertainty flag.

## Quick start

```bash
pip install pyarrow==11.0.0
pip install git+https://github.com/danielberhane/finvet-v1.git

financial-misinfo config --hf-token YOUR_HF_TOKEN --google-api-key YOUR_GOOGLE_API_KEY
financial-misinfo ui
```

Verify a single claim from the command line:

```bash
financial-misinfo verify "Tesla's stock price doubled in 2023"
```

Requires Python 3.8 or later, 3.10 recommended, a HuggingFace token, and a Google API key with
the Fact Check API enabled. The index files `metadata.pkl` and `faiss_index.bin` download
automatically, or can be placed in `~/.financial-misinfo/`.

## License

MIT. See [LICENSE](LICENSE).
