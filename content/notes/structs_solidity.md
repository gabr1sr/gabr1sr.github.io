+++
title = "Structs (Solidity)"
author = ["Gabriel Rosa"]
date = 2023-09-06
draft = false
+++

tags
: [Tipos Definidos pelo Usuário (Solidity)]({{< relref "tipos_definidos_pelo_usuario_solidity.md" >}})

source
: [Digging deeper into Solidity's syntax](https://learnweb3.io/degrees/ethereum-developer-degree/sophomore/digging-deeper-into-soliditys-syntax/#structs)

O conceito de estuturas (structs) existe em várias linguagens de programação de alto nível. Eles são utilizados para definir seus próprios tipos de dados que agrupa junto informações relacionadas.

```solidity
contract TodoList {
    struct TodoItem {
        string text;
        bool completed;
    }

    TodoItem[] public todos;

    function createTodo(string calldata _text) public {
        // Método 1 - chamar como se fosse uma função
        todos.push(TodoItem(_text, false));

        // Método 2 - definir suas chaves explicitamente
        todos.push(TodoItem({ text: _text, completed: false }));

        // Método 3 - inicializar uma struct vazia e então definir as propriedades individualmente
        TodoItem memory todo;
        todo.text = _text;
        todo.completed = false;
        todos.push(todo);
    }

    function update(uint256 _index, string memory _text) public {
        todos[_index].text = _text;
    }

    function toggleCompleted(uint256 _index) public {
        todos[_index].completed = !todos[_index].completed;
    }
}
```
