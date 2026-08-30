# Taller 1 — Introducción a Python para modelación hidrológica

**ICYA 4710 · Modelación de Sistemas y Procesos Hidrológicos**


Universidad de los Andes · Departamento de Ingeniería Civil y Ambiental · 2026-2

Este repositorio contiene el material del Taller 1. Antes de empezar debe haber completado el
*Tutorial de configuración del entorno* (WSL · Miniconda · VS Code · Git · GitHub · SPOTPY).

---

## Estructura

```
taller1-hidrologia/
├── README.md
├── environment.yml            <- archivo de configuración del environment
├── .gitignore
├── datos/                     <- series de entrada (no modificar)
│   ├── hymod_input.csv                  cuenca de ejemplo de SPOTPY
│   ├── cuenca_andina_21167080.csv       Tolima (CAMELS-COL)
│   └── cuenca_caribe_28037030.csv       Cesar  (CAMELS-COL)
├── notebooks/
│   └── Taller1_Python_Hidrologia.ipynb  <- aquí trabaja usted
└── resultados/                <- figuras y tablas que quiera guardar
```

---

## Cómo empezar

### 1. Obtener el repositorio

Desde la terminal de Ubuntu (WSL), en su carpeta de proyectos:

```bash
cd ~/proyectos/hidrologia
git clone git@github.com:jshernandezs/taller1-hidrologia.git
cd taller1-hidrologia
```

Como este repositorio va a ser **suyo**, desconéctelo del original y conéctelo al que usted cree:

```bash
git remote remove origin
# cree el repositorio vacío 'taller1-hidrologia' en github.com (privado está bien)
git remote add origin git@github.com:SU-USUARIO/taller1-hidrologia.git
git branch -M main
git push -u origin main
```

Si instaló GitHub CLI (Opción B del tutorial), los tres últimos pasos son uno solo:

```bash
gh repo create taller1-hidrologia --private --source=. --push
```

### 2. Crear el entorno (*environment*)

Si ya creó el environment `hidro` con el `environment.yml` del tutorial, sáltese este paso.

```bash
conda env create -f environment.yml
conda activate hidro
python -m ipykernel install --user --name hidro --display-name "Python (hidro)"
```

### 3. Abrir el cuaderno

```bash
code .
```

Abra `notebooks/Taller1_Python_Hidrologia.ipynb` y, en la esquina superior derecha, seleccione el
kernel **Python (hidro)**. La primera celda del cuaderno verifica que todo esté bien conectado.

---

## Cómo entregar

1. Complete las celdas marcadas con ✏️ (8 de código y 9 de respuesta escrita).
2. Reinicie el kernel y corra el cuaderno completo (`Run All`). **No debe quedar ningún error.**
3. Guarde y publique:

```bash
git add notebooks/ resultados/
git commit -m "Taller 1 resuelto"
git push
```

4. Si su repositorio es privado, agregue al profesor como colaborador en
   *Settings → Collaborators*.

**Plazo:** una semana después de la sesión.

---

## Datos

| Archivo | Fuente | Licencia |
|---|---|---|
| `hymod_input.csv` | Conjunto de ejemplo distribuido con SPOTPY (Houska et al., 2015) | MIT |
| `cuenca_andina_21167080.csv` | CAMELS-COL (Jiménez et al., 2025), estación IDEAM 21167080 | CC-BY 4.0 |
| `cuenca_caribe_28037030.csv` | CAMELS-COL (Jiménez et al., 2025), estación IDEAM 28037030 | CC-BY 4.0 |

Las dos series colombianas son un recorte del período 2001–2008 del conjunto original, que está
disponible completo en <https://zenodo.org/records/18794895>.

**Columnas de las series colombianas:** `fecha`, `P_mm` (precipitación CHIRPS, mm/día),
`ETP_mm` (evapotranspiración potencial MSWX, mm/día), `T_min_C`, `T_max_C`,
`Q_m3s` (caudal observado IDEAM, m³/s) y `Q_mm` (el mismo caudal como lámina, mm/día).

---

## Referencias

- Houska, T., Kraft, P., Chamorro-Chavez, A. & Breuer, L. (2015). *SPOTting Model Parameters Using a
  Ready-Made Python Package.* PLoS ONE 10(12): e0145180.
- Jiménez, D. A. et al. (2025). *CAMELS-COL: A Large-Sample Hydrometeorological Dataset for Colombia.*
  Earth System Science Data (en revisión). <https://doi.org/10.5281/zenodo.18794895>
- Refsgaard, J. C. & Henriksen, H. J. (2004). *Modelling guidelines — terminology and guiding
  principles.* Advances in Water Resources, 27(1), 71–82.
- Wagener, T. et al. (2001). *A framework for development and application of hydrological models.*
  Hydrology and Earth System Sciences, 5(1), 13–26.
