### BackEnd Projeto mandaTrampo

:mask: Devido a pandemia estabelecida ao redor do nosso planeta, a turma de Sistemas para Internet :mortar_board: está desenvolvendo um jeitinho para ajudar quem está precisando, nesse momento dificil ou não. :mask:

- API pra integração do Projeto MandaTrampo FATEC Araras

<p align="center">
   <img src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=RED&style=for-the-badge"/>
</p>

### Tarefas completas ou em execução

- [x] Cadastro de usuário
- [x] Permitir acesso de usuário
- [x] Cadastro de Serviços
- [x] Cadastro de Curriculum
- [x] Cadastro de Profissão
- [x] Cadastro de Categoria
- [x] Cadastro de Imagens para Serviço
- [x] Listagem de Serviços
- [x] Listagem de Serviços por Categoria
- [x] Listagem de Serviços por Usuário
- [x] Listagem de Curriculum
- [x] Listagem de Curriculum por Usuário
- [x] Listagem de Curriculum por Profissão
- [x] Update Cadastro de Curriculum
- [x] Update Cadastro de Serviço
- [x] Update Usuário
- [x] Aprovação do Serviço
- [x] Envio de E-mail do Cadastro do Serviço para Usuário
- [x] Envio de E-mail da Alteração do Serviço para Usuário
- [x] Envio de E-mail para Administrador de um Novo Serviço
- [x] Envio de E-mail para Administrador de uma Alteração de Serviço
- [x] Aprovação do Serviço - Redirecionamento para o Site
- [x] Remoção de Fotos do Serviço
- [x] Relacionamento de CV com a Profissão

## Como rodar a aplicação :arrow_forward:

No terminal, clone o projeto após clonar:

Instale as dependecias:

```
yarn install
```

Altere o aquivo .env e entre com as credênciais
Altere o ormconfig e entre com as credênciais

Rodar as Migrations:

```
yarn typeorm migration:run
```

Execute a aplicação:

```
yarn dev:start
```

Se tudo estiver certo, vai aparecer uma mensagem que o servidor está funcionando.
Pronto, agora é possível acessar a aplicação a partir da rota http://localhost:3000/

## Rotas

| Rota   | Método | Requer Autenticação |
| ------ | :----- | :-----------------: |
| /users | POST   |        :-1:         |

:speech_balloon: Cadastro basico para acesso ao sistema

> Enviar

```
{
	"name" : "John Joe",
	"email": "john@email.com",
	"login": "jhonjoe",
	"password":"123456"
}
```

> Retorno

```
{
  "name": "John Joe",
  "email": "john@email.com",
  "id": "55f9cf1c-01a6-4110-bc8b-1a849f2e663e",
  "avatar_url": null
}
```

Obs: vai ser gerado um ID ... O acesso deve ser pelo login e senha.

---

| Rota      | Método | Requer Autenticação |
| --------- | :----- | :-----------------: |
| /sessions | POST   |        :-1:         |

:speech_balloon: Login para o sistema

> Enviar

```
{
	"login": "jhonjoe",
	"password": "123456"
}
```

> Retorno

```
{
  "user": {
    "id": "55f9cf1c-01a6-4110-bc8b-1a849f2e663e",
    "name": "John Joe",
    "email": "john@email.com",
    "avatar": null,
    "phone": null,
    "celphone": null,
    "address": null,
    "city": null,
    "country": null,
    "iswhats": false,
    "avatar_url": null
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE1OTI4NDEwMzAsImV4cCI6MTU5MzAxMzgzMCwic3ViIjoiNTVmOWNmMWMtMDFhNi00MTEwLWJjOGItMWE4NDlmMmU2NjNlIn0.e5LaqRI3Ri7gVV0SvnhCvYWJkvIc7nmBCFXYcEOE000",
  "countService": 0,
  "serviceAproved": 0,
  "serviceReproved": 0,
  "access": {
    "ip": "67.205.187.90",
    "city": "North Bergen",
    "region": "New Jersey",
    "country": "US",
    "loc": "40.8043,-74.0121",
    "postal": "07047"
  }
}
```

Obs: O Token deve ser passado em rotas que reque autenticação.
---

