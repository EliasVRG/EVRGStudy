Vamos dar uma olhada nas vantagens que ela trás e quais problemas ela resolve?

Uma parada bacana do **axios** é que ele é um cliente HTTP baseado em promessas totalmente agnóstico, ou seja, que não depende de  **frameworks e bibliotecas** . Ele é super maleável, podendo ser utilizado do lado do cliente ([React](https://www.alura.com.br/artigos/react-js), Vue, [Svelte](https://www.alura.com.br/artigos/svelte-versus-react-quais-diferencas), etc) e do lado do **backend** ( **express, nest, etc** ). Então vamos mergulhar um pouco mais fundo e ver o que a gente consegue fazer com ele.

Para termos o `axios` disponível em nossa aplicação, basta instalá-lo com via NPM:

```
npm i axios
```

Ou importá-lo de uma CDN, por exemplo:

```
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

Depois, importamos ele diretamente e já estamos pronto para fazer a primeira chamada:

Com require:

```
const axios = require('axios').default;
```

Com `default import`:

```
import axios from 'axios'
```

Finamente com o axios em mãos, podemos de fato fazer o pedido:

```
axios.get('https://catfact.ninja/fact')
```

Como eu disse anteriormente, ele é baseado em promessas então podemos lidar com o sucesso e a falha da chamada:

```
axios.get('https://catfact.ninja/fact')
  .then(function (response) {
    // aqui acessamos o corpo da resposta:
    console.log(response.data);
  })
  .catch(function (error) {
    // aqui temos acesso ao erro, quando alguma coisa inesperada acontece:
    console.log(error);
  })
```

O axios é tão melhor amigo da gente que ele oferece vários atalhos para os tipos de requisições:

* `axios.get('url')`
* `axios.delete('url')`
* `axios.head('url')`
* `axios.options('url')`
* `axios.post('url', { ...dados })`
* `axios.put('url', { ...dados })`
* `axios.patch('url', { ...dados })`

Vamos agora pensar numa [API Rest](https://www.alura.com.br/artigos/rest-conceito-e-fundamentos), onde temos **endpoints** para criar, deletar, alterar e exibir recursos. Alguma coisa do tipo:

```
https://api.aluroni.com.br/pratos
```

Então, para realizarmos todas as operações do **CRUD** (**acrônimo** do inglês  **Create** ,  **Read** , **Update** and **Delete** que são as quatro operações básicas:  **criação** ,  **consulta** , **atualização** e  **destruição de dados** ) temos o seguinte:

Consultar todos os pratos:

```
axios.get('https://api.aluroni.com.br/pratos')
  .then(function (resposta) {
    // aqui acessamos o corpo da resposta:
    console.log(resposta.data) // lista de todos os pratos do Aluroni
  })
```

Consultar um prato específico:

```
axios.get('https://api.aluroni.com.br/pratos/42')
  .then(function (resposta) {
    // aqui acessamos o corpo da resposta:
    console.log(resposta.data) // obtemos os dados do prato cujo o id (identificador único) é 42
  })
```

E para criar um prato fazemos um POST:

```
axios.post('https://api.aluroni.com.br/pratos', {
    nome: 'Lasanha',
    descricao: 'O jantar mais gostoso do mundo inteirinho!'
})
  .then(function () {
    // se tudo der certo, o prato vai ser criado!
  })
```

E se quisermos alterar um prato:

```
axios.put('https://api.aluroni.com.br/pratos/42', { // dependendo da API, pode ser um PATCH ao invés do PUT
    nome: 'Lasanha',
    descricao: 'O jantar mais gostoso do UNIVERSO!'
})
  .then(function () {
    // se tudo der certo, o prato vai ser atualizado!
  })
```

E finalmente podemos deletar um prato, dado um identificador:

```
axios.delete('https://api.aluroni.com.br/pratos/42')
  .then(function () {
    // se tudo der certo, o prato vai ser removido!
  })
```

Assim temos todas as operações. Mas não para por aí! Ainda tem mais coisas legais que podemos fazer.

Imagine que queremos definir algumas opções comuns a todas as requisições… por exemplo algumas informações do cabeçalho das requisições. Algo do tipo "User Agent" para identificar quem está realizando os pedidos ou um "Authorization" para mandarmos um  **token de segurança** . Ou mesmo a URL base, que se repete a cada pedido (no nosso exemplo, `https://api.aluroni.com.br/pratos`). Podemos então criar uma **instância do axios** com as opções que queremos:

```
export const http = axios.create({
    baseURL: 'https://api.aluroni.com.br,
    headers: {'User-Agent': 'AluroniAdmin'}
  });
```

E assim podemos simplificar as chamadas anteriores para:

```
http.get('pratos')
http.get('pratos/42')
http.post('pratos', {...dados})
http.put('pratos/42', {...dados})
http.delete('pratos')
```

Além disso, temos uma funcionalidade bacanissima, que é a interceptação de requisições e respostas:

```
// Adiciona um interceptador de requisição
http.interceptors.request.use(function (config) {
    // Faça algo antes do pedido ser enviado
    return config;
  }, function (error) {
    // Faça algo com caso algo dê errado
    return Promise.reject(error);
  });

// Adiciona um interceptor de resposta
http.interceptors.response.use(function (response) {
    // Qualquer código de status que esteja dentro do intervalo de 2xx faz com que esta função seja acionada
    // Faça algo com os dados de resposta
    return response;
  }, function (error) {
    // Qualquer código de status que esteja fora do intervalo de 2xx faz com que esta função seja acionada
    //Faça algo com erro de resposta
    return Promise.reject(error);
  });
```

[aqui na documentação](https://axios-http.com/ptbr/docs/intro).
