# jpmap

## Creating map file which topojson format

see also:
>http://qiita.com/ran/items/d88c5126362576be3291
>http://qiita.com/cieloazul310/items/6dfd73952304ab61cd20

## Install GDAL

```
apt-get install gdal-bin
npm install topojson
```

## Download Geo data

[Download here](http://www.naturalearthdata.com/http//www.naturalearthdata.com/download/10m/cultural/ne_10m_admin_1_states_provinces.zip)

## Convert shp file to GeoJSON

Extract downloaded zip file. Then run following command.
```sh
ogr2ogr -f GeoJSON -where "adm0_a3 = 'JPN'" features.json ne_10m_admin_1_states_provinces.shp
```

## Convert GeoJSON to TopoJson

Run following commands.

```sh
geo2topo -q 1e6 -o topo.json features.json
toposimplify -P 0.05 -o topo.json topo.json
```
