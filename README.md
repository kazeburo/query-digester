# query-digester

pt-query-digest wrapper to make ops simple.

query-digester changes slow_query_log_file and enable slow_query_log.
wait several seconds and restores them.
After finish logging slow query log, query-digester call pt-query-digest and save result to /tmp.

# Usage

sudo is recommended. slowlog will be stores like `-rw-r----- 1 mysql  mysql   178 Oct 20 00:06 slow_query_20210920000610.log`.
root privileges will be required to read it.

```
% sudo perl ./query-digester -duration 10        
exec mysql to change long_query_time and slow_query_log_file
save slowlog to /tmp/slow_query_20200811172244.log
wait 10 seconds
finished capturing slowlog.
start query-digest
finished pt-query-digest.
digest saved to /tmp/slow_query_20200811172244.digest

% head /tmp/slow_query_20200811172244.digest
```
