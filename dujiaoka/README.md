## Base on stilleshan dockerfiles

#### HOW TO USE
1. Use the `config.sh` script to set the base variables for Dujiaoka. This script will create the `env.conf` and `epusdt/epusdt.conf` files.

``` bash
chmod +x config.sh

./config.sh
```

2. Create directories `storage` and `uploads` within the `shop` directory.
``` bash
mkdir -p shop/storage shop/uploads && chmod -R 777 shop/storage shop/uploads
```

3. Grant `777` permissions ---> `env.conf`
``` bash
chmod -R 777 env.conf
``` 

4. Now you can deploy your Docker container.
``` bash
docker-compose up -d
```
5. Enter epusdt & run the command
``` bash
cd epusdt
docker exec -i YOUR_DB_SERVER -c 'exec mysql -uepusdt -pCHANGE_YOUR_PASSWORD epusdt' < epusdt.sql
```
6. Restart
``` bash
# restart
docker-compose down
docker-compose up -d
# or
docker-compose restart

# check server status
docker logs -f YOUR_Epusdt_SERVER
```
