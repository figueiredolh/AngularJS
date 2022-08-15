# Link da Playlist:

- https://www.youtube.com/playlist?list=PLQCmSnNFVYnTD5p2fR4EXmtlR6jQJMbPb

# Anotações

## Parte 2 - 13/08/2022

### Diretivas

- ngApp
- ngModule
- ngController
- ngBind
- ngModel

### Criação de uma lista telefônica simples

- ngBind x Interpolação {{}}
- 3 formas de uso do ngModel (atribuir novos valores na tabela) - segundo o autor:
    - Forma "ruim" : Atribuir nenhum parâmetro em adicionarContato() e ler valor diretamente de $scope. É recomendado apenas atribuir valor para $scope.

    <code>
        <input class="form-control mb-2" type="text" placeholder="nome" ng-model="nome">
        <input class="form-control" type="text" placeholder="número" ng-model="numero">
        <button class="btn btn-primary btn-block mt-3" ng-click="adicionarContato()">Adicionar Contato</button>


        $scope.adicionarContato = function(){
            $scope.contatos.push({nome: $scope.nome, telefone: $scope.telefone});
        }
    </code>

    - Forma "média": Passar parâmetros em adicionarContato(nome, telefone) e atribuir normalmente os valores sem o $scope {nome: nome, telefone: telefone}.

    <code>
        <input class="form-control mb-2" type="text" placeholder="nome" ng-model="nome">
        <input class="form-control" type="text" placeholder="número" ng-model="numero">
        <button class="btn btn-primary btn-block mt-3" ng-click="adicionarContato(nome, numero)">Adicionar Contato</button>


        $scope.adicionarContato = function(){
            $scope.contatos.push({nome: $scope.nome, telefone: $scope.telefone});
        }
    </code>

    - Forma "boa": Criar usando ngModel="contato.nome" e "contato.telefone", que já cria automaticamente um objeto, posteriormente passando parâmetro adicionarContato(contato). As desvantagem é que, ao apagar o conteúdo dos inputs, modificam o conteúdo do DOM, por isso sendo utilizados o método angular.copy()

## Parte 3 - 13/08/2022

### Diretivas

- ng-disabled
- ng-options

- ng-class
- ng-style

- ng-if: Insere ou não elemento no DOM, conforme condição
- ng-hide: Oculta a exibição do elemento na página, conforme condição. Não remove elemento do DOM.
- ng-show: Exibe o elemento na página, conforme condição. Não remove elemento do DOM.

### Tarefas

- Desabitar botão de adicionar caso haja algum valor vazio nos inputs

- Adicionar lista de Operadoras com seu nome e código

- Criar Select List para as Operadoras
    - Docs: https://docs.angularjs.org/api/ng/directive/ngOptions

- Adicionar o código no campo operadora do objeto Contato
    - Formato: select as label for value in array
    <code>ng-options="operadora.codigo as operadora.nome for operadora in operadoras" ng-model="contato.operadora"</code>

- Exibir nome da Operadora na tabela

- Exibir código da Operadora na tabela*
    - <td>{{contato.operadora.codigo}}</td>

- Criar checkbox para cada contato 
    - Trocar cor de fundo da linha ao clicar no checkbox

- Criar botão de Apagar Contato(s)
    - Desabilitá-lo ou ocultá-lo caso não haja algum contato selecionado

