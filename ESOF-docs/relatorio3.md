[ESOF] Relatório 3 - Arquitetura de Software
===================

<img src="res/logo.png" width="500 px" alt="Bootstrap"/>



### <a name="introducao"></a>Introdução


O objetivo deste relatório é a explicitação de alguns aspetos relativos à arquitetura do projeto Bootstrap, seguindo o [modelo de vistas 4+1](https://en.wikipedia.org/wiki/4%2B1_architectural_view_model). Ao longo do relatório serão mostrados alguns diagramas exemplificativos do funcionamento e implementação deste modelo.

----------


O Modelo 4+1
-------------

O modelo de vistas 4+1 de Arquitetura de Software permite juntar várias pontos de vista sobre o mesmo software para dar uma perspectiva o mais completa possível sobre o mesmo. Este modelo baseia-se então nos pontos de vista apresentados a seguir.

![](https://upload.wikimedia.org/wikipedia/commons/f/f2/4%2B1_Architectural_View_Model.jpg)

> **Note:**

> O Modelo 4+1 foi desenvolvido por [Philippe Kruchten](https://en.wikipedia.org/wiki/Philippe_Kruchten), um engenheiro de Software, nascido em 1952, no Canadá. Segundo Phillipe, este modelo foi criado com a intenção de descrever a arquitectura de **software intensive systems**, baseado no uso de muitas vistas e todas elas concorrentes. 

Este uso de múltiplos pontos de vista permite abordar separadamente as preocupações dos vários *stakeholders* da arquitetura: o usuário final, desenvolvedores, engenheiros de sistemas, gerentes de projeto, etc., e para lidar separadamente os requisitos funcionais e não funcionais. Cada um dos cinco pontos de vista é descrito, em conjunto com uma notação de apreender todas as noções que as envolvem. 




#### Logical View
*The Object-Oriented Decomposition*

A vista lógica, de maneira sucinta, é responsável por suportar os requisitos funcionais - o que o sistema deve providenciar em termos de serviços aos seus utilizadores. O sistema é decomposto com conjunto de abstrações essenciais, retiradas maioritariamente do domínio do nosso problema, na forma de *objects* ou *object classes*, que permitem explorar os principios da abstração, encapsulação e herança. Esta decomposição não é apenas essencial para uma análise funcional do sistema, mas permite também identificar os mecanismos mais comuns e retratar elementos valiosos que existem nas várias plataformas do projecto. Para representar a arquitectura lógica, usam-se *class diagrams* e *class templates*, também conhecida por *Rational/Booch approach*.
Um diagrama de classes mostra um conjunto de classes e as suas relações lógicas: associação, uso, composição, herança, etc. Um conjunto de classes associadas podem ser agrupadas em categorias de classes. Os *class templates* focam-se em cada *class* individualmente, enfatizando as operações principais da classe e identificando as características principais de cada objecto. 

![](https://raw.githubusercontent.com/luistelmocosta/bootstrap/master/ESOF-docs/res/logicalview.png)
<br>
No *bootstrap* a *logical view* está dividida em quatro partes:<br><br>
	-**less** : contem os ficheiros de css não compliados que posteriormente se irão juntar no ficheiro **bootstrap.css**;<br><br>
	-**fonts**: contem as fontes e icons utilizados pelo bootstrap;<br><br>
	- **js**: contem os ficheiros todos de javascript não compilados que posteriormente se irão juntar no ficheiro **bootstrap.js**;<br><br>
	- **dist**: contem os ficheiros compilados do bootstrap.<br><br>


#### The Development View

*Subsystem Decomposition*

A arquitectura ou vista de desenvolvimento centra-se na organização modular do software no seu ambiente de desenvolvimento. O software é *packaged* em pequenos pedaços - *program libraries* ou *subsystems* -  que podem ser desenvolvidos por um ou um pequeno grupo de *developers*. Os *subsystems* são organizados numa hierarquia em camadas, sendo que, cada camada, providencia uma estreita e bem definida *interface* para as camadas acima dela. 
A arquitectura de desenvolvimento de um sistema é representada por módulos e *subsystem diagrams*, mostrando relacionamentos de *export* e *import*. A arquitectura de desenvolvimento apenas pode ser completamente descrita quando dos os elementos do software forem identificados. É, no entanto, possível, listar todas as regras que regem a arquitectura de desenvolvimento: o particionamento, agrupamento, visibilidade. 
Para uma análise mais genérica, podemos dizer que a arquitecura de desenvolvimento leva em conta requisitos internos, relacionados com a facilidade de desenvolvimento, gerenciamento de software, reuso, bem como restrições impostas pelo *toolset* ou a linguagem de programação. A vista de desenvolvimento serve de base para o conhecimento da exigência, para o planeamento de trabalho da equipa (ou ate mesmo da organização responsável), para a avaliação dos custos e planeamento, para monitorizar o progresso do projecto, portabilidade e segurança. É a base para o estabelecimento de uma linha de produto.



#### The Process View

*The Process Decomposition*

A arquitectura de processo tem em conta alguns dos requisitos não funcionais, como a *performance* e a disponbilidade. Aborda questões de simultaneidade e distribuição, da integridade do sistema, de tolerância a falhas, e como as principais abstrações da vista lógica se ajustam dentro da arquitectura de processo - em que segmento de controlo é executada uma operação relativa a um determinado objecto. A **vista de processo** pode ser descrita em vários níveis de abstração, cada nível com diferentes tipos de preocupações. 
Um **processo** é um conjunto de tarefas que formam uma unidade executável. Processos representam a camada onde a arquitectura de processo pode ser tacticamente controlada (iniciada, recuperada, reconfigurada, desligada). Em adição, os processos podem ser replicados para uma maior distribuição da carga de processamento, ou para melhorar a disponibilidade.

![](https://raw.githubusercontent.com/luistelmocosta/bootstrap/master/ESOF-docs/res/processview.png)

Quanto à vista de processo no bootstrap, é do entender dos autores que o conjunto de atividades que são executadas no lado do cliente são as que possuem uma maior relevância, justificando-se a sua inclusão neste relatório, ainda que outras pudessem ser identificadas, nomeadamente no lado do servidor.<br>

#### Deployment View

*Mapping the software to the hardware*

A vista física leva em conta os requisitos não-funcionais do sistema, tais como disponibilidade, confiabilidade (tolerância a falhas), desempenho (taxa de transferência) e escalabilidade. 
Um diagrama de deployment permite mostrar de que modo os artefactos de um sistema são distribuídos em nós de hardware. Os artefactos de um sistema são manifestações físicas dos seus componentes de software, e relacionam-se com determinados componentes de hardware.
É esperado que algumas das configurações fisicas sejam utilizadas: algumas para desenvolvimento e teste e outras para implantação (*deployment*). O mapeamento do software para os **nodes** precisa, portanto, ser altamente flexível e ter um impacto mínimo sobre o próprio código fonte.


----------


Correspondência entre vistas
-------------------

As várias vistas não são completamente ortogonais ou independentes. Elementos de uma vista estão conectados aos elementos de outra vista, seguindo regras de *design* e heurística.

##### **A partir da vista lógica para a vista de processo**

Identificamos já as várias características importantes das classes da vista lógica:




> - Autonomia: os objectos são activos, passivos ou protegidos?
>  - Objectos activos tomam a iniciativa de invocar operaçoes de outros objectos ou suas próprias operações e tem controlo total sobre a invocação das suas póprias operações por outros objectos.
>  - Um objecto passivo não invoca espontaneamente quaisquer operações e não tem qualquer controlo sobre a invocação das suas operaçoes quando invocado por outros objectos.
>  - Um objecto protegido não invoca espontaneamente quaisquer operações, mas tem alguma arbitrariedade na invocação das suas operações.
> - Persistência: são os objetos transientes ou permanentes? Provocam alguma falha de um processo ou do processador?
> - Subordinação: são a existência ou persistência de um objecto de acordo com outro objecto?
> - Distribuição: são o estado ou as operações de um objeto acessível a partir de muitos nós na vista fisica, a partir de processos explicitados na vista de processos? 

Na vista lógica da arquitectura consideramos cada objeto como ativo e potencialmente "concorrente", isto é, comporta-se "em paralelo" com outros objetos e não se presta mais atenção para o grau exato de simultaneidade que é necessário para conseguir este efeito. Daí a arquitectura lógica levar apenas em conta o aspecto funcional dos requisitos. 
No entanto, quando chegamos à parte de definir a arquitectura de processos, implementar cada objecto com a sua própria tarefa de controlo não é muito prático por causa da sobrecarga que isso pode trazer. Além disso, se os objetos são concorrentes, deve haver alguma forma de conseguir arbitrar a maneira como são invocadas as suas operações. Existem, porém, factores como aumentar a utilização do CPU ou prioritizar actividades (aumentando o tempo de resposta) que fazem com que vários *threads* de controlo sejam necessários. 
Usam-se duas estratégias para determinar o montante "certo" de simultaneidade e definir o conjunto de processos que são necessários. Tendo em mente o conjunto de arquitecturas físicas que podem ser alvo, pode proceder-se de duas maneiras:

>- Inside-out (De dentro para fora ou do *avesso*)
Começando a partir da arquitectura lógica: definir as tarefas de um *agent* que multiplexa uma única thread de controlo ao longo de multiplos objectos activos de uma classe; objetos cuja persistência ou duraçao é subordinado a um objeto activo também são executados no mesmo *agent*; várias classes que precisam ser executadas por *mutual exclusion*, ou que exigem apenas uma pequena quantidade quota de processamento partilham, também, um único *agent*. Este agrupamento prossegue até reduzirmos os processos a um número razoavelmente pequeno que permita a distribuição e utilização dos recursos físicos. 

> - Outside-in (de fora para dentro)
Começando pela arquitectura fisica: identificar estimulos externos (pedidos) para o sistema, definir os *client processes* para lidar com os estímulos e processos que apenas providenciam serviços e não os inciam; identificar os objectos que precisam ser distribuidos.

O resultado é um mapeamento das classes (e seus objetos) para um conjunto de tarefas e processos da arquitectura de processos. Tipicamente, existe sempre um *agent task* para uma classe activa, com algumas variações: alguns *agents* para uma determinada classe para aumentar o rendimento, ou várias classes mapeadas num único *agent* porque as suas operações raramente são invocadas ou para garantir uma execução sequencial.
De salientar que este não é um processo linear e determinista que leva a uma arquitectura de processos óptima; requer algumas iterações para que possa receber um *compromisso* fiável. 

##### **Da vista lógica para a vista de desenvolvimento**

Uma classe normalmente é implementada como um módulo. Classes extensas são decompostas em multiplos *packages*. Conjuntos de classes que estão intimamente ligadas-*class categories*- são agrupadas em *subsystems*. Outros factores têm de ter tido em conta para a definição de *subsystems* como a organização da equipa, a magnitude do codigo (tipicamente de 5K a 20K SLOC por *subsystem*, o grau de reutilização e semelhança esperado e rigorosos príncipios de estratificação (questões de visibilidade), a política de lançamento e o gerenciamento de configuração. Portanto, geralmente acaba-se sempre com uma vista que não possui uma correspondência 1-1 com a vista lógica estabelecida. 
As vistas lógicas e de desenvolvimento são muito proximas, mas têm diferentes preocupações. Está comprovado que quanto maior for o projecto, maior é a distância entre as vistas. 

##### **A partir da vista de processo para a vista física**

Processos e grupos de processos são mapeados para o hardware fisico disponível, em várias configurações, para teste ou *deployment*.

Adaptação do Modelo
-------------------

Nem todos os projectos precisam de uma arquitectura de software com as "4+1" views. Vistas que são inúteis podem ser omitidas da descrição da arquitectura, como a vista fisica, se houver apenas um processador ou até mesmo a vista de processos se apenas existe um unico processo ou programa. Para um sistema muito pequeno, as semelhanças entre a vista de desenvolvimento e a vista lógica são tão grandes que não são necessárias descrições separadas. 

Conclusão
-------------------
Este modelo "4+1" tem sido utilizado com sucesso em vários projectos grandes, cou ou sem algumas adaptações na sua terminologia. Este modelo permite que os varios *stakeholders* encontrem aquilo que querem saber sobre a arquitectura do software. *System Engineers* vão olhar para a arquitectura através da **vista física**, por seu lado, *end-users*, clientes, *data specialists* vão querer saber da **vista lógica** e por fim, *project managers*, ou equipas de manutenção de software vão prestar atenção na **vista de desenvolvimento**.



### <a name="info"></a>Informações

##### Autores:

* Luís Telmo Costa - 200806068
* José Carlos da Rocha Lima - ei10012
* Alexandre Marques de Castro Ribeiro - ee12288

Faculdade de Engenharia da Universidade do Porto - MIEIC

2015-11-08






