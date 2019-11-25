![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 如何查询SQL审核日志
#### How To Query The SQL Audit Log
**发布-日期: 2014年7月10日 (评论)**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一个查询SQL审核日志的快速脚本。切记你可以做一个SELECT * FROM sys.fn_get_audit_file，但这可能在得到你想要的结果之前经历很长的一段时间，因为它看起来是在磁盘上的文件。
如果想找到一个更好的视图，试一下这个小小的逻辑。



## English
Here’s a quick script to query the SQL Audit log. Remember; you could always do a SELECT * FROM sys.fn_get_audit_file, but this could be a reeeaaallly looong time before you get the results you want cause it’s look across a file on the disk.
For a more isolated view of what you are looking for; try this little piece of logic.


---
## Logic
```SQL
use master;
set nocount on
select
'run at' = convert(char, event_time, 9) , 'user' = database_principal_name
, 'database' = database_name
, 'object' = object_name
, 'statement' = statement
from
sys.fn_get_audit_file
(
'\\MyShare\MyFolder\My_Audit_file_770000.sqlaudit'
, default
, default
)
where
database_name = 'MyDatabase'
and event_time between '2014-07-10 15:00' and '2014-07-10 16:00' order by
event_time desc


```
希望对你有帮助。 （Hope this is useful）


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

