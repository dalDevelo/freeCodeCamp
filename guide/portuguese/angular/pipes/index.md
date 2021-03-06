---
title: Pipes
localeTitle: Pipes
---
# Pipes

#### Motivação

Transformações de dados na saída garantem que os dados estejam em um formato desejável no momento em que são exibidos na tela do usuário. Normalmente, os dados se transformam nos bastidores. Com _pipes_ a transformação de dados pode ocorrer no modelo HTML. Os _pipes_ transformam os dados do modelo diretamente.

Os _pipes_ têm uma boa aparência, são convenientes e ajudam a manter a classe do componente enxuta de transformações básicas. Tecnicamente, os _pipes_ a lógica de transformação de dados para exibição.

#### Transformação de Saída

Conforme mencionado na seção anterior, os pipes transformam os dados _inline_. A sintaxe de pipes correlaciona scripts de shell. Em muitos scripts, a saída de uma parte do comando é "canalizada" como saída para servir de entrada a próxima parte do _script_. Essa mesma tendência caracteriza os _pipes_ do Angular.

Em Angular, existem muitas maneiras de interagir com dados no modelo HTML. Os _pipes_ podem ser aplicados em qualquer lugar em que os dados sejam analisados no HTML do modelo. Eles podem ocorrer dentro da lógica das interpolações de variáveis. Os _pipes_ respondem por todas as transformações sem recorrer à classe do componente para tal feito.

_Pipes_ também são encadeados. Você pode integrar _pipes_ um após o outro para executar transformações cada vez mais complexas. Como transformadores de dados especializados, os _pipes_ dificilmente são triviais.

#### Casos de Uso

Angular vem com um conjunto básico de _pipes_ e trabalhar com alguns deles desenvolverá a intuição para lidar com o restante. A lista a seguir fornece dois exemplos.

*   AsyncPipe
    
*   DatePipe
    

Esses dois executam tarefas simples. Sua simplicidade é extremamente benéfica.

##### AsyncPipe

Esta seção requer uma compreensão básica de promessas ou observáveis para tirar um bom proveito pois o AsyncPipe opera em qualquer um dos dois. O AsyncPipe extrai dados de Promises / Observables como saída para o que vem a seguir.

No caso do Obervables, o AsyncPipe assina automaticamente a fonte de dados. Independentemente de onde os dados vêm, o AsyncPipe se associa à fonte observável. `async` é o nome sintático do AsyncPipe, conforme mostrado abaixo.

```html

<ul *ngFor=“let potato of (potatoSack$ | async); let i=index”> 
  <li>Potatoe {{i + 1}}: {{potato}}</li> 
 </ul> 
```

No exemplo, `potatoSack$` é um Observable pendente de um _upload_ de batatas. Quando as batatas chegam, de forma síncrona ou assíncrona, o AsyncPipe as recebe como um array iterável e o elemento da lista é preenchido com o retorno de batatas.

##### DatePipe

A formatação de strings de data pode ser trabalhosa com o objeto JavaScript `Date` . O DatePipe fornece uma maneira poderosa de formatar datas, assumindo que a entrada dada é um formato de hora válido.

```typescript
// example.component.ts 
 
 @Component({ 
  templateUrl: './example.component.html' 
 }) 
 export class ExampleComponent { 
  timestamp:string = '2018-05-24T19:38:11.103Z'; 
 } 
```

```html

<!-- example.component.html --> 
 
 <div>Current Time: {{timestamp | date:'short'}}</div> 
```

