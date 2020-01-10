## Passo a passso de como padronizar os commits

 - ### Primeiro passo: Instalando o commitlint
 ```
  yarn add @commitlint/config-conventional @commitlint/cli -D
 ```

 Crie um arquivo com nome "commitlint.config.js" com o conteudo abaixo:

 ```js
  module.exports = {
    extends: ['@commitlint/config-conventional']
  }
 ```

 - ### Segundo passo: Instalando o husky e configurando o package.json
  Antes de instalar e configurar o husky, é obrigatório rodar o comando ```git init```

 ```
  yarn add husky -D
 ```

 ```json
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS"
    }  
  }
 ```

 - ### Terceiro passo: Instalando e configurando o commitizen
 ```
  yarn add commitizen -D
 ```

 Agora, depois de intalado, rode o código abaixo no terminal (antes de exexutar esse passo, é importanta estar com cli do commitizen instalada de forma global):
 ```
  commitizen init cz-conventional-changelog --yarn --dev --exact
 ```

 E por fim vamos adicionar mais uma comando ao husky no package.json:

 ```json
  "husky": {
    "hooks": {
      "commit-msg": "commitlint -E HUSKY_GIT_PARAMS",
      "prepare-commit-msg": "exec < /dev/tty && git cz --hook || true"
    }
  }
 ```