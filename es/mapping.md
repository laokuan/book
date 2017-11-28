###格式
  this is a code;
  <>
  
> ## 这是一个标题。
> 
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
> 
> 给出一些例子代码：
> 
>    return shell_exec("echo $input | $markdown_script");


```
//用put方法提交，my_index是索引名字
PUT my_index
{
  "mappings": {
    //这个是type类型
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