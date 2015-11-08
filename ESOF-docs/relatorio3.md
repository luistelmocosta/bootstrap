
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

##### <i class="icon-pencil"></i> Notação da vista lógica
=======

<img src="res/logicalview.png" width="500 px"alt="LogicalView"/>


A notação para a vista lógica é derivada da *Booch Notation*. O que torna as coisas consideravelmente mais simples é ter apenas em conta os items que são significantes a nível de arquitectura. Em particular, o número de adornos que possam existir a nível estrutural não são, de todo, importantes para este nível de *design*

##### <i class="icon-folder-open"></i> Estilo para a vista lógica
O estilo que se usa para a vista lógica é um *object oriented style*. O principal objectivo para o *design* correcto da vista lógica é tentar manter um único, coerente *object model* ao longo de todo o sistema, para evitar uma especialização prematura de classes e mecanismos.

#### The Development View

*Subsystem Decomposition*

A arquitectura ou vista de desenvolvimento centra-se na organização modular do software no seu ambiente de desenvolvimento. O software é *packaged* em pequenos pedaços - *program libraries* ou *subsystems* -  que podem ser desenvolvidos por um ou um pequeno grupo de *developers*. Os *subsystems* são organizados numa hierarquia em camadas, sendo que, cada camada, providencia uma estreita e bem definida *interface* para as camadas acima dela. 
A arquitectura de desenvolvimento de um sistema é representada por módulos e *subsystem diagrams*, mostrando relacionamentos de *export* e *import*. A arquitectura de desenvolvimento apenas pode ser completamente descrita quando dos os elementos do software forem identificados. É, no entanto, possível, listar todas as regras que regem a arquitectura de desenvolvimento: o particionamento, agrupamento, visibilidade. 
Para uma análise mais genérica, podemos dizer que a arquitecura de desenvolvimento leva em conta requisitos internos, relacionados com a facilidade de desenvolvimento, gerenciamento de software, reuso, bem como restrições impostas pelo *toolset* ou a linguagem de programação. A vista de desenvolvimento serve de base para o conhecimento da exigência, para o planeamento de trabalho da equipa (ou ate mesmo da organização responsável), para a avaliação dos custos e planeamento, para monitorizar o progresso do projecto, portabilidade e segurança. É a base para o estabelecimento de uma linha de produto.

##### <i class="icon-pencil"></i> Notação da vista de arquitectura

<img src="res/archlview.png" width="500 px"alt="ArchView"/>
<<<<<<< HEAD
=======



>>>>>>> 5f8614f4705d39f8af5bb7d9dc51af49b4bb893d

