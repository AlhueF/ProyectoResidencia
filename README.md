#PYTHON PARA OPTIMIZACIÓN DE PROCESOS DE ADMISIÓN Y  TAREAS DE GESTIÓN DE SOLICITUDES EN RESIDENCIA DE ESTUDIANTES
##Descripción general
Trabajo en una residencia de estudiantes, cubriendo el puesto de Recepcionista/Front Desk. 

El funcionamiento del alojamiento es similar a Hoteles y Hostels en cuanto a la gestión de reservas, disponibilidad, ocupación, departamentos de limpieza y mantenimiento.
Lo que los diferencia es que para hospedarse en Onix, es requisito formar parte del ámbito académico. Se alojan tanto estudiantes, como profesores, como investigadores.

Hay distintos tipos de estancia: de día (entre una  y seis noches), semanal (siete  noches), mes (entre uno y tres meses) y estancias de curso (más de 3 meses).

Dependiendo el tipo de estancia será el procedimiento a seguir para formalizar la reserva.

##Problema

Este proyecto se enfoca en la optimización de los procesos de admisión y gestión de solicitudes en un alojamiento de estudiantes (Residencia Onix). Actualmente, estas tareas son manuales y repetitivas, generando ineficiencias y pérdida de tiempo. La solución propuesta utiliza Python, específicamente la librería Pandas, para automatizar la extracción, limpieza y procesamiento de datos de los formularios de solicitud, buscando reducir la carga de trabajo, mejorar la calidad de los datos y agilizar la comunicación con los solicitantes

##Problema Identificado

La gestión de solicitudes de admisión se ve afectada por varios desafíos:
-Recepción de Solicitudes: Los formularios web llegan a una dirección de correo general, perdiéndose entre otros emails y dificultando su seguimiento.
-Procesamiento Manual: La impresión, clasificación física y transcripción manual de datos a hojas de cálculo Excel consume mucho tiempo.
-Comunicación Ineficiente: La respuesta individualizada a cada solicitud es un proceso manual y lento.
-Calidad de Datos: El formato inconsistente en campos como "Dirección", "Fecha de Entrada/Salida" y "Teléfono" en el formulario web requiere aclaraciones manuales, generando ineficiencias en la recolección de datos.

##Objetivos del Proyecto

###El objetivo general es utilizar Python para optimizar y automatizar los procesos de gestión de solicitudes y admisión, reduciendo la carga de trabajo manual y mejorando la eficiencia operativa del departamento de Front Desk.

###Objetivos específicos:
-Identificar tareas manuales y repetitivas susceptibles de automatización.
-Implementar soluciones basadas en Python para integrar la información procesada con los sistemas de gestión existentes.
-Reducir el tiempo promedio de procesamiento por solicitud.
-Disminuir la tasa de errores relacionados con los campos del formulario.
-Generar informes y dashboards para un mejor análisis de datos.



Separamos los formularios de los solicitantes en dos categorías:

Curso 2024/2025 (del 01/09/2024 al 30/06/2025)

Curso 2025/2026 (del 01/09/2025 al 30/06/2026)

Cargamos los datos de los Formularios en Excel
Uno con las solicitudes del Curso 2024/2025
Otro con las solicitudes del Curso 2025/2026

En este momento del año estamos trabajando en las solicitudes y admisiones del próximo curso. Respondemos a cada uno de los formularios recibidos, escribimos correo por correo lo cual implica mucha pérdida de tiempo.

Sería óptimo trabajar con datos limpios desde el primer momento. Algunos patrones repetitivos identificados:

Cuando completan en el el Formulario el campo “Dirección”, no coincide el formato. Algunos ponen solo el nombre de la ciudad, otros calle, numeración, manzana, código postal, otros ponen una referencia ( Ej. al lado de Sagrada Familia). Cambiaría el Formulario de tal modo que la dirección escrita deba ser tal como aparece en Google Maps, es decir, una dirección válida.

En los campos “Fecha de Entrada” y “Fecha de salida” lo ideal sería definir el formato en el mismo formulario para evitar que utilicen algunos str (ej. “JUNIO”, “verano”, otros utilizan este formato: 01-02-25, otros: 01/02/2025, otros en formato estadounidense, lo cual además genera confusiones sobre todo en meses como Enero y febrero que si lo han puesto en formato estadounidense indicaría otra fecha que también podría ser válida).

En “Teléfono” y “Teléfono de emergencia” Aplicaría una opción de prefijo que sea seleccionable y luego que escriban el número, para que quede en el mismo formato.

Al no ser claro el formulario desde el primer momento, en muchos casos tenemos que contactar a los emisores para aclarar dudas, genera ineficiencias en el proceso de recolección de datos, ya que su interpretación a menudo requiere tiempo adicional.

3.Objetivos
El objetivo general
El objetivo principal de este proyecto es  utilizar Python como herramienta para optimizar y automatizar los procesos de gestión de solicitudes y admisión para reducir la carga de trabajo manual y mejorar la eficiencia operativa del departamento de Front Desk en Residencia Onix.

Objetivos específicos
-Identificar tareas manuales y repetitivas del proceso de admisión que son susceptibles de automatización.
-Implementar soluciones basadas en Python para integrar la información procesada con los sistemas de gestión existentes, reduciendo la necesidad de transcripción manual.
-Reducir tiempos promedios de procesamiento de cada solicitud.
-Disminuir la tasa de errores relacionados a los campos del Formulario.
-Generar informes y dashboards.

4. Aplicación en el procesamiento de solicitudes del próximo curso
Los datos de los solicitantes están cargados en Excel (“Formularios2025-2026.txt”).

Para garantizar la privacidad y cumplir con las normativas de protección de datos, los datos empleados son ficticios, no corresponden a información real.

Desde Jupyter importé la librería de pandas
!pip install pandas
import pandas as pd
import pandas as pd
df = pd.read_csv('Formularios2025-2026.csv.csv')

Si quiero obtener los nombres de los solicitantes:
print(df['Nombre']) 
Si quiero obtener los datos de Raúl Sosa y John Perez puedo hacerlo rápidamente mediante:

print(df.iloc[2])  
print(df.loc[1])    
Si quiero obtener los valores únicos de ID
unique_ID = df['DNI/Pasaporte'].unique()
print(unique_ID)
Si quiero saber cuántas solicitudes hay, lo cual informamos una vez a la semana:
len(unique_ID)
Para crearle un usuario dentro de Ulysses Cloud necesito sólo algunos de esos datos. 

Quiero extraer solo Nombre, Apellido, DNI/Pasaporte, País y asignarlo a la variable huésped

huésped = df[['Nombre','Apellido','DNI/Pasaporte', 'País']]
huésped
Con lo cual ya puedo generarles el usuario a los huéspedes en el sistema (aún no tienen una reserva asignada, ya que son solicitantes por el momento no sabemos si habrá disponibilidad o no).
Para analizar datos sobre qué países predominan, si hay más huéspedes femeninos que masculinos, y a qué universidad o centro asistirán.
reserva = df[['Nombre','Apellido', 'País', 'Género', 'Mes de Llegada', 'Mes de Salida']]
reserva
Supongamos que sólo quiero Nombre, Apellido y Fecha de nacimiento:
df.iloc[0:14, 0:3]
Hay datos que sólo servirán como datos de contacto, los podemos filtrar:
df.loc[0:14,'Nombre':'Teléfono de Urgencias']

Necesito sólo Nombre, Apellido y Número de teléfono para agendarlos en WhatsApp.
contacto = df[['Nombre','Apellido', 'Teléfono']]
contacto
