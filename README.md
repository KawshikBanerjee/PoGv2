# PoGv2

==========================================

[modified from the source for test purpose]

==========================================

## Knowledge Graph and Datasets

Before executing PoG, you need to deploy **Freebase** on your local machine. Please follow the [installation instructions](https://github.com/GasolSun36/ToG/tree/main/Freebase).
We utilize CWQ, WebQSP, and GrailQA datasets to evaluate PoG. These datasets are located in `data/` with aliases in `cope_alias/`.

### Running

After installing all necessary configurations, you can execute PoG using the following command:

```sh
python main_freebase.py \
--dataset cwq \ # the dataset
--max_length 4096 \ # the max length of LLMs output
--temperature_exploration 0.3 \ # the temperature in exploration stage
--temperature_reasoning 0.3 \ # the temperature in reasoning stage
--depth 4 \ # the search depth
--remove_unnecessary_rel True \ # whether removing unnecessary relations
--LLM_type gpt-3.5-turbo \ # the LLM
--opeani_api_keys sk-xxxx \ # your own api keys
```

All prompts used in experiments are in the `prompt_list.py` file.

### Evaluation

We use **Exact Match** as the evaluation metric. After obtaining the final result file, please evaluate the results using the following command:

```sh
python eval.py \
--dataset cwq \ # the dataset
--output_file PoG_cwq_gpt-3.5-turbo.jsonl \ # the result file
```
