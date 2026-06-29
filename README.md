# Random Forest su immagini satellitari per il riconoscimento e il conteggio di piante

> Tesi di Laurea in Informatica — Università degli Studi di Ferrara  
> Anno Accademico 2025–2026

| | |
|---|---|
| **Laureando** | Tobia Sacchetto |
| **Relatore** | Prof. Guido Sciavicco |

---

## Descrizione

Questa tesi propone un metodo per **identificare e contare automaticamente piante di avocado e di altre tipologie** in terreni agricoli a partire da immagini satellitari multispettrali, mediante tecniche di machine learning simbolico.

Il cuore del sistema è una **Foresta Casuale** (*Random Forest*) che opera pixel per pixel sulle bande infrarosse dell'immagine. Una volta classificati i pixel, gli agglomerati di pixel identificati come pianta vengono analizzati da un modello di **regressione lineare** per stimare il numero di piante presenti.

Sono stati sviluppati e confrontati due modelli:

- **Modello NIR+SWIR** — sfrutta entrambe le bande infrarosse, addestrato su dataset satellitare aziendale (risoluzione 30 cm/px)
- **Modello solo NIR** — lavora con la sola banda NIR, addestrato su dataset aziendale + dataset open source [Faet et al. 2025](https://doi.org/10.5281/zenodo.17866344)

---

## Struttura della repository

```
.
├── thesis/              # Sorgenti LaTeX e PDF della tesi
│   ├── *.tex
│   ├── *.bib
│   └── thesis.pdf       # PDF già compilato
│
└── presentation/        # Sorgenti LaTeX e PDF della presentazione
    ├── *.tex
    └── presentation.pdf # PDF già compilato
```

> I PDF compilati sono già inclusi nella repository: non è necessario ricompilare i sorgenti LaTeX per leggere il lavoro.

---

## Risultati principali

| Modello | Accuracy (F1) | Note |
|---|---|---|
| NIR + SWIR | **0.89** | Migliore discriminazione tra specie |
| Solo NIR | **0.85** | Supporta una tipologia di pianta aggiuntiva (aranci) |

La disponibilità della banda SWIR porta a un miglioramento significativo nella classificazione, in linea con l'analisi spettrale preliminare. Entrambi i modelli mostrano performance ridotte sulle classi con minor numero di campioni (dataset sbilanciato).

---

## Stack tecnologico

| Strumento | Utilizzo |
|---|---|
| Python | Implementazione del modello |
| [Scikit-learn](https://scikit-learn.org/) | Random Forest e regressione lineare |
| [QGIS](https://qgis.org/) | Visualizzazione e annotazione immagini satellitari |
| LaTeX | Stesura tesi e presentazione |

---

## Riferimenti

- Faet, G. M. et al. (2025). *Dataset for orange fruit detection from UAV in citrus orchards*. Zenodo. https://doi.org/10.5281/zenodo.17866344
- Fu, B. et al. (2017). *Comparison of object-based and pixel-based Random Forest algorithm for wetland vegetation mapping*. Ecological Indicators, 73, 105–117.
- Yao, L. et al. (2021). *Tree counting with high spatial-resolution satellite imagery based on deep neural networks*. Ecological Indicators, 125, 107591.
- Russell, S. J. & Norvig, P. (2022). *Intelligenza artificiale. Un approccio moderno*.
