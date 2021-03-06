# Relatório 4 - ESOF
##Bootstrap - Verificação e Validação de Software

<img src="res/logo.png" width="500 px" alt="Bootstrap"/>


### <a name="introducao"></a>Introdução

O objetivo deste relatório consiste na análise dos processos de verificação e validação (V&V) seguidos no desenvolvimento da biblioteca Bootsrap, com a descrição de algumas das características deste projeto que digam respeito à aplicação desses processos.

Numa primeira fase, explorar-se-á o grau de testabilidade do software, analisando a controlabilidade do estado dos componentes, a observabilidade dos resultados e a isolabilidade dos componentes, assim como o grau de separação de funcionalidades, de inteligibilidade dos componentes e de heterogeneidade das tecnologias utilizadas.

Numa segunda fase, serão apresentadas algumas estatísticas pertinentes relacionadas com a verificação e validação do software.

Finalmente, será realizado um exercício que consistirá na seleção de um bug report e na conceção de casos de teste que possam, eventualmente, conduzir à resolução do mesmo.

## Bug Reports, Testes e Revisão de Código

### Grau de Testabilidade

Quanto à sua Testabilidade, o *bootstrap*, está muito bem organizado. O facto da sua arquitectura ser baseada em *packets* e classes, faz com que o projecto se torne mais modular e forneça assim, uma separação coerente, que permite que os testes se façam de uma maneira simples e eficaz. 

De seguida, apresentamos e clarificamos algumas das características que permitem avaliar a testabilidade.

Nas subsecções seguintes serão analisados em maior detalhe os vários aspetos que permitem avaliar as características de testabilidade.

#### Controlabilidade dos componentes em estudo

O Bootstrap apresenta uma organização de código e um paradigma de programação orientado ao objecto, recorrendo a todas as vantagens e capacidades que o *javascript* disponibiliza. A linguagem de programação utilizado fornece ferramentas preciosas para que haja uma manipulação rigorosa e correcta dos objetos instanciados bem como o valor neles guardados.
Nota para os testes unitarios que são muito utilizados neste projecto e que têm como finalidade o estudo do comportamento de uma class e/ou objecto em particular, sendo criada vários tipo de abstrações, como veremos ao longo deste relatório.

