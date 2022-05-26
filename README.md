# Cross Browser testing com cypress✨

## O que é cross browser testing🤔

O cross browser test é um método de garantia de qualidade para aplicativos web que visa garantir que uma pagina web tenha o mesmo comportamento em diferentes versões do navegador e versões do sistema operacional utilizados no mercado, ou seja, garante a qualidade do seu site em diferentes telas. 

## Como realizar com cypress🧐
Para a realização de cross browser testing com cypress existem duas abordagens possíveis.
A primeira utilizando a configuração do próprio cypress para que o teste seja executado nos diferentes navegadores disponíveis na sua máquina local ou no seu ambiente de CI. 
A segunda forma utilizando algum ambiente de teste em nuvem que permita a realização de múltiplos navegadores com cypress.

Nessa publicação daremos enfase a segunda forma, no entanto, futuramente trarei algum post sobre a primeira forma.

## Pre requisitos📑
* Conta no browserstack criada
* [Node.js](https://nodejs.org/en/) instalado

## Mão na massa👩‍💻
### escolhendo o ambiente de nuvem 
Para essa categoria de teste utilizaremos o ambiente de cloud test Browserstack. É importante a criação de uma conta no browserstack, pois será necessário um token de acesso ao ambiente de execução e dashboard de resultados. Para mais informações de como criar uma conta no [browserstack](https://www.browserstack.com/users/sign_up)

### clonando o projeto para testes
Nesse tutorial utilizaremos o projeto [cypress serve rest](https://github.com/marlo2222/cypress-serve-rest) para execução. Para isso, sera necessario clona o projeto para sua máquina conforme o comando abaixo: 

```
git clone https://github.com/marlo2222/cypress-serve-rest.git
```

Após clona o projeto, será necessário entra no diretório clonado e realizar a instalação das dependências para execução utilizando os comandos a seguir: 
```
cd cypress-serve-rest

npm install
```

### configurando browserstack
O primeiro passo de configuração do browserstack no seu projeto cypress é a instalação do CLI Browserstack-Cypress, para isso basta utilizar o seguinte comando: 

```
npm install -g browserstack-cypress-cli
```

Com o CLI instalado, precisamos criar um arquivo browserstack.json, utilizaremos ele para definir, por exemplo, as credenciais do usuário. Para a criação do arquivo basta utilizar o seguinte comando: 

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

A lista de navegadores que você deseja executar seus testes e versões para os navegadores escolhidos também devera ser informando no arquivo browserstack.json, na sessão **browsers**. Observe que podemos diferentes versões para um mesmo browser, como mostrado a seguir: 

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

Por fim, precisamos apenas configurar o run_settings do projeto no arquivo browserstack.json. O seu arquivo deverá ser semelhante ao demostrado a seguir: 
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
* O campo build name será utilizado como nome do build a ser executado no ambiente de nuvem. 
* Apesar de o arquivo está definido com execução paralela com 5 instâncias, a execução será realizada em apenas 1 instância. 

## Executando😎

Para a execução dos teste utilizando o ambiente de nuvem você deve utilizar o seguinte comando: 

```
browserstack-cypress run
```

## Resultados😀

E aqui está!!! Caso você tenha informando o usuário e token validos no arquivo browserstack.json a execução poderá ser acompanhada por meio  do link informado no console que o levará direto para a execução. Os testes estarão agrupados por combinações de Navegador/SO definidos no arquivo browserstack.json, conforme mostrado na imagem abaixo:

![image](https://user-images.githubusercontent.com/40809563/170388452-7b636a2e-d23f-4d48-b1e2-9790e64a5bdb.png)

A saida com os resultados tambem estará disponivel no console após a execução, como mostrado na imagem abaixo:

![image](https://user-images.githubusercontent.com/40809563/170388731-d2a4426b-95f6-4d91-bfab-3c79409c0da3.png)


Espero que tenham gostado do conteúdo.👍

Gostou? Deixe sua⭐ para me ajudar😀

Me acompanhem nas redes sociais: 

📩 [linkedin](https://www.linkedin.com/in/marlo-henrique-84a940109/)

