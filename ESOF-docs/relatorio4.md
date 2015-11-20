# Relatório 4 - ESOF
##Bootstrap - Verificação e Validação de Software

<img src="res/logo.png" width="500 px" alt="Bootstrap"/>


### <a name="introducao"></a>Introdução

O objetivo deste relatório consiste na análise dos processos de verificação e validação (V&V) seguidos no desenvolvimento da biblioteca Bootsrap, com a descrição de algumas das características deste projeto que digam respeito à aplicação desses processos.

Numa primeira fase, explorar-se-á o grau de testabilidade do software, analisando a controlabilidade do estado dos componentes, a observabilidade dos resultados e a isolabilidade dos componentes, assim como o grau de separação de funcionalidades, de inteligibilidade dos componentes e de heterogeneidade das tecnologias utilizadas.

Numa segunda fase, serão apresentadas algumas estatísticas pertinentes relacionadas com a verificação e validação do software.

Finalmente, será realizado um exercício que consistirá na seleção de um bug report e na conceção de casos de teste que possam, eventualmente, conduzir à resolução do mesmo.


[JSHint, A Static Code Analysis Tool for JavaScript](http://jshint.com/about/)

JSHint is a community-driven tool to detect errors and potential problems in JavaScript code and to enforce your team's coding conventions. It is very flexible so you can easily adjust it to your particular coding guidelines and the environment you expect your code to execute in. JSHint is open source and will always stay this way.  O objectivo deste projecto é ajudar os desenvolvedores de JavaScript a escrever programas completos sem se preocuparem com *typos* ou *language gotchas* 


[Grunt - The JavaScript Task Runner](http://gruntjs.com/)


Why use a task runner?

In one word: automation. The less work you have to do when performing repetitive tasks like minification, compilation, unit testing, linting, etc, the easier your job becomes. After you've configured it through a Gruntfile, a task runner can do most of that mundane work for you—and your team—with basically zero effort.

[PhantomJS](http://phantomjs.org/headless-testing.html)

One major use case of PhantomJS is headless testing of web applications. It is suitable for general command-line based testing, within a precommit hook, and as part of a continuous integration system.

<img src="res/PhantomJS.png" width="500 px" alt="PhantomJS"/>

#####Test Frameworks

PhantomJS itself is not a test framework, it is only used to launch the tests via a suitable test runner.

The following table summarizes the list of various test frameworks and the corresponding test runners. If the framework does not need an external/third-party runner, it is marked as "built-in".


[QUNIT](http://qunitjs.com/intro/)

You probably know that testing is good, but the first hurdle to overcome when trying to write unit tests for client-side code is the lack of any actual units; JavaScript code is written for each page of a website or each module of an application and is closely intermixed with back-end logic and related HTML. In the worst case, the code is completely mixed with HTML, as inline events handlers.

This is likely the case when no JavaScript library for some DOM abstraction is being used; writing inline event handlers is much easier than using the DOM APIs to bind those events. More and more developers are picking up a library such as jQuery to handle the DOM abstraction, allowing them to move those inline events to distinct scripts, either on the same page or even in a separate JavaScript file. However, putting the code into separate files doesn’t mean that it is ready to be tested as a unit.

What is a unit anyway? In the best case, it is a pure function that you can deal with in some way — a function that always gives you the same result for a given input. This makes unit testing pretty easy, but most of the time you need to deal with side effects, which here means DOM manipulations. It’s still useful to figure out which units we can structure our code into and to build unit tests accordingly.


[JSCS](http://jscs.info/)

JSCS is a code style linter for programmatically enforcing your style guide. You can configure JSCS for your project in detail using over 150 validation rules, including presets from popular style guides like jQuery, Airbnb, Google, and more. 

[jQuery](https://jquery.com/)

#####What is jQuery?

jQuery is a fast, small, and feature-rich JavaScript library. It makes things like HTML document traversal and manipulation, event handling, animation, and Ajax much simpler with an easy-to-use API that works across a multitude of browsers. With a combination of versatility and extensibility, jQuery has changed the way that millions of people write JavaScript.
