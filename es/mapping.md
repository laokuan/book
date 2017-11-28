###格式

```
//用put方法提交，my_index是索引名字
PUT my_index
{
  "mappings": {
    "user": {
      "_all":       { "enabled": false  },
      "properties": {
        "title":    { "type": "text"  },
        "name":     { "type": "text"  },
        "age":      { "type": "integer" }
      }
    },
    "blogpost": {
      "_all":       { "enabled": false  },
      "properties": {
        "title":    { "type": "text"  },
        "body":     { "type": "text"  },
        "user_id":  {
          "type":   "keyword"
        },
        "created":  {
          "type":   "date",
          "format": "strict_date_optional_time||epoch_millis"
        }
      }
    }
  }
}
```