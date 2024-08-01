<p align="center">
<img src="https://cwmkt.com.br/wp-content/uploads/2024/04/logo_github.png" width="240" />
<p align="center">Seja bem-vindo ao Guia de Instalação EasyPanel N8N Modo Fila 🚀</p>
</p>
  
<p align="center"> 
<a href="https://hubconnect.top" target="_blank">👉 Participe da Comunidade HubConnect 👈</a>
</p>

<hr />
<hr />

## Comando para Instalar EasyPanel

```bash
curl -sSL https://get.easypanel.io | sh
```

Adicione nome de Project

![48098522-0c485df00f5cadb0d329061c35fee46c](https://github.com/cwmkt/easypanelevotypebot/assets/91642837/b72c1359-91ca-4bf6-9fb1-32525ba5747b)

Clique na aba Templates

![48098535-90f9b4f370bb8b06cfd7e4acf0ee0f97](https://github.com/cwmkt/easypanelevotypebot/assets/91642837/03c1830c-621c-40b3-94ee-93eb568c8d2e)

Va ate final da pagina

![image](https://github.com/comunidadehubconnect/easypanelwoofedcrm/assets/91642837/828a9e88-45f2-4b6b-98f1-ab4f164d2889)

Adicione codigo abaixo dentro do Schema

![image](https://github.com/comunidadehubconnect/easypanelwoofedcrm/assets/91642837/74b97f33-e5d2-495d-aaba-25bb8b433adf)

```bash
{
  "services": [
    {
      "type": "postgres",
      "data": {
        "projectName": "n8n-db",
        "serviceName": "n8n-db",
        "image": "bitnami/postgresql:16"
      }
    },
    {
      "type": "redis",
      "data": {
        "projectName": "n8n",
        "serviceName": "n8n-redis",
        "password": "senharedis"
      }
    }
  ]
}
```

Adicione codigo abaixo dentro do Schema com credenciais Postgres e Redis alteradas

![image](https://github.com/comunidadehubconnect/easypanelwoofedcrm/assets/91642837/74b97f33-e5d2-495d-aaba-25bb8b433adf)

```bash
{
  "services": [
    {
      "type": "app",
      "data": {
        "projectName": "n8n",
        "serviceName": "n8n",
        "source": {
          "type": "image",
          "image": "n8nio/n8n:latest"
        },
        "domains": [
          {
            "host": "$(EASYPANEL_DOMAIN)",
            "port": 5678
          }
        ],
        "env": "DB_TYPE=postgresdb \nDB_POSTGRESDB_DATABASE=n8n_db \nDB_POSTGRESDB_HOST=postgres \nDB_POSTGRESDB_PORT=5432 \nDB_POSTGRESDB_USER=postgres \nDB_POSTGRESDB_PASSWORD=356c84c2878e8a42f64b \nN8N_ENCRYPTION_KEY=r3djGX2vPoeL9zKL \nN8N_HOST=https://$(PRIMARY_DOMAIN) \nN8N_EDITOR_BASE_URL=https://$(PRIMARY_DOMAIN) \nN8N_PROTOCOL=https \nNODE_ENV=production \nWEBHOOK_URL=https://n8nwebhook.seudominio \nEXECUTIONS_MODE=queue \nQUEUE_BULL_REDIS_HOST=testes_n8n-redis \nQUEUE_BULL_REDIS_PORT=6379 \nQUEUE_BULL_REDIS_DB=2 \nQUEUE_BULL_REDIS_USER=default \nQUEUE_BULL_REDIS_PASSWORD=senharedis \nNODE_FUNCTION_ALLOW_EXTERNAL=moment,lodash,moment-with-locales \nEXECUTIONS_DATA_PRUNE=true \nEXECUTIONS_DATA_MAX_AGE=336 \nGENERIC_TIMEZONE=America/Sao_Paulo \nTZ=America/Sao_Paulo \n",
        "mounts": []
      }
    }
  ]
}
```


Pronto tudo Funcionando ✅😎

Creditos: Andre Marques
