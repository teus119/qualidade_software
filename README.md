# Projeto de Qualidade Educacional

Este é um projeto educacional em Java usando Spring Boot e Maven para ensinar conceitos de qualidade aos alunos. O projeto implementa um sistema simples de cadastro de alunos e professores com uma interface web básica.

## Funcionalidades

- Cadastro e gerenciamento de alunos
- Cadastro e gerenciamento de professores
- Interface web simples usando Thymeleaf e Bootstrap
- Banco de dados MongoDB para armazenamento de documentos

## Tecnologias Utilizadas

- Java 17
- Spring Boot 3.2.0
- Maven
- Spring Data MongoDB
- Thymeleaf
- Bootstrap
- Banco de Dados MongoDB

## Configuração do Banco de Dados (MongoDB Atlas)

Este projeto requer uma instância do MongoDB. Para fins educacionais, recomendamos criar uma conta gratuita no **MongoDB Atlas**.

### Passo a Passo para Criar sua Conta:

1. Acesse [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) e crie uma conta gratuita.
2. Crie um novo projeto e, em seguida, um **Cluster gratuito (M0)**.
3. No painel do Cluster, vá em **Database Access** e crie um usuário com permissões de leitura e escrita (Read and write to any database). **Anote a senha!**
4. Vá em **Network Access** e adicione seu endereço IP atual (ou `0.0.0.0/0` para permitir acesso de qualquer lugar - use com cautela).
5. Clique em **Connect**, escolha **Connect your application** e copie a **Connection String** (URI).

### Onde Configurar no Projeto:

Para que a aplicação utilize o seu banco de dados pessoal, você deve atualizar o arquivo:
`src/main/resources/application.properties`

Substitua o valor da propriedade `spring.data.mongodb.uri` pela sua Connection String, garantindo que a senha e o nome do banco de dados estejam corretos:

```properties
spring.data.mongodb.uri=sua_connection_string_aqui
```

## Começando

### Pré-requisitos

- Java 17 ou superior
- Maven 3.6.0 ou superior

### Instalação do Maven

#### No Windows:
1. Baixe o Maven do site oficial: https://maven.apache.org/download.cgi
2. Extraia o arquivo ZIP para um diretório como `C:\apache-maven-3.9.5`
3. Adicione a variável de ambiente `MAVEN_HOME` apontando para o diretório do Maven
4. Adicione `%MAVEN_HOME%\bin` ao seu PATH
5. Verifique a instalação com o comando:
```cmd
mvn -version
```

#### No Linux (Ubuntu/Debian):
```bash
sudo apt update
sudo apt install maven
```

#### No Linux (CentOS/RHEL/Fedora):
```bash
sudo yum install maven
# ou para Fedora:
sudo dnf install maven
```

### Executando a Aplicação

1. Clone o repositório
2. Navegue até o diretório do projeto
3. Execute a aplicação usando Maven:

```bash
./mvnw spring-boot:run
```

Ou construa e execute o JAR:

```bash
./mvnw clean package
java -jar target/educational-quality-project-0.0.1-SNAPSHOT.jar
```

### Comandos úteis do Maven

- Para compilar o projeto: `mvn compile`
- Para executar os testes: `mvn test`
- Para empacotar o projeto: `mvn package`
- Para limpar os arquivos gerados: `mvn clean`
- Para executar a aplicação: `mvn spring-boot:run`

### Acessando a Aplicação

Após iniciar a aplicação, você pode acessá-la em:
- Página principal: http://localhost:8080
- Página de alunos: http://localhost:8080/students
- Página de professores: http://localhost:8080/teachers

### API Endpoints

A aplicação também disponibiliza endpoints RESTful para integração com outras aplicações:

#### Estudantes
- `GET /api/students` - Listar todos os estudantes
- `GET /api/students/{id}` - Obter detalhes de um estudante específico
- `POST /api/students` - Criar um novo estudante
- `PUT /api/students/{id}` - Atualizar informações de um estudante
- `DELETE /api/students/{id}` - Excluir um estudante

#### Professores
- `GET /api/teachers` - Listar todos os professores
- `GET /api/teachers/{id}` - Obter detalhes de um professor específico
- `POST /api/teachers` - Criar um novo professor
- `PUT /api/teachers/{id}` - Atualizar informações de um professor
- `DELETE /api/teachers/{id}` - Excluir um professor

## Estrutura do Projeto

- `entity/` - Entidades MongoDB para Aluno e Professor
- `repository/` - Interfaces da camada de acesso a dados
- `service/` - Camada de lógica de negócios
- `controller/` - Controladores web
- `templates/` - Templates Thymeleaf com Bootstrap

## Valor Educacional

Este projeto demonstra:
- Operações CRUD básicas
- Arquitetura MVC
- Fundamentos do Spring Boot
- Uso do Spring Data MongoDB
- Injeção de dependência
- Design de API RESTful
- Integração com banco de dados NoSQL
- Template frontend com Thymeleaf

## Guia de Testes (Aula 02)

Nesta etapa, focamos em garantir a qualidade do código através de testes automatizados, isolando a lógica de negócio e validando múltiplos cenários.

### 1. Testes Unitários (Mocados)

Testes unitários verificam a menor unidade de código (geralmente um método) em isolamento. Usamos o **Mockito** para "mocar" (simular) dependências, como repositórios ou serviços externos, garantindo que o teste foque apenas na lógica da classe testada.

**Passo a passo para criar um teste mocando o Service:**

1.  **Anotações:** Use `@ExtendWith(MockitoExtension.class)` na classe de teste.
2.  **Mocks:** Use `@Mock` para as dependências que deseja simular.
3.  **Injeção:** Use `@InjectMocks` na classe que será testada.
4.  **Configuração (Given):** Defina o comportamento do mock usando `when(...).thenReturn(...)`.
5.  **Ação (When):** Chame o método que está sendo testado.
6.  **Verificação (Then):** Use `assertEquals(...)` ou `verify(...)` para validar o resultado.

Exemplo conceitual:
```java
@ExtendWith(MockitoExtension.class)
class StudentServiceTest {
    @Mock
    private StudentRepository repository;

    @InjectMocks
    private StudentService service;

    @Test
    void deveSalvarEstudanteComSucesso() {
        Student student = new Student("João", "joao@email.com");
        when(repository.save(any())).thenReturn(student);

        Student salvo = service.save(student);

        assertNotNull(salvo);
        verify(repository, times(1)).save(student);
    }
}
```

### 2. Testes Parametrizados

Testes parametrizados permitem executar o mesmo teste várias vezes com diferentes conjuntos de dados, evitando repetição de código.

**Passo a passo:**

1.  **Anotação:** Use `@ParameterizedTest` em vez de `@Test`.
2.  **Fonte de Dados:** Use `@ValueSource`, `@CsvSource`, ou `@MethodSource` para prover os dados.
3.  **Parâmetros:** O método de teste deve receber os parâmetros na mesma ordem da fonte.

Exemplo com `@CsvSource`:
```java
@ParameterizedTest
@CsvSource({
    "João, joao@email.com, true",
    " , erro@email.com, false",
    "Maria, , false"
})
void validarDadosDoEstudante(String nome, String email, boolean esperado) {
    boolean resultado = service.validar(nome, email);
    assertEquals(esperado, resultado);
}
```

### Executando os Testes

Para rodar todos os testes do projeto:
```bash
mvn test
```