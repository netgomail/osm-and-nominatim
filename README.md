# UBUNTU 17.04
## Шаг 1: Установка PostgreSQL DB Server с PostGIS

```
sudo apt install postgresql postgresql-contrib postgis postgresql-9.6-postgis-2.3
```

```
sudo -u postgres -i
```

Создаем пользователя PostgreSQL с именем openstreet
```
createuser openstreet
```

