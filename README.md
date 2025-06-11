# 12stmall (order - delivery - product 주문 처리 연동)
https://labs.msaez.io/#/189596125/storming/09a408b2fc1593ce174cd486230faca8

![스크린샷 2025-06-10 133848](https://github.com/user-attachments/assets/56a6b476-2197-467f-bf52-ddd1e9e7c530)

![스크린샷 2025-06-10 211303](https://github.com/user-attachments/assets/59394368-8f63-4fa2-b8ce-8b38c02c4761)
![스크린샷 2025-06-10 211313](https://github.com/user-attachments/assets/a0be8371-a97a-4cbf-94dc-dca2388783b7)
![스크린샷 2025-06-10 211335](https://github.com/user-attachments/assets/7faa78c1-c6d6-4ec1-8922-9d8c38ef7e71)
![스크린샷 2025-06-10 211227](https://github.com/user-attachments/assets/f2f0ee8b-bd79-417f-9258-a6a6f2d673de)
![스크린샷 2025-06-10 211347](https://github.com/user-attachments/assets/6d3d5826-ed58-4568-bb62-0b9e56f2bc32)

## Before Running Services
### Make sure there is a Kafka server running
```
cd kafka
docker-compose up
```
- Check the Kafka messages:
```
cd infra
docker-compose exec -it kafka /bin/bash
cd /bin
./kafka-console-consumer --bootstrap-server localhost:9092 --topic
```

## Run the backend micro-services
See the README.md files inside the each microservices directory:

- order
- delivery
- product
- dashboard


## Run API Gateway (Spring Gateway)
```
cd gateway
mvn spring-boot:run
```

## Test by API
- order
```
 http :8088/orders id="id"customerId="customerId"itemId="itemId"qty="qty"address="address"status="status"
```
- delivery
```
 http :8088/deliveries id="id"orderId="orderId"customerId="customerId"itemId="itemId"qty="qty"address="address"status="status"
```
- product
```
 http :8088/inventories id="id"name="name"stock="stock"
```
- dashboard
```
```


## Run the frontend
```
cd frontend
npm i
npm run serve
```

## Test by UI
Open a browser to localhost:8088

## Required Utilities

- httpie (alternative for curl / POSTMAN) and network utils
```
sudo apt-get update
sudo apt-get install net-tools
sudo apt install iputils-ping
pip install httpie
```

- kubernetes utilities (kubectl)
```
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```

- aws cli (aws)
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

- eksctl 
```
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
```
