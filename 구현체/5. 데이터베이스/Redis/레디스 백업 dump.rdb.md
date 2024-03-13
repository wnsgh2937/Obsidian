dumb.rdb 파일 뜨기
- 수동
	- redis-cli bgsave

redis 실행시 dumb.rdb 파일로 실행
```
redis-server --dbfilename dump.rdb --dir /home/in_which_directory_rdb_file_exists
```