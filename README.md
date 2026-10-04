# RE/MAX Glassdoor NLP Analysis

Diagnóstico de marca empleadora y experiencia de asociados de **RE/MAX** frente a cinco empresas comparables del sector inmobiliario, realizado a partir de 5.006 reseñas de Glassdoor.

El proyecto combina análisis exploratorio, análisis de sentimiento y modelado de temas para identificar fortalezas, riesgos y áreas prioritarias de actuación para Recursos Humanos.

## Objetivo

Responder a dos preguntas de negocio:

1. ¿Qué fortalezas puede aprovechar RE/MAX para atraer y fidelizar talento?
2. ¿Qué problemas requieren una intervención prioritaria de Recursos Humanos?

La comparación incluye las siguientes empresas:

- RE/MAX
- Keller Williams
- Colliers
- Savills
- Realtor.com
- Century 21

## Metodología

El análisis se desarrolla sobre una muestra equilibrada de hasta 1.000 reseñas por empresa:

1. Preparación y exploración de los datos.
2. Comparación de rating, recomendación, evolución temporal y situación laboral.
3. Análisis de sentimiento de `pros` y `cons` con **DistilBERT**.
4. Generación de embeddings con **all-MiniLM-L6-v2**.
5. Modelado temático con **BERTopic**, UMAP y HDBSCAN.
6. Revisión y agrupación manual de los temas en 11 categorías de negocio.
7. Benchmarking de RE/MAX frente a sus peers.
8. Validación de los hallazgos mediante rating y recomendación.
9. Construcción de una matriz de priorización y recomendaciones para RR. HH.

## Principales resultados

- RE/MAX obtiene un rating medio de **4,10**, frente a **3,78** de sus peers.
- La marca y reputación constituye su principal fortaleza relativa, con una ventaja de **8,69 puntos porcentuales**.
- Compensación, comisiones y costes concentra el **27,2 %** de las críticas y presenta una desventaja de **9,35 puntos porcentuales** frente a los peers.
- Las personas actuales valoran su experiencia con **4,36**, frente a **3,75** entre quienes ya salieron.
- Las recomendaciones se centran en transparencia económica, seguimiento de cultura y liderazgo por oficina y un onboarding estructurado de 90 días.

## Estructura del proyecto

```text
.
├── data/raw/              # Archivos de entrada locales
├── docs/                  # Enunciado y presentación ejecutiva
├── imagenes/              # Visualizaciones exportadas
├── models/                # Embeddings y artefactos locales no versionados
├── notebooks/
│   ├── analisis_remax_glassdoor.ipynb
│   └── Glassdoor_ejemplo.ipynb
├── outputs/               # Resultados agregados en CSV
├── .python-version
├── requirements.txt
└── README.md
```

## Instalación local

El entorno utilizado fue validado con **Python 3.12.13**.

```bash
git clone https://github.com/JOBdeini/remax-glassdoor-nlp-analysis.git
cd remax-glassdoor-nlp-analysis

python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
```

Para registrar el entorno como kernel de Jupyter:

```bash
python -m ipykernel install --user \
  --name proyecto-modular-nlp \
  --display-name "Python 3.12 - RE/MAX NLP (.venv)"
```

## Datos

El dataset `glassdoor_reviews_hr.parquet` no se incluye en el repositorio debido a su tamaño y a las condiciones de distribución del material académico.

Para ejecutar el análisis, debe colocarse en:

```text
data/raw/glassdoor_reviews_hr.parquet
```

El notebook también admite el archivo en la raíz del proyecto o subido directamente al entorno de Google Colab.

## Ejecución

```bash
jupyter lab
```

Abrir y ejecutar:

```text
notebooks/analisis_remax_glassdoor.ipynb
```

El notebook guarda las visualizaciones en `imagenes/` y los resultados tabulares en `outputs/`.

## Presentación ejecutiva

La presentación con el planteamiento, la metodología, los resultados y las recomendaciones se encuentra en:

[docs/presentacion-remax-analisis-asociados.pdf](docs/presentacion-remax-analisis-asociados.pdf)

La versión completa del notebook en PDF, con código, explicaciones y resultados ejecutados, está disponible en:

[docs/analisis-remax-glassdoor-notebook.pdf](docs/analisis-remax-glassdoor-notebook.pdf)

## Limitaciones

- Las reseñas son voluntarias y pueden presentar sesgo de autoselección.
- La muestra combina países, oficinas, funciones y modelos de relación laboral diferentes.
- La fecha de publicación no siempre coincide con el periodo exacto de la experiencia descrita.
- La agrupación de temas en categorías de negocio incorpora revisión y criterio manual.
- Los resultados muestran asociaciones y no permiten establecer causalidad individual.

## Autor

**Job Delgado Iniesta**  
Proyecto modular de Deep Learning y NLP.
