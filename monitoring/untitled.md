# Backup

## Mysqldump

```bash
$ mysqldump -h pdsoft3.c5pfyech7y8i.ap-northeast-2.rds.amazonaws.com
  -u nchild -ppndg0401
  --port=3306
  --single-transaction
  --routines
  --triggers
  --databases
  nchild > ./nchild-dump.sql
```

## TAR and GZ

no additional space required. tar sends stream to gz.

```bash
$ nohup tar -cvzf nchild.tar.gz nchild &
```

monitoring the progress

```bash
$ watch -d 'ls -hl | grep gz && echo && tail -5 nohup.out && echo && cat nohup.out |wc'
```



