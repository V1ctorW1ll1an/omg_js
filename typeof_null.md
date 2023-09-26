# typeof null

## Capítulo 1: Os Primeiros Passos do JavaScript

O JavaScript foi criado em 1995 por Brendan Eich enquanto trabalhava na Netscape Communications Corporation. Naquela época, JavaScript era uma linguagem jovem e simples, usada principalmente para adicionar interatividade a páginas web. Para manter as coisas leves e ágeis, a linguagem foi projetada de forma a não ter tipos de dados rígidos como outras linguagens.

## Capítulo 2: A Ambiguidade do Valor null

Quando se tratava de tipos de dados, o JavaScript tinha apenas alguns tipos primitivos, como números, strings e objetos. null foi introduzido para representar a ausência de valor ou a falta de um objeto. No entanto, havia uma peculiaridade - o operador typeof retornava "object" quando aplicado a null. Isso confundiu muitos programadores na época e continua a confundir até hoje.

## Capítulo 3: O Que Significa typeof null Retornar "Object"?

A razão por trás disso estava relacionada a uma escolha de implementação. Quando JavaScript foi criado, os desenvolvedores tinham pouco tempo e recursos para definir todos os detalhes da linguagem. Então, eles decidiram usar os bits disponíveis de maneira eficiente. Os bits mais à esquerda de um ponteiro para um objeto eram usados para determinar se o objeto era primitivo ou não (uma pequena tag de 1-3 bits). O null foi representado com o ponteiro NULL (0x00 na maioria das plataformas). Consequentemente, null teve 0 como sua tag de tipo, portanto o typeof retorna esse valor.O que significava que o JavaScript o tratava como um objeto, embora não fosse realmente um objeto.

### Pequena tabela dos bits e o que eles representam no contexto das tags:

<ul>
  <li>000: object</li>
  <li>1: int </li>
  <li>010: número com ponto flutuante (number) </li>
  <li>100: string</li>
  <li>110: boolean</li>
</ul>

## Capítulo 4: O Problema de null instanceof Object

O enigma ficou ainda mais complicado quando os programadores tentaram usar instanceof para verificar se uma variável era um objeto. Quando alguém tentava:
```javascript
null instanceof Object
```
a resposta era surpreendentemente "false". Isso acontece porque o instanceof não se baseava no resultado do typeof, mas sim na cadeia de protótipos do objeto. Como null não tinha um protótipo (não era um objeto real), instanceof retornava "false".

## Capítulo 5: A Persistência do Enigma

Ao longo dos anos, esse enigma continuou a desafiar os programadores JavaScript, causando confusão e levando a erros sutis. Embora tenha sido reconhecido como um "problema" pela comunidade de desenvolvedores, não foi corrigido devido a preocupações de retrocompatibilidade.

## Conclusão: Explicando o Enigma

Então, por que typeof null retorna "object", mas null instanceof Object retorna "false"? É uma peculiaridade histórica da linguagem JavaScript que foi mantida por razões de compatibilidade. O typeof verifica como o valor é representado internamente, enquanto o instanceof verifica a herança de protótipo. Como null não possui um protótipo, o instanceof retorna "false". É uma anomalia da linguagem que os desenvolvedores precisam estar cientes ao trabalhar com JavaScript.

## Referências:
[ECMA: The typeof Operator](https://262.ecma-international.org/5.1/#sec-11.4.3) <br>
[ECMA: The instanceof Operator](https://262.ecma-international.org/5.1/#sec-11.8.6)<br>
[stackoverflow: Why is typeof null "object"?](https://stackoverflow.com/questions/18808226/why-is-typeof-null-object)<br>
[Mozilla documentation](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Operators/typeof)<br>
[The history of “typeof null”](https://2ality.com/2013/10/typeof-null.html)<br>
[Proposal for typeof null === 'null'](https://web.archive.org/web/20160331031419/http://wiki.ecmascript.org:80/doku.php?id=harmony:typeof_null)<br>
