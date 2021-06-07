# Título de la investigación

# “Escribir un Titulo”

<br/>

<br/>

<br/>

<h2 style="text-align:center;">Maestría en Ciencia de Datos e Información</h2>

<br/>

<h3 style="text-align:center;">Equipo 902-E:</h3>

<h3 style="text-align:center;">Ismael Medina Muñoz</h3>

<h3 style="text-align:center;"> Helio Jiménez García</h3>



<div style="page-break-after: always; break-after: page;"></div>

##  Resumen

El resumen es una referencia breve del planteamiento del problema, los  objetivos que dicha investigación quiere alcanzar y los métodos usados.  No debe exceder de las 250 palabras.

## Introducción

Las empresas disponen de recursos que aplicados de manera correcta, la distinguen de otras empresas similares.  Dentro de dichos recursos el mas importante es el personal que compone la empresa.

Uno de los objetivos empresariales permanentes a través del tiempo ha sido como aprovechar al máximo los recursos disponibles y desde luego incluimos el recurso humano porque en algunos casos es uno de los gastos mas importantes para la organización.

El presente trabajo busca aplicar el conocimiento científico para la mejor asignación de trabajos a un grupo de empleados en una empresa de software.  Es decir, nuestra empresa cuenta con un grupo de ingenieros calificados que son llamados a atender las necesidades de servicio de la cartera de clientes con los que cuenta la empresa.  La particularidad de esta situación es que por lo regular la cantidad de servicios o reparaciones es mayor a la cantidad de ingenieros con los que la compañía  cuenta y la dirección de la empresa busca aprovechar al máximo los recursos humanos y al mismo tiempo cubrir las expectativas de calidad de servicio y tiempo de entrega para cada uno de los clientes.

La complejidad de la situación se incrementa ya que cada solicitud de servicio tiene su nivel de complejidad y de manera similar cada ingeniero posee una serie de habilidades y experiencia que los diferencian a unos de otros al momento de atender las solicitudes.  También tenemos otro aspecto que aumenta la complejidad y es que se hace necesario empatar el calendario de espacios de tiempo disponible de cada ingeniero con el periodo de tiempo que cada solicitud de servicio tiene asignada.

Dadas las características del problema, donde tenemos recursos limitados que compiten por la realización de ciertas actividades, lo hemos empatado con la rama de la Investigación de Operaciones y mas en especifico dentro de la Programación Lineal Entera.  Lo consideramos de esta manera ya que tenemos un problema de optimización de recursos de un proceso de la actividad humana.  En especifico deseamos minimizar los costos generados por la atención de los ingenieros sobre las solicitudes de servicio de los clientes.

En esencia este trabajo busca implementar una solución ya conocida dentro del mundo de la Programación Lineal, denominada modelo de asignación, a un problema real sacado del mundo empresarial de México y encontrar la mejor solución a una problemática a la que los administradores se enfrentan de manera cotidiana. 

## Planteamiento del problema

*El planteamiento del problema es la justificación científica del motivo  de la investigación. Se aclara el problema científico presentado y el  porqué del uso de una investigación para resolver el problema.*

En una empresa de servicios especializados entregados por ingenieros calificados, los ingenieros viajan a la localidad de los clientes para la entrega de los mismos. La entrega de cada servicio sólo dura una semana, por lo que la planeación de asignaciones se hace con esta cadencia. Los ingenieros tienen una matriz de acreditaciones para la entrega de servicios, por lo que dependiendo de la solicitud de los clientes, sólo algunos ingenieros estarían acreditados para entregar el servicio solicitado.

 Dado que los servicios se solicitan en toda Latinoamérica y que los ingenieros están localizados en ciertos países, un ingeniero con una acreditación en el servicio solicitado cerca del país donde el cliente se ubica puede ser un primer indicio de una reducción de costos bajo ciertas restricciones.

 Los ingenieros tienen una agenda muy ocupada y los clientes buscan recibir sus servicios lo antes posible. Por política de la empresa, cada cliente debe estar siendo visitado por un ingeniero antes de dos meses.

### Matriz de solicitudes

A continuación se muestra la matriz de solicitudes de servicio que se han realizado a la compañía por diversos clientes.

| **IdServicio** | **IdCliente** | **Fecha de la solicitud** |
| -------------- | ------------- | ------------------------- |
| **1**          | 10            | 2021-06-07                |
| **1**          | 12            | 2021-06-14                |
| **4**          | 3             | 2021-05-24                |
| …              | …             | …                         |
| **2**          | 9             | 2021-06-07                |

