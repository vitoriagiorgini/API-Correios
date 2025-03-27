**Documentação da API - Consulta de Endereço por CEP**

## Descrição

Esta API foi desenvolvida em **Node.js** utilizando o framework **Express** e a biblioteca **Axios** para consultar informações de endereço (como logradouro, cidade e estado) a partir do **CEP** fornecido. A API interage com a **ViaCEP**, uma API pública que fornece dados de localização baseados no CEP.

A principal funcionalidade da API é validar o formato do CEP, realizar a consulta via **ViaCEP**, e retornar os dados em formato **JSON** para o usuário. A API está configurada para rodar na porta **3000**.

## Tecnologias Utilizadas

- **Node.js**: Ambiente de execução JavaScript para desenvolvimento do backend.
- **Express**: Framework para Node.js, utilizado para facilitar a criação de rotas e manipulação de requisições HTTP.
- **Axios**: Biblioteca de cliente HTTP para fazer requisições para a API ViaCEP.
- **ViaCEP**: API pública utilizada para fornecer os dados de localização a partir do CEP informado.

## Funcionalidade

A API oferece uma única funcionalidade principal:

- **Consulta de Endereço**: A partir de um CEP fornecido pelo usuário, a API valida o formato do CEP, realiza a consulta na API ViaCEP e retorna as informações de endereço em formato JSON. Se o CEP estiver incorreto ou não encontrado, a API retornará um erro com o código de status HTTP adequado.

### Exemplo de resposta:
```json
{
  "cep": "01001-000",
  "logradouro": "Praça da Sé",
  "complemento": "lado ímpar",
  "bairro": "Sé",
  "localidade": "São Paulo",
  "uf": "SP",
  "ibge": "3550308",
  "gia": "1004",
  "ddd": "11",
  "siafi": "7107"
}
```

## Como Instalar e Usar

### Pré-requisitos

Certifique-se de ter o **Node.js** instalado em sua máquina. Se não tiver, você pode baixá-lo e instalá-lo a partir do [site oficial do Node.js](https://nodejs.org).

### Passos para Instalação

1. **Clone o repositório**:

   Execute o comando abaixo para clonar o repositório em sua máquina:
   ```bash
   git clone https://github.com/vitoria.giorgini/API-Correios.git
   ```

2. **Instale as dependências**:

   Navegue até o diretório do projeto e instale as dependências necessárias com o npm:
   ```bash
   cd Correios
   npm install
   ```

3. **Inicie o servidor**:

   Após instalar as dependências, inicie o servidor com o seguinte comando:
   ```bash
   npm start
   ```

   O servidor estará rodando em `http://localhost:3000`.

### Como Utilizar

- **Realizando uma requisição**:
  
  A API expõe o endpoint `/cep/:cep`, onde `:cep` é o CEP que você deseja consultar. Você pode fazer uma requisição GET para esse endpoint.

  **Exemplo de requisição**:
  
  Usando o **Postman**, **Insomnia**, ou diretamente no navegador, você pode fazer a seguinte requisição:

  ```
  GET http://localhost:3000/cep/01001000
  ```

  Ou usando o **curl**:
  ```bash
  curl http://localhost:3000/cep/01001000
  ```

  A resposta será um JSON contendo as informações de endereço, cidade e estado, conforme exemplo mostrado acima.

### Exemplos de erros:

- **CEP inválido**:
  
  Caso o CEP fornecido seja inválido, a API retornará um erro 400 (Bad Request).
  ```json
  {
    "error": "CEP inválido."
  }
  ```

- **CEP não encontrado**:

  Se a ViaCEP não encontrar o CEP informado, a resposta será um erro 404 (Not Found).
  ```json
  {
    "error": "CEP não encontrado."
  }
  ```




