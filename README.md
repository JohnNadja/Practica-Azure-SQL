# Práctica sobre la creación y uso de servicios de  *Azure SQL Database*.

![Azure-sql](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Azure-SQL.png)
## Índice

### [Introducción](https://github.com/JohnNadja/Practica-Azure-SQL#introducci%C3%B3n-1) 
### [Requisitos](https://github.com/JohnNadja/Practica-Azure-SQL#requisitos-1) 
### [Práctica SQL Database](https://github.com/JohnNadja/Practica-Azure-SQL#pr%C3%A1ctica-sql-database) ![sqlmini](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/10130-icon-service-SQL-Database.svg)
### [Práctica Cosmos DB](https://github.com/JohnNadja/Practica-Azure-SQL#pr%C3%A1ctica-cosmos-db) ![cosmosmini](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/10121-icon-service-Azure-Cosmos-DB.svg)
 


### Introducción
#### Azure SQL Database
![sql-database](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/sql-database-generic.png)
El servicio de ***Azure SQL Database*** se basa en los principios de una base de datos, sea (o no) relacional, además los más conocidos son **Azure Database for MySQL** y **Azure Database for PostgreSQL**. Ambos servicios son tipo [PaaS](https://azure.microsoft.com/es-mx/overview/what-is-paas/). Ambos trabajan para uso básico general, pero ***Azure Database for MySQL*** tiene como característica principal de tener **Alta disponibilidad y copias de seguridad automáticas**, y ***Azure Database for PostgreSQL*** viene en 2 versiones:
 - *Un servidor único*
 - *Admición de grandes cargas de datos ([HyperScale Citus](https://docs.microsoft.com/es-mx/azure/postgresql/hyperscale/overview))*.

Para saber más sobre los objetivos de estos servicios en Azure, se puede consultar la siguiente [información](https://azure.microsoft.com/es-es/services/sql-database/).


##### Azure Cosmos DB
![cosmos-db](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/azure-cosmos.png)
El servicio de ***Azure Cosmos DB*** es una base de datos **no estructurada**, **no relacional** y **no SQL**. Es un servicio de tipo [PaaS](https://azure.microsoft.com/es-mx/overview/what-is-paas/) que guarda datos de manera inmediata, además de realizar consultas e inserciones de manera rápida y eficiente. Puede hacer también consultas con SQL y soporta MongoDB, Cassandra, Gemlin. Si se desea saber más, se puede consultar la siguiente [información](https://azure.microsoft.com/es-es/services/cosmos-db/).


---

### Requisitos
 - Tener una cuenta de Azure para realizar la práctica en su [*Portal*](https://portal.azure.com/#home) (si aún no se cuenta con alguna, se puede hacer el registro en el siguiente [*enlace*](https://azure.microsoft.com/es-mx/free/)). 
 - Contar con una suscripción activa de Azure para poder realizar la práctica (en el enlace anterior se muestra como se puede hacer).
 - Contar con una ***Cuenta de almacenamiento***, (se puede realizar siguiendo únicamente el [punto 1 de este repositorio](https://github.com/JohnNadja/Practica-Cuenta-de-Almacenamiento)) para poder realizar esta práctica.

----
### Práctica SQL Database
![sql-database](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/sql-database-generic.png)
1. Iniciar la terminal de Azure (Azure Cloud Shell). Si es la primera vez que se ejecuta, se mostrarán dos opciones para configurar el entorno (Bash o Powershell) para ejecutar los comandos; debería aparecerá una ventana similar a la siguiente:
![venetanaInicio-acs](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/ventanaInicio-acs.png)
    - Los comandos de esta práctica serán en Bash, por lo que se mantendrá el entorno de con esa selección por el momento (se puede reconfiguar después). 
    - Los comandos a ejecutar (uno por uno) son: 
        ```Bash
        git clone https://github.com/MicrosoftLearning/DP-900T00A-Azure-Data-Fundamentals dp-900
        ```
        ```Bash
        cd dp-900/sql
        ```
        ```Bash
        bash setup.sh
        ```
    - Al terminar ejecutar este último comando, y se mostrará una ventana similar a la  siguiente:
    ![Running](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Running.gif)
    - Cuando se termine de ejecutar el comando, se habrá creado un grupo de recursos con la base de datos:
    ![GrupoRecursos-DB](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/GrupoRecursos-BD.gif)

2. Accederemos al rescuso ***Base de Datos SQL***.
    - En la **Información general** seleccionamos el panel de **Establecer firewall de servidor**. Aqui se realizará la conexión con la base de datos.
    - Agregamos una nueva regla de firewall que será la dirección de una IP (del proveedor de servicios de internet) a la base de datos. Se agrega pulsando el botón de ***+ Agregar la dirección IPv4 del cliente (IP)***
    - Se pulsa el botón de **Guardar**.
    ![Firewall](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Firewall.gif)

3. Regresando al recurso de la base de datos, en el panel izquierdo, se buscará la opción de ***Editor de consultas*** y se mostrará una ventana para iniciar sesión.
    - Los datos de acceso son:
        |*Inicio de sesión*|*Contraseña*|
        |---|---|---|
        |**`sampleLogin`**|**`samplePassword123!`**|
    ![EditorConsultas](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/EditorConsultas.gif)

4. Una vez dentro de la base de datos, se puede ejecutar una consulta en el panel derecho. Ejemplos:
    - Para realizar una consulta general:
    `SELECT * FROM CustomerOrder`
    ![Consulta1](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Consulta1.gif)
    - Para insertar un dato en una tabla:
    `INSERT INTO Inventory (Id, Inventory.Name, Stock) VALUES (7, 'rambutan', 420)` 
    ![Consulta2](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Consulta2.gif)
        - Para observar la nueva inserción de un dato en una tabla:
        `SELECT * FROM Inventory` 
        ![Consulta3](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/Consulta3.gif)

[⚠](https://github.com/JohnNadja/Practica-Azure-SQL#importante)
###### <sub>[Volver al índice](https://github.com/JohnNadja/Practica-Azure-SQL#%C3%ADndice)<sub>

---
### Práctica Cosmos DB
![cosmos-db](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/azure-cosmos.png)
1. Buscar el recurso ***Azure Cosmos DB*** en el Portal de Azure y se pulsa el botón de **Crear***.
    - Aparecerá una ventana que muestra las diferentes opciones de creación de una base de datos con este servicio. En este caso, se selecciona la opción de **Núcelo (SQL)**.
    - En Conceptos básicos:
        | Parámetro | Descripción |
        |---|---|
        | Grupo de recursos | Seleccionar el grupo de recursos donde se quiera guardar la nueva instancia. Si no exite, se debe crear uno nuevo. |
        | Nombre de cuenta | Escribir nombre de la nueva cuenta. |
        | Aplicar descuento de nivel Gratis | Seleccionar **Aplicar**. |
    
    - Se confirma la creación de la base de datos pulsando en **Revisar y Crear**.
    ![CrearCosmosDB](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/CrearCosmosDB.gif)
    - Creamos y esperamos a que Azure finalice la creación del recurso.

2. Accederemos al recurso en la misma ventana actualizada.
    - En el panel izquierdo, se busca la opción de ***Inicio rápido*** y se mostrará una ventana para seleccionar la plataforma. En esta ocasión, será **Node.js**.
    - Continuamos los pasos que indican en dicha ventana:
        1. Adición de contenedor.
        2. (Opcional, esto es si queremos *consumir* la base de datos) Descargar y ejecución de aplicación **.NET**.
        3. Abrir el explorador de datos.
    ![InicioRapido](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/InicioRapido.gif)

3. Para agregar un **item**, se presiona en el botón de ***New item***. Ejemplo:
    ```
    {
        "id": "1",
        "name": "rambutan",
        "stock": 420
    }
    ```
    - Presionamos en el botón de ***Save***.
    ![NewItem](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/NewItem.gif)

4. Para consultas, se presiona en el botón de ***New SQL query***. Ejemplo:
    ```
    SELECT * FROM c where c.id = "1"
    ```
    - Presionamos en el botón de ***Save query*** con su nombre del query.
    - Ejectuamos la consulta.
    ![NewQuery](https://github.com/JohnNadja/Practica-Azure-SQL/blob/main/images/NewQuery.gif)

[⚠](https://github.com/JohnNadja/Practica-Azure-SQL#importante)
###### <sub>[Volver al índice](https://github.com/JohnNadja/Practica-Azure-SQL#%C3%ADndice)<sub>


#### Listo, ahora se conocen diferentes de los servicios que se pueden realizar gracias a ***Azure SQL Database***.

----
# **⚠Importante⚠** 
### Recordar eliminar el grupo de recursos que se creó en Azure para evitar costos extras no deseados en caso de no ocupar el servicio.
Se puede hacer desde el panel de Azure en inicio y buscando el tipo de recurso que se llama **Grupo de Recursos**.

###### <sub>[Volver al índice](https://github.com/JohnNadja/Practica-Azure-SQL#%C3%ADndice)<sub>

## Hasta aquí la finalización de la práctica.

