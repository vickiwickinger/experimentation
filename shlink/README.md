sudo docker run \
    --rm \
    --name my_shlink \
    -p 8080:8080 \
    -e GEOLITE_LICENSE_KEY=kjh23ljkbndskj345 \
    -e SHORT_DOMAIN_HOST=8080-coral-elephant-8mzhpj90.ws-eu03.gitpod.io \
    -e SHORT_DOMAIN_SCHEMA=https \
    shlinkio/shlink:stable

docker exec -it my_shlink shlink api-key:generate

docker run --rm --name shlink-web-client -p 8000:80 -v ${PWD}/servers.json:/usr/share/nginx/html/servers.json shlinkio/shlink-web-client:stable