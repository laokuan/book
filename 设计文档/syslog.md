1. ###前端和后端的数据模型
##### syslog的趋势图前端数据结构如下
```
最终的json结构
const result = {
  list: dataSource,
  pagination: {
    total: dataSource.length,
    pageSize,
    current: parseInt(params.currentPage, 10) || 1,
  },
};
```
```
//上面的list中的对象结构
let syslogDataSource = {
  //表格数据
  tableList: [
    {
      id: i,
      dev_ip: '10.37.54.220',
      to_ip: '10.125.16.110',
      record_time: '1506578530432',
      msg_overview: '<1' + i + ' > CEF: 0 | Imperva Inc.',
      from_ip: '9.5.0.8',
      msg: '来自10.37.54.220的级别为1 - 6的日志--index: 1'
    }
  ],
  //图表数据
  chartList: [
    {name: '高', data: [[10000, 30000], []}, 
    {name: '中', data: []}, 
    {name: '低', data: []}
  ],
  //设备列表
  devList: [
    {
      name: "华为测试1",
      id: 141,
      type: 1,
      org_id: 1,
      ip: "172.16.254.2"
    }
  ],
  //组织结构
  orgList: [{
    name: "集团总部", 
    parent_ids: "0", 
    id: 1
  },{
    name: "FLOW测试设备",
    parent_ids: "1",
    id: 9
  }],
};
```
##### syslog的TOP数据结构如下
```
最终的json结构
const result = {
  list: dataSource,
  pagination: {
    total: dataSource.length,
    pageSize,
    current: parseInt(params.currentPage, 10) || 1,
  },
};
```
```
//上面的dataSource的数据结构如下
let syslogDataSource = {
  //返回的数据表
  tableList: [
    { "value": 聚合之后的数量, "name": "不同的聚合字段值 " }
  ],
  //饼图的数据
  chartList: [
    {"value": 聚合之后的数量, "name": "不同的聚合字段值 ", "sort": 排序值}
  ],
  //设备列表
  devList: [{
    name: "华为测试1",
    id: 141,
    type: 1,
    org_id: 1,
    ip: "172.16.254.2"
  }],
  //设备分类
  devTypeList: [{
    type_name: "网络设备",
    id: 1
  },{
    type_name: "安全设备",
    id: 2
  },{
    type_name: "服务器设备",
    id: 3
  },{
    type_name: "应用设备",
    id: 4
  }],
  //组织结构
  orgList: [{
    name: "集团总部",
    parent_ids: "0",
    id: 1
  }],
  //聚合条件,其中的vale必须和es中的字段对应
  aggregation: [
      {name: "设备类型", value: "dev_type"},
      {name: "设备IP", value: "dev_ip_addr"},
      {name: "事件优先级", value: "log_level"},
      {name: "事件名称", value: "msg_overview"},
      {name: "源地址", value: "log_src_ip"},
      {name: "目的地址", value: "log_dst_ip"},
    ],
};
```

