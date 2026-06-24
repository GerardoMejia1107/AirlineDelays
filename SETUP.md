# Configuración — Retraso en Aerolíneas

## Requisitos previos

- Python 3.11 o superior (el proyecto fue desarrollado con **Python 3.13.13**)
- `pip` disponible en el PATH del sistema

---

## 1. Crear el entorno virtual

Ejecuta esto desde la raíz del proyecto (la carpeta que contiene `notebooks/` y `data/`):

```bash
python -m venv .venv
```

---

## 2. Activar el entorno

**Windows (PowerShell)**
```powershell
.venv\Scripts\Activate.ps1
```

**Windows (cmd)**
```cmd
.venv\Scripts\activate.bat
```

**macOS / Linux**
```bash
source .venv/bin/activate
```

El prompt de la terminal debería mostrar `(.venv)` al estar activo.

---

## 3. Instalar dependencias

```bash
pip install -r requirements.txt
```

### Qué se instala

| Paquete | Propósito |
|---|---|
| `pandas` | Carga, limpieza y transformación de datos en el notebook |
| `jupyterlab` | Entorno de notebooks en el navegador |
| `ipykernel` | Conecta el kernel de Python de `.venv` con JupyterLab |

---

## 4. Registrar el kernel (solo la primera vez)

Esto hace visible el intérprete de `.venv` como kernel seleccionable dentro de JupyterLab:

```bash
python -m ipykernel install --user --name retraso-aerolineas --display-name "Python (retraso-aerolineas)"
```

---

## 5. Abrir JupyterLab

```bash
jupyter lab
```

Abre `notebooks/01_data_exploration.ipynb` y selecciona el kernel **Python (retraso-aerolineas)**.

---

## Estructura del proyecto

Solo se listan los directorios que contienen archivos.

```
Retraso en Aerolíneas/
├── .venv/                        # entorno virtual — NO subir al repositorio
├── data/
│   ├── raw/                      # archivos fuente originales del DOT
│   │   ├── flights.csv
│   │   ├── airlines.csv
│   │   └── airports.csv
│   └── processed/                # CSVs limpios exportados por el notebook
│       ├── flights_clean_all.csv
│       ├── flights_arrived.csv
│       ├── flights_cancelled.csv
│       ├── flights_diverted.csv
│       ├── airlines_clean.csv
│       └── airports_clean.csv
├── notebooks/
│   └── 01_data_exploration.ipynb # exploración, limpieza y exportación
├── .gitignore
├── requirements.txt
└── SETUP.md                      # este archivo
```

### Reglas para el equipo

- **`data/raw/`** — coloca aquí los archivos fuente tal como están; nunca los modifiques.
- **`data/processed/`** — generados por el notebook; vuelve a ejecutarlo para regenerarlos. No los edites manualmente.
- **`notebooks/`** — un notebook por etapa, con prefijo de dos dígitos (`01_`, `02_`, …) para que se ordenen por orden de ejecución.
- **`.venv/`** — nunca subas esta carpeta al repositorio. Ya está incluida en `.gitignore`.
- No crees directorios nuevos a menos que vayan a contener archivos; las carpetas vacías generan ruido y confunden la estructura.
