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

### How to know if a huggingface post is an architecture or a checkpoint?
Architecture:  
The underlying design (ex. Qwen3). It defines the model’s structure (layers, attention mechanisms, etc.) but has no trained weights.  
Clues: Named generically (e.g., "GPT", "BERT"). Appears in library docs or research papers, not as downloadable files.  
  
Model (Checkpoint):  
A trained instance of an architecture (weights + config). ex. Qwen3-Coder-480B-A35B-Instruct (this is a checkpoint of the Qwen architecture).  
Clues:Has a specific version (e.g., "480B-A35B-Instruct"). Listed under Files and versions with downloadable files (e.g., pytorch_model.bin).  
