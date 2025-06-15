#PYTHON PARA OPTIMIZACIÓN DE PROCESOS DE ADMISIÓN Y  TAREAS DE GESTIÓN DE SOLICITUDES EN RESIDENCIA DE ESTUDIANTES

##Descripción general
Trabajo en una residencia de estudiantes, cubriendo el puesto de Recepcionista/Front Desk. 

El funcionamiento del alojamiento es similar a Hoteles y Hostels en cuanto a la gestión de reservas, disponibilidad, ocupación, departamentos de limpieza y mantenimiento.
Lo que los diferencia es que para hospedarse en Onix, es requisito formar parte del ámbito académico. Se alojan tanto estudiantes, como profesores, como investigadores.

Hay distintos tipos de estancia: de día (entre una  y seis noches), semanal (siete  noches), mes (entre uno y tres meses) y estancias de curso (más de 3 meses).

Dependiendo el tipo de estancia será el procedimiento a seguir para formalizar la reserva.

##Estructura

ProyectoResidencia/
|
|___ .git/
|___ venv/
|__src/
| |__main.py     
|  |__Formularios2025-2026.csv.csv
|___.gitognore
|___README.md
|__requirements.txt

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

##Instalación
!pip install pandas
import pandas as pd
import pandas as pd
df = pd.read_csv('Formularios2025-2026.csv.csv')

##Tareas simplificadas
Obtención de los nombres de los solicitantes:
print(df['Nombre']) 

Obtención de datos de solicitantes a través del índice:
print(df.loc[1])    

Para obtener los valores únicos de ID
unique_ID = df['DNI/Pasaporte'].unique()
print(unique_ID)

Para saber cuántas solicitudes hay, lo cual informamos una vez a la semana:
len(unique_ID)

Para crearle un usuario dentro de Ulysses Cloud necesito sólo algunos de esos datos. 
Quiero extraer solo Nombre, Apellido, DNI/Pasaporte, País y asignarlo a la variable huésped:

huésped = df[['Nombre','Apellido','DNI/Pasaporte', 'País']]
huésped

Con lo cual ya puedo generarles el usuario a los huéspedes en el sistema y crear una reserva.

Para analizar datos sobre qué países predominan, si hay más huéspedes femeninos que masculinos, y a qué universidad o centro asistirán.

reserva = df[['Nombre','Apellido', 'País', 'Género', 'Mes de Llegada', 'Mes de Salida']]
reserva

Para análisis etarios (Nombre, Apellido y Fecha de nacimiento)
df.iloc[0:14, 0:3]

Para obtener rápidamente datos de contacto:
df.loc[0:14,'Nombre':'Teléfono de Urgencias']

contacto = df[['Nombre','Apellido', 'Teléfono']]
contacto

##Autora

Alhue Fernandez Quiroga

##Licencia

Uso Educativo

##Notas

Se puede ampliar la librería añadiendo nuevas funciones para otras gestiones.
Si tienes alguna duda, consulta o sugerencia, te invito un issue en el repositorio.
