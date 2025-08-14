# Milvus  

## What is Milvus?
Milvus is a vector database that supports local deployment (MilvusLite), single machine deployment in a docker container(Milvus Standalone), and deployment into cloud containers (Milvus Distributed) over Kubernetes.  

Disclaimer: It has its own embedding model, but it is weak, so it is better to use external embedding models.
Disclaimer: Towhee and Langchain provide pipelines that can automate embedding generation -> storage into Milvus. Worth looking into, ask Deepseek. However, this gives us less control over settings obviously.  

## Basics of MilvusLite  
`pip install pymilvus` to download Milvus' Python library  

Import MilvusClient, which is MilvusLite's module. Then, create a local vector DB
```
from pymilvus import MilvusClient

client = MilvusClient("demoDatabase.db") # To read/write and close the created DB, we conduct functions on the object 'client'
```

## Creating Schema - CUstomizing the fields in our collection  
```
from pymilvus import FieldSchema, CollectionSchema, DataType
fields = [
            FieldSchema(name="doc_id", dtype=DataType.INT64, is_primary=True, auto_id=False),
            FieldSchema(name="embedding", dtype=DataType.FLOAT_VECTOR, dim=512),  # CLIP embedding dimension
            FieldSchema(name="content", dtype=DataType.VARCHAR, max_length=65535),
            FieldSchema(name="source", dtype=DataType.VARCHAR, max_length=255),
            FieldSchema(name="content_type", dtype=DataType.VARCHAR, max_length=50),
            FieldSchema(name="ref", dtype=DataType.VARCHAR, max_length=255),
        ]
schema = CollectionSchema(fields=fields, description="---")
```
Alternatively, https://milvus.io/docs/create-collection.md
## Basics of MilvusStandalone  

When creating a collection, always specify its schema and index params (these params specify how the vector field is stored and how similarity search in the vector field is going to occur.  
```
from pymilvus import connections

try:
    connections.connect(host="", port="", timeout=10)
except MilvusException as e:
    ...

if utility.has_collection(collection_name):
    collection = Collection(collection_name)
else:
    collection = Collection(collection_name, schema=schema)
    # Create index for vector field
        index_params = {
            "metric_type": "L2",
            "index_type": "IVF_FLAT",
            "params": {"nlist": 1024}
        }
    collection.create_index(field_name="embedding", index_params=index_params)

# basic operations on collection (collection in this case is kinda similar to client, except that it is an individual collection and only collection-related operations
collection.load()
collection.insert()
```
See base64 milvus shi (the one I created while working for HASLA) for more examples  

## Operations on Client  
See https://milvus-io.github.io/milvus-sdk-python/pythondoc/v0.3.0/api.html#client  


#### Creating a Collection using create_collection()
In Milvus, we need a collection to store vectors and their associated metadata. You can think of it as a table in traditional SQL databases.  
When creating a collection, you can define schema and index params to configure vector specs such as dimensionality, index types and distant metrics.  

```
if client.has_collection(collection_name="demo_collection"):
    client.drop_collection(collection_name="demo_collection")
client.create_collection(
    collection_name="demo_collection",
    schema = schema, # once we already defined the schema (see below)
    dimension=768,  # The vectors we will use in this demo has 768 dimensions
)
```

#### Schema: What is Schema?  
A Milvus collection is like a table in a traditional database, but optimized for vector operations. **Each collection has a schema that defines its fields (which are like columns)**.  
Typical fields in a standard collection include:
- id: id of sample
- vector: the vector embedding of the sample
- text (optional): original text of the sampel
- subject (optional): the subject the original text classify under

We define particular custom fields using FieldSchema(). Then, we use CollectionSchema() to combine all the fields together.  
```
from pymilvus import FieldSchema, CollectionSchema, DataType

# Define fields
id_field = FieldSchema(
    name="id", 
    dtype=DataType.INT64, 
    is_primary=True,  # Primary key
    auto_id=True      # Let Milvus auto-generate IDs (optional)
)

text_field = FieldSchema(
    name="text", 
    dtype=DataType.VARCHAR, 
    max_length=500    # Required for VARCHAR
)

vector_field = FieldSchema(
    name="vector", 
    dtype=DataType.FLOAT_VECTOR, 
    dim=384           # Dimension of embeddings (e.g., 384 for all-MiniLM-L6-v2)
)

# Combine fields into a schema
schema = CollectionSchema(
    fields=[id_field, text_field, vector_field],
    description="A collection for text embeddings with author metadata"
)
```

#### Storing Data into the VectorDB using insert() and flush()
```
client.insert(collection_name="demo_collection", data=data)
client.flush() # saves the data
```
The data should be a list of dictionaries (where each dictionary is a sample), whose keys match the field headers of the schema.
```
data = [
  {"id": 0, "vector": embeddings[0]}
] # for example only
```
