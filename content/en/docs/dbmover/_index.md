---
title: "Migrate MySQL"
linkTitle: "Migrate MySQL"
weight: 2
description: >
  a light and smart database migration tool,no installtion.
---

# DBMover for MySQL

DBMover is a database migration tool for developers and DBA,you can use it to migrate object structure and data between MySQL databases.

# Key Feature

#### Easy to use
DBMover is writen in Go,little and light,you just supply target/source db info ,it can work well.

#### On flying,no middle-data store,cross OS-platform
DBMover pull and sink data on flying,do not take space to save temp data,it's stateless,and you can migrate MySQL between Linux/Windows/MacOS/SUSE.

#### Efficient mulit thread model
DBMover automated split tables(or one bigtable) into slices,and use Goroutines to handle one or more table slices,
by this way we can achive a great migrate throughtput.

#### Flexible configuration
DBMover supply kinds of args to run migrate job,you can migrate table/view/procedure/trigger,or migrate a whole schema.You can put data and structure into one job,it will finish all things. It can accept commandline args or JSON file input.

#### Docker container running
You can run dbmover in k8s or k3s platform,supply different tablelist args to each dbmover pod,it's really a parallel working model across multiple hosts.
In this mode,you should collect every pod's migrate status to get a summary view by yourself.

# Quick Start

