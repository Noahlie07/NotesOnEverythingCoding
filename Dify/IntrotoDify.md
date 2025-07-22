# Dify  
---  
### What is Dify?
Dify is an open-source platform for developing AI applications without using much code. It contains both ready-made AI applications for us to try with their UI or extract to our own applications via their API, and an interface for us to create our own AI application to be tried and extracted.  

#### Application Types  
Dify offers five application types with both example templates and blank templates for us to plug, play, and extract.
1. Chatbot - A conversational LLM
2. Text generator - for text generation tasks like writing stories, reports, etc
3. Agent - A conversational intelligent assistant capable of task decomposition, reasoning, and tool invocation
4. Workflows
Workflows are designed to break down complex tasks into simpler ones, allowing us to define how tasks shall be solved, and which LLMs to use.
There are two types of workflows:
1. Chatflow - Designed for conversational scenarios, including customer service, semantic search, and other conversational applications that require multi-step logic in response construction.
2. Workflow - Geared towards automation and batch processing scenarios, suitable for high-quality translation, data analysis, content generation, email automation, and more.

**Prompt Engineering is absolutely critical for maximizing the capabilities of LLMs, and therefore of Dify.**  

## Creating a Workflow: Key Terminology and Concepts  

### Nodes  
Nodes are the key components of a workflow. By connecting node with different functionalities, you can execute a series of operations within the workflow.  

#### Start Node
The “Start” node is a critical preset node in the Chatflow / Workflow application. It provides essential initial information, such as user input and uploaded files, to support the normal flow of the application and subsequent workflow nodes.  
##### Configuring the Start Node  
On the Start node’s settings page, you’ll find two sections: **“Input Fields”** and preset **System Variables**.  
**Input Fields** - prompt users for additional information. These Additional Informations include:
1. Text/Paragraph
2. Numerical Value
3. Single File/Bunch of Files
**Preset System Variables** -  preset system-level parameters in Chatflow / Workflow applications that can be globally accessed by other nodes in the application. They are typically used in advanced development scenarios, such as building multi-turn dialogue applications, collecting application logs and monitoring data, or recording usage behavior across different applications and users.
https://docs.dify.ai/en/guides/workflow/node/start for more info.

#### End Node  
The "End" node defines the final output content of a workflow. Every workflow needs at least one end node after complete execution to output the final result.  
The end node must declare one or more output variables, which can reference any upstream node’s output variables.  

### Variables  
Variables are used to link the input and output of node within a workflow.  

#### Normal Workflow Variables  
a data container for the output of a node. Can be referenced by other nodes (ex. the output variable of a previous node is referenced by the "end" node as the variable to be outputted to the user)  

#### System Variables  
pre-set system-level parameters within Chatflow / Workflow App that can be globally read by other nodes.  

#### Environment Variables  
Environment variables are used to protect sensitive information involved in workflows, such as **API keys and database passwords used when running workflows**. They are stored in the workflow rather than in the code, allowing them to be shared across different environments.  

#### Conversational Variables  
Temporary variables stored within the same Chatflow session, ensuring that this information can be referenced across multiple rounds of chatting within the current chatflow. This can include context, files uploaded to the chatting box(coming soon), user preferences input during the conversation. Conversational Variables can be defined and written to using variable assigners nodes.  

  
