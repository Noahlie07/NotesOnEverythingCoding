# Introduction to Prompt Engineering  
Prompt engineering is useful for altering the response of an LLM to make it closer to what we need.  

## Elements of Prompt Engineering  
A prompt may contain the following elements:
1. Instruction - a specific task or instruction you want the model to perform
PRO TIP: Try giving the AI a persona. (ex. You are a food reviewer.) 
3. Context - external information or additional context that can steer the model to better responses
4. Input Data - the input or question that we are interested to find a response for
5. Output Indicator - the type or format of the output.

```
Classify the following text into negative, neutral, and positive. // Instruction
Text: This food is amazing! //Input Data
Sentiment: //Output Inidicator
```

## Variables in Prompt Engineering  
In prompt engineering, variables are simply placeholders that users can quickly change to generate different responses.  
ex.  
Generate a {tone='professional'} email about {subject}.  
tone and subject are variables for the user to alter. However, tone is set as professional as default, and will take on that value unless specified otherwise by the user.  
There are tools for users to easily alter variables. Ex.  
  
```
prompt_template = "Explain {concept} to a {audience} in {tone}."
filled_prompt = prompt_template.format(
    concept="blockchain", 
    audience="beginner", 
    tone="simple terms"
)
response = openai.ChatCompletion.create(model="gpt-4", messages=[{"role": "user", "content": filled_prompt}])
```

## General Tips for Designing Prompts  
1. Use **Commands** (ex. "Write", "Classify", "Summarize", "Translate", "Order", etc)
2. Be more **specific**. The more descriptive and detailed the prompt is, the better the results.
3. Provide **Examples** of input and output that you want
4. **Separate** Instruction, Context, and Examples using clear separators like "###"
5. **Avoid saying what not to do but say what to do instead**
6. Add **constraints** whenever they apply