O formato do `timestamp` acima é [ISO 8601 1](https://en.wikipedia.org/wiki/ISO_8601) e não é o mais fácil de ler. O DatePipe ( `date` ) transforma o formato de data ISO em um formato mais convencional(`mm/dd/yy, hh:mm AM|PM`). Existem muitas outras opções de formatação. Todas essas opções estão na [documentação oficial](https://angular.io/api/common/DatePipe) .

#### Criando _Pipes_

Embora o Angular tenha apenas um número definido de _pipes_, o decorador `@Pipe` permite que os desenvolvedores criem seus próprios _pipes_. O processo começa com `ng generate pipe [nome-do-pipe]`, substituindo `[nome-do-pipe]` por um nome de arquivo preferível. Este é um comando da [CLI Angular](https://cli.angular.io) . Isso produz o seguinte.

```typescript
import { Pipe, PipeTransform } from '@angular/core'; 
 
 @Pipe({ 
  name: 'example' 
 }) 
 export class ExamplePipe implements PipeTransform { 
  transform(value: any, args?: any): any { 
      return null; 
  } 
 } 
```

Este modelo de _pipe_ simplifica a criação de pipe personalizado. O decorador `@Pipe` diz ao Angular que a classe é um _pipe_. O valor do `name: 'example'` , neste caso sendo `example` , é o valor que o Angular reconhece ao varrer HTML de modelo para canais personalizados.

Para a lógica de classes. A implementação do `PipeTransform` fornece as instruções para a função de `transform` . Esta função tem um significado especial dentro do contexto do decorador `@Pipe` e ele recebe dois parâmetros por padrão.

`value: any` é a saída que o pipe recebe. Pense em `<div>{{ someValue | example }}</div>` . O valor de someValue é passado para o `value: any` da função de `transform`. Esta é a mesma função de `transform` definida na classe ExamplePipe.

`args?: any` é qualquer argumento que o pipe receba opcionalmente. Pense em `<div>{{ someValue | example:[algum-argumento] }}</div>` . `[algum-argumento]` pode ser substituído por qualquer valor. Este valor é passado para o parâmetro `args?: any` da função de `transform`, ou seja, a função de `transform` definida na classe ExamplePipe.

O que quer que a função retorne ( `return null;` ) se torna a saída da operação do pipe. Dê uma olhada no próximo exemplo para ver um exemplo completo de ExamplePipe. Dependendo da variável que o _pipe_ recebe, ele coloca em maiúsculas ou minúsculas a entrada como nova saída. Um argumento inválido ou inexistente fará com que o pipe retorne a mesma entrada como saída.

```typescript
// example.pipe.ts 
 
 @Pipe({ 
  name: 'example' 
 }) 
 export class ExamplePipe implements PipeTransform { 
  transform(value:string, args?:string): any { 
    switch(args || null) { 
      case 'uppercase': 
        return value.toUpperCase(); 
      case 'lowercase': 
        return value.toLowerCase(); 
      default: 
        return value; 
    } 
  } 
 } 
```

```typescript
// app.component.ts 
 
 @Component({ 
  templateUrl: 'app.component.html' 
 }) 
 export class AppComponent { 
  someValue:string = "HeLlO WoRlD!"; 
 } 
```

```html

<!-- app.component.html --> 
 
 <!-- Outputs “HeLlO WoRlD!” --> 
 <h6>{{ someValue | example }}</h6> 
 
 <!-- Outputs “HELLO WORLD!” --> 
 <h6>{{ someValue | example:'uppercase' }}</h6> 
 
 <!-- Outputs “hello world!” --> 
 <h6>{{ someValue | example:'lowercase' }}</h6> 
```

Compreender o exemplo acima significa que você entende os _pipes_ angulares. Há apenas mais um tópico para discutir.

#### Tubulações Puras e Impuras

Tudo o que você viu até agora foi um tubo _puro_ . `pure: true` é definido por padrão nos metadados do `@Pipe` decorator. A diferença entre os dois constitui a detecção de alterações do Angular.

Os _pipes_ puros são atualizados automaticamente sempre que o valor de sua entrada derivada é alterado. O pipe será reexecutado para produzir nova saída após uma alteração detectável no valor de entrada. As alterações detectáveis são determinadas pelo loop de detecção de alterações do Angular.

Os _pipes_ Impure são atualizados automaticamente sempre que ocorre um ciclo de detecção de alteração. A detecção de alterações do Angular acontece com bastante frequência. Ele indica se ocorreram mudanças nos dados dos membros da classe do componente. Em caso afirmativo, o modelo HTML é atualizado com os dados atualizados. Caso contrário, nada vai acontecer.

No caso de um pipe impuro, ele será atualizado independentemente de haver uma alteração detectável ou não. Um pipe impuro é atualizado sempre que os loops de detecção de alterações são alterados. _Pipes_ impuros geralmente consomem muitos recursos e geralmente são mal aconselhados. Dito isto, eles operam mais como uma escotilha de escape. Se você precisar de um `@Pipe` sensível à detecção, alterne `pure: false` nos metadados do `@Pipe` decorator.

#### Conclusão

Isso cobre cachimbos. Os _pipes_ têm muito potencial além do escopo deste artigo. Os Pipes contribuem com transformações de dados sucintas para o HTML do modelo de seus componentes. Eles são uma boa prática em situações em que os dados precisam passar por pequenas transformações.

## Fontes

1.  [Comunidade Wiki. _ISO 8601_ Wikipédia. Acessado em 27 de maio de 2018](https://en.wikipedia.org/wiki/ISO_8601)

## Recursos

*   [Documentação Angular](https://angular.io/guide/pipes)
*   [Repositório Angular GitHub](https://github.com/angular/angular)
*   [Lista de Pipes Pré-embalados com Angular](https://angular.io/api?query=pipe)
*   [CLI Angular](https://cli.angular.io)
