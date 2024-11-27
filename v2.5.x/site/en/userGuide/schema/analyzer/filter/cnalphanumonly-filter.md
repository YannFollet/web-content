---
id: cnalphanumonly-filter.md
title: Cnalphanumonly​ Filter
summary: The `cnalphanumonly` filter removes tokens that contain any characters other than Chinese characters, English letters, or digits.​
---

# Cnalphanumonly​

The `cnalphanumonly` filter removes tokens that contain any characters other than Chinese characters, English letters, or digits.​

## Configuration​

The `cnalphanumonly` filter is built into Milvus. To use it, simply specify its name in the `filter` section within `analyzer_params`.​

```python
analyzer_params = {​
    "tokenizer": "standard",​
    "filter": ["cnalphanumonly"],​
}​

```

The `cnalphanumonly` filter operates on the terms generated by the tokenizer, so it must be used in combination with a tokenizer.

After defining `analyzer_params`, you can apply them to a `VARCHAR` field when defining a collection schema. This allows Milvus to process the text in that field using the specified analyzer for efficient tokenization and filtering. For details, refer to [Example use](analyzer-overview.md#Example-use).​

## Example output​

Here’s an example of how the `cnalphanumonly` filter processes text:​

**Original text**:​

```python
"Milvus 是 LF AI & Data Foundation 下的一个开源项目，以 Apache 2.0 许可发布。"​
```

**Expected output**:​

```python
["Milvus", "是", "LF", "AI", "Data", "Foundation", "下", "的", "一个", "开源", "项目", "以", "Apache", "2.0", "许可", "发布"]​
```