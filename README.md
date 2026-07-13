# <img src="https://img.icons8.com/?size=50&id=81093&format=png&color=000000" align="center"/> SQL Relational Database: Acupuncture Clinic
## Base de Datos Relacional: Clínica de Acupuntura y MTC

> **EN** · Relational database project modeling a Traditional Chinese Medicine clinic's electronic health records system, built with Python and SQLite.
> Five interconnected tables capture patient records, TCM diagnoses, acupuncture points, treatment sessions, and point-per-session details; enabling complex relational queries that mirror real clinical workflows.
>
> **ES** · Proyecto de base de datos relacional que modela el expediente clínico de una clínica de Medicina Tradicional China, construido con Python y SQLite.
> Cinco tablas interconectadas capturan pacientes, diagnósticos MTC, acupuntos, sesiones de tratamiento y puntos por sesión; permitiendo consultas relacionales que reflejan flujos clínicos reales.

---

## <img src="https://img.icons8.com/?size=40&id=80717&format=png&color=000000" align="center"/> Database Schema / Esquema de Base de Datos

    pacientes (patients)
    │
    ├──< diagnosticos (diagnoses)
    │         │
    │         └──< sesiones (sessions)
    │                   │
    └──────────────────<┘
    │
    └──< puntos_por_sesion (points_per_session)
    │
    └──> acupuntos (acupuncture_points)

### Tables / Tablas

| Table / Tabla | Rows / Filas | Columns / Columnas | Description / Descripción |
|---|---|---|---|
| `pacientes` | 17 | 7 | Patient demographics · Datos demográficos del paciente |
| `diagnosticos` | 25 | 8 | TCM diagnoses with tongue & pulse · Diagnósticos MTC con lengua y pulso |
| `acupuntos` | 28 | 8 | Acupuncture point reference catalog · Catálogo de referencia de acupuntos |
| `sesiones` | 42 | 8 | Treatment sessions · Sesiones de tratamiento |
| `puntos_por_sesion` | 99 | 7 | Points used per session · Puntos utilizados por sesión |

---

## <img src="https://img.icons8.com/?size=40&id=80842&format=png&color=000000" align="center"/> TCM Clinical Framework / Marco Clínico MTC

### How TCM diagnosis works / Cómo funciona el diagnóstico MTC

**EN** · Traditional Chinese Medicine diagnoses through pattern differentiation: identifying syndromes by observing the tongue, palpating the pulse, and analyzing symptoms. Each pattern points to a specific organ-meridian imbalance with its own treatment protocol.

**ES** · La Medicina Tradicional China diagnostica mediante diferenciación de patrones: identificando síndromes a través de la observación de la lengua, la palpación del pulso y el análisis de síntomas. Cada patrón apunta a un desequilibrio específico del sistema de órganos-meridianos con su propio protocolo de tratamiento.

### Diagnostic patterns included / Patrones diagnósticos incluidos

| Pattern / Patrón | Tongue / Lengua | Pulse / Pulso |
|---|---|---|
| Kidney Yin Deficiency · Deficiencia de Yin de Riñón | Red, no coating, dry · Roja, sin saburra, seca | Thin & rapid · Delgado y rápido |
| Spleen Qi Deficiency · Deficiencia de Qi de Bazo | Pale, scalloped edges · Pálida, bordes dentados | Weak & sunken · Débil y hundido |
| Liver Qi Stagnation · Estancamiento de Qi de Hígado | Slightly purple edges · Ligeramente morada en bordes | Wiry · En cuerda |
| Wind-Cold External · Viento-Frío Externo | Thin white coating · Saburra blanca y delgada | Superficial & slow · Superficial y lento |
| Lung Qi Deficiency · Deficiencia de Qi de Pulmón | Pale, thin white coat · Pálida, saburra blanca | Weak in Lung position · Débil en posición del Pulmón |
| Kidney Yang Deficiency · Deficiencia de Yang de Riñón | Pale, swollen, tooth marks · Pálida, hinchada, marcas | Deep, weak & slow · Profundo, débil y lento |
| Damp-Heat Stomach-Intestine · Humedad-Calor Estómago-Intestino | Greasy yellow coat · Saburra amarilla y grasienta | Slippery & rapid · Resbaladizo y rápido |
| Blood Stagnation · Estancamiento de Sangre | Purple with petechiae · Morada con petequias | Choppy · Rugoso |

