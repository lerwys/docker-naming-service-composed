# Docker Compose for Wildfly (running Naming Service) + Postgres

## Running instructions

	> docker network create dockerrbacauthservicescomposed_postgres-rbac

Setup network

	docker-compose up -d

The webpage should be available at:

	http://localhost:8080/names-3.2.5
