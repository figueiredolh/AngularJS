# Link da Playlist:

- https://www.youtube.com/playlist?list=PLQCmSnNFVYnTD5p2fR4EXmtlR6jQJMbPb

# Anotações

## 13/08/2022

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