#PYTHON PARA OPTIMIZACIÓN DE PROCESOS DE ADMISIÓN Y  TAREAS DE GESTIÓN DE SOLICITUDES EN RESIDENCIA DE ESTUDIANTES
##Descripción general
Trabajo en una residencia de estudiantes, cubriendo el puesto de Recepcionista/Front Desk. 

El funcionamiento del alojamiento es similar a Hoteles y Hostels en cuanto a la gestión de reservas, disponibilidad, ocupación, departamentos de limpieza y mantenimiento.
Lo que los diferencia es que para hospedarse en Onix, es requisito formar parte del ámbito académico. Se alojan tanto estudiantes, como profesores, como investigadores.

Hay distintos tipos de estancia: de día (entre una  y seis noches), semanal (siete  noches), mes (entre uno y tres meses) y estancias de curso (más de 3 meses).

Dependiendo el tipo de estancia será el procedimiento a seguir para formalizar la reserva.

##Problema

Este proyecto se enfoca en la optimización de los procesos de admisión y gestión de solicitudes en un alojamiento de estudiantes (Residencia Onix). Actualmente, estas tareas son manuales y repetitivas, generando ineficiencias y pérdida de tiempo. La solución propuesta utiliza Python, específicamente la librería Pandas, para automatizar la extracción, limpieza y procesamiento de datos de los formularios de solicitud, buscando reducir la carga de trabajo, mejorar la calidad de los datos y agilizar la comunicación con los solicitantes.

##Objetivos del Proyecto

###El objetivo general es utilizar Python para optimizar y automatizar los procesos de gestión de solicitudes y admisión, reduciendo la carga de trabajo manual y mejorando la eficiencia operativa del departamento de Front Desk.

###Objetivos específicos:
-Identificar tareas manuales y repetitivas susceptibles de automatización.
-Implementar soluciones basadas en Python para integrar la información procesada con los sistemas de gestión existentes.
-Reducir el tiempo promedio de procesamiento por solicitud.
-Disminuir la tasa de errores relacionados con los campos del formulario.
-Generar informes y dashboards para un mejor análisis de datos.

##Aplicación
Este proyecto demuestra cómo se pueden procesar los datos de los solicitantes utilizando Pandas en Python.
Para garantizar la privacidad y cumplir con las normativas de protección de datos, los datos empleados son ficticios, no corresponden a información real.

##Requisitos
Python
Librería Pandas (pip install pandas)
Archivo CSV con los datos de los formularios (ej. Formularios2025-2026.csv.csv)

###Su aplicación permitió:
-Cargar y manipular datos desde archivos CSV.
-Acceder rápidamente a registros específicos (ej. por índice o nombre).
-Obtener valores únicos de campos (ej. DNI/Pasaporte).
-Extraer subconjuntos de datos necesarios para tareas específicas, como:
Creación de usuarios en Ulysses Cloud (campos: Nombre, Apellido, DNI/Pasaporte, País).
-Análisis demográfico (País, Género, Universidad o centro).
-Extracción veloz de la información relevante para crear reservas (campos: Nombre, Apellido, País, Género, Mes de Llegada, Mes de Salida).
-Creación de listas de datos de contacto (campos: Nombre, Apellido, Teléfono, Correo Electrónico).

Este enfoque permite trabajar con datos limpios desde el primer momento, sentando las bases para una gestión de solicitudes más eficiente.

##Instalación
Desde Jupyter instalé la librería de pandas.

##Funcionalidad

Para obtener los nombres de los solicitantes:
print(df['Nombre']) 

Para obtener los valores únicos de ID
unique_ID = df['DNI/Pasaporte'].unique()
print(unique_ID)

Para saber cuántas solicitudes hay, lo cual informamos una vez a la semana:
len(unique_ID)

Para crearle un usuario dentro de Ulysses Cloud necesito sólo algunos de esos datos. 

Aplicado a distintas gestiones, reduce los tiempos, extraer sólo algunos datos Nombre, Apellido, DNI/Pasaporte, País y asignarlo a la variable huésped

huésped = df[['Nombre','Apellido','DNI/Pasaporte', 'País']]
huésped

Permite analizar datos demográficos y de género de las solicitudes de un determinado curso.
reserva = df[['Nombre','Apellido', 'País', 'Género', 'Mes de Llegada', 'Mes de Salida']]
reserva

Permite identificar edades

df.iloc[0:14, 0:3]

 datos de contacto, los podemos filtrar:
df.loc[0:14,'Nombre':'Teléfono de Urgencias']


Necesito sólo Nombre, Apellido y Número de teléfono para agendarlos en WhatsApp.
contacto = df[['Nombre','Apellido', 'Teléfono']]
contacto


##Autora

Alhue Fernandez Quiroga

##Licencia

Uso educativo

##Notas

El proyecto es mi rama main.

Se puede modificar la librería añadiendo funciones, aplicandolo a otras gestiones de la 
Residencia.

Si tienes alguna consulta o sugerencia, puedes añadir un issue en mi repositorio.

