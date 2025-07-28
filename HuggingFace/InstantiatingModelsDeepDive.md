# Instantiating Models  
This note dives deeper into step 2 of the pipeline process; Passing input into the model.  

The AutoModel class and its associates are actually simple wrappers designed to fetch the appropriate model architecture for a given checkpoint. It’s an “auto” class meaning it will guess the appropriate model architecture for you and instantiate the correct model class. However, if you know the type of model you want to use, you can use the class that defines its architecture directly:
```
from transformers import AutoModel

model = AutoModel.from_pretrained("bert-base-cased")

from transformers import BertModel

model = BertModel.from_pretrained("bert-base-cased")

# same thing
```

## Saving and Reusing Models  
A model's save_pretrained() method saves the model’s weights and architecture configuration.  
```
model.save_pretrained("directory_on_my_computer")
```
This will save two files in the directory, **config.json** and **pytorch_model.bin**  
- The config.json file has all the necessary attributes needed to build the model architecture. This file also contains some metadata, such as where the checkpoint originated and what 🤗 Transformers version you were using when you last saved the checkpoint.
- The pytorch_model.bin file is known as the state dictionary; it contains all your model’s weights.
The two files work together: the configuration file is needed to know about the model architecture, while the model weights are the parameters of the model.

To reuse a saved model, use the from_pretrained() method again:
```
from transformers import AutoModel

model = AutoModel.from_pretrained("directory_on_my_computer")
```

## Uploading our Models to the hub  
At our terminal, run huggingface-cli login. (this can also be done in our code, just search up the way)  
Then, push the model into the hub via `model.push_to_hub("my-model-name")`  

Then, others can access my model via:
```
from transformers import AutoModel

model = AutoModel.from_pretrained("your-username/my-awesome-model")
```

