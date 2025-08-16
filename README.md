# Blind DB

O Repositório consiste em rodar o mongo DB localmente para podermos utilizar as features pagas do mongo sem a necessidade de pagar enquanto estivermos em desenvolvimento. Por enquanto o recurso em questão é a possibilidade de observarmos mudanças em documentos.

### Requisitos

- Docker & Docker Compose
- Ubuntu 20.04+

### Instale o Docker

```bash
sudo apt update
sudo apt install docker.io docker-compose -y
sudo systemctl enable docker
sudo systemctl start docker
```

### Configuração Do Docket Com Replica-set

```bash
# Primeira vez
docker-compose up -d

# Entra no bash do mongo
docker exec -it mongodb mongosh

# Inicia Replica-set, requisito para utilizar Watch
rs.initiate({_id: "rs0", members: [{ _id: 0, host: "localhost:27017" }]})

# Confirma a criação de Replica-set
rs.status()
```

### Inicie e encerre o docker

```bash
# Inicia
docker-compose up -d

# Finaliza e Salva o voulume
docker-compose down -v
```

### Ferramenta Recomendada para visualização dos dados

[Mongo Compass](https://www.mongodb.com/pt-br/products/tools/compass)

```bash
# URL para coneção
mongodb://localhost:27017/?replicaSet=rs0
```
