# KI-Modelle zur Optimierung der Brustkrebsdiagnose

Dieses Projekt stellt eine vollständige Deep-Learning-Pipeline zur Verfügung, die auf multimodalen MRT-Daten basiert und zwei Hauptaufgaben erfüllt:

1. **Klassifikation** von Tumoren in benigne oder maligne  
2. **Segmentierung** von Tumorregionen

Zum Einsatz kommen zwei spezialisierte Modelle:

- Ein multimodales **EfficientNetB0-Klassifikator** für die Klassifikation  
- Ein **Attention U-Net**, aufgebaut mit Skip-Verbindungen aus EfficientNetB0 für die Segmentierung  

Die Architektur wurde im Rahmen einer wissenschaftlichen Arbeit zur Verbesserung der diagnostischen Genauigkeit bei Brustkrebs entwickelt.

---

## Eigenschaften

- Verarbeitung und Vorverarbeitung medizinischer DICOM-Daten  
- Integration strukturierter klinischer Merkmale  
- Klassifikation mit EfficientNetB0 + Focal Loss  
- Segmentierung mit Attention U-Net + Hybrid Dice/Focal Tversky Loss  
- Visualisierungen, Trainingsmetriken und automatische Speicherung  
- Patientinnenbasierter Datensplit (Train/Val/Test)

---

## Python-Umgebung

- Das Skript wurde in einem Jupyter-Notebook mit der Python-Version **3.11.11** in einer **WSL (Ubuntu)-Umgebung** erstellt und ausgeführt.  
  Solange die Anforderungen in der Datei ``requirements.txt`` sowie die korrekte **Python-Version** verwendet werden, kann der Code ohne Probleme ausgeführt werden.

- Um eine neue virtuelle Umgebung zu erstellen, in der **TensorFlow**, **CUDA** und **cuDNN** von Nvidia kompatibel sind, wurde anhand eines YouTube-Tutorials eine **Linux-Umgebung auf Windows** eingerichtet.  

  🔗 [YouTube Tutorial](https://www.youtube.com/watch?v=1u1OK54J7D8&list=WL&index=31&t=2171s)

---

## Verwendeter Datensatz

Für die Nutzung des Skriptes wurde der Datensatz **Advanced-MRI-Breast-Lesions** 🔗 [https://doi.org/10.7937/C7X1-YN57](https://doi.org/10.7937/C7X1-YN57) von der öffentlichen Datenbank **The Cancer Imaging Archive** verwendet.
Die größe des Datensatzes beträgt 645,62 GB.

---

## Daten und Verzeichnisse

Die erzeugten Daten werden in folgende Verzeichnisse gespeichert und sollten bei Verwendung an eigene Anforderungen angepasst werden.

**Relevante Pfade:**
- `EXCEL_PATH` = `/.../Advanced-MRI-Breast-Lesions/Advanced-MRI-Breast-Lesions-DA-Clinical-Sep2024.xlsx`  
- `DICOM_FOLDER` = `/.../Advanced-MRI-Breast-Lesions/DICOM Images/manifest-1713182663002/Advanced-MRI-Breast-Lesions`  

**Erzeugte Daten:**
- `INTERMEDIATE_FOLDER` = `/.../data/intermediate_caches`  
- `FINAL_CACHE_FILE` = `/.../data/geladene_Daten.pkl`  
- `FINAL_SUMMARY_CSV` = `/.../data/Datenzusammenfassung.csv`  
- `SPLIT_INDICES_FILE` = `/.../data/patient_split_indices.pkl`

**Gespeicherte Plots und Modelle:**
- Modelle, Trainingsverlauf, Checkpoints, History: `Linux/Ubuntu/home/melisa/projects/tf217/results`  
- Plots (AUC, Konfusionsmatrix, visueller Maskenvergleich): `Linux/Ubuntu/home/melisa/projects/tf217/plots`

Die **Plots, Modelle, etc.** werden lokal im Ordner vom ausgeführten Skript gespeichert, alles andere muss, wie schon erwähnt, an die eigenen verwendeten Ordner angepasst werden.

---

## Skript

Der Code befindet sich im GitHub-Repository unter dem Namen: **`BA_Code - Version EfficientNetB0 + Attention U-Net.ipynb`**

Es befindet sich eine weiterer Code namens **`Vergleich der DICOM-Bilder.ipynb`**, der lediglich zum Vergleich der verarbeiteten und unverarbeitetn DICOM-Bilder einer beliebigen Patientin dient.

---

### Hinweis

Dieses Projekt dient ausschließlich zu **Forschungs- und Ausbildungszwecken**.  
Es ist **nicht für klinische Anwendungen** oder den Einsatz in der medizinischen Praxis zugelassen.
