# install mariadb single node








mariadb 設定
vars/main.yaml

```bash
mariadb_ver: "mariadb-{{mariadb_version}}"
mariadb_APP_dir: "/opt/APP"
mariadb_DB_dir: "/opt/db"
mariadb_bin_path: "{{mariadb_APP_dir}}/mariadb/bin"
mariadb_base_path: "{{mariadb_APP_dir}}/mariadb"
mariadb_log_path: "{{mariadb_DB_dir}}/logs"
mariadb_user: "mysql"
mariadb_group: "mysql"
mariadb_group_GID: 1200
mariadb_user_UID: 1200
mariadb_print_defaults: "{{mariadb_APP_dir}}/mariadb/bin/my_print_defaults"
profile_file: "/etc/profile"
#### mysqld config
mariadb_port: 3306
mariadb_socket_path: "/var/run/mysqld"
mariadb_socket: "{{mariadb_socket_path}}/mysql.soket"
mariadb_lc_messages_dir: "{{mariadb_base_path}}/share"
mariadb_lc_messages: "en_US"
mariadb_bind_address: "0.0.0.0"
mariadb_key_buffer_size: "128M"
mariadb_max_connections: "100"
mariadb_connect_timeout: 5
mariadb_wait_timeout: 600
mariadb_max_allowed_packet: "16M"
mariadb_thread_cache_size: 128
mariadb_thread_stack: "192k"
mariadb_sort_buffer_size: "4M"
mariadb_bulk_insert_buffer_size: "16M"
mariadb_tmp_table_size: "32M"
mariadb_max_heap_table_size: "32M"
mariadb_join_buffer_size: "4M"
mariadb_read_buffer_size: "2M"
mariadb_read_rnd_buffer_size: "2M"
## MyISAM config
mariadb_myisam_recover: "BACKUP"
mariadb_table_open_cache: 200
mariadb_myisam_sort_buffer_size: "512M"
mariadb_concurrent_insert: 2
## Query Cache Configuration
mariadb_query_cache_limit: "128K"
mariadb_query_cache_size: "64M"
## Logging and Replication
mariadb_general_log: 1
mariadb_general_log_file: "{{mariadb_log_path}}/general.log"
## Error log - should be very few entries.
mariadb_log_warnings: 2
mariadb_log_error: "{{mariadb_log_path}}/error.log"
##slow query log
mariadb_slow_query_log: 0
mariadb_slow_query_log_file: "{{mariadb_DB_dir}}/mysql-slow.log"
mariadb_long_query_time: 10
###
mariadb_log_bin: "mysql-bin"
mariadb_log_bin_index: "{{mariadb_DB_dir}}/log_bin.index"
mariadb_binlog_format: "row"
mariadb_expire_logs_days: "7"
# InnoDB  
# innodb_log_group_capacity = innodb_log_file_size * innodb_log_files_in_group
mariadb_default_storage_engine: "InnoDB"
mariadb_innodb_buffer_pool_size: "256M"
mariadb_innodb_buffer_pool_instances: 4
mariadb_innodb_log_buffer_size: "8M"
mariadb_innodb_file_per_table: 1
mariadb_innodb_open_files: 400
mariadb_innodb_io_capacity: 400
mariadb_innodb_flush_method: "O_DIRECT"
mariadb_innodb_read_io_threads: 64
mariadb_innodb_write_io_threads: 64
mariadb_innodb_flush_log_at_trx_commit: 0
mariadb_innodb_log_file_size: "512M"
mariadb_innodb_lock_wait_timeout: 10
```

