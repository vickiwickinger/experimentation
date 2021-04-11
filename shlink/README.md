# Start the shlink server

**Change the short domain host e.g. to http://localhost:8080**

sudo docker run \
    --rm \
    --name my_shlink \
    -p 8080:8080 \
    -e GEOLITE_LICENSE_KEY=kjh23ljkbndskj345 \
    -e SHORT_DOMAIN_HOST=8080-coral-elephant-8mzhpj90.ws-eu03.gitpod.io \
    -e SHORT_DOMAIN_SCHEMA=https \
    shlinkio/shlink:stable

# Generate api key

docker exec -it my_shlink shlink api-key:generate

# Start web ui

**Generate servers.json and adapt url e.g. http://localhost:8080**

```json
[
    {
      "name": "Local",
      "url": "https://8080-coral-elephant-8mzhpj90.ws-eu03.gitpod.io",
      "apiKey": "8463dbbb-22bd-4ba4-bebb-7cccd1468447"
    }
]
```
**Serve web ui**

docker run --rm --name shlink-web-client -p 8000:80 -v ${PWD}/servers.json:/usr/share/nginx/html/servers.json shlinkio/shlink-web-client:stable



# other commands

docker exec -it my_shlink shlink api-key:list

docker exec -it my_shlink shlink short-url:generate https://youtu.be/kVOwuNY_vGA

docker exec -it my_shlink shlink short-url:list

docker run --rm --name shlink-web-client -p 8000:80 -v ${PWD}/servers.json:/usr/share/nginx/html/servers.json shlinkio/shlink-web-client:stable

docker run --rm --name shlink-web-client -p 8000:80 shlinkio/shlink-web-client:stable