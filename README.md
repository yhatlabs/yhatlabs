# YHat Labs

Prediction models for structured data, served through a hosted API.

| Model | What | Card |
|---|---|---|
| **ChakraTS** | zero-shot probabilistic time-series forecasting | https://huggingface.co/yhatlabs/ChakraTS |
| **ChakraTS-Lab** | research configuration of ChakraTS (benchmarks only) | https://huggingface.co/yhatlabs/ChakraTS-Lab |
| **ChakraTab** | tabular classification and regression | coming |

API access: https://yhatlabs.com

## Contents

- `benchmarks/` result files exactly as submitted to the public leaderboards.
  - `gift_eval/<entry>/all_results.csv` + `config.json`: [GIFT-Eval](https://github.com/SalesforceAIResearch/gift-eval) format, 97 dataset configurations.
- `notebooks/`
  - `gift_eval_reproduce.ipynb`: regenerates the GIFT-Eval `all_results.csv` by calling the API (official `gift_eval` data loading and `gluonts` metrics). Run it from the `notebooks/` folder of the [gift-eval](https://github.com/SalesforceAIResearch/gift-eval) repository; it starts with a quick subset and prints each rerun next to the submitted row. Needs an API key; evaluation keys are issued on request.

A Python client (`pip install yhatlabs`) will be published here once the API surface is final.

## License

The code and result files in this repository are released under the [Apache License 2.0](LICENSE). The models are not distributed; they are served through the API under the YHat Labs API terms.
