# Understanding LLM Settings  
We can configure different LLM parameters to get different results for your prompts. Different parameters values are best-suited for different use cases.  

#### Temperature
Increasing temperature leads to more randomness, which encourages more diverse or creative outputs.  
In general, low temperatures (0-1) are suitable for fact-based QA as it encourages more factual and concise responses. High temperatures are more suitable for text generation (essay/poem creation, etc).  

#### Top_P  
If you use Top P it means that only the tokens comprising the top_p probability mass are considered for responses, so a low top_p value selects the most confident responses.  
This means that a high top_p value will enable the model to look at more possible words, including less likely ones, leading to more diverse outputs.  
**The general recommendation is to alter temperature or Top P but not both.**  

#### Max Length  
Number of tokens the model generates. Essentially output response length.  

#### Penalty  
Frequency Penalty - applies a penalty on the next token proportional to how many times that token already appeared in the response and prompt.
Presence Penalty - similar to the former, but the penalty is the same for all repeated tokens instead of increasing with every repeat.  
This setting prevents the model from repeating phrases too often in its response. If you want the model to generate diverse or creative text, you might want to use a higher presence penalty.  
**The general recommendation is to alter the frequency or presence penalty but not both.**
