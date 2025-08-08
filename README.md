# DAMI01 - Berlin Unternehmensstandort Clustering Analyse

## 📋 Projektbeschreibung

Dieses Projekt analysiert Unternehmensstandorte in Berlin mittels fortgeschrittener Clustering-Verfahren. Das Ziel ist es, verschiedene Typen von Unternehmensstandorten zu identifizieren und ihre Charakteristika hinsichtlich Bevölkerungsstruktur, wirtschaftlicher Ausrichtung und räumlicher Verteilung zu verstehen.

### 🎯 Forschungsfrage
*Inwiefern lassen sich durch Clusteranalysen verschiedene Typen von Unternehmensstandorten in Berlin identifizieren, und wie unterscheiden sie sich hinsichtlich Bevölkerungsstruktur und wirtschaftlicher Ausrichtung?*

## 📊 Datenquellen

- **IHK Berlin Gewerbedaten**: ~350.000 Gewerbedatensätze mit Informationen zu Unternehmen, Branchen und Standorten
- **Bodenrichtwerte Berlin**: Immobilienwerte nach Bezirken und Stadtteilen
- **Einwohnerdichte 2023**: Demografische Daten zur Bevölkerungsverteilung in Berlin
- **WZ-2008 Klassifikationen**: Standardisierte Wirtschaftszweig-Klassifizierungen

## 🗂️ Projektstruktur

```
DAMI01/
├── README.md                                    # Projektdokumentation
├── requirements.txt                             # Python-Abhängigkeiten
├── input/                                       # Rohdaten und verarbeitete Daten
│   ├── raw/                                     # Originaldaten
│   ├── clean/                                   # Bereinigte Daten
│   ├── ihk_gewerbedaten_with_brw_einwohnerdichte.csv.gz  # Hauptdatensatz
│   ├── klassifikationen-wz-2008.pdf            # Wirtschaftszweig-Klassifikationen
│   └── nachweis_brw.png                         # Bodenrichtwert-Nachweis
└── notebooks/                                   # Jupyter Notebooks
    ├── main.ipynb                               # Hauptanalyse mit Clustering
    ├── data_preprocessing_ihk_gewerbedaten.ipynb # IHK-Daten Vorverarbeitung
    ├── data_preprocessing_bodenrichtwert.ipynb  # Bodenrichtwert-Integration
    └── data_preprocessing_einwohnerdichte.ipynb # Demografische Daten-Integration
```

## 🛠️ Technologie-Stack

### Machine Learning & Data Science
- **pandas** (2.2.3) - Datenmanipulation und -analyse
- **numpy** (2.2.5) - Numerische Berechnungen
- **scikit-learn** (1.6.1) - Machine Learning Algorithmen
- **matplotlib** (3.10.1) - Datenvisualisierung
- **seaborn** (0.13.2) - Statistische Datenvisualisierung

### Clustering-Algorithmen
- **K-Means** - Zentroid-basiertes Clustering
- **Gaussian Mixture Models (GMM)** - Probabilistisches Clustering
- **DBSCAN** - Dichtebasiertes Clustering
- **HDBSCAN** (0.8.40) - Hierarchisches dichtebasiertes Clustering

### Geospatiale Analyse
- **geopandas** (1.1.1) - Geospatiale Datenverarbeitung
- **folium** (0.20.0) - Interaktive Karten
- **contextily** (1.6.2) - Kartenhintergründe

### Evaluationsmetriken
- **Silhouette Score** - Cluster-Qualitätsbewertung
- **Calinski-Harabasz Index** - Cluster-Separation
- **Davies-Bouldin Index** - Cluster-Kompaktheit
- **Hopkins Statistik** - Cluster-Tendenz

## 🚀 Setup und Installation

### Virtual Environment
1. **Erstelle Virtual Environment**:
   ```bash
   python3 -m venv .venv
   ```

2. **Aktiviere Virtual Environment**:
   ```bash
   # macOS/Linux
   source .venv/bin/activate
   
   # Windows
   .venv\Scripts\activate
   ```

3. **Installiere Abhängigkeiten**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Überprüfe Installation**:
   ```bash
   pip freeze --local
   ```

### Jupyter Notebook starten
```bash
jupyter notebook notebooks/
```