*Full catalog of 25 diagnostics in `diagnosticos.csv`*

### Key acupuncture points / Acupuntos clave

| Code | Name (Pinyin) | Meridian | Primary Action |
|---|---|---|---|
| ST36 | Zusanli | Stomach | Tonifies Qi & Blood, strengthens Spleen |
| SP6 | Sanyinjiao | Spleen | Tonifies Yin & Blood, regulates menstruation |
| LV3 | Taichong | Liver | Moves Liver Qi & Blood |
| KD3 | Taixi | Kidney | Nourishes Kidney Yin & Yang |
| PC6 | Neiguan | Pericardium | Calms the mind, regulates Heart Qi |
| GV20 | Baihui | Governing Vessel | Raises Yang, clears the mind |
| HT7 | Shenmen | Heart | Calms the Shen, nourishes Heart Blood |
| BL23 | Shenshu | Bladder | Strengthens Kidney, nourishes Jing |

*Full catalog of 28 acupoints in `acupuntos.csv`*

---

## <img src="https://img.icons8.com/?size=40&id=80431&format=png&color=000000" align="center"/> Tools / Herramientas

![Python](https://img.shields.io/badge/Python-8B9E8B?style=flat&logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-7A9E9F?style=flat&logo=sqlite&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-6B7F6B?style=flat&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-C4A882?style=flat&logo=jupyter&logoColor=white)

---

## <img src="https://img.icons8.com/?size=40&id=81350&format=png&color=000000" align="center"/> SQL Queries Covered / Consultas SQL Cubiertas

### INNER JOIN

EN · Returns only records with matching values in all joined tables.
Used for: full treatment history, sessions linked with patient and diagnosis, and acupoint applications with clinical context.

ES · Devuelve solo los registros con coincidencias en todas las tablas relacionadas.
Usado para: historial completo de tratamiento, sesiones vinculadas con paciente y diagnóstico, y aplicación de acupuntos con contexto clínico.

### LEFT JOIN

EN · Returns all records from the left table and matching records from the right table; when no match exists, NULL values are returned.
Used for: patients without sessions and diagnoses with no treatment started.

ES · Devuelve todos los registros de la tabla izquierda y las coincidencias de la derecha; si no existen, muestra valores NULL.
Usado para: pacientes sin sesiones y diagnósticos sin tratamiento iniciado.

---

## <img src="https://img.icons8.com/?size=40&id=shBqcY2jqNl3&format=png&color=000000" align="center"/> Note / Nota

**EN** · The author is a licensed acupuncturist (RENATED certified, Folio A-43253) and a professional in data science and analytics. Patient data is entirely fictional. The 28 acupuncture points, 25 TCM diagnostic patterns, and treatment protocols reflect real Traditional Chinese Medicine practice.

**ES** · La autora es acupunturista certificada (RENATED, Folio A-43253) y profesional de la analítica y aiencia de datos. Los datos de pacientes son completamente ficticios. Los 28 acupuntos, 25 patrones diagnósticos MTC y protocolos de tratamiento reflejan práctica real de Medicina Tradicional China.

---

## <img src="https://img.icons8.com/?size=40&id=PhymLYNNjf3I&format=png&color=000000" align="center"/> Repository Structure / Estructura del Repositorio
    sql-acupuncture-clinic/
    ├── notebook/
    │   └── sql_acupuncture_clinic.ipynb    # Main analysis / Análisis principal
    ├── data/
    │   ├── acupuntos.csv                   # 28 acupuncture points / acupuntos
    │   ├── diagnosticos.csv                # 25 TCM diagnoses / diagnósticos MTC
    │   ├── pacientes.csv                   # 17 patients (fictional) / pacientes (ficticios)
    │   ├── sesiones.csv                    # 42 treatment sessions / sesiones del tratamiento
    │   └── puntos_por_sesion.csv           # 99 point-session records / registros acupunto-sesión
    ├── README.md
    └── requirements.txt

---

*Project developed as part of the Data Scientist Certificate · 
Proyecto desarrollado como parte del certificado Científico de Datos — EBAC (2026)* <img src="https://img.icons8.com/?size=35&id=FgMs84V9yrMV&format=png&color=000000" align="center"/>
