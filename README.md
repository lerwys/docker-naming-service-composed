# Docker Compose for Wildfly (running Naming Service) + Postgres

## Running instructions

	docker network create dockerrbacauthservicescomposed_postgres-rbac

Setup network

	docker-compose up -d

The webpage should be available at:

	http://localhost:8080/names-3.2.5

## Systemd Integration

To integrate this as a systemd service, do:

    make install

To remove the systemd service and its additional files:

    make uninstall

## Host IP mapping

The RBAC/Cable images have the following names:

  - RBAC management studio: sirius-rbac.lnls.br
  - RBAC auth services: sirius-rbac-auth.lnls.br
  - Cable service: sirius-cable.lnls.br

If running on the same host, with the same
docker network, the mapping must be the internal
docker IP, such as 172.18.0.3. This is necessary
as the port mapping between the container/host
might change and the docker DNS services knows
how to deal with this. If running on the same,
but the actual IP is used, the docker DNS service
will not be used and the services will try to
use the actual specified port, which could be
incorrect due to container/host port mapping.

So, in summary, if running services on the same
host, use

  extra_hosts:
    - "sirius-rbac.lnls.br:172.18.0.3"
    - "sirius-rbac-auth.lnls.br:172.18.0.4"
    - "sirius-cable.lnls.br:172.18.0.5"

where 172.18.0.3/172.18.0.4/172.18.0.5 are the internal
docker IPs

If running the services on different host, just use
the destination IPs.

