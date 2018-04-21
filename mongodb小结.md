## node.js操作mongodb
#### 1. 所需模块：
- mongodb 模块
- mc对象:
> const mc = mongodb.MongoClient;
#### 2.连接数据库

```
var db = null;
mc.connect('mongodb://localhost:27017',(error,client)=>{
    db = client.db('1801');
});
```
#### 3.数据库操作
- 增加文档

```
async insert(_collection,_data){
    try{
        let result = await db.collection(_collection).insert(_data);
        return apiResult(result.insertedCount > 0,result.result)
        
    }catch(error){
        // 抛出错误
        return apiResult(false,error);
    }
}
```
- 查询文档

```
async select(_collention,_condition={}){
    try{
        let items = await db.collection(_collection).find(_condition).toArray();
        let result = apiResult(items.length > 0,items);
        return result;
    }catch(error){
        return apiResule(false,error);
    }
};
```

- 删除文档
- 修改文档

