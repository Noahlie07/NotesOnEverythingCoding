# Data Preprocessing  

This note will cover loading datasets from huggingface and preprocessing it, including three steps:
1. Loading dataset from HF
2. Tokenizing Dataset
3. Dynamic Padding

## Loading Dataset from HF  
Load a dataset on HF from HF's dataset library
```
from datasets import load_dataset

raw_datasets = load_dataset("glue", "mrpc") # load a random dataset called mrpc
raw_datasets
```
Datasets loaded from HF will normally be in the following format:
```
DatasetDict({
    train: Dataset({
        features: ['sentence1', 'sentence2', 'label', 'idx'],
        num_rows: 3668
    })
    validation: Dataset({
        features: ['sentence1', 'sentence2', 'label', 'idx'],
        num_rows: 408
    })
    test: Dataset({
        features: ['sentence1', 'sentence2', 'label', 'idx'],
        num_rows: 1725
    })
})
```

## Tokenizing the Dataset  
```
tokenized_training_dataset = tokenizer(
    raw_datasets["train"]["sentence1"],
    raw_datasets["train"]["sentence2"],
    padding=True,
    truncation=True,
)
```

## Dynamic Padding  
Padding all samples in the dataset to be of the same length  
```
from transformers import DataCollatorWithPadding

data_collator = DataCollatorWithPadding(tokenizer=tokenizer)
padded_tokenized_training_dataset = data_collator(tokenized_training_dataset)
```
