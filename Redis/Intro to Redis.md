# Redis  

## What is Redis?
Redis is an open-source, in memory (RAM) data structure store. As its in-memory, its frequently used as a caching layer in front of larger databases to store frequently accessed data from memory.  
Redis supports various data structures in simple **key-value pairs**, including values as lists, sets, sorted sets, hashes, and more.  
It is frequenlty used in **Multi-Session Supporting** due to its cache nature!

## Redis Python API/SDK  
https://redis.io/docs/latest/develop/clients/redis-py/  
Create an instance of Redis Client
```
r = redis.Redis(host='localhost', port=6379, decode_responses=True)
```

### Storing Key - Value Pairs
**storing strings as values**
```
r.set("key-name", "string")
string = r.get("key-name")
print(string.decode('utf-8'))
```  
**storing lists, dictionaries, and list of dictionaries as values** - method 1: utilize JSON strings  
```
my_dict = {"key_1":"val_1", "key_n":"val_n"}
my_dict_json = json.dumps(my_dict)
r.set("key_name", my_dict_json)
my_list = [bla, bla, bla]
my_list_json = json.dumps(my_list)
r.set("key_name", my_list_json)
my_list_of_dicts = [
{"key_1":"val_1", "key_n":"val_n"},
{"key_1":"val_1", "key_n":"val_n"}
]
my_list_of_dicts_json = json.dumps(my_list_of_dicts)
r.set("key_name", my_list_of_dicts_json)
```
**storing lists** - method 2: utilizing rpush
RPUSH is a Redis command that inserts one or more specified values at the tail (right end) of a list stored at a given key. I flist does not exist, it will be the first entry.
LRANGE is a command to return the list
```
r.rpush("key-name", value)
r.lrange("key-name", 0, -1) # whole list
r.lrange("key-name", 0, 3) # indexes 0, 1, and 2
```
  
**storing dictionaries as redis hashes** 
```
r.hset("key-name", mapping={"key_1":"val_1", "key_n":"val_n"})
val_1 = r.hget("key-name", "key_1")
whole_dict = r.hgetall("key-name")
```

## Session Timeouts  
This is vital for multi-session supporting using redis.  
Using session timeout in Redis primarily involves setting an expiration time (TTL - Time To Live) for the keys that store session data. When a key's TTL expires, Redis automatically deletes it, effectively ending the session.  
The EXPIRE command sets a timeout on an existing key.  
```
r.expire("key_name", 3600) # 3600 seconds TTL, 
```
