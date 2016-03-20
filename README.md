# docker-couchdb
docker image for couchdb 2.0-dev on ubuntu 14.04

- creates couchdb user and group
- installs needed dependencies
- clones couchdb master (development version)
- builds it under `/usr/src/couchdb` and installs it under `/usr/local/lib/couchdb/`

# problems
Using `/usr/src/couchdb/dev/run` it works.
But starting the installed single-node version produces:
```
14:38:14.799 [error] gen_server chttpd_auth_cache terminated with reason: {database_does_not_exist,[{mem3_shards,load_shards_from_db,"_users",[{file,"src/mem3_shards.erl"},{line,282}]},{mem3_shards,load_shards_from_disk,1,[{file,"src/mem3_shards.erl"},{line,270}]},{mem3_shards,load_shards_from_disk,2,[{file,"src/mem3_shards.erl"},{line,286}]},{mem3_shards,for_docid,3,[{file,"src/mem3_shards.erl"},{line,85}]},{fabric_doc_open,go,3,[{file,"src/fabric_doc_open.erl"},{line,38}]},{chttpd_auth_cache,ensure_auth_ddoc_exists,2,[{file,"src/chttpd_auth_cache.erl"},{line,187}]},...]}
14:38:14.799 [error] CRASH REPORT Process chttpd_auth_cache with 0 neighbours exited with reason: {database_does_not_exist,[{mem3_shards,load_shards_from_db,"_users",[{file,"src/mem3_shards.erl"},{line,282}]},{mem3_shards,load_shards_from_disk,1,[{file,"src/mem3_shards.erl"},{line,270}]},{mem3_shards,load_shards_from_disk,2,[{file,"src/mem3_shards.erl"},{line,286}]},{mem3_shards,for_docid,3,[{file,"src/mem3_shards.erl"},{line,85}]},{fabric_doc_open,go,3,[{file,"src/fabric_doc_open.erl"},{line,38}]},{chttpd_auth_cache,ensure_auth_ddoc_exists,2,[{file,"src/chttpd_auth_cache.erl"},{line,187}]},...]} in gen_server:terminate/6 line 744
14:38:14.800 [error] Supervisor chttpd_sup had child chttpd_auth_cache started with chttpd_auth_cache:start_link() at <0.324.0> exit with reason {database_does_not_exist,[{mem3_shards,load_shards_from_db,"_users",[{file,"src/mem3_shards.erl"},{line,282}]},{mem3_shards,load_shards_from_disk,1,[{file,"src/mem3_shards.erl"},{line,270}]},{mem3_shards,load_shards_from_disk,2,[{file,"src/mem3_shards.erl"},{line,286}]},{mem3_shards,for_docid,3,[{file,"src/mem3_shards.erl"},{line,85}]},{fabric_doc_open,go,3,[{file,"src/fabric_doc_open.erl"},{line,38}]},{chttpd_auth_cache,ensure_auth_ddoc_exists,2,[{file,"src/chttpd_auth_cache.erl"},{line,187}]},...]} in context child_terminated
```

I really dont understand much of linux oder docker, but needed it for me and maybe somebody else also can use it too.
