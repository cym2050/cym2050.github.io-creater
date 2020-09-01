---
title: "Node"
date: 2020-08-21T22:05:19+08:00
draft: true
---

global
process
__dirname 当前文件所在路径
module node全局对象

内置模块：
fs：
    readFile('文件路径', (err, data) => {}) #toString("默认是utf8")，readFile是异步的
    readFileSync 同步读取文件方法，会等待它读取完才执行后面的操作

<img src="C:\Users\Alan\AppData\Roaming\Typora\typora-user-images\image-20200821233209282.png" alt="image-20200821233209282" style="zoom:50%;" />


http：


nodemon：node服务开发时实时编译库

body-parser：解析请求的body
app.use(bodyParser.urlencoded(extended: false)) 作为中间件使用，urlencoded、json

express  RESTful api(GET\POST\PUT\DELETE)

```
响应返回简单的文字或json对象
const app = express();
app.get('/', (req, res) => {
    req.query #请求的查询字符串
    req.body 
    req.header
    req.params
    re.status().send('something');
})
响应返回HTML文件
const app = express();
app.use(express.static(__dirname + '/public'))
app.listen();

```

console.time('tag:')
comsole.timeEnd('tag:')

'sdfsdfs'.split -> ['s',....]
['s', 'f', 'r'].splice(index, number) 删除


SQL:
createdb
insert info
select * from 插入一个数据
alter table 为表添加一个项
update tablename set item where 更新值
模糊搜索
排序
对所有数据进行数学计算
join连接两个表
Drop table

knex.js:nodeJS连接数据库的包，可以用于所有关系型数据库

transcation() ：多个数据库操作同时成功，此次操作才成功，只有部分操作成功，则会回退一完成的操作




### 完善
输入框格式检查
服务端邮箱检查
错误弹出 邮箱错，密码错
一刷新就要重新登录怎样解决

heroku:一个可以部署服务端，数据库的服务商
heroku create
git push heroku master
heroku open
heroke log --tail 可以在命令行里调试

CMD设置代理： set http_proxy=http://127.0.0.1:11081