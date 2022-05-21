# Realizando Cross Browser testing com cypress

## o que é cross browser testing

O cross browser test é um metodo de garantia de qualidade para aplicativos Web que visa garatir que uma pagina web tenha o mesmo comportamento em diferentes versões do navegador e versoes do sistemas operacionais utilizados no mercado, ou seja, garante a qualidade do seu site em diferentes telas. 

## Como realizar com cypress
Para a realização de cross browser testing com cypress axistem duas abordagens possiveis. A primeira utilizando a configuração do proprio cypress para que o teste seja executado nos diferentes navegadores disponiveis na sua maquina local ou no seu ambiente de CI. A segunda forma utilizando algum ambiente de teste em nuvem que permita a realização de multiplos browsers com cypress.

Nessa publicação daremos enfase a segunda forma, no entando futuramento trarei algum post sobre a primeira forma.

## Mão na massa
### escolhendo o ambiente de nuvem 
Para esse tipo de teste utilizaremos o ambiente de cloud test Browserstack. É importante que você criem uma conta no browserstack, pois mais afrente precisaremos do token que o ambiente forcene para o usuarios para executarmos os testes e termos acesso ao dashboard de execução. Para mais informações de como criar uma conta vocês podem acessar 

