# erpnext_docker

## Backup
```
> cp -f /var/lib/docker/volumes/erpnext_docker_sites-vol/_data/erp.localhost/site_config.json /home/site_config.json
> docker exec -i 2cea10b3739f sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > /home/db.sql
```

## Restore
```
> docker exec -i 95b5fa325691 sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < /home/db.sql
> cp -f /home/site_config.json /var/lib/docker/volumes/erpnext_docker_sites-vol/_data/erp.localhost/site_config.json
```
