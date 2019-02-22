
ujson – JSON encoding and decoding
=====

This module implements a subset of the corresponding CPython module, as described below. For more information, refer to the original CPython documentation: [json](https://docs.python.org/3.5/library/json.html#module-json).

This modules allows to convert between Python objects and the JSON data format.

## Functions

### dump

```python
ujson.dump(obj, stream)
```

Serialise obj to a JSON string, writing it to the given stream.

### dumps

```python
ujson.dumps(obj)
```

Return obj represented as a JSON string.

### load

```python
ujson.load(stream)
```

Parse the given stream, interpreting it as a JSON string and deserialising the data to a Python object. The resulting object is returned.

Parsing continues until end-of-file is encountered. A ValueError is raised if the data in stream is not correctly formed.

### loads

```python
ujson.loads(str)
```

Parse the JSON str and return an object. Raises ValueError if the string is not correctly formed.

