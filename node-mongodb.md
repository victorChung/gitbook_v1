
#####命令位置

*    `/usr/local/mongodb/bin`
    
    > 该命令会显示占用8080端口的进程，有其 pid ,可以通过pid关掉该进程


#####默认配置启动服务

*    `mongod`
	> 默认数据库文件位置/data/db



#####指定位置启动服务

*    `sudo mongod --dbpath /usr/local/mongodb/data/db --logpath /usr/local/mongodb/logs/mongod.log --logappend --fork`

	> --dbpath数据库文件位置，--logpath日志文件位置，--logappend追加的形式，--fork后台运行的方式
	
	


#####连接mongodb服务

*    `mongo`

#####退出连接

*    `exit`

---

#####新建/切换数据库

*    `use test`

	> 存在则切换，没有则创建
	

#####查看所有数据库

*    `show dbs`
	
	
#####查看当前所在数据库

*    `db`
	
#####删除当前数据库

*    `db.dropDatabase()`

---

[官方文档](https://www.mongodb.org.cn/manual/Collection/)

#####新建集合（表）

*    `db.createCollection("colname")`

	> 执行insert或save可直接创建集合
	
#####查看该数据库下所有集合（表）

*    `show collections 或 show tables`

#####删除集合（表）

*    `db.colname.drop() `

---

#####插入文档（行）

*    `db.colname.insert(<document>)`

*    `db.colname.save(<document>)`

	> 如果不指定 _id 字段 save() 方法类似于 insert() 方法。如果指定 _id 字段，则会更新该 _id 的数据。
	
#####插入多条数据

*    `db.colname.insertMany([<document 1>, <document 2>], {
      writeConcern: <document>,
      ordered: <boolean>
   })`

	> document：要写入的文档。
	
	> writeConcern：写入策略，默认为 1，即要求确认写操作，0 是不要求。
	
	> ordered：指定是否按顺序写入，默认 true，按顺序写入。

#####更新数据(update / replaceOne)

*    `db.collection.update(
		   <query>,
		   <update>,
		   {
		     upsert: <boolean>,
		     multi: <boolean>,
		     writeConcern: <document>
		   }
		)`
		
	> query : update的查询条件，类似sql update查询内where后面的。
	
	> update : update的对象和一些更新的操作符（如$,$inc...）等，也可以理解为sql update查询内set后面的
	
	> upsert : 可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
	
	> multi : 可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
	
	> writeConcern :可选，抛出异常的级别。
	
 upsert | multi | desc
 :-----:|-----:|:-----:
 true | true | 全部添加
 false | true | 全部更新
 true | false | 只添加第一条
 false | false | 只更新第一条
	
		
*    `db.collection.replaceOne(<query>, <update>, {
		     upsert: <boolean>
		   })`
		   
---

#####删除数据

*	`db.collection.deleteOne()`   

#####删除多条数据

*	`db.collection.deleteMany()`