| Rota     | Método | Requer Autenticação | Tipo de Autenticação |
| -------- | :----- | :-----------------: | :------------------: |
| /profile | PUT    |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Alteração do Usuário com dados faltantes

> Enviar

```
{
	"name": "Jhon Joe",
	"email": "jhon@email.com",
	"login": "jhonjoe",
	"phone": "551999999999",
	"celphone": "551999999999",
	"address" : "ANTONIO DE ALMEIDA",
	"city": "ARARAS",
	"state": "SP",
	"iswhats": true
}
```

> Retorno

```
{
  "id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "name": "Jhon Joe",
  "email": "jhon@email.com",
  "avatar": null,
  "phone": "551999999999",
  "celphone": "551999999999",
  "address": "ANTONIO DE ALMEIDA",
  "city": "ARARAS",
  "country": null,
  "state": "SP",
  "iswhats": true,
  "avatar_url": null
}
```

---

| Rota     | Método | Requer Autenticação | Tipo de Autenticação | Requer Parametros  |
| -------- | :----- | :-----------------: | :------------------: | :----------------: |
| /profile | PATCH  |     :thumbsup:      |    Bearer - Token    | Multpart/form-data |

:speech_balloon: Alteração do Avatar Usuário

> Enviar

Enviar o file como input:name ( avatar )

> Retorno

```
{
  "id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "name": "Jhon Joe",
  "email": "jhon@email.com",
  "avatar": "15d1237cb3b30d3562dc-WhatsApp Image 2019-03-13 at 10.28.52.jpeg",
  "phone": "551999999999",
  "celphone": "551999999999",
  "address": "ANTONIO DE ALMEIDA",
  "city": "ARARAS",
  "country": null,
  "state": "SP",
  "iswhats": true,
  "avatar_url": "http://www.mandatrampo.com.br:3333/files/15d1237cb3b30d3562dc-WhatsApp Image 2019-03-13 at 10.28.52.jpeg"
}
```

---



| Rota       | Método | Requer Autenticação | Tipo de Autenticação |
| ---------- | :----- | :-----------------: | :------------------: |
| /categorie | POST   |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Cadastro de Categoria para ser usado no Cadastro de Serviços

> Enviar

```
{
	 "name": "MECANICA DE AUTOS E LAVAGEM"
}
```

> Retorno

```
{
  "name": "MECANICA DE AUTOS E LAVAGEM",
  "id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da"
}
```

---





| Rota        | Método | Requer Autenticação | Tipo de Autenticação |
| ----------- | :----- | :-----------------: | :------------------: |
| /profession | POST   |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Cadastro de profissão para ser usado no Cadastro de CV

> Enviar

```
{
	 "name": "ANALISTA DE BUGS"
}
```

> Retorno

```
{
  "name": "ANALISTA DE BUGS",
  "id": "7c7d2f2c-6e30-46d1-ba52-f13987ab5ccd"
}
```

---




| Rota        | Método | Requer Autenticação | Tipo de Autenticação |
| ----------- | :----- | :-----------------: | :------------------: |
| /curriculum | POST   |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Cadastro de CV

> Enviar

```
{
  "curriculum": "",
  "link_mediasocial": "/pauloamigoni",
  "description": "PROGRAMADOR FULLSTACK OVERFLOW",
  "profession_id": "f9202f92-facc-4ac4-a710-88985a1e91f7",
  "profession_others": "",
  "experience_time": "4"
}
```

> Retorno

```
{
  "user_id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "curriculum": "",
  "link_mediasocial": "/pauloamigoni",
  "description": "PROGRAMADOR FULLSTACK OVERFLOW",
  "profession_id": "f9202f92-facc-4ac4-a710-88985a1e91f7",
  "profession_others": "",
  "experience_time": "4",
  "id": "7b319295-da16-4bb0-adb0-cdc63809e72c"
}
```

---





| Rota        | Método | Requer Autenticação | Tipo de Autenticação |
| ----------- | :----- | :-----------------: | :------------------: |
| /services   | POST   |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Cadastro de serviços

> Enviar

