# proj-kafka
Introduction to Kafka on Docker 🐳
Baixar o Repositório
Instalar o Docker (completo)
Entrar na Pasta Multinode pelo Shell (Windows ou Linux) e inicializar o ambiente com o seguinte comando:

# start services
docker-compose up -d
Após o download, provisão e instalação de tudo, consulte o ambiente com o comando:

# get name brocker
docker-compose ps
Os logs podem ser vistos com o comando:

# ver os logs dos clusters
docker logs -f proj-kafka_kafka-1_1
Entre no Container do Kafka:

# access container broker
CONTAINER_NAME=proj-kafka_kafka-1_1
docker exec -it $CONTAINER_NAME bash
Crie estas variáveis de ambiente:

# declare variables on container
BOOTSTRAP_SERVER=localhost:19092
TOPIC=topico
GROUP=grupo
Crie os Tópicos do Kafka (serão 3 partições e 3 réplicas):

# create topic with kafka cli
kafka-topics --create --bootstrap-server $BOOTSTRAP_SERVER \
--replication-factor 3 \
--partitions 3 \
--topic $TOPIC
Use o comando abaixo para listar os tópicos:

# list topics after created
kafka-topics --list --bootstrap-server $BOOTSTRAP_SERVER
Use o seguinte comando para descrever os tópicos:

# configs about topic
kafka-topics --bootstrap-server $BOOTSTRAP_SERVER \
--describe \
--topic $TOPIC
Crie um Produtor (para fins de testes):

# create producer
kafka-console-producer --broker-list $BOOTSTRAP_SERVER \
--topic $TOPIC
Mande as mensagens que quiser:

# send message to topic
abc
def
ghi
jkl
mno
pqr
stu
vwx
yza
Crie um Consumidor (para fins de testes):
kafka-console-consumer --bootstrap-server $BOOTSTRAP_SERVER \
--topic $TOPIC \
--from-beginning
Crie Consumidores baseados em cada Partição (para fins de testes):
# read topic and partitions
kafka-console-consumer --bootstrap-server $BOOTSTRAP_SERVER \
--topic $TOPIC \
--group $GROUP
Leia os dados desde o início:
# read topic from beginning
kafka-console-consumer --bootstrap-server $BOOTSTRAP_SERVER \
--topic $TOPIC \
--from-beginning
Encerre o exercício desprovisionando tudo:
# stop services
docker-compose down