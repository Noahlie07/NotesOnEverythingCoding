## What are Config Files for?  
Config files make sure a certain thing (could be software, os, frameworks, hosting, etc) work in a specific way.  
For example, there are some config files (ex. prettier) that define how your code should be written syntax-wise. They are used so that everyone follows a uniform code syntax.   
There are also config files (ex. eslite) that monitor the quality of your code (ex. produces an error if we have a variable that is defined but is never used.  
In Web Dev, we need a config file to declare all the javascript packages we will be using. Then, we need to bundle up JavaScript modules if we use them. Module bundlers like Vite have config files that determine how exactly the modules are to be bundled.

Normally, config files can be written in multiple different languages; json, javascript, yaml, etc.  

## What is YAML?
YAML is a data serialization language and is normally used for config files. Its difference from other config file languages is only its syntax, where it uses spacing and indentation for structure.  
It is referred to with the dot extension .yaml or .yml

### YAML syntax
key-value pairs  
string - automatically detect, don't need to put quotation marks around strings, but can use single or double quotes if we'd like.
multilined-string - >, newline, and single space indentation
ex.
multilinestring: >
  bla
  bla 
  bla
integer/float - automatically detect
boolean - true/false, on/off  

#### List
1 .List Syntax One
``` # famous_players become a list object. Kane, Son are treated as lists
famous_players:
 - Kane
 - Son 
```
2. List Syntax Two
```
famous_players_2: [Kane, Son]
```

#### Dictionary
```
management_staff:
 general_manager: Thomas Frank
 fitness_coach: bla bla
```
