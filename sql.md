## 存储过程
``` sql
CREATE [ OR ALTER ] { PROC | PROCEDURE }
    [schema_name.] procedure_name [ ; number ]
    [ { @parameter [ type_schema_name. ] data_type }
        [ VARYING ] [ = default ] [ OUT | OUTPUT | [READONLY]
    ] [ ,...n ]
[ WITH <procedure_option> [ ,...n ] ]
[ FOR REPLICATION ]
AS { [ BEGIN ] sql_statement [;] [ ...n ] [ END ] }
[;]

<procedure_option> ::=
    [ ENCRYPTION ]
    [ RECOMPILE ]
    [ EXECUTE AS Clause ]
```

### \[OR ALTER\]
CREATE,创造一个新的存储过程<br>
OR ALTER,修改一个已存在的存储过程<br>
### {PROC|PROCEDURE}
创建语句既可以是PROC 或者 PROCEDRUE;
### \[schema_name\]
procedure 所以位于的数据库名称
### \[; number\]
创建一个整数来代表一组存储过程.当删除的时候可以用数据代表这组存储过程
### \[type_schema_name\]
该类型所位于的数据库名称
### \[VARYING\]
仅适用于cursor,该参数指定参数是支持作为输出参数的。
### \[=default\]
该参数提供一个参数的默认值
### \[,....n\]
可以提供多个参数
