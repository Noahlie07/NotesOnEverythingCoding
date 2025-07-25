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
