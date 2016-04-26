# Docker container with Mapproxy and Mapnik on apache2

This container runs Apache 2 with Mapproxy configured to working together. It requires pre-rendered tiles.

This container has the following parameters:

* Port "80", where Apache 2 listens on.
* Volume "/var/www/osm_tiles", where pre-rendered tiles are placed.

The following URLs are available:

* Tiles http://container-ip/osm_tiles/{z}/{x}/{y}.png
* Mapproxy interface http://container-ip/mapproxy/
* WMS service URL: http://container-ip/mapproxy/service

# Starting the container

```sh
docker run -v "${PWD}/tiles:":/var/www/osm_tiles -p 80:80 alleveenstra/mapproxy
```

# Creating pre-rendered tiles

In the subdirectory tiles/ you will find "fetch.py".
Edit this file to change the parameters found in its top.
And run it to fetch rendered tiles.