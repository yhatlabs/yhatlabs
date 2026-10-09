# YHat Labs

Foundation AI models for tabular data, served through a hosted API. Send your data, get predictions back in one call, no training or tuning.

| Model | What it does | Card | Access |
|---|---|---|---|
| **ChakraTS** | Zero-shot probabilistic time-series forecasting: nine quantiles per step, known-future covariates, any regular frequency | https://huggingface.co/yhatlabs/ChakraTS | API |
| **ChakraTab** | Classification and regression on tables, with class probabilities | https://huggingface.co/yhatlabs/ChakraTab | API |
| **ChakraTS-Lab** | Research configuration of ChakraTS, benchmark entries only | https://huggingface.co/yhatlabs/ChakraTS-Lab | evaluation on request |

Website and results: https://yhatlabs.com/models · API access: https://yhatlabs.com/models/access

## Benchmark standing (October 2026)

| Benchmark | Model | Standing | Status |
|---|---|---|---|
| [fev-bench](https://huggingface.co/spaces/autogluon/fev-bench) (Amazon) | ChakraTS | 1st by win rate (85.5%), 2nd by skill score | merged, [autogluon/fev #192](https://github.com/autogluon/fev/pull/192) |
| [TIME](https://huggingface.co/spaces/Real-TSF/TIME-leaderboard) (ICML 2026) | ChakraTS | 2nd of 31 | published, [Real-TSF/TIME-Output PR #46](https://huggingface.co/datasets/Real-TSF/TIME-Output/discussions/46) |
| [GIFT-Eval](https://huggingface.co/spaces/Salesforce/GIFT-Eval) (Salesforce) | ChakraTS | 3rd among non-agentic models (MASE 0.670, CRPS 0.461) | merged, [gift-eval #225](https://github.com/SalesforceAIResearch/gift-eval/pull/225) |
| [TabArena](https://tabarena.ai) | ChakraTab | top 5 | under review |

Every entry is zero-shot under the benchmark's official protocol; benchmark data is never used for anything other than scoring.

## Contents

- `benchmarks/` result files exactly as submitted to the leaderboards.
  - `fev_bench/ChakraTS/chakrats_api.csv`: the [fev](https://github.com/autogluon/fev) summary file (100 tasks, SQL, MASE, WAPE, WQL per task).
  - `gift_eval/<entry>/all_results.csv` + `config.json`: [GIFT-Eval](https://github.com/SalesforceAIResearch/gift-eval) format, 97 dataset configurations.
  - TIME per-task predictions (93 MB of `.npz`) live in the TIME dataset repository linked above.
- `notebooks/`
  - `gift_eval_reproduce.ipynb`: regenerates the GIFT-Eval `all_results.csv` by calling the API (official `gift_eval` data loading and `gluonts` metrics). Run it from the `notebooks/` folder of the [gift-eval](https://github.com/SalesforceAIResearch/gift-eval) repository; it starts with a quick subset and prints each rerun next to the submitted row. Needs an API key; evaluation keys are issued on request.

Coming here next: head-to-head results against classical methods (seasonal naive, ETS, ARIMA, LightGBM, CatBoost, tuned gradient boosting) on public industry datasets, as shown on the website, and a Python client (`pip install yhatlabs`).

## License

The code and result files in this repository are released under the [Apache License 2.0](LICENSE). The models are not distributed; they are served through the API under the [YHat Labs terms](https://yhatlabs.com/terms).
