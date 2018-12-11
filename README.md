# PHP(installed Laravel) + nginx + postgres + pdAdmin on Docker

## How to create laravel project.

1. Run `docker-compose exec php laravel new {project_name}`
2. Edit laravel_docker/nginx/conf.d/default.conf

  ```
  root /src/{projcet_name}/public;
  ```


## launch.json sample for VS Code

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "XDebug on docker",
      "type": "php",
      "request": "launch",
      "port": 9000,
      "serverSourceRoot": "/src",
      "localSourceRoot": "${workspaceRoot}/src"
    },
  ]
}
```