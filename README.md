# erpnext_docker

## Set bench developer mode on the new site
```
> bench --site erp.localhost set-config developer_mode 1
> bench --site erp.localhost clear-cache
```

## Backup
```
> cp -f /var/lib/docker/volumes/erpnext_docker_sites-vol/_data/erp.localhost/site_config.json /home/site_config.json
> docker exec -i 2e39d0bee4de sh -c 'exec mysqldump --all-databases -uroot -p"$MYSQL_ROOT_PASSWORD"' > /home/db.sql
```

## Restore
```
> docker exec -i 95b5fa325691 sh -c 'exec mysql -uroot -p"$MYSQL_ROOT_PASSWORD"' < /home/db.sql
> cp -f /home/site_config.json /var/lib/docker/volumes/erpnext_docker_sites-vol/_data/erp.localhost/site_config.json
```