## 📈 Analyse-Pipeline

### 1. Datenvorverarbeitung
- **IHK-Daten**: Bereinigung, Kategorisierung von Branchen, Altersberechnung
- **Bodenrichtwerte**: Geocoding und Zuordnung zu Unternehmensstandorten
- **Einwohnerdichte**: Integration demografischer Merkmale

### 2. Feature Engineering
- Normalisierung numerischer Variablen
- One-Hot-Encoding kategorialer Variablen
- PCA-Dimensionsreduktion für Visualisierung
- Ausreißer-Behandlung mittels IQR-Methode

### 3. Clustering-Analyse
- **K-Means**: Optimierung via Elbow-Methode und Silhouette-Analyse
- **GMM**: BIC/AIC-basierte Modellauswahl mit verschiedenen Kovarianz-Typen
- **DBSCAN**: ε-Optimierung durch k-Distanz-Analyse

### 4. Evaluation & Interpretation
- Umfassende Cluster-Qualitätsbewertung
- Geschäftsorientierte Interpretation der Cluster
- Visualisierung in 2D/3D-Raum
- Geospatiale Cluster-Darstellung

## 📊 Hauptergebnisse

### Cluster-Charakteristika
Das optimierte Clustering identifiziert verschiedene Unternehmensstandort-Typen:

1. **Etablierte Geschäftszentren**: Hoher Bodenrichtwert, reife Unternehmen
2. **Emerging Tech-Hubs**: Junge Unternehmen, innovative Branchen  
3. **Traditionelle Gewerbegebiete**: Produktion/Handel, mittlere Immobilienwerte
4. **Dichtebasierte Cluster**: Räumlich konzentrierte Unternehmensansiedlungen

### Performance-Metriken
- **Bester Algorithmus**: DBSCAN (Silhouette Score: 0.519)
- **Cluster-Anzahl**: 2-20 je nach Algorithmus
- **Datenabdeckung**: 50.000 Sample aus 350.000 Unternehmen

## 💡 Business Insights

### Handlungsempfehlungen
1. **Standortförderung**: Gezielte Unterstützung basierend auf Cluster-Profilen
2. **Stadtplanung**: Infrastrukturentwicklung für identifizierte Hotspots
3. **Unternehmensberatung**: Standortempfehlungen basierend auf Branche und Größe
4. **Wirtschaftsförderung**: Cluster-spezifische Förderprogramme

### Methodische Erkenntnisse
- Silhouette Score als robusteste Bewertungsmetrik
- DBSCAN optimal für dichtebasierte Standortmuster
- Bodenrichtwert als wichtiger Differenzierungsfaktor
- Demografische Merkmale verstärken Cluster-Interpretierbarkeit

## 🔬 Wissenschaftlicher Ansatz

### Methodische Rigorosität
- Multiple Clustering-Algorithmen für Robustheit
- Systematische Hyperparameter-Optimierung
- Kreuzvalidierung verschiedener Bewertungsmetriken
- Statistische Signifikanz-Tests

### Reproduzierbarkeit
- Vollständig dokumentierte Datenverarbeitungs-Pipeline
- Versionierte Abhängigkeiten
- Standardisierte Random Seeds
- Modular aufgebauter, wiederverwendbarer Code

## 📁 Datenmanagement

### Input-Verzeichnis Struktur
- Komprimierte Formate (.csv.gz) für große Datensätze
- Dokumentation der Datenquellen und -transformationen

### Datenqualität
- Systematische Missing-Value-Behandlung
- Ausreißer-Erkennung und -Behandlung
- Datentyp-Validierung
- Konsistenz-Checks zwischen Datensätzen

## 🎓 Verwendung für Lehre/Forschung

Dieses Projekt eignet sich hervorragend für:
- **Data Mining Kurse**: Clustering-Verfahren in der Praxis
- **Urban Analytics**: Anwendung von ML auf Stadtdaten
- **Business Intelligence**: Datengetriebene Standortanalysen
- **Geospatiale Analyse**: Integration räumlicher und betriebswirtschaftlicher Daten

## 📞 Weitere Informationen

Für Fragen zur Implementierung, Datenquellen oder methodischen Details kontaktieren Sie den Projektverantwortlichen.

---