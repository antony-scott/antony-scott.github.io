---
layout:     post
title:      SQL Server in Docker Compose
date:       2024-04-24
categories: Docker
---
### SQL Server in Docker Compose

```yaml
name: my-app
services:
  mssql:
    container_name: mssql
    image: mcr.microsoft.com/mssql/server:latest
    hostname: mssql
    restart: always
    ports:
      - 1433:1433
    volumes:
      - ./data/mssql:/var/opt/mssql/data
    environment:
      - "ACCEPT_EULA=Y"
      - "MSSQL_SA_PASSWORD=C0mplexP@ssword"
      - "MSSQL_PID=Developer"
```

In order to persist data so it survives the container/app being torn down completely, I usually map the `/var/opt/mssql/data` folder to a relative folder within my project and ignore it both in git and vscode

###### .gitignore
```gitignore
data/
```

###### .vscode/settings.json
```json
{
  "files.exclude": {
    "data/": true
  }
}
```

#### Gotchas
- Mapping the `/var/opt/mssql` folder will cause issues with failed attempts to run `chmod`, and result in repeated crashes.