# Tokenizers In Depth  
This note dives deeper into the first step of a pipeline; Passing inputs to a tokenizer  

## What is Tokenizing  
It is a two-step process;  
1. Converting text to smaller texts called tokens. There are multiple different methods for doing so (ex.character-based tokenization, word-based, subword-based, etc)
2. Converting tokens to input IDs (numerical representation). Each tokenizer model will have different vocabularies (ways in which they map tokens to their input id)
```
Method 1:
tokens = tokenizer.tokenize(original_text)
input_ids = tokenizer.convert_tokens_to_ids(tokens)
or
Method 2:
encoded_input = tokenizer(original_text) # encoded_input["input_ids"] for input_ids
```

## What is the output of a tokenizer?
```
original text = "Hello, I'm a single sentence!"
encoded_input = tokenizer(original text)
print(encoded_input)
```
This will return a dictionary with three fields:
- input_ids: numerical representations of your tokens
- token_type_ids: these tell the model which part of the input is sentence A and which is sentence B 
- attention_mask: this indicates which tokens should be attended to and which should not (discussed more in a bit)
```
{'input_ids': [101, 8667, 117, 1000, 1045, 1005, 1049, 2235, 17662, 12172, 1012, 102], 
 'token_type_ids': [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0], 
 'attention_mask': [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1]}
```
We can decode input_ids back to our original text.  
```
orginal text = tokenizer.decode(encoded_input["input_ids"])
```

## Specific Arguments of a Tokenizer  
1. return_tensors = "pt"/"np" - tokenizer will return output in the form of pytorch or numpy tensors.
2. padding inputs - If we ask the tokenizer to pad the inputs, it will make all sentences the same length by adding a special padding token to the sentences that are shorter than the longest one
3. truncatng inputs - some tensors may be too long for a particular model to process. Hence, we truncate/cut all tensors that pass a specific length.
```
encoded_input = tokenizer(original_text, padding=True, truncation=True, max_length=5 #5 tokens, return_tensors="pt")
```