```
{
      "name": "ARRUMA CERTA CAR",
      "description": "AUTO MECANICA E LAVAGEM EM GERAL",
      "address": "TIRADENTES",
      "city": "ARARAS",
	    "state": "SP",
      "phone": "19992250066",
      "celphone": "19992250066",
      "email": "paulo.amigoni@gmail.com",
      "site": "arrumacar.com.br",
      "link_facebook": "/arrumacar",
      "link_instagram": "@arrumacar",
      "opening_hours": "24HRS",
      "categories_id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da",
      "categories_others": "",
		  "iswhats": true
}
```

> Retorno

```
{
 "user_id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "name": "ARRUMA CERTA CAR",
  "description": "AUTO MECANICA E LAVAGEM EM GERAL",
  "address": "TIRADENTES",
  "city": "ARARAS",
  "state": "SP",
  "phone": "19992250066",
  "celphone": "19992250066",
  "email": "paulo.amigoni@gmail.com",
  "site": "arrumacar.com.br",
  "link_facebook": "/arrumacar",
  "link_instagram": "@arrumacar",
  "opening_hours": "24HRS",
  "iswhats": true,
  "categories_id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da",
  "id": "b187d99f-f1b8-4a8e-be39-e8ce1c58df9f"
}
```

---




| Rota            | Método | Requer Autenticação | Tipo de Autenticação | Requer Parametros  |
| --------------- | :----- | :-----------------: | :------------------: | :----------------: |
| /services/photo | POST   |     :thumbsup:      |    Bearer - Token    | Multpart/form-data |

:speech_balloon: Cadastro de imagens ao serviço

> Enviar

Enviar o file como input:name ( url )
e Enviar input:name ( service_id ) -> ID do serviço que pretende adicionar a imagem

> Retorno

```
{
{
  "services_id": "b187d99f-f1b8-4a8e-be39-e8ce1c58df9f",
  "url": "5a3983ac154cc7872573-P_20190721_163128_vHDR_On.jpg",
  "id": "319f3c27-6251-43db-9e02-d803dcf23645",
  "local_url": "http://www.mandatrampo.com.br:3333/files/5a3983ac154cc7872573-P_20190721_163128_vHDR_On.jpg"
}
```

---






| Rota        | Método | Requer Autenticação | Tipo de Autenticação |
| ----------- | :----- | :-----------------: | :------------------: |
| /services   | PUT    |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Altera Serviços

> Enviar

```
{
  	"id": "b187d99f-f1b8-4a8e-be39-e8ce1c58df9f",
    "name": "ARRUMA CERTA CAR",
    "description": "AUTO MECANICA E LAVAGEM EM GERAL",
    "address": "Antonio de Cadastro, 710",
    "city": "LIMEIRA",
    "state": "SP",
    "phone": "199922222266",
    "celphone": "19992250066",
    "email": "paulo.amigoni@gmail.com",
    "site": "www.jhonjoe.com.br",
    "link_facebook": "/jhonjoe",
    "link_instagram": "/jhonjoe",
    "opening_hours": "08hrs às 18hrs - horario de Brasilia",
    "iswhats": true,
    "categories_id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da",
    "categories_others": ""
}
```

> Retorno

