Biblioteca para inserir mascarás em inputs em html puro.
Já existem algumas máscaras padornizadas mas há a opção de passar um regex.

#### Máscara de Telefone

```js
 const element = document.getElementById('phone');
    const maskOptions = {
      mask: '(00) 00000-0000'
    };
    IMask(element, maskOptions);
```


