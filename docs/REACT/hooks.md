### Hooks Básicos do React

O React introduziu **Hooks** na versão 16.8, permitindo o uso de estados e outros recursos do React sem a necessidade de escrever classes. Os três principais hooks básicos são:

1. `useState`: Para adicionar estado aos componentes funcionais.
2. `useEffect`: Para realizar efeitos colaterais, como chamadas de APIs, sincronizações com o DOM ou assinaturas.
3. `useContext`: Para consumir contextos de forma mais simples em componentes funcionais.

### 1. `useState`

O hook `useState` permite adicionar e gerenciar estados em componentes funcionais. Ele retorna um array com dois elementos: o estado atual e uma função para atualizá-lo.

#### Exemplo:

```jsx
import React, { useState } from 'react';

function Contador() {
  // Inicializa o estado com valor 0
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      {/* Atualiza o estado incrementando o contador */}
      <button onClick={() => setContador(contador + 1)}>
        Clique aqui
      </button>
    </div>
  );
}

export default Contador;
```

#### Explicação:

- `useState(0)` inicializa o estado `contador` com valor `0`.
- `setContador` é a função usada para atualizar o valor do estado quando o botão é clicado.

---

### 2. `useEffect`

O hook `useEffect` é utilizado para lidar com efeitos colaterais em componentes funcionais, como fazer fetch de dados, manipular o DOM diretamente ou configurar um timer. Ele pode ser visto como uma combinação dos métodos `componentDidMount`, `componentDidUpdate` e `componentWillUnmount` das classes.

#### Exemplo:

```jsx
import React, { useState, useEffect } from 'react';

function ExemploEfeito() {
  const [contagem, setContagem] = useState(0);

  // useEffect roda após cada renderização
  useEffect(() => {
    document.title = `Você clicou ${contagem} vezes`;

    // Limpeza opcional (chamada quando o componente é desmontado ou antes de atualizar o efeito)
    return () => {
      console.log('Limpando efeito');
    };
  }, [contagem]); // Dependência: só executa o efeito quando 'contagem' muda

  return (
    <div>
      <p>Você clicou {contagem} vezes</p>
      <button onClick={() => setContagem(contagem + 1)}>
        Clique aqui
      </button>
    </div>
  );
}

export default ExemploEfeito;
```

#### Explicação:

- O efeito atualiza o título da página cada vez que o valor de `contagem` é alterado.
- A dependência `[contagem]` significa que o efeito só será executado quando `contagem` mudar.
- O retorno da função (`return () => { ... }`) é opcional e serve para limpar o efeito anterior, útil em casos de timers ou assinaturas.

---

### 3. `useContext`

O hook `useContext` facilita o consumo de valores de um **Contexto** sem precisar de um componente consumidor (como `<Context.Consumer>`).

#### Exemplo:

Primeiro, criamos o contexto:

```jsx
import React, { createContext, useContext } from 'react';

// Criando o contexto
const TemaContext = createContext('claro');

function ExibeTema() {
  // Usando o contexto no componente funcional
  const tema = useContext(TemaContext);

  return <div>O tema atual é: {tema}</div>;
}

function App() {
  return (
    <TemaContext.Provider value="escuro">
      <ExibeTema />
    </TemaContext.Provider>
  );
}

export default App;
```

#### Explicação:

- O `TemaContext` é criado com o valor padrão `'claro'`.
- O `useContext(TemaContext)` permite acessar o valor do contexto diretamente no componente `ExibeTema`, sem a necessidade de usar um wrapper `<TemaContext.Consumer>`.
- O valor do contexto é fornecido através do `TemaContext.Provider`, que define o valor atual como `'escuro'`.

---

### Resumo:

- **`useState`**: Para gerenciar estados locais em componentes funcionais.
- **`useEffect`**: Para lidar com efeitos colaterais como chamadas de API ou atualizações no DOM.
- **`useContext`**: Para consumir valores de contexto diretamente em componentes funcionais.

Esses três hooks formam a base da maioria das funcionalidades de componentes funcionais no React.
