---

# Web Scraping de Informes IAMC (Renta Fija)

## 📌 Descripción

Este proyecto automatiza la descarga de informes diarios históricos desde el sitio del IAMC.

El objetivo es construir un dataset de cotizaciones (en particular, primas de opciones) a partir de PDFs publicados día a día desde el año 2009.

---

## 📌 Estado del sitio

Al momento de desarrollar este proyecto, los informes diarios del IAMC se encontraban disponibles y accesibles desde el sitio web.

Actualmente, dichos informes ya no se exponen públicamente (aproximadamente hasta octubre de 2025).

Por lo tanto:

* el script refleja la estructura y comportamiento del sitio en ese período
* puede no funcionar correctamente en la actualidad debido a cambios en la web

Este repositorio se mantiene con fines:

* académicos
* de referencia sobre técnicas de web scraping

---

## ⚠️ Uso responsable

Si se adapta el script a otros sitios o versiones:

* evitar ejecuciones en horarios de alta demanda
* no generar tráfico innecesario
* respetar las políticas del sitio

---

## ⚙️ Problema

El sitio no ofrece descarga masiva.

La única alternativa manual es:

* acceder día por día
* abrir el informe
* descargar el PDF

Esto implica miles de iteraciones.

---

## 🛠️ Solución

Se implementó un scraper que:

* navega el calendario con Selenium
* identifica el informe correspondiente a cada fecha
* valida que la fecha del informe sea correcta
* descarga el PDF usando `requests` cuando es posible
* organiza los archivos por año y mes

---

## 🚀 Cómo ejecutar

### 1. Clonar repositorio

```bash
git clone <URL_DEL_REPO>
cd <NOMBRE_REPO>
```

---

### 2. Instalar dependencias

```bash
pip install -r requirements.txt
```

Si no usás requirements.txt:

```bash
pip install selenium webdriver-manager requests
```

---

### 3. Configurar año a descargar

En el archivo `webscrappin.py`, modificar la variable:

```python
AÑO_A_DESCARGAR = 2009
```

---

### 4. Ejecutar script

```bash
python webscrappin.py
```

---

## 📁 Carpeta de descarga

Por defecto, los archivos se guardan en una carpeta generada automáticamente con el nombre:

IAMC_Informes_<AÑO>

Esta carpeta se crea en el mismo directorio donde se ejecuta el script.

Si se desea cambiar la ubicación, se puede modificar en el código la variable:

```python
CARPETA_BASE_AÑO = "ruta/deseada"
```

---

## 📊 Output

El script genera:

* Carpeta por año
* Subcarpetas por mes
* PDFs descargados automáticamente
* Reporte final con:

  * informes faltantes
  * errores de descarga
  * inconsistencias de fecha

---

## ⚠️ Consideraciones

* El scraping depende de la estructura del sitio (puede cambiar)
* Algunos días no tienen informes
* Se utiliza Selenium para navegación dinámica
* Se prioriza `requests` para descarga directa por eficiencia

---

## 🧠 Notas

El desarrollo se realizó combinando:

* conocimientos de HTML y programación
* uso de IA como herramienta de apoyo para acelerar el desarrollo

---

## 📌 Uso

Proyecto desarrollado con fines académicos (tesis de maestría en estadística).

