# Social Net Deployment

## Docker
Build docker image:
```docker
docker build -f docker/Dockerfile -t socialnet:<tag> .
```

Run: 
```docker
docker run -dp  8080:80 --name test1 socialnet:0.0.1
```

Check the next endpoints:
- http://localhost:8080/weatherforecast
- http://localhost:8080/api/users

## Kubernetes
