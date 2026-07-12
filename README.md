# Barcelona's Ageing Population, Mapped at the Census-Section Level

Choropleth maps and analysis of average resident age across Barcelona's
1,068 census sections (secciones censales), 2015 to 2023, built for a
review of spatial demographic patterns and their implications for local
public service planning.

## What's in the notebook

`bcn_avg_age_map.ipynb` walks through, in order:

1. Loading census-section boundaries and the demographic indicator data
2. A 2023 choropleth of average resident age
3. A 2023 choropleth of the share of residents aged 65 and over, and how it
   relates to average age
4. A four-panel comparison across 2015, 2019, 2021 and 2023 on a shared
   color scale
5. Tables of the oldest census sections and districts (population-weighted)
   each year, and whether the ranking is stable over time
6. An animated GIF cycling through all nine years
7. A map of the nine-year change in average age (2015 to 2023), with the
   fastest-ageing and fastest-de-ageing sections
8. A closing summary tying the findings together

All figures share consistent styling and, where the underlying variable is
the same (average age), a fixed color scale across every figure so that a
given shade always represents the same value throughout the notebook.

## Data sources

| File | Content | Source |
|---|---|---|
| `data/BarcelonaCiutat_SeccionsCensals.json` | Census-section polygon boundaries for Barcelona city (WGS84 and ETRS89) | Ajuntament de Barcelona, Open Data BCN |
| `data/30904.json` | Demographic indicators (average age, population, % aged 65+) for all municipalities and census sections in Barcelona province | *(fill in the exact portal and dataset ID you downloaded this from, e.g. Idescat or Diputació de Barcelona's statistics portal)* |

Both files are joined on a constructed 10-digit section code: municipality
code (`08019` for Barcelona) plus a 2-digit district code plus a 3-digit
section code.

## Setup

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
python3 -m venv .venv
source .venv/bin/activate      # on Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Place the two data files in a `data/` folder at the repository root (see
table above), and create an empty `outputs/` folder; the notebook writes
the generated maps and animation there.

```
your-repo/
├── bcn_avg_age_map.ipynb
├── requirements.txt
├── data/
│   ├── BarcelonaCiutat_SeccionsCensals.json
│   └── 30904.json
└── outputs/
```

Then launch Jupyter and run all cells:

```bash
jupyter notebook bcn_avg_age_map.ipynb
```

## Notes

- `data/30904.json` is roughly 46 MB. GitHub's hard limit is 100 MB per
  file, so it can be committed directly, though large-file warnings may
  appear around 50 MB. If you would rather not version large data files,
  add `data/` to `.gitignore` and note the download source in this README
  instead.
- The animation (`outputs/bcn_avg_age_animation.gif`) is regenerated each
  time the notebook runs and is git-ignored by default.
