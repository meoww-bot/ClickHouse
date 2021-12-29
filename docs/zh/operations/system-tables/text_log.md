# system.text_log {#system_tables-text_log}

此系统表包含日志条目。 可以在服务器设置中的 `text_log.level` 限制进入该表的日志级别。

列:

-   `event_date` (Date) — 条目的日期.
-   `event_time` (DateTime) — 条目的时间.
-   `event_time_microseconds` (DateTime) — 精度为微秒的条目时间.
-   `microseconds` (UInt32) — 条目的微秒数.
-   `thread_name` (String) — 进行日志记录的线程名称.
-   `thread_id` (UInt64) — 操作系统的线程 ID.
-   `level` (`Enum8`) — 日志条目等级. 可选值:
    -   `1` 或者 `'Fatal'`.
    -   `2` 或者 `'Critical'`.
    -   `3` 或者 `'Error'`.
    -   `4` 或者 `'Warning'`.
    -   `5` 或者 `'Notice'`.
    -   `6` 或者 `'Information'`.
    -   `7` 或者 `'Debug'`.
    -   `8` 或者 `'Trace'`.
-   `query_id` (String) — 查询的 ID.
-   `logger_name` (LowCardinality(String)) — 日志记录器(logger)的名称 (i.e. `DDLWorker`).
-   `message` (String) — 消息本身.
-   `revision` (UInt32) — ClickHouse 修订版本.
-   `source_file` (LowCardinality(String)) — 进行日志记录的源文件.
-   `source_line` (UInt64) — 进行日志记录的源文件的所在行数.

**示例**

``` sql
SELECT * FROM system.text_log LIMIT 1 \G
```

``` text
Row 1:
──────
event_date:              2020-09-10
event_time:              2020-09-10 11:23:07
event_time_microseconds: 2020-09-10 11:23:07.871397
microseconds:            871397
thread_name:             clickhouse-serv
thread_id:               564917
level:                   Information
query_id:
logger_name:             DNSCacheUpdater
message:                 Update period 15 seconds
revision:                54440
source_file:             /ClickHouse/src/Interpreters/DNSCacheUpdater.cpp; void DB::DNSCacheUpdater::start()
source_line:             45
```

 [原文](https://clickhouse.com/docs/zh/operations/system-tables/text_log) <!--hide-->
