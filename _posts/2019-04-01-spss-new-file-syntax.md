---
layout: post
title:  "SPSS Define new variables in empty data set"
date:   2019-04-01 19:07:19
categories: [SPSS]
comments: false
---
The Problem;

> When working with SPSS syntax, you would like to create a new datafile, i.e. one that does not have any records/data. If you try the normal `compute`,`string` or `Var1 (f1.0)`, you will get an error;
```
>Error # 100.  Command name: COMPUTE
>This command is not permitted before the beginning of file definition
>commands.
>This command not executed”
```

The workaround for this is;
```
NEW FILE. 
INPUT PROGRAM. 
NUMERIC v1 (f2) v2 (f2) v3 (f2). 
STRING str1 (a8). 
NUMERIC v4 (f3) v5 (f5). 
END FILE. 
END INPUT PROGRAM. 
EXECUTE. 
```
or
```
DATA LIST FREE /VAR1 to VAR100.
FORMATS VAR1 TO VAR100 (F1.0).
BEGIN DATA.
END DATA.
EXECUTE.
```



