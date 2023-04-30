# <center> ChatGPT
Sin duda en el último semestre del 2022 y el primero del 2023 Chatgpt ha sido nombrado en distintos medios como una Inteligencia Artificial con el poder de dejarnos sin trabajo a los que intentamos análizar datos, es verdad nos quitara trabajo pero no el trabajo, así como lo leés, muchos programadores de alto nivel concuerdan que las computadoras deben trabajar para los humanos y no al revez, es por ello que las inteligencias artificiales son de gran ayuda para quitarnos tareas basicas y que nos dediquemos a lo importante y que nos diferencia de las máquinas es decir, razonar y pensar los problemas.

## Conocimientos 

Quizas la IA pueda crearte una página web para tu negocio cuando tu no tengas conocimiento minímo ni siquiera en HTML, puede resultar excelente pero la probabilidad que eso pase es casi nula, ¿Porqué? Sencillamente porque las intrucciones que le des serán muy ambiguas, por ejemplo: Dame el código para una página con tema de recauderia con un logo de platano sonriendo :v, quizas te de algo pero no esperes que sea como lo piensas, en ello interviene el conocimiento técnico, un desarrollador web con esa tarea tendra que tener mínimo un framwork, le pedira que haga el código para enlistar todos los productos, el backend entero podrá ser diseñado por el y la IA sólo se dedicara a escribir el cógido más repetitivo y que sinceramente quita tiempo valioso, por lo atnto la información es importante pero el comocimiento es el que la hace funcionar.

## ChatGPT y SQL 

Sin duda una de las mayores utilidades es para las consultas que he tenido que hacer, las consultas sencillas que filtran datos con WHERE, BEETWEEN son mñas faciles de hacer pues usualmente toman unos segundos escribirlas, sin embargo que pasa si queremos una subconsulta anidada en una consulta multitabla, se puede considerar avanzada, como lo describo en mi repositorio de SQL dichas consultas resultan un reto pues al hablar de tablas con millones de datos, decenas de columnas, identación no normalizada o en este ejemplo:

Divide the msa_income groups up so tha tmsa_incomes between 1 and 20,000 are labeled 'low', msa_incomes between 20,001 and30,000 arelabeled 'med-low', msa_incomes between 30,001 and 40,000 arelabeled 'medhigh', andmsa_incomes between 40,001 and 60,000 are labeled 'high'. Which ofthese groups has the highest average daily revenue (as defined in Teradata Week5 Exercise Guide) per store?
```SQL
SELECT SUM(revenue_per_store.revenue)/SUM(numdays)AS avg_group_revenue,
CASE WHEN revenue_per_store.msa_income BETWEEN 1 AND 20000 THEN 'low'
WHEN
revenue_per_store.msa_income
BETWEEN
20001
AND
30000
THEN
'med-­‐low'
WHEN
revenue_per_store.msa_income
BETWEEN
30001
AND
40000
THEN
'med-­‐high'
WHEN
revenue_per_store.msa_income
BETWEEN
40001
AND
60000
THEN
'high'
END
as
income_group
FROM
(SELECT
m.msa_income,
t.store,
CASE
when
extract(year
from
t.saledate)
=
2005
AND
extract(month
from
t.saledate)
=
8
then
'exclude'
END
as
exclude_flag,
SUM(t.amt)
AS
revenue,
COUNT(DISTINCT
t.saledate)
as
numdays,
EXTRACT(MONTH
from
t.saledate)
as
monthID
FROM
store_msa
m
JOIN
trnsact
t
ON
m.store=t.store
WHERE
t.stype='P'
AND
exclude_flag
IS
NULL
AND
t.store||EXTRACT(YEAR
from
t.saledate)||EXTRACT(MONTH
from
t.saledate)
IN(SELECT
store||EXTRACT(YEAR
from
saledate)||EXTRACT(MONTH
from
saledate)
FROM
trnsact
GROUP
BY
store,
EXTRACT(YEAR
from
saledate),
EXTRACT(MONTH
from
saledate)
HAVING
COUNT(DISTINCT
saledate)>=
20)
GROUP
BY
t.store,
m.msa_income,
monthID,
exclude_flag)
AS
revenue_per_store
GROUP
BY
income_group
ORDER
BY
avg_group_revenue;
```
Quizas un nivel experto con 5 años en el ambiente lo realize en dos minutos, pero un nivel medio o basico tendrá que hacer un diagrama, saber usar las clausulas WHEN y CASE de manera fluida, sin embargo es dónde ChatGPT nos haría la tarea en un par de minutos y sólo debmos corroborar con nuestro analísis para ello las intrucciones tienen que se **definitivas**


## ChatGPT y los macros 

## ChatGPT con Python 
Si es un programador de Python en 2023, puede usar ChatGPT para facilitar la codificación. Por ejemplo, si no está familiarizado con una biblioteca de Python utilizada en la ciencia de datos, puede pedirle a ChatGPT que se la explique.


O, si desea escribir un script que haga algo en particular, puede pedirle a ChatGPT que lo genere por usted. Por lo general, los desarrolladores usarían Google para estas tareas. Pero con esta herramienta, puede obtener un mejor resultado. Entonces, cualquier cosa para la que usaría Google, puede usar ChatGPT como reemplazo.

Caso de uso n.º 1: código de depuración
Puede usar ChatGPT para depurar código. Si encontró un error que no esperaba, puede intentar usar ChatGPT para generar una respuesta que podría serle útil.


Tenga en cuenta que esta herramienta no está diseñada para la depuración, sino para una conversación general, por lo que es posible que su uso no le brinde información útil.


Sin embargo, sigue siendo una buena herramienta para explorar posibles soluciones o ideas relacionadas con su problema.

Caso de uso n.º 2: generación de datos
Si trabaja mucho con datos JSON, puede usar ChatGPT para producir datos ficticios. Por ejemplo, si está creando una base de datos del lugar de trabajo y le gustaría probar algunos datos ficticios, puede pedirle a ChatGPT que la cree con sus requisitos específicos. Aquí está el ejemplo:



## Chatgpt y los modelos 