#### Get dbmover for MySQL
- Download [dbmover_for_linux](https://grdscloud.github.io/website/download/dbmover/1.0.0/dbmover_for_linux)
- Download [dbmover_for_mac](https://grdscloud.github.io/website/download/dbmover/1.0.0/dbmover_for_mac)




#### Privileges and grants
```
# source MySQL
grant process,select on *.* to connectUser@'%';
flush privileges;

# target MySQL
grant process,select,insert,update,delete on *.* to connectUser@'%';
flush privileges;

```

#### Little migrate examples

- migrate grds.table1-3 data to target database,no truncate,launch 8 threads to work


```
./dbmover --source-dbstring=dbuser/pwd@10.10.98.232:3306 /
          --target-dbstring=dbuser/pwd@10.10.98.239:3306 /
		  --tables=grds.table1,grds.table2,grds.table3 /
		  --move-model=onlydata --do-truncate=n --work-threads=8
```

- migrate grds objects structure to target database,ignore if target objects exists


```
./dbmover --source-dbstring=dbuser/pwd@10.10.98.232:3306 /
          --target-dbstring=dbuser/pwd@10.10.98.239:3306 /
		  --tables=grds.table1,grds.table2 --views=grds.view1 --procedures=p_usercount --triggers=tri_firewall /
		  --move-model=onlymeta --exists-handle=ignore
```

- migrate whole database(saledb,orderdb) to target MySQL,including structure and data(target database must exists)


```
#schemas is conflict with object option(views/tables/procedures/triggers)
#dbmover will ignore object option if you supply schemas option

./dbmover --source-dbstring=dbuser/pwd@10.10.98.232:3306 /
          --target-dbstring=dbuser/pwd@10.10.98.239:3306 /
		  --schemas=saledb,orderdb  /
		  --move-model=all --exists-handle=ignore --do-truncate=n
```

#### View migrate prograss and status
- get migrate result,you can supply summary/detail args

```
./dbmover --get-result=detail
./dbmover --get-result=summary
```


#### Handle object/schema mapping
if source/target object has different schema or name,we supply object mapping,just like this:


```
# table mapping(tab1 map to target sch2:maptab1,tab2,tab3 no mapping)
--tables=sch1.tab1:sch2:maptab1,sch.tab2,sch.tab3

# schema mapping(schema must exists)
--schemas=sourceschm:targetschm
```

#### Pre-checking before migrate
before your  migration,you can use --only-check to pre-check source/target envirment,dbmover will give you a checklist


```
./dbmover --source-dbstring=dbuser/pwd@10.10.98.232:3306 /
          --target-dbstring=dbuser/pwd@10.10.98.239:3306 /
		  --schemas=saledb,orderdb --only-check=y
```


# Parameters


parameter | description
---|---
--source-dbstring | source db connect string: username/pwd@192.168.0.1:3306
--target-dbstring | target db connect string: username/pwd@192.168.0.1:3306
--enable-ssl-source | enable source SSL connect (default n)
--enable-ssl-target | enable target SSL connect (default n)
--ssl-cafile-source | source SSL CA file path
--ssl-cafile-target | target SSL CA file path
--only-check | n \| y,only check the migrating conditions and give you a checklist,do not migrate anything (default "n")
--move-model | onlydata \| onlymeta \| all, you can choose move table data,object structure or both (default "onlydata")
--exists-handle | ignore \| drop,used for onlymeta\|all model,when target object exists (default "ignore")
--do-truncate | n \| y,truncate target table before data moving (default "n")
--enable-merge | n \| y,enable replace/merge to target table,if table has no PK/UK,it will run in insert mode (default "n")
--tables | use comma to split tables,colon to map table,for example --tables=sc1.table1,sc1.table2,sc1.tableA:sc1.tableC
--triggers | special the trigger list
--views | special the view list
--procedures | special the procedure list
--schemas | special the schema list,it will ignore tables/triggers/procedures/views option
--work-threads | number of working thread,max value 48 (default 4)
--max-connections | max source or target database connections,max value 64 (default 8)
--count-model | estimate \| count,the way we get a table row count (default "estimate")
--split-rowcount | special table split size,used for parallel moving a table data,max 999999 (default 50000)
--commit-batchsize | batch commitsize for target table rows insert/merge,max 50000 (default 200)
--fetch-batchsize | batch fetchsize for source table rows,max 100000 (default 10000)
--json-file | use jsonfile to special move objects,this option will ignore objects/schemas option
--json-model | object \| schema,special jsonfile content is about objects or whole schemas,must be used with --json-file
--get-result | summary \| detail,get moving prograss and error status
--log-output | console \| file,log output model,the file is dbmover.log (default "console")


# Little tips about dbmover

#### How dose data migration work
DBMover use goroutine threads to migrate data in parallel mode,we estimate table's rowcount,and split table into slices,scatter table slices into goroutine threads,every goroutine handle one or more table slice,it's in charge of source pulling, target writing , progress status updating.

We use serveral parameters to control the data migration,you can try and test different parameter combinations.


```
--work-threads special the number of goroutine threads for working
--split-rowcount special table split size,default is 50000,max is 999999,for example a 1,000,000 rows table will be splited into 20 slices
--fetch-batchsize special the rowcount every time we fetched,this rows will be stored in memory,and writen to target in batch mode
--commit-batchsize special the size of target table commit transtion,default is 200,max is 50000
```

#### How dose table splitting work
We estimate a table's rowcount,use --split-rowcount to compute the slice number,firstly,we choose primary key/unique key columns,if it's a nokeys table,we choose another columns to split. number/datetime/timestamp column can be uses for splitting,if a table dose not have any such columns,splitting will fail.
When we choose one column for splitting,we will get the column's max/min value,comput the step length,
finally each slice will have its own data range.

#### About --count-model and EstimateRows,SyncedRows
Default --count-model=estimate,this is a fast way to sample table rowcount,
but the result is not exactly，another option is count,slowly but exactly,we recommend using estimate to speed up your sample prograss.If the changes on source table haven't stopped, whatever option you choose,EstimateRows will hardly equel to SyncedRows.

#### JSON input support
You can use --json-file and --json-model to special input args,here is the JSON example

- [objectddl.json](http://note.youdao.com/s/dhyvIIfp)
- [schemaddl.json](http://note.youdao.com/s/FrnsUm8h)
- [tablesync.json](http://note.youdao.com/s/BkO5R7Pt)
- [schemasync.json](http://note.youdao.com/s/PoDPRSny)

# Support datatype

DataType | isSupport
---|---
tinyint | yes
smallint | yes
mediumint | yes
int | yes
bigint | yes
integer | yes
tinyint unsigned| yes
smallint unsigned| yes
mediumint unsigned| yes
int unsigned| yes
bigint unsigned| yes
integer unsigned| yes
double | yes
float | yes
decimal | yes
numeric | yes
char | yes
varchar | yes
tinytext | yes
smalltext | yes
mediumtext | yes
text | yes
longtext | yes
tinyblob | yes
smallblob | yes
mediumblob | yes
blob | yes
bool | yes
date | yes
time | yes
datetime | yes
timestamp | yes

# Known issues

- unexpected EOF/busy buffer

```
# sometimes you may encounter error,it means that migration get failed
# make sure the network throughtput between your source/target database and dbmover host is good
# truncate target data and retry your migration
[mysql] 2020/11/09 17:38:50 packets.go:72: unexpected EOF
[mysql] 2020/11/09 17:38:50 packets.go:427: busy buffer
[mysql] 2020/11/09 17:38:51 packets.go:72: unexpected EOF
[mysql] 2020/11/09 17:38:51 packets.go:427: busy buffer
[mysql] 2020/11/09 17:38:51 packets.go:72: unexpected EOF
[mysql] 2020/11/09 17:46:00 packets.go:72: read tcp 126.126.0.58:54225->10.10.98.232:3306: read: connection reset by peer
```







