# Kafka-EX-02: Kafka ve Zookeeper Docker Kurulumu

##  Proje Hakkında

Bu proje, Apache Kafka ve Zookeeper'ı Docker kullanarak Google Cloud VM üzerinde çalıştırmak amacıyla hazırlanmıştır. Proje kapsamında Kafka broker kurulumu, topic oluşturma ve doğrulama adımları başarıyla gerçekleştirilmiştir.

##  Kullanılan Teknolojiler

- 🐳 Docker
- 🐳 Docker Compose
- 🦉 Apache Kafka (Confluentinc/cp-kafka:7.5.0)
- 🦍 Apache Zookeeper (Confluentinc/cp-zookeeper:7.5.0)
- ☁️ Google Cloud Platform (GCP) — Compute Engine VM (Debian)

---

##  Proje Yapısı
kafka-ex-02-docker-setup/
├── docker-compose.yml      # Kafka ve Zookeeper için Docker Compose dosyası
├── README.md                # Bu dosya
├── KAFKA-EX-02.docx         # Yazılı rapor
├── docker compose.png       # Docker Compose dosyasının ekran görüntüsü
├── kafka ps.png             # Çalışan container’ların görüntüsü
└── kafka test-topic.png     # Kafka topic oluşturma ve listeleme kanıtı

---

## ⚙️ Docker Compose Yapılandırması

### `docker-compose.yml` içeriği:

```yaml
version: '3'

services:
  zookeeper:
    image: confluentinc/cp-zookeeper:7.5.0
    container_name: zookeeper
    ports:
      - "2181:2181"
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000

  kafka:
    image: confluentinc/cp-kafka:7.5.0
    container_name: kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: 'zookeeper:2181'
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://35.205.10.107:9092,PLAINTEXT_HOST://localhost:9092
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1

