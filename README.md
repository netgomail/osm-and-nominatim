# UBUNTU 17.04
## Шаг 1: Установка PostgreSQL DB Server с PostGIS

```
sudo apt install postgresql postgresql-contrib postgis postgresql-9.6-postgis-2.3
```

```
sudo -u postgres -i
```

Создаем пользователя PostgreSQL с именем от которого работаете в Убунту
```
createuser USER
```

Создаем базу данный gisdb

```
createdb -E UTF8 -O USER gisdb

Удалить базу если нужно dropdb DB
```

```
psql -c "CREATE EXTENSION hstore;" -d gisdb

psql -c "CREATE EXTENSION postgis;" -d gisdb

psql -c "CREATE EXTENSION postgis_topology;" -d gisdb

exit
```
## Шаг 2: Установка стилей карты а данных

```
wget https://github.com/gravitystorm/openstreetmap-carto/archive/v4.1.0.tar.gz

tar xvf openstreetmap-carto-4.1.0.tar.gz

wget -c http://data.gis-lab.info/osm_dump/dump/latest/RU-YAN.osm.pbf
```

### Импорт данных 

```
sudo apt install osm2pgsql

osm2pgsql --slim -d gisdb -C 600 --hstore -S openstreetmap-carto-4.1.0/openstreetmap-carto.style RU-YAN.osm.pbf
```