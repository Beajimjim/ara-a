# Proyecto de Gestión de Datos con SQLite y Web Scraping

## Descripción

Este proyecto incluye varios scripts en Python diseñados para realizar tareas de scraping de datos, almacenamiento en una base de datos SQLite y consulta de información mediante una interfaz gráfica.

## Componentes del Proyecto

### 1. Web Scraping con SQLite

- **Archivo:** `006-criterio multiple.py`
- **Descripción:**
  - Realiza búsquedas en `Paginas Amarillas` para obtener información relevante sobre empresas y servicios.
  - Almacena los resultados en una base de datos SQLite (`mercado.db`).
  - Utiliza la librería `requests` para hacer solicitudes HTTP y `BeautifulSoup` para analizar el contenido HTML.
  - Implementa pausas aleatorias entre solicitudes para evitar bloqueos por parte del servidor.
  
### 2. Buscador de Datos en la Base de Datos

- **Archivo:** `buscador.py`
- **Descripción:**
  - Proporciona una interfaz gráfica desarrollada en `Tkinter` para buscar información en la base de datos `mercado.db`.
  - Permite la consulta de registros en la tabla `target_attributes`.
  - Muestra los resultados en una tabla interactiva con desplazamiento vertical.
  
### 3. Eliminación de Duplicados en la Base de Datos

- **Archivo:** `c001-eliminar duplicados.py`
- **Descripción:**
  - Busca y elimina registros duplicados en la tabla `emails` de la base de datos `mercado.db`.
  - Utiliza consultas SQL para identificar y conservar solo una ocurrencia de cada email.
  - Garantiza la limpieza y consistencia de los datos almacenados.

## Instalación y Requisitos

### Requisitos

Este proyecto requiere las siguientes dependencias:
- Python 3.x
- `requests` (para scraping web)
- `beautifulsoup4` (para parseo de HTML)
- `sqlite3` (para manejo de bases de datos)
- `tkinter` (para la interfaz gráfica)

Para instalar las dependencias necesarias, ejecutar:

```
pip install requests beautifulsoup4
```

### Configuración

1. Clonar el repositorio o descargar los archivos.
2. Asegurarse de que la base de datos `mercado.db` está en la misma carpeta que los scripts.
3. Ejecutar `006-criterio multiple.py` para poblar la base de datos.
4. Usar `buscador.py` para consultar los datos almacenados.
5. Ejecutar `c001-eliminar duplicados.py` si es necesario limpiar registros duplicados.

## Uso

### Ejecución del Scraper

Para obtener datos de `Paginas Amarillas` y almacenarlos en SQLite:
```
python 006-criterio multiple.py
```

### Uso del Buscador

Para buscar registros en la base de datos desde la interfaz gráfica:
```
python buscador.py
```

### Eliminación de Duplicados

Para limpiar registros repetidos en la base de datos:
```
python c001-eliminar duplicados.py
```

## Estructura del Proyecto

```
├── 006-criterio multiple.py    # Script de web scraping y almacenamiento en SQLite
├── buscador.py                 # Interfaz gráfica para búsqueda en la base de datos
├── c001-eliminar duplicados.py  # Eliminación de duplicados en SQLite
├── mercado.db                   # Base de datos SQLite
```
---


# 📝 Explicación del código de los archivos subidos

---

## 1️⃣ `006-criterio multiple.py`
📌 **Este script extrae información de Páginas Amarillas y la almacena en una base de datos SQLite.**

- **Toma palabras clave** y busca empresas en Páginas Amarillas.
- **Extrae enlaces de sitios web** de las empresas listadas.
- **Limpia las URLs eliminando parámetros** y las guarda en `mercado.db`.
- **Realiza múltiples solicitudes HTTP** con `requests` y `BeautifulSoup`.
- **Evita bloqueos con pausas aleatorias entre peticiones**.

### 🔍 **Cómo funciona**
1. **Define una lista de palabras clave**, como `"web"`, `"programación"`, `"marketing"`, etc.
2. **Para cada palabra clave, realiza una búsqueda** en Páginas Amarillas.
3. **Obtiene los enlaces de empresas** (clase `web` en HTML).
4. **Limpia las URLs** quitando parámetros innecesarios.
5. **Guarda las URLs en la base de datos SQLite** (`mercado.db`).
6. **Repite el proceso para 4 páginas de resultados por palabra clave**.
7. **Espera entre 2 y 5 segundos** antes de la siguiente petición para evitar bloqueos.

✅ **Útil para:** recolectar sitios web de empresas en un nicho específico.

---

## 2️⃣ `buscador.py`
📌 **Este script es una interfaz gráfica (`Tkinter`) para buscar datos en `mercado.db`.**

- **Permite buscar términos** en la base de datos.
- **Muestra resultados en una tabla interactiva**.
- **Maneja errores y muestra alertas** si no encuentra coincidencias.

### 🔍 **Cómo funciona**
1. **El usuario ingresa un término de búsqueda** en una caja de texto.
2. **El script consulta la base de datos (`mercado.db`)** buscando coincidencias en la tabla `target_attributes`.
3. **Muestra los resultados en una tabla**.
4. **Si no hay coincidencias, muestra un mensaje** de "Sin resultados".
5. **Incluye un scrollbar para manejar listas largas**.

✅ **Útil para:** consultar rápidamente las URLs almacenadas en la base de datos.

---

## 3️⃣ `c001-eliminar duplicados.py`
📌 **Este script elimina correos electrónicos duplicados de la base de datos `mercado.db`.**

- **Busca emails repetidos** en la tabla `emails`.
- **Mantiene solo la primera ocurrencia** de cada email.
- **Elimina las copias duplicadas**.

### 🔍 **Cómo funciona**
1. **Conecta a la base de datos SQLite (`mercado.db`)**.
2. **Busca correos electrónicos duplicados** en la tabla `emails`.
3. **Para cada email duplicado**:
   - Encuentra la primera aparición (con el menor `rowid`).
   - Borra todas las demás copias del email.
4. **Guarda los cambios** y cierra la base de datos.

✅ **Útil para:** limpiar bases de datos eliminando información redundante.

---

## 4️⃣ `mercado.db`
📌 **Este archivo es una base de datos SQLite** que almacena:
- **Las URLs recolectadas de Páginas Amarillas** (`target_attributes` en `006-criterio multiple.py`).
- **Los correos electrónicos de empresas** (`emails`, usado en `c001-eliminar duplicados.py`).

✅ **Útil para:** manejar datos de empresas de forma estructurada.

---

## 🚀 **Conexión entre los scripts**
1️⃣ **`006-criterio multiple.py`** → Extrae URLs de empresas y las almacena en `mercado.db`.  
2️⃣ **`buscador.py`** → Permite buscar las URLs almacenadas en `mercado.db`.  
3️⃣ **`c001-eliminar duplicados.py`** → Elimina correos electrónicos repetidos en `mercado.db`.  

✅ **Sistema completo para extraer, almacenar, consultar y limpiar datos de empresas en Páginas Amarillas.** 🚀


