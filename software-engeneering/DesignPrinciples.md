# Design Principles

##  SOLID
Es un conjunto de principios que se deben tener en cuenta para el desarrollo de software de buena calidad, mantenible, testeable y escalabe.

https://medium.com/@ger86/los-5-principios-solid-68d697984abd
https://es.wikipedia.org/wiki/SOLID
https://www.adictosaltrabajo.com/2003/12/22/grasp/

### S-SRP-Single Responsibility Principle
Una clase debería concentrarse sólo en hacer una cosa de tal forma que  cuando  cambie  algún  requisito  en  mayor  o  menor medida  dicho  cambio  sólo afecte a dicha clase por una razón. 


### O-OCP-Open / Closed Principle
Las entidades de software (clases, módulos, funciones, etcétera) deberían estar abiertas a la extensión pero cerradas a la modificación.
Cambia  el  comportamiento  de  una  clase  mediante  herencia, polimorfismo y composición.

### L-LSP-Liskov Substitution Principle
Las  subclasses  deben  comportarse  adecuadamente  cuando  sean usadas en lugar de sus clases base

### I-ISP-Interface Segregation Principle
Los clientes no deberían ser forzados a depender de interfaces que no utilizan.
Mantén  las  interfaces  pequeñas  y  cohesivas,  que  puedan  coexistir unas con otras

### D-DIP-Dependency Inversion Principle
para   conseguir   robustez   y   flexibilidad   y   para   posibilitar   la reutilización haz que tu código dependa de abstracciones y no de concreciones, esto es,  utiliza  muchas  interfaces  y  muchas  clases  abstractas  y,  sobretodo,  expón,  por constructor o por parámetros, las dependencias que una clase pueda tener.

## GRASP
GRASP son una serie de buenas prácticas enfocadas a la calidad del software, calidad "estructural"  por  llamarla  de  alguna  manera,  ya  que  no  se  ha  centrado  en  pruebas sino en la estructura y las responsabilidades de las clases que componen el software que desarrollamos. GRASP son siete patrones o “consejos”: 

http://www.lsi.us.es/docencia/get.php?id=906
https://www.slideshare.net/Indiana_1969/patrones-grasp-76283581
https://en.wikipedia.org/wiki/GRASP_(object-oriented_design)

### Alta cohesión y bajo acoplamiento 
Alta Cohesion, Nos dice que la información que almacena una  clase debe de ser coherente y debe estar, en la medida de lo posible, relacionada con la clase.
Bajo Acoplamiento, la  idea  de  tener  las clases  lo  menos  ligadas  entre  sí  que  se  pueda, de  tal  forma que,  en  caso  de  producirse  una  modificación  en  alguna  de  ellas,  tenga  la  mínima repercusión   posible   en   el   resto   de   clases,   potenciando   la   reutilización,   y disminuyendo  la  dependencia  entre  las  clases

### Controlador
Separar la capa del modelo de la vista, que el controlador solo sea llamado desde la UI y se comunique con las clases del Modelo, ej: MVC, MVVM, MVVMP

### Creador
El  patrón  creador  nos  ayuda  a  identificar  quién  debe  ser  el  responsable  de  la creación  o  instanciación  de  nuevos  objetos  o  clases.

### Experto en Información
Experto en información nos dice que la responsabilidad de la creación de un objeto o la  implementación  de  un  método,  debe  recaer  sobre  la  clase  que  conoce  toda  la información  necesaria  para  crearlo  o  ejecutarlo

### Fabricacion Pura
La fabricación pura se da en las clases que no representan un ente u objeto real del dominio  del  problema  sino  que  se  han  creado  intencionadamente  para  disminuir  el acoplamiento, aumentar la cohesión y/o potenciar la reutilización del código.

### Indirección
Asignar la responsabilidad a un objeto que medie entre los elementos para proteger al primer objeto de los posibles cambios del segundo.

### Polimorfismo
polimorfismo  es  permitir  que  varias  clases  se comporten de manera distinta dependiendo del tipo que sean. 

### Variaciones Protegidas
Este principio está muy relacionado con el polimorfismo y la indirección.