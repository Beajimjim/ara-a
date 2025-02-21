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

## Contribución

Si deseas contribuir a este proyecto, puedes hacer un `fork`, realizar mejoras y enviar un `pull request` con tus cambios.

## Licencia

Este proyecto está bajo la licencia MIT. Puedes usarlo libremente en proyectos personales y comerciales.

