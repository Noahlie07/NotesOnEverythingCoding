# Transformer Models in HF
The 🤗 Transformers library provides the functionality to create and use shared transformer models. HF's Model Hub contains millions of pretrained models that anyone can download and use.  

## Working with HF pipelines
```
from transformers import pipeline
```
The most basic object in the 🤗 Transformers library is the pipeline() function. It connects a model with its necessary preprocessing and postprocessing steps, simplifying the process of using a HF model.