###La matriz de acreditaciones de ingenieros.

 La empresa tiene un registro de las acreditaciones de sus ingenieros con un identificador binario. Estos se muestran en la siguiente tabla

| Id_Ingeniero | IDServ_01 | IDServ_02 | IDServ_03 | IDServ_04 | IDServ_05 | IDServ_06 |
| ------------ | :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| 1            |     0     |     0     |     1     |     1     |     0     |     1     |
| 2            |     0     |     0     |     1     |     0     |     1     |     1     |
| 3            |     1     |     1     |     0     |     1     |     0     |     0     |
| 4            |     0     |     1     |     0     |     0     |     1     |     1     |
| 5            |     0     |     0     |     0     |     1     |     0     |     1     |
| 6            |     1     |     1     |     1     |     1     |     0     |     0     |

###  La matriz de la agenda de ingenieros

La empresa tiene un registro de las semanas que un ingeniero ya tiene asignaciones. Un ejemplo de los datos existentes se puede encontrar en la siguiente tabla:

| **IdIngeniero** | **IdServicio** | **Fecha 		de inicio asignación** |
| --------------- | -------------- | -------------------------------------- |
| **1**           | 10             | 2021-06-07                             |
| **1**           | 12             | 2021-06-14                             |
| **4**           | 3              | 2021-05-24                             |
| …               | …              | …                                      |
| **2**           | 9              | 2021-06-07                             |

 Con estas asignaciones, los científicos de datos armaron una matriz que contiene el número de semanas libres del   ingeniero en el lapso de las siguientes 8 semanas (2 meses aproximadamente). Tenemos 6 ingenieros contratados.

| ID_Ingeniero | Semanas Libres |
| ------------ | -------------- |
| 1            | 2              |
| 2            | 1              |
| 3            | 3              |
| 4            | 2              |
| 5            | 1              |
| 6            | 3              |

###  La matriz de costos de entrega de servicios por cliente e ingenieros

 La empresa tiene un registro de los gastos esperados de enviar un ingeniero a las instalaciones de cada cliente sin importar el servicio. De esta manera, los científicos de datos pueden asociar costos en las asignaciones para así minimizar los gastos de viaje de un ingeniero a algún servicio en particular. Aquí se anexa la tabla de los costos en USD de tener un ingeniero asignado una semana.

| **IdIngeniero** | **IdCliente_01** | **IdCliente_02** | **IdCliente_03** | **IdCliente_04** | **IdCliente_05** |
| --------------- | ---------------- | ---------------- | ---------------- | ---------------- | ---------------- |
| **1**           | 120              | 113              | 91               | 97               | 60               |
| **2**           | 68               | 97               | 68               | 127              | 113              |
| **3**           | 111              | 115              | 120              | 114              | 119              |
| **4**           | 93               | 113              | 113              | 93               | 112              |
| **5**           | 108              | 67               | 115              | 115              | 114              |
| **6**           | 125              | 107              | 60               | 113              | 64               |

 Con los datos proporcionados, defina la asignación de ingenieros que minimice el costo de los servicios de los clientes pero que todos los clientes tengan ingeniero asignado para ejecutar el ser. Si es posible, busque que todos los clientes tengan asignaciones de ingenieros para entregar los servicios solicitados.

En este trabajo se propone encontrar una solución a la problemática planteada basados en realidades científicas que nos garanticen la mejor solución posible para las condiciones dadas y evitar la utilización de métodos de prueba y error que son tardados y no garantizan la mejor solución posible.

Dadas las características planteadas anteriormente este caso se ajusta a un problema de optimización del tipo de “asignación” que se resuelve utilizando la teoría de programación lineal entera. 



## Marco teórico

Dada la problemática expuesta con anterioridad, utilizaremos el modelo de programación lineal entera de asignación, ya que debemos de empatar recursos limitados (ingenieros) con actividades competidoras (los clientes).

El modelo de asignación clásico trata de hacer coincidir a los ingenieros (con diferentes habilidades) con los clientes. Presumiblemente, la variación de habilidades afecta el costo de completar un trabajo. El objetivo es determinar el costo mínimo de asignación de ingenieros a los clientes que requieren servicio. El modelo de asignación general con n trabajadores y n puestos de trabajo se representa en la figura 1. El elemento $c_{ij}$ representa el costo de asignar al ingeniero $i$ al cliente $j$ $(i, j = 1, 2, …, n)$. No hay pérdida de generalidad al suponer que el número de ingenieros y el número de clientes son iguales, porque siempre podemos agregar trabajadores ficticios o trabajos ficticios para satisfacer este supuesto. (Taha, 2017)

