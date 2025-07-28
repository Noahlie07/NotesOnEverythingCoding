# Tokenizers In Depth  
This note dives deeper into the first step of a pipeline; Passing inputs to a tokenizer  

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
