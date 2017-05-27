• https://raw.githubusercontent.com/Benzinga/api-docs/master/swagger/benzinga/Newsfeed-API-REST-v2.yaml

• https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v2.0/yaml/petstore.yaml

• https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v2.0/json/petstore.json

Auth 0 inspired swagger-ui: 
• https://github.com/jensoleg/swagger-ui

• https://github.com/twskj/pretty-swag

• https://github.com/swagger-api/swagger-codegen

• https://twskj.github.io/pretty-swag/examples/pet.html

• https://github.com/bootprint/bootprint-openapi

• https://github.com/yvasiyarov/swagger

• https://github.com/go-swagger/go-swagger

• http://darosh.github.io/angular-swagger-ui-material/

swagger combined:
• https://www.npmjs.com/package/swagger-combined

swagger lint:
• https://github.com/whitlockjc/swagger-lint

> http://stackoverflow.com/questions/34733253/converting-a-swagger-yaml-file-to-json-from-the-command-line
	
```
swagger-codegen generate -i swagger.yaml -l swagger
```

Docker

If you use Docker, then I suggest you try weiyang/swagger-codegen.

You can generate a json file using docker with the following command:

```
docker run -v ./docs:/docs weiyang/swagger-codegen generate -i /docs/swagger.yaml -l swagger -o /docs
```

I like to setup a docker-compose.yml to "alias" this command for easy reuse:


```
version: "2"
services:
    gen-swagger:
    volumes:
      - ./docs:/docs
    image: weiyang/swagger-codegen
    command: generate -i /docs/swagger.yaml -l swagger -o /docs
```

And now I can just run docker-compose run gen-swagger

