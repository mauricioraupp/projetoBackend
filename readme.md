# 2º Passo: Clonar o projeto do gitHub, criar configuração da API e testar

* Comando clone do git
* Configurar pacotes instalados
* Criar comando para rodar o servidor
* Testar servidor

<hr>

#### Copiar a url do projeto

* Acessar repositório do projeto no gitHub
* Clicar no botão verde '<> Code'
* Clicar no ícone para copiar a URL, conforme a imagem

#### Clonar o repositório na sua máquina

* Abrir o gitBash em um local do computador
* Digitar o comando 'git clone' junto com a URL do seu repositório

```
git clone URL_REPOSITORIO
```

#### Acessar pasta
* Digitar o comando 'cd' e o nome do seu repositório
* cd (change directory): acessar outra pasta
```
cd NOME_REPOSITORIO
```

#### Reinstalar os pacotes da aplicação
```
npm i
```
* Este comando irá recriar a pasta node_modules no projeto

#### Criar arquivo .env na raiz do projeto
* Este arquivo é utilizada para armazenar as variáveis que serão reutilizadas na aplicação
* Com o comando nano, podemos criar e editar um arquivo pelo terminal
* Ctrl + o: Salvar o arquivo
* Enter: Confirmar
* Ctrl + x: Fechar o arquivo
```
nano .env
```

#### Digitar no arquivo .env
```
PORT = 3008
```
* Variável que contém a porta que o servidor estará rodando
* Esta arquivo .env não enviamos pro gitHub, pois contém informações sensíveis do sistema

#### Adicionar arquivo .env no .gitignore
```
nano .gitignore
```
```
.env
```

#### Abrir o VSCode
```
code .
```

#### Criar arquivo de exemplo para para as variáveis necessárias da aplicação
* Como não enviamos o arquivo .env para o gitHub, precisamos criar o exemplo das variáveis necessárias da aplicação
* Este arquivo conterá apenas as variáveis, sem os valores correspondentes
```
nano .env.example
```

#### Adicionar no arquivo .env.example
```
PORT = 
```

#### Abrir o arquivo app.js e digitar o código
* Importar o pacote express (servidor)
```
const express = require('express');
```

* Importar o pacote dotenv, gerenciador de variáveis de ambiente
```
const dotenv = require('dotenv').config();
```

* Instanciar o express na variável app
```
const app = express();
```

* Setar a porta do servidor a partir do arquivo .env
* O operador condicional '||' significa 'OU', caso não tenha a variável PORT, será utilizado o valor '3333'
```
app.set('port', process.env.PORT || 3333);
```

* Exportar as configurações na variável app
```
module.exports = app;
```


#### Abrir o arquivo server.js e digitar os códigos
* Importar o arquivo app
```
const app = require('./app');
```

* Importar a porta do servidor
```
const port = app.get('port');
```

* Testar API com a função listen
* 1º parâmetro: passamos a porta do servidor
* 2º parâmetro: arrow function para retornar um console informando a porta que está rodando o servidor
```
app.listen(port, () => {
    console.log(`Running on port ${ port }!`);
});
```

## Depois de configurar os pacotes e o teste do servidor, vamos criar o comando para executar

#### Abrir o arquivo package.json e alterar a chave 'scripts'
* Substituir o comando 'test' pelo comando 'start' na linha 7
```
"start":"nodemon src/server.js"
```

#### Rodar o comando no termial com gitBash
```
npm run start
```

#### Atualizar projeto no gitHub
* Adicionar todos arquivos ao versionamento
```
git add .
```

* Salvar projeto e escrever comentário sobre o processo realizado
```
git commit -m 'configuração do projeto'
```

* Enviar os arquivos atualizados para o gitHub
```
git push
```

### Atualize a página no gitHub e verifique se os arquivos foram atualizados 
* Com o projeto no servidor remoto podemos remover os arquivos na nossa máquina
```
cd ..
```
* Comando para acessar uma pasta anterior
* Fechar o VSCode com o projeto aberto

```
rm -rf projetoBackend
```
* rm (remove): comando utilizado para apagar arquivo
* -r (recursive): apaga pastas e subpastas de forma recursiva
* -f (force): não pergunta confirmações
* projetoBackend: nome da pasta que contem os arquivos da aplicação

## Conclusão do Passo 2
#### URL do repositório com:
 * Estrutura do projeto 
 * Arquivo readme de documentação dos passos realizados
 * Configuração 
 * Retorno de teste da API

#### Enviar a URL na tarefa do teams
 * Tarefa 2 - Configuração inicial