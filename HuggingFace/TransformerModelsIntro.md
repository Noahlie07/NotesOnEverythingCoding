# Transformer Models in HF
The 🤗 Transformers library provides the functionality to create and use shared transformer models. HF's Model Hub contains millions of pretrained models that anyone can download and use.  

## Working with HF pipelines
```
from transformers import pipeline
```
The most basic object in the 🤗 Transformers library is the pipeline() function. It connects a model with its necessary preprocessing and postprocessing steps, simplifying the process of using a HF model.  
  
**FYI: The model is downloaded and cached when you create the classifier object. If you rerun the command, the cached model will be used instead and there is no need to download the model again.**  

HF Pipelines work by accepting a task parameter where we state the task we want to conduct. An object is then instantiated from the task-specified pipeline.  
To conduct the task, we pass in all necessary arguments necessary for the task into the object.  

```
# for example, a question-answering pipeline
question_answerer = pipeline("question-answering") # question_answerer object is created
question_answerer(
    question="Where do I work?",
    context="My name is Sylvain and I work at Hugging Face in Brooklyn",
) # question_answerer object takes in specific arguments required for its task
```

**Which model will the pipeline use?**  
HF defines a default model for each task. However, we can specify the model we would like to use using the model argument. 
```
# for example
translator = pipeline("translation", model="Helsinki-NLP/opus-mt-fr-en")
```

## Under the Hood of HF Pipelines  
Pipelines handle all of preprocessing (converting text to numerical representations), passing inputs through the model, and postprocessing (cnverting numerical representations to text).  

### First Step: Preprocessing with a Tokenizer  
The first step inside a pipeline is to preprocess the text using a tokenizer.  
We can either use the default tokenizer defined by the pipeline or define a specific tokenizer to use.  
The process of tokenizing, in detail, involves:
- Splitting the input into words, subwords, or symbols (like punctuation) that are called tokens
- Mapping each token to an integer
- Adding additional inputs that may be useful to the model
Preprocessing needs to be done in exactly the same way as when the model was pretrained. This means we must use the same checkpoint weights as our model.
Below is code for initializing a tokenizer.  
```
# For Example
from transformers import AutoTokenizer

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
tokenizer = AutoTokenizer.from_pretrained(checkpoint)
```
The tokenizer will take raw input (string or a list of strings), and output a tensor (of size num.of.inputs x vector_space_of_token_vector_representation).  
This is because our model later on will only accept tensors.  
```
raw_inputs = [
    "I've been waiting for a HuggingFace course my whole life.",
    "I hate this so much!",
]
inputs = tokenizer(raw_inputs, padding=True, truncation=True, return_tensors="pt") #"pt" for pytorch tensors, "np" for numpy tensors
```

### Second Step: Model  
The model takes an input numerical tensor (produced by preprocessing) and generates an output numerical tensor (to be passed on to postprocessing).  
The model needs to be loaded with the same checkpoint as the pre-processing.
```
from transformers import AutoModel

checkpoint = "distilbert-base-uncased-finetuned-sst-2-english"
model = AutoModel.from_pretrained(checkpoint)
```
The vector output by the Transformer module is usually large. It generally has three dimensions:
- Batch size: The number of sequences processed at a time (2 in our example).
- Sequence length: The length of the numerical representation of the sequence (16 in our example).
- Hidden size: The vector dimension of each model input.
```
outputs = model(**inputs)
# print(outputs.last_hidden_state.shape) to see the shape of the model's vector output
```
