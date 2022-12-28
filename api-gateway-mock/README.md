# Mock data

Please se *.json files. 

More information at [https://www.mock-server.com](https://www.mock-server.com)



# Run

## build and run via docker

```
docker build -f Dockerfile -t illegal-dump/api-gateway-mock .

docker run -i --rm -p 8081:1080 illegal-dump/api-gateway-mock
```

## build and run via docker-compose

```
docker-copose up --build
```