```
{
  "id": "b187d99f-f1b8-4a8e-be39-e8ce1c58df9f",
  "user_id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "name": "ARRUMA CERTA CAR",
  "description": "AUTO MECANICA E LAVAGEM EM GERAL",
  "address": "Antonio de Cadastro, 710",
  "city": "LIMEIRA",
  "state": "SP",
  "country": null,
  "phone": "199922222266",
  "celphone": "19992250066",
  "email": "paulo.amigoni@gmail.com",
  "site": "www.jhonjoe.com.br",
  "link_facebook": "/jhonjoe",
  "link_instagram": "/jhonjoe",
  "opening_hours": "08hrs às 18hrs - horario de Brasilia",
  "aproved": "N",
  "denunciation": 0,
  "iswhats": true,
  "categories_id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da",
  "categories_others": null,
  "user": {
    "id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
    "name": "Jhon Joe",
    "email": "jhon@email.com",
    "avatar": "15d1237cb3b30d3562dc-WhatsApp Image 2019-03-13 at 10.28.52.jpeg",
    "phone": "551999999999",
    "celphone": "551999999999",
    "address": "ANTONIO DE ALMEIDA",
    "city": "ARARAS",
    "country": null,
    "state": "SP",
    "iswhats": true,
    "avatar_url": "http://www.mandatrampo.com.br:3333/files/15d1237cb3b30d3562dc-WhatsApp Image 2019-03-13 at 10.28.52.jpeg"
  },
  "categories": {
    "id": "99818f86-49c7-4d27-9f79-c9e3d6b4f8da",
    "name": "MECANICA DE AUTOS E LAVAGEM"
  },
  "photo": [
    {
      "id": "319f3c27-6251-43db-9e02-d803dcf23645",
      "services_id": "b187d99f-f1b8-4a8e-be39-e8ce1c58df9f",
      "url": "5a3983ac154cc7872573-P_20190721_163128_vHDR_On.jpg",
      "local_url": "http://www.mandatrampo.com.br:3333/files/5a3983ac154cc7872573-P_20190721_163128_vHDR_On.jpg"
    }
  ]
}
```

---








| Rota        | Método | Requer Autenticação | Tipo de Autenticação |
| ----------- | :----- | :-----------------: | :------------------: |
| /curriculum | PUT    |     :thumbsup:      |    Bearer - Token    |

:speech_balloon: Altera CV

> Enviar

```
{
  "curriculum": "",
  "link_mediasocial": "/jhonjoe",
  "description": "ANALISTA TDD",
  "profession_id": "497f0417-841d-48a7-beff-b883b1feb112",
  "profession_others": "",
  "experience_time": "7 ANOS"
}
```

> Retorno

```
{
  "id": "7b319295-da16-4bb0-adb0-cdc63809e72c",
  "user_id": "af070e92-f0ef-4a66-8ed3-431ac7d7e7de",
  "curriculum": "",
  "link_mediasocial": "/jhonjoe",
  "description": "ANALISTA TDD",
  "profession_id": "497f0417-841d-48a7-beff-b883b1feb112",
  "profession_others": "",
  "experience_time": "7 ANOS",
  "professions": {
    "id": "497f0417-841d-48a7-beff-b883b1feb112",
    "name": "ANALISTA DE TDD"
  }
}
```

---



















[![Abra no Insomnia}](https://insomnia.rest/images/run.svg)](https://insomnia.rest/run/?label=&uri=https%3A%2F%2Fgitlab.com%2Fmandatrampo%2Fbackend%2F-%2Fedit%2Fdevelopment%2FInsomnia.json)

## Linguagens e libs utilizadas :books:

- [NodeJs]: versão 12

## Desenvolvedores/Contribuintes

| [<img src="https://avatars1.githubusercontent.com/u/2119919?s=460&u=21b7da9ce9be2163076f1fa85f0986198f98f152&v=4" width=115 > <br> <sub> Paulo Amigoni </sub>](https://github.com/pauloamigoni) | [<img src="https://avatars1.githubusercontent.com/u/38158576?s=460&u=3234c66d4177b59c240780628dd0d7eab074ff7b&v=4" width=115 > <br> <sub> Fabio Suzarth</sub>](https://github.com/fabiosuzarth) | [<img src="https://avatars0.githubusercontent.com/u/53358155?s=460&u=822996342e5d9b7f57aeb85ce399b0e1664ab852&v=4" width=115 > <br> <sub> Jhonny Marques</sub>](https://github.com/jhonnymarques) | [<img src="https://avatars2.githubusercontent.com/u/47534815?s=460&v=4" width=115 > <br> <sub> Jair Lopes Junior </sub>](https://github.com/JairLopesJunior) | [<img src="https://avatars3.githubusercontent.com/u/51486508?s=460&u=aea8d6c7921b7a053f23bf0480d6154d747fa23d&v=4" width=115 > <br> <sub> Everton Barramansa </sub>](https://github.com/evertonbarramansa) |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |


## Licença

The [MIT License]() (MIT)

Copyright :copyright: 2020 - MandaTrampo FATEC
