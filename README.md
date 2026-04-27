
 # Mineria de Dades - Anàlisi de Salut Mental en Estudiants

Cristina Espasa Cárdenas  

---

## Descripció del projecte

Aquest projecte aborda un cas real de mineria de dades aplicat a la **salut mental dels estudiants**. L'objectiu és identificar patrons i relacions entre variables acadèmiques, psicològiques i sociodemogràfiques que afecten el benestar emocional dels estudiants.

El projecte segueix el cicle de vida complet de la mineria de dades:
1. Plantejament del problema analític
2. Selecció i preparació de les dades
3. Anàlisi exploratòria i neteja
4. Aplicació de models no supervisats (clustering)
5. Aplicació de models supervisats (classificació)
6. Avaluació i comparativa de resultats

---

## Dataset utilitzat

**Student Depression Dataset** (Kaggle)

- **Font:** [Kaggle - Student Depression Dataset](https://www.kaggle.com/datasets/adilshamim8/student-depression-dataset)
- **Observacions:** ~28.000 estudiants
- **Variables:** Rendiment acadèmic (CGPA), pressió acadèmica, estrès financer, hores d'estudi, gènere, edat, depressió (variable objectiu), etc.

### Requisits complerts
| Requisit | Compliment |
|----------|------------|
| ≥500 observacions | ~28.000 |
| ≥5 variables numèriques | CGPA, pressió acadèmica, hores d'estudi, estrès financer, edat |
| ≥2 variables categòriques | Gènere, durada del son, professió |
| 1 variable binària | Depressió (0/1) |

---

## Estructura del repositori
## PRA1: Selecció, preparació i anàlisi exploratòria

### Objectius
- Plantejar un problema analític sobre salut mental estudiantil
- Seleccionar i justificar un dataset adequat
- Realitzar anàlisi exploratòria de dades (EDA)
- Netejar i condicionar les dades per a modelatge
- Aplicar tècniques de discretització
- Realitzar Anàlisi de Components Principals (PCA)

### Principals resultats
| Trobada | Conclusió |
|---------|-----------|
| Distribució CGPA | Majoria d'estudiants entre 6-9 (distribució normal) |
| Pressió acadèmica | Nivells moderats (2-3) associats a millor rendiment |
| Gènere i depressió | Dones presenten taxa lleugerament superior |
| PCA | 2 primers components expliquen >55% de variància |

### Tècniques aplicades
- **Neteja:** Eliminació de NA, tractament d'outliers (CGPA >3 i <10)
- **Discretització:** CGPA (Baix/Mitjà/Alt/Excel·lent), Edat (grups d'edat)
- **PCA:** Reducció de dimensionalitat amb `prcomp()` i visualització amb `factoextra`

---

## PRA2: Modelització supervisada i no supervisada

### Objectius
- Aplicar algorismes de **clustering** (no supervisat)
- Aplicar algorismes de **classificació** (supervisat)
- Avaluar i comparar el rendiment dels models
- Identificar limitacions i riscos dels models

### Exercicis realitzats

| Exercici | Tècnica | Descripció |
|----------|---------|-------------|
| 1 | **k-means** | Clustering amb dades originals vs normalitzades |
| 2 | **k-medians / PAM** | Comparativa amb k-means |
| 3 | **k-means (distància Manhattan)** | Comparativa de mètriques |
| 4 | **DBSCAN** | Clustering basat en densitat |
| 5 | **Train/Test split** | Particionament per a validació |
| 6 | **Arbres de decisió (regles)** | Model supervisat amb i sense poda |
| 7 | **CART / c5.0** | Comparativa amb diferents criteris de partició |
| 8 | **Limitacions i riscos** | Anàlisi crítica dels models |

### Mètriques d'avaluació
- **Clustering:** Inèrcia, silueta, Davies-Bouldin
- **Classificació:** Matriu de confusió, precisió, sensibilitat, especificitat, F1-score

---

## Principals conclusions del projecte

### Sobre la salut mental dels estudiants
1. **Pressió acadèmica moderada** (nivells 2-3) s'associa amb millor rendiment
2. **Excés de pressió** (nivell 5) redueix significativament el CGPA
3. **Diferències de gènere:** Les dones presenten més depressió però també més satisfacció acadèmica
4. **Factors clau:** CGPA i pressió acadèmica són els principals discriminants (PCA)

### Sobre els models aplicats
| Model | Millor rendiment | Quan utilitzar-lo |
|-------|------------------|-------------------|
| k-means | Dades normalitzades | Grups esfèrics i balancejats |
| DBSCAN | Dades amb outliers | Estructures no esfèriques |
| Arbres decisió | Amb poda | Interpretabilitat i regles clares |

---

## Requisits tècnics

### Llibreries necessàries (R)

```r
# Per a PRA1
library(tidyverse)
library(ggplot2)
library(factoextra)

# Per a PRA2
library(cluster)      # k-means, k-medians, PAM
library(dbscan)       # DBSCAN
library(rpart)        # Arbres de decisió
library(rpart.plot)   # Visualització d'arbres
library(caret)        # Matrius de confusió i mètriques
library(RColorBrewer) # Paletes de colors
