# Desafio Módulo 5 - Api para PDV

Este é o resultado do último desafio do curso de Desenvolvimento de Software com foco em Backend da [Cubos Academy](https://cubos.academy/cursos/desenvolvimento-de-software).

## Descrição 
Bem-vindo à API PDV desenvolvida para facilitar a gestão de Frente de Caixa em pequenos comércios. Essa API permite aos usuários realizar operações como cadastrar produtos, efetuar pedidos e gerenciar seu inventário de maneira eficiente.

---

<details>
<summary>Endpoints</summary>

##### Relação de endpoints: 
<div style="margin-left: 2rem;" >
<details>
<summary>Usuários</summary>

#### `POST` `/usuario`

- Cadastra um novo usuário no sistema.
- Campos obrigatórios:
    - nome
    - email (único)
    - senha
- Entrada pelo body da requisição, em formato json. 


#### `POST` `/login`

- Login no sistema de usuário cadastrado.
- Entrada dos dados pelo body da requisição, em formato json. 

> Um token será retornado no body, e será utilizado para acessar as demais rotas via Bearer Token.


#### `GET` `/usuario`

- Permite o usuário logado a visualizar os dados do seu próprio perfil
- Os dados do usuário apresentados são referentes ao token de autenticação fornecido no Bearer Token.


#### `PUT` `/usuario`

- Atualiza as informações do próprio usuário logado.
- Entrada dos dados pelo body da requisição, em formato json. 
- Referente ao usuário cujo token de autenticação foi fornecido no Bearer Token.

<br>
</details>

<details>
<summary>Produtos</summary>

#### `GET` `/categoria`

- Listar todas as categorias de produtos cadastradas.
- As categorias cadastradas são as seguintes: 
    - 1 - Informática
    - 2 - Celulares
    - 3 - Beleza e Perfumaria
    - 4 - Mercado
    - 5 - Livros e Papelaria
    - 6 - Brinquedos
    - 7 - Moda
    - 8 - Bebê
    - 9 - Games

#### `POST` `/produto`

- Permite o usuário logado cadastrar um novo produto no sistema.
- Campos obrigatórios:
    - descricao
    - quantidade_estoque
    - valor (em centavos)
    - categoria_id ( valor do id da [categoria](#get-categoria)).
- Entrada dos dados pelo body da requisição, em formato json. 

#### `PUT` `/produto/:id`

- Permite o usuário logado atualizar as informações de um produto cadastrado.
- Campos obrigatórios:
    -   descricao
    -   quantidade_estoque
    -   valor (em centavos)
    -   categoria_id ( valor do id da [categoria](#get-categoria)).
- Entrada dos dados pelo body da requisição, em formato json. 

#### `GET` `/produto`

- Lista para o usuário logado todos os produtos cadastrados.
- Permite um parâmetro do tipo query **categoria_id** que filtra os produtos por categoria (veja [aqui](#get-categoria)).
- Caso nenhum valor de **categoria_id** seja fornecido, todos os produtos serão listados.
- Saida pelo body em formato json.


#### `GET` `/produto/:id`

- Apresenta ao usuário os detalhes de um produto cadastrado em específico, identificado pelo parâmetro de rota **id**.  


#### `DELETE` `/produto/:id`

- Exclui o produto cadastrado, identificado pelo parâmetro de rota **id**.  

<br>
</details>


<details>
<summary>Clientes</summary>
<br>

#### `POST` `/cliente`

- Permite o usuário logado cadastrar um novo cliente no sistema.
- Campos obrigatórios:
    - nome
    - email (único)
    - cpf (único)

- Entrada dos dados pelo body da requisição, em formato json. 

#### `PUT` `/cliente/:id`

- Atualiza os dados de um cliente cadastrado, identificado pelo parâmetro de rota **id**.
- Campos obrigatórios:
    - nome
    - email (único)
    - cpf (único)
- Entrada dos dados pelo body da requisição, em formato json. 


#### `GET` `/cliente`

- Listar todos os clientes cadastrados.

>

#### `GET` `/cliente/:id`

- Retorna os detalhes de um dos clientes cadastrados.  
- Cliente identificado pelo parâmetro de rota *id*

<br>
</details>

<details>
<summary>Pedidos</summary>
<br>

#### `POST` `/pedido`

- Cadastra um novo pedido no sistema.
- Cada pedido deverá conter ao menos um produto vinculado.
- A concluir um pedido, um e-mail é enviado para o cliente.
- Campos obrigatórios:
    -   cliente_id
    -   pedido_produtos
        -   produto_id
        -   quantidade_produto
- Entrada dos dados pelo body da requisição, em formato json.


#### `GET` `/pedido`

- Lista todos os pedidos cadastrados.
- Permite o uso de um parâmetro do tipo query **cliente_id** o qual filtra os edidos por clientes.
- Caso o **cliente_id** não seja informado, todos os pedidos cadastrados são retornados.
- Resposta pelo body em formato json

</details>
</div>

</details>

---

## Funcionalidades

1. Cadastrar Usuário
2. Fazer Login
3. Detalhar Perfil do Usuário Logado
4. Editar Perfil do Usuário Logado
5. Listar Categorias
6. Cadastrar Produto
7. Editar Dados do Produto
8. Listar Produtos
9. Detalhar Produto
10. Excluir Produto
11. Cadastrar Cliente
12. Editar Dados do Cliente
13. Listar Clientes
14. Detalhar Cliente
15. Cadastrar Pedido
16. Listar Pedidos

---

## Como executar o projeto

⚠️ Para a execução do projeto, é necessário ter o [Node.js](https://nodejs.org/en) instalado em sua máquina.

1) Faça um clone do projeto

```bash
git clone git@github.com:bruna-rferreira/sistema-PDV.git
```

2) Abra o diretório do projeto

```bash
cd sistema-PDV
```

3) Instale as dependências utilizando o comando:

```bash
npm i
```

| Dependências  | Versão |
| :------------- | ------- |
| Express        | 4.18.2  |
| Nodemon        | 3.0.1   |
| PG             | 8.11.3  |
| Dotenv         | 16.3.1  |
| Json Web Token | 9.0.2   |
| Knex           | 3.0.1   |
| Joi            | 17.11.0 |
| Cors           | 2.8.5   |
| Bcrypt         | 5.1.1   |
| Aws sdk        | 2.1479.0|
| Handlebars     | 4.7.8  |
| Nodemailer     | 6.9.7  |

4) Inicialize o servidor local:

```bash
npm run dev
```

---

## Tecnologias Utilizadas

[![My Skills](https://skillicons.dev/icons?i=js,nodejs,beekeeper,express,git,github,postgres)](https://skillicons.dev)

---

## Autoras

[Marcela Linhares](https://www.linkedin.com/in/marcelagabilan/)

[Bruna Ferreira](https://www.linkedin.com/in/brunarodferreira/)

[Debora Francislayne](https://www.linkedin.com/in/debora-francislayne-silva1/)

[Karolayne Arantes](https://www.linkedin.com/in/karolayne-arantes/)

[Thais Paixão](https://www.linkedin.com/in/tha%C3%ADs-paix%C3%A3o-742932141/)


