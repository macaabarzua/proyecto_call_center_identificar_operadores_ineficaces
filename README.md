# Call center: identificar operadores ineficaces  

**Descripción del proyecto**:  

Este proyecto se realiza con los datos de la empresa de telefonía virtual "CallMeMaybe"; la cual pretende desarrollar una nueva función que brinde información a los supervisores sobre los operadores que resulten ser menos eficaces.  
Se considera que un operador es ineficaz si:

- Tiene una gran cantidad de llamadas entrantes perdidas (internas o externas).
- El tiempo de espera para las llamadas entrantes es prolongado.
- El operador debe realizar llamadas salientes; será ineficaz al tener un número reducido de estas.

**Motivación**  

Los clientes de este servicio son organizaciones que necesitan distribuir gran cantidad de llamadas entrantes entre varios operadores, o realizar llamadas salientes a través de los mismos, por lo que es importante mantener un nivel de eficacia para el óptimo servicio, retención de clientes y atracción de nuevos clientes.  

**Características de los Datasets**  

*telecom_dataset_us.csv* contiene información sobre el servicio; los operadores, llamadas y usuarios:

- user_id: ID de la cuenta del cliente
- date: fecha en la que se recuperaron las estadísticas
- direction: dirección de llamada (*out* para saliente, *in* para entrante)
- internal: si la llamada fue interna; entre los operadores de un cliente
- operator_id: identificador único del operador
- is_missed_call: si fue una llamada perdida
- calls_count: número de llamadas
- call_duration: duración de la llamada (sin incluir el tiempo de espera)
- total_call_duration: duración de la llamada (incluido el tiempo de espera)

*telecom_clients_us.csv* contiene datos de las tarifas:  

- user_id: ID de usuario/a
- tariff_plan: tarifa actual de la clientela
- date_start: fecha de registro de la clientela

**Herramientas utilizadas**:  
- Lenguaje: Python 3
- Librerías:
    - Pandas para la manipulación de los datos
    - Numpy para cálculos numéricos
    - Matplotlib y Seaborn para las visualizaciones
    - Scipy el módulo stats para las pruebas de hipótesis
 
**Proceso del proyecto**:  
**1. Carga y exploración de datos:**  
- Análisis inicial del dataset: información general de cada data, revisión de los valores faltantes y tipos de datos.

**2. Limpieza y Preprocesamiento:**  
- Reemplazo en valores nulos en las columnas correspondientes a si la llamada es interna, y al id del operador.
- Cambio a formato *datetime* para las columnas con fecha, y extracción del mes en cuestión.

**3. Análisis exploratorio de datos:**  
- Se contemplan las fechas del registro; llamadas desde el 02/Agosto al 28/Noviembre de 2019.
- Existen 1092 operadores únicos identificados.
- Se cuenta con 3 planes de tarifas: A, B y C.

**4. Análisis de los Datos:**  
- Se identifican 3 operadores con > 10% de llamadas perdidas.
- Existen 21 operadores con tiempo de esperan > a 5 minutos.
- Se realizan pruebas de hipótesis.  

**5. Resultados:**  
- Se notan días con gran peak en la cantidad de llamadas diarias, por lo que es recomendable que en estos momentos exista mayor disponibilidad de operadores que enfrenten la demanda y otorgar una respuesta adecuada a los usuarios; en pos de reducir los tiempos de espera.
- El plan A tiene considerablemente mayores tiempos de espera en comparación a los otros 2 planes; lo que es posible relacionar con la mayor demanda de llamadas que recibe vs el plan B y C; lo cual es un relevante aspecto a abordar para evitar la pérdida de estos clientes.
- Las hipótesis probadas ayudan a entender que existen diferencias significativas entre la cantidad de llamadas que reciben y la cantidad de llamadas perdidas entre los operadores con gran tiempo de espera vs aquellos con un tiempo menor. 

**6. Dashboard:**
- Puedes revisarlo en Tableau con el siguiente link: https://public.tableau.com/views/ProyectofinalCallMeMaybe/DashboardOperadoresineficaces?:language=es-ES&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