El modelo de asignación es un caso especial del modelo de transporte donde los trabajadores representan fuentes y los trabajos representan destinos. La cantidad de oferta (demanda) en cada fuente (destino) es exactamente igual a 1. El costo de “transportar” al trabajador $i$ al trabajo $j$ es $c_{ij}$. En efecto, el modelo de asignación se puede resolver directamente como un modelo de transporte regular (o como un problema de PL regular) (Taha, 2017).

![Fig1](/Users/michelin/Documents/_hsjg/MCDI/2021-1/A- Matematicas para la Ciencia de Datos/UProyectoFinal/Fig1.png)

El problema de asignación en el cual $n$ trabajadores son asignados a $n$ trabajos puede ser representado como un modelo de programación lineal de la siguiente manera. Sea $c_{ij}$ el costo de asignar el trabajador $i$ al trabajo $j$, y definimos a:
$$
x_{ij} = \left\{
	\begin{array}{ll}
		1, & \text{si el trabajador } i \text{ es asignado al trabajo }j \\
		0, & \text{en cualquier otro caso}
	\end{array}
\right.
$$
Entonces el modelo de programación lineal esta dado por:
$$
\text {Minimizar }z= \sum_{i=1}^{n} \sum_{j=1}^{n} c_{ij} x_{ij} 
$$
Sujeto a las siguientes restricciones:
$$
\sum_{j=1}^{n} x_{ij} = 1, i=1,2,...,n \\
\sum_{i=1}^{n} x_{ij} = 1, j=1,2,...,n \\
x_{ij} = 0 \text{ o } 1
$$



## Objetivos

1. Plantear el problema descrito como un modelo de programación lineal de asignación.
2. Resolver el modelo de optimización y obtener el mínimo costo de asignación de ingenieros a los clientes que han solicitado servicio.



## Metodología

*La metodología describe la forma que se conducirá la investigación. En  este apartado se puede incluir el tipo y diseño general del estudio, el  universo de estudio, la selección y tamaño de la muestra, las unidades  de análisis y observación, los criterios, los procedimientos y recursos  utilizados para la recolección de información, los instrumentos a  utilizar, los métodos para el control de calidad de los datos,  investigación y análisis de resultados.*

La empresa cuenta con un conjunto limitado de ingenieros especializados que deben atender solicitudes de servicio para los clientes.  La cantidad de clientes que debn ser atendidos por lo general supera la cantidad de ingenieros disponibles para un periodo cualquiera.

Existen una serie de restricciones que aplican tanto para los ingenieros disponibles como para la atencion de los clientes.  Los ingenieros cuentan cada uno, con ciertas acreditaciones que reflejan el nivel de habilidad y experiencia para cada uno de ellos, por lo tanto cada uno se diferencía por su nivel de acreditación que viene asociado a un costo individualizado.

Los clientes también cuentan con una serie de características que los hacen diferentes, como la distancia a la que se encuentran de la planta de los ingenieros, el tipo de cliente y el nivel de problema presentado.

La problemática se centra en encontrar la asignación optima de ingenieros a los clientes que necesitan un servicio de tal forma que el problema del cliente se resuelva de manera definitiva y se minimicen los costos totales del servicio.



## Plan de análisis de resultados

En el plan de análisis de resultados se definen programas a utilizar  para el análisis de datos y los tipos de variables que se utilizarán.

## Referencias bibliográficas

*Las referencias bibliográficas contienen todas las fuentes y materiales  consultadas a lo largo de la investigación. Se reflejan en una lista por el orden en que fue hecha la consulta en el informe final.*

1. Hamdy A. Taha. (2017). *Operations Research an Introduction, 10th Edition*.  Pearson Education.

## Cronograma

El cronograma o calendario define el tiempo que tomará cada etapa de la  investigación. Tiene como objetivo definir las fechas límites para la  finalización de un proyecto.

## Anexos

Los anexos son informaciones relevantes que no fueron incluidas en las  secciones anteriores. Puede incluir instrumentos de recolección de  información o ampliación de métodos y procedimientos a utilizar.