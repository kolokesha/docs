---
sourcePath: ru/ydb/ydb-docs-core/ru/core/reference/ydb-sdk/example/go/_includes/run_docker.md
---
Для соединения с развернутой локальной базой данных YDB по сценарию [Docker](../../../../../getting_started/self_hosted/ydb_docker.md) в конфигурации по-умолчанию выполните следующую команду:

``` bash
( export YDB_ANONYMOUS_CREDENTIALS=1 && cd ydb-go-examples && \
go run ./basic -ydb="grpc://localhost:2136?database=/local" )
```