1. ###前端和后端的数据模型
##### syslog的趋势图前端数据结构如下
```
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
    {name: '高', data: []}, 
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