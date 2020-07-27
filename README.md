# Exemplo de Escalabilidade com Docker Compose

Este repositório contém os códigos de uma aplicação multisserviços utilizando os containers `traefik` e `whoami` para exemplificar como funciona a escalabilidade de serviços/containers utilizando o docker-compose.

### Executando a aplicação:

```console
foo@bar# docker-compose up -d

Creating network "whoami_default" with the default driver
Creating whoami_whoami_1        ... done
Creating whoami_reverse_proxy_1 ... done
```

### Verificando a aplicação:
```console
foo@bar# docker-compose ps

         Name                       Command               State          Ports        
--------------------------------------------------------------------------------------
whoami_reverse_proxy_1   /entrypoint.sh --providers ...   Up      0.0.0.0:8080->80/tcp
whoami_whoami_1          /whoami                          Up      80/tcp              
```

### Escalando o serviço `whoami`
```console
foo@bar# docker-compose up -d --scale whoami=3

whoami_reverse_proxy_1 is up-to-date
Starting whoami_whoami_1 ... done
Creating whoami_whoami_2 ... done
Creating whoami_whoami_3 ... done
```

### Parando a aplicação
```console
docker-compose down

Stopping whoami_whoami_2        ... done
Stopping whoami_whoami_3        ... done
Stopping whoami_whoami_1        ... done
Stopping whoami_reverse_proxy_1 ... done
Removing whoami_whoami_2        ... done
Removing whoami_whoami_3        ... done
Removing whoami_whoami_1        ... done
Removing whoami_reverse_proxy_1 ... done
Removing network whoami_default
```
