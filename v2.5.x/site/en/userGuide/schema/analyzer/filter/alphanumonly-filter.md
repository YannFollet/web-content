---
id: alphanumonly-filter.md
title: Alphanumonly​ Filter
summary: The `alphanumonly` filter removes tokens that contain non-ASCII characters, keeping only alphanumeric terms. This filter is useful for processing text where only basic letters and numbers are relevant, excluding any special characters or symbols.
---

# Alphanumonly​

The `alphanumonly` filter removes tokens that contain non-ASCII characters, keeping only alphanumeric terms. This filter is useful for processing text where only basic letters and numbers are relevant, excluding any special characters or symbols.​

## Configuration​

The `alphanumonly` filter is built into Milvus. To use it, simply specify its name in the `filter` section within `analyzer_params`.​

```python
analyzer_params = {​
    "tokenizer": "standard",​
    "filter": ["alphanumonly"],​
}​
```

The `alphanumonly` filter operates on the terms generated by the tokenizer, so it must be used in combination with a tokenizer.

After defining `analyzer_params`, you can apply them to a `VARCHAR` field when defining a collection schema. This allows Milvus to process the text in that field using the specified analyzer for efficient tokenization and filtering. For details, refer to [Example use](analyzer-overview.md#Example-use).​

## Example output​

Here’s an example of how the `alphanumonly` filter processes text:​

**Original text**:​

```python
"Milvus 2.0 @ Scale! #AI #Vector_Databasé"​
```

**Expected output**:​

```python
["Milvus", "2", "0", "Scale", "AI", "Vector"]​
```