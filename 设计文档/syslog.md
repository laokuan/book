```
let syslogDataSource = {
  tableList: [],
  chartList: [{name: '高', data: []}, {name: '中', data: []}, {name: '低', data: []}],
  devList: [{
    name: "华为测试1",
    id: 141,
    type: 1,
    org_id: 1,
    ip: "172.16.254.2"
  }
  ],
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