A nível intermédio também é possível salientar as capacidades de análise de comportamento fornecidas pelo [PhantomJS](#phantomjs), uma ferramenta **headless testing**. O principal uso de PhantomJS é testar abstratamente aplicações web. Não é, em si, uma framework de testes mas sim usado para correr testes, através de um *test runner* apropriado. Durante a execução do PhantomJS são corridas *test frameworks* como [JSCS](#jscs), [QUnit](#qunit), [JSHint](#jshint). 


###Testabilidade:

Iremos agora avaliar o quão testável o projeto *Bootstrap* é. Até que ponto é possível verificar e validar o mesmo em termos de implementação. É importante salientar que após uma análise do projeto podemos constatar que é utilizada a ferramenta [QUnit](#qunit) que permite testar componentes da aplicação, através de testes unitários.

####Controlabilidade:

A controlabilidade está relacionada com o grau com que é possível controlar o estado de uma componente a ser testada. Uma vez que o estado de cada uma das componentes princípais do *Bootstrap* é independente, é possível criar testes unitários para testar o estado de cada uma destas separadamente.

####Observabilidade:

Na testabilidade de *software* a observabilidade é o grau com que é possível observar o resultado dos testes realizados. A equipa do *Bootstrap* criou um *plugin* de teste chamado *Test Suite* e recomenda correr este *plugin* de duas maneiras, através do [PhantomJS](#phantomjs) apartir do [Grunt](#grunt) ou através do *web browser* apatir de um *html* fornecido.



<img src="res/PhantomJS.png" width="500 px" alt="PhantomJS"/>

>***Test Suite* testado com *PhantomJS*:**




<img src="res/testsuite.png" alt="testsuite"/>

>***Test Suite* testado com *Web Browser*:**


####Isolabilidade:

A Isolabilidade refere-se à serparação de cada componente na criação de testes unitários. Através da análise do repositório conseguimos ver que são criados ficheiros de teste independentes para cada uma das componentes do *Bootstrap*, existindo assim grande facilidade em testar as componentes sem depender de outras.

<img src="res/isol.png"  alt="isol"/>

> Ficheiros de teste disponiblizados pela equipa do *Bootstrap* para teste das componentes **affix**, **alert** e **button**.


#### Separação das responsabilidades de cada componentes

Para uma verificação e validação de requisitos de software, a separação das responsabilidades de cada componente torna-se muito relevante e vantajosa. Uma classe/componente que assuma demasiadas responsabilidades ou que dependa de outras, torna-se sensível a erros e à introdução de falhas. Definir um teste de na maior abstração possível, faz com que seja possível fazer testes à sua funcionalidade e integridade de uma maneira eficaz.

*Bootstrap* assenta numa estrutura modular composta por packages. Esses packages são responsáveis pela implementação de diversos componentes que permitem que o *software* esteja sempre no vigor das suas funcionalidades. Assim, o [*Bootstrap*](getbootstrap.com/), apresenta uma estrutura externa de responsabilidades altamente segmentadas e claramente definidas, reservando para si apenas o papel de gestor e coordenador das diferentes *packages* centrais ao funcionamento correcto do programa. 



#### Compreensibilidade
O [*Bootstrap*](https://getbootstrap.com/) está [bem documentado](http://getbootstrap.com/getting-started/), em parte devido à sua natureza *open-source*, que obriga a que a documentação seja explícita e concisa para que possa ser consultada e aprendida celeremente e compreendida pelo maior número de pessoas possível.

A arquitetura do [*Bootstrap*](https://getbootstrap.com/) é complexa e algo extensa, resultando a sua cuidada separação de responsabilidades num leque alargado de classes cujos nomes e comportamento podem não resultar evidentes para um leigo no que a terminologia de editores de texto diga respeito. Posto isto, os autores do relatório consideram que existe, integrado no código, uma organização documental suficiente para suprir o problema descrito, e para permitir a quem o estuda uma compreensão adequada dos objetivos de cada componente, quer ao nível da classe quer ao nível dos métodos individuais. 

#### Heterogeneidade

Uma vez que o projecto é open-source e, consequentemente aberto a contribuições de vários colaboradores, é necessário garantir que, após a modificação do código, originada por um dado pull request, o sistema permanece globalmente funcional.

Por um lado, a realização de testes unitários permite garantir o correto funcionamento dos componentes (isolados) da biblioteca. Por outro lado, é preciso averiguar o correcto funcionamento dos vários módulos constituintes do software, quando combinados, surgindo a necessidade de realizar testes de integração. Através da ferramenta Travis CI garante-se a automatização destes testes de integração.

A passagem do código submetido nos testes é uma condição necessária (embora possam ser abertas algumas exceções) à sua aceitação por parte da core team.

Pode assim concluir-se que a utilização de um repositório público do GitHub, aberto a vários colaboradores, resulta numa heterogeneidade das ferramentas de teste utilizadas.

No repositório do [*Bootstrap*](https://getbootstrap.com/) está disponível uma sólido conjunto de testes.


####Observação:

Através da análise das ferramentas acima citadas, verifica-se que a equipa de desenvolvimento do Bootstrap tem preocupações no que diz respeito à eficácia do código desenvolvido assim como com a maneira como este é desenvolvido. Tentam automatizar tarefas e garantir que o código segue certas *guidelines* que o tornam menos propício a erros, assim como amplamente compatível.

-----
#### Conceitos Importantes

[JSHint, A Static Code Analysis Tool for JavaScript](http://jshint.com/about/)

JSHint é uma ferramenta que tem como finalidade detetar erros e potenciais problemas de código JavaScript, permitindo assim que os desenvolvedores se possam focar em escrever programas, não tendo a preocupação com alguns problemas como *typos* ou *language gotchas*. Uma das suas caracteristicas mais importantes é a sua flexibilidade que permite uma fácil adaptação a diferentes tipos de projetos.

<div id='grunt'/>
[Grunt - The JavaScript Task Runner](http://gruntjs.com/)

Por que usar um *task runner*?

Porque permite automatizar as tarefas repetitivas inerentes ao desenvolvimento de software como a minificação e compilação, poupando desta forma tempo e esforço a quem o desenvolve.

<div id='phantomjs'/>
[PhantomJS](http://phantomjs.org/headless-testing.html)

O principal uso de PhantomJS é testar abstratamente aplicações web. Não é, em si, uma framework de testes mas sim usado para correr testes, através de um *test runner* apropriado.

<div id='travisci'/>
[TravisCI](https://travis-ci.org/)

É um serviço utilizado para construir projectos e realizar testes de integração sobre o código alojado no GitHub. Sempre que um commit e push são feitos, esta ferramenta automaticamente tenta fazer *build* do projecto e seguidamente correr os testes, de forma a possibilitar a adição, sem conflitos com outras partes do código, das novas funcionalidades. 



#####Test Frameworks

The following table summarizes the list of various test frameworks and the corresponding test runners. If the framework does not need an external/third-party runner, it is marked as "built-in".

<div id='qunit'/>
[QUNIT](http://qunitjs.com/intro/)

QUnit é uma framework de testes para JavaScript. Surgiu pela necessidade de ter uma unidade de testes para código *client-side*. Por unidade de testes entenda-se um conjunto de funções que, dado um input, produz sempre o mesmo output.


[JSCS](http://jscs.info/)

JavaScript Code Style (JSCS) é uma ferramenta para detecção de anomalias no código JavaScript. Este tipo de ferramentas são particularmente úteis em linguagens de programação interpretadas, tal como o JavaScript.
Permite a configuração em específico para um projecto, tendo disponível mais de 150 regras de validação, incluindo estilos populares pré-definidos como jQuery e Google.


[jQuery](https://jquery.com/)

jQuery é a mais famosa e utilizada biblioteca de JavaScript. A sintaxe do jQuery foi desenvolvida com o intuito de tornar mais simples a navegação do documento HTML, a seleção de elementos DOM, a criação de animações, a manipulação de eventos e o desenvolvimento de aplicações AJAX.
Entre as suas principais características destacam-se: resolução da incompatibilidade entre navegadores, redução de código, reutilização do código através de plugins e implementação segura de recursos das várias versões de CSS.



------------------

### <a name="info"></a>Informações

##### Autores:

* Luís Telmo Costa - 200806068
* José Carlos da Rocha Lima - ei10012
* Alexandre Marques de Castro Ribeiro - ee12288

Faculdade de Engenharia da Universidade do Porto - MIEIC

2015-11-22
