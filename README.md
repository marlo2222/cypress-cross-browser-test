# Cross Browser testing com cypress

## O que é cross browser testing

O cross browser test é um metodo de garantia de qualidade para aplicativos Web que visa garatir que uma pagina web tenha o mesmo comportamento em diferentes versões do navegador e versoes do sistemas operacionais utilizados no mercado, ou seja, garante a qualidade do seu site em diferentes telas. 

## Como realizar com cypress
Para a realização de cross browser testing com cypress existem duas abordagens possiveis. A primeira utilizando a configuração do proprio cypress para que o teste seja executado nos diferentes navegadores disponiveis na sua maquina local ou no seu ambiente de CI. A segunda forma utilizando algum ambiente de teste em nuvem que permita a realização de multiplos browsers com cypress.

Nessa publicação daremos enfase a segunda forma, no entando futuramento trarei algum post sobre a primeira forma.

## pre requisitos
[] Conta no browserstack criada
[] [Node.js](https://nodejs.org/en/) instalado

## Mão na massa
### escolhendo o ambiente de nuvem 
Para esse tipo de teste utilizaremos o ambiente de cloud test Browserstack. É importante a criação de uma conta no browserstack, pois será necessario um token de acesso ao ambiente de execução e dashboard de resultados. Para mais informações de como criar uma conta no [broserstack](https://www.browserstack.com/users/sign_up)

### clonando projeto para testes
Nesse tutorial utilizaremos o projeto xxx para execução. Para isso, sera necessario clona o projeto para sua máquina conforme o comando abaixo: 

```
git clone projeto
```

após clona o projeto, será necessario entra no diretorio clonado e realizar a instalação das dependências para execução utilizando os comandos a seguir: 

```
cd projeto

npm install
```

### configurando browserstack
O primeiro passo de configuração do browserstack no seu projeto cypress é a instalação é a instalação do CLI Browserstack-Cypress, para isso basta utilizar o seguinte comando: 

```
npm install -g browserstack-cypress-cli
```

Com o CLI instalado, precisamo criar um arquivo de browserstack.json, utilizaremos ele para definir por exemplo as credenciais do usuario. Para a criação do arquivo basta utilizar o seguinte comando: 

```
browserstack-cypress init
```

No arquivo browserstack.json, adicione suas credenciais de login do Browserstack na seção **auth** 

```
{
  ...
  "auth": {
    "username": "YOUR_USERNAME",
    "access_key": "YOUR_ACCESS_KEY"
  }
  ...
}
```

A lista de navegadores que você deseja executar seus testes e versões para o navegaroes escolhidos tambem devera ser informando no arquivo browserstack.json, na sessão **browsers**. Observe que podemos diferentes versões para um mesmo browser, como mostrado a seguir: 

```
{
  ...
  "browsers": [{
      "os": "Windows 10",
      "browser": "chrome",
      "versions": ["69", "80", "81"]
    },
    {
      "os": "Windows 10",
      "browser": "edge",
      "versions": ["94", "95"]
    },
    {
      "os": "Windows 10",
      "browser": "firefox",
      "versions": ["97", "98"]
    },
    {
      "os": "Windows 10",
      "browser": "opera",
      "versions": ["83", "84"]
    },
    {
      "os": "OS X Catalina",
      "browser": "edge",
      "versions": ["94", "95"]
    }
  ]
  ...
}
```

Por fim, precisamos apenas configurar o run_settings do projeto no arquivo browserstack.json. o seu arquivo deverá ser semelhante ao demostrado a seguir: 
```
{
 ...
  "run_settings": {
    "cypress_proj_dir": "./",
    "build_name": "Cypress Build: 1556",
    "parallels": 5,
    "npm_dependencies": {}
  },
  "connection_settings": {
    "local": false,
    "local_identifier": null
  }
 ...
}
```
**observação:**
* o campo build name será utilizado como nome do build a ser executado no ambiente de nuvem. 
* apesar de o arquivo está definido com execução paralela com 5 instâncias, a execução será realizada em apenas 1 instância. 

## Executando

