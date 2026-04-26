# DM_SQL_RPT

`DM_SQL_RPT` 是一个基于 `EXEC_ID` 的 SQL 分析包，用来集中查看一次 SQL 执行相关的对象、计划和运行信息。

## 功能说明

- `GET_ALL_INFO`：按顺序输出完整诊断信息
- `GET_TAB_INFO`：查看 SQL 涉及的表信息
- `GET_IDX_INFO`：查看相关表的索引信息
- `GET_STAT_INFO`：查看相关表和列的统计信息
- `GET_SQL_PLAN`：查看 SQL 执行计划
- `GET_SQLET_INFO`：查看 ET 节点运行信息
- `GET_SQLPLN_CACHE`：查看缓存执行计划相关信息

## 使用前提

- 已在达梦数据库中创建 `DM_SQL_RPT` 包
- 已拿到需要分析的 `EXEC_ID`
- 当前账号有相关系统视图和系统表的查询权限

## 使用步骤

1. 执行源码文件创建包

```sql
DM_SQL_RPT_v1.0_sourcecode.sql
```

2. 准备要分析的 `EXEC_ID`
3. 按需调用单个过程，或直接调用 `GET_ALL_INFO`

## 调用示例

```sql
CALL DM_SQL_RPT.GET_ALL_INFO(11410);
CALL DM_SQL_RPT.GET_TAB_INFO(10303);
CALL DM_SQL_RPT.GET_IDX_INFO(10303);
CALL DM_SQL_RPT.GET_STAT_INFO(10303);
CALL DM_SQL_RPT.GET_SQLET_INFO(11148);
```

## 输出内容

- 表信息：查看 SQL 访问了哪些表，以及表的基础属性
- 索引信息：查看目标表上的索引定义和索引列
- 统计信息：查看表和列的统计信息情况
- 执行计划：查看本次执行对应的计划树
- ET 信息：查看节点耗时、内存、磁盘等运行信息
- 缓存计划信息：查看缓存计划和进一步导出线索

## 说明

- `EXEC_ID` 对应一次具体 SQL 执行
- 如果某个过程没有输出，通常表示该次执行没有对应数据，或者环境中相关历史信息不可用
