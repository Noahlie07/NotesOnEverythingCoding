# Transfer Learning  

## Pretrained Model Vs Fine-tuned Model  
Base Model - the architecture of the model along with random weights  
Pretrained Model - Base Model trained on an extremely large amount of data (ex. model trained to understand english)
Fine-tuned Model - taking a pretrained model and training it on additional databases related to the specific task we are conducting.  
(ex. training a model that understands English (pretrained model) and training it on a financial news database)  
The act of converting a pretrained model to a finetuned model is called **transfer learning**, as the knowledge of the pretrained model is essentially transferred to the finetuned model.  

## Architecture Vs Checkpoint
Architecture - the skeleton of a model, meaning the definiton of its layers and operations between layers)
Checkpoints - The weights that will be loaded into an architecture  
(For example, BERT is an architecture while bert-base-cased, a set of weights trained by the Google team for the first release of BERT, is a checkpoint.)
