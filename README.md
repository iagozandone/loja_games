# 🎮 Loja Games - API REST com Spring Boot  

## 📖 Descrição  
Projeto de uma **Loja de Games** desenvolvido em **Spring Boot** com integração ao **MySQL**, que permite o gerenciamento de **Produtos** e **Categorias** através de uma **API REST**.  

O sistema foi projetado para simular um ambiente real de varejo digital, incluindo **consultas avançadas por nome e preço**, relacionamento entre entidades e boas práticas de desenvolvimento backend.  

---

## ✨ Funcionalidades Principais  

### 📦 Gestão de Produtos  
- Cadastro, atualização e exclusão de produtos.  
- Consulta por ID, nome (ignora maiúsculas/minúsculas), preço maior ou menor que um valor.  
- Relacionamento com categorias.  

### 🗂️ Gestão de Categorias  
- Cadastro, atualização e exclusão de categorias.  
- Consulta por ID ou tipo (ignora maiúsculas/minúsculas).  
- Visualização de todos os produtos relacionados a uma categoria.  

### 🔄 Integração Produto-Categoria  
- Cada produto pertence a uma categoria (**ManyToOne**).  
- Categoria mantém uma lista de produtos (**OneToMany**).  
- Exclusão de uma categoria pode excluir os produtos relacionados (cascade).  

### 📈 Consultas Avançadas  
- Produtos filtrados por nome.  
- Produtos com preço maior que o valor informado (ordenados do menor para o maior).  
- Produtos com preço menor que o valor informado (ordenados do maior para o menor).  

---

## 🧩 Estrutura do Projeto  

### 🕹️ Modelo Produto  
- **id**: Long  
- **nome**: String (mín. 5, máx. 100 caracteres, obrigatório)  
- **foto**: String (URL da imagem)  
- **preco**: BigDecimal (obrigatório, maior que zero)  
- **categoria**: Categoria (ManyToOne)  
- **data**: LocalDateTime (atualizado automaticamente)  

### 🗃️ Modelo Categoria  
- **id**: Long  
- **tipo**: String (mínimo 5 caracteres, obrigatório)  
- **produto**: Lista de produtos relacionados (OneToMany)  

---

## 🔗 Endpoints da API  

### Produtos  
| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/produto` | Retorna todos os produtos |
| GET | `/produto/{id}` | Retorna um produto por ID |
| GET | `/produto/nome/{nome}` | Retorna produtos cujo nome contenha o valor informado |
| GET | `/produto/preco_maior/{preco}` | Retorna produtos com preço maior que o valor informado |
| GET | `/produto/preco_menor/{preco}` | Retorna produtos com preço menor que o valor informado |
| POST | `/produto` | Cadastra um novo produto |
| PUT | `/produto` | Atualiza um produto existente |
| DELETE | `/produto/{id}` | Deleta um produto pelo ID |

### Categorias  
| Método | Endpoint | Descrição |
|--------|----------|-----------|
| GET | `/categoria` | Retorna todas as categorias |
| GET | `/categoria/{id}` | Retorna uma categoria por ID |
| GET | `/categoria/tipo/{tipo}` | Retorna categorias cujo tipo contenha o valor informado |
| POST | `/categoria` | Cadastra uma nova categoria |
| PUT | `/categoria` | Atualiza uma categoria existente |
| DELETE | `/categoria/{id}` | Deleta uma categoria pelo ID |

---

## 🛠️ Tecnologias Utilizadas  

### Backend  
- **Java 17**  
- **Spring Boot 3 (Spring Web, Spring Data JPA, Validation)**  
- **Hibernate Validator**  
- **MySQL**  
- **Maven**  
- **Jackson** (manipulação de JSON)  

### Frontend (Opcional)  
- A API pode ser consumida por qualquer SPA (React, Angular, Vue, etc).  

---

## ⚙️ Configuração do Banco de Dados  

Arquivo `application.properties`:  

```properties
spring.application.name=lojagames
spring.jpa.hibernate.ddl-auto=update
spring.jpa.database=mysql
spring.datasource.url=jdbc:mysql://localhost/db_lojagames?createDatabaseIfNotExist=true&serverTimezone=America/Sao_Paulo&useSSl=false
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect = org.hibernate.dialect.MySQLDialect
spring.jpa.properties.jakarta.persistence.sharedCache.mode=ENABLE_SELECTIVE
spring.jackson.date-format=yyyy-MM-dd HH:mm:ss
spring.jackson.time-zone=Brazil/East

```
## ▶️ Como Executar o Projeto Localmente
Pré-requisitos
- Java 17+
- Maven
- MySQL

Passos
```bash
# Clone o repositório
git clone https://github.com/iagozandone/loja_games.git
cd loja_games

# Configure o banco no application.properties

# Execute o projeto
./mvnw spring-boot:run
```
A API estará disponível em:
## 👉 http://localhost:8080

## 📞 Contato

Desenvolvido por Iago Zandone.

* [GitHub](https://github.com/iagozandone)
* [LinkedIn](https://www.linkedin.com/in/iagozandone)
* [Portfólio Pessoal](https://iagozandone.github.io/portfolio_fundweb/)

