# clickhouse-zabbix

Template to monitor main Clickhouse parameters _without using additional scripts_

It uses HTTP interface to read metrics from _system_ database using Zabbix Agent's HTTP client

Gathered metrics:

- MaxPartCountForPartition
- ReplicasMaxQueueSize
- Uptime
- InsertedBytes
- InsertedRows
- Query
- InsertQuery
- SelectQuery
- Merge
- Inactive parts count
- HTTPConnection
- TCPConnection
- InterserverConnection
- LeaderReplica
- ReadonlyReplica
- Used memory (this is roughly calculated from metrics and is not accurate)
- Ping (`/ping` HTTP endpoint)

Requirements:

- Zabbix 4.2+ (for Javascript support)
- Clickhouse 19.16+ (tested on, but should work on earlier versions)

Macros:

- `{$CH_URL}` Clickhouse URL (`http://127.0.0.1:8123` default)
- `{$CH_MAX_INACTIVE_PARTS}` for triggering on too much inactive parts
- `{$CH_MAX_PARTS}` for triggering on too much parts in partition
- `{$CH_MAX_REPLICA_QUEUE}` for triggering on too large replication queue
