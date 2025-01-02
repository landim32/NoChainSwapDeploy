# CodeDevClubDeploy

### Install Network
	
```
docker ps
docker network inspect docker-network
docker network create docker-network
```

### Install Postgres
```
docker run --name postgres1 -e POSTGRES_PASSWORD=mysecretpassword --network docker-network -d postgres
docker network connect docker-network postgres1
```

### Install Background Service
```
cd BackgroundService
docker build -t nochainswap-bg -f Dockerfile .
docker run --name nochainswap-bg1 --network docker-network nochainswap-bg &
```

### Install Backend API
```
cd Backend
docker build -t nochainswap-api -f Dockerfile .
docker run --name nochainswap-api1 -p 8080:443 -e ASPNETCORE_URLS="https://+" -e ASPNETCORE_HTTPS_PORTS=8080 --network docker-network nochainswap-api &
```

### Install Frontend APP
```
cd Frontend
docker build -t nochainswap-app .
docker run --name nochainswap-app1 -p 80:80 -p 443:443 nochainswap-app
```