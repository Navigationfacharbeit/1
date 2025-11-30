# Facharbeit – Routen mit Unfalldaten / Graph-Tool

Dieses Repository enthält zwei Teile:

- `Straßennetz.py`: Erstellt auf Basis von OSM-Daten und Unfalldaten eine Karte mit 3 Routen (schnell/sicher/mix) und speichert sie als HTML.
- `Graphen.py`: Interaktives Tkinter-Tool zum Experimentieren mit Graphen und Dijkstra.

## Nutzung ohne VS Code (allgemein)

- Python 3.10+ installieren
- Abhängigkeiten installieren (siehe unten)
- Skripte aus einem beliebigen Terminal ausführen (PowerShell, CMD, iTerm, etc.)

```pwsh
# Windows PowerShell Beispiel (aus dem Repo-Ordner)
python Straßennetz.py
python Graphen.py
```

## Veröffentlichbare Website (GitHub Pages)

`Straßennetz.py` speichert die Karte nach `./docs/index.html`. Wenn du GitHub Pages in den Repository-Einstellungen aktivierst (Branch: `main`, Ordner: `docs/`), ist die Seite überall erreichbar.

Schritte:

1) Lokal `python Straßennetz.py` ausführen (erzeugt `docs/index.html`).
2) Dateien committen und pushen:

```pwsh
git add docs/index.html
git commit -m "Update map"
git push origin main
```

3) Auf GitHub: Settings → Pages → Source: `Deploy from a branch` → Branch: `main` und Folder: `docs/` → Save.
4) Nach wenigen Minuten ist die Seite unter der angezeigten URL erreichbar.

## Abhängigkeiten installieren

Hinweis: `osmnx`/`geopandas` haben Systemabhängigkeiten. Unter Windows ist `conda`/`mamba` empfohlen. Alternativ funktionieren die vorgefertigten Wheels per `pip` in der Regel.

### Variante A: pip (versuchen)

```pwsh
pip install -r requirements.txt
```

### Variante B: conda (empfohlen für Geo-Stack)

```pwsh
conda create -n facharbeit python=3.10 -y
conda activate facharbeit
conda install -c conda-forge osmnx geopandas shapely fiona pyproj rtree -y
pip install folium networkx scikit-learn pillow
```

## iPad / überall verwenden

- Website: Nach Aktivierung von GitHub Pages kannst du die Karte direkt im Browser aufrufen.
- Ohne Rechen-Backend: Die Karte ist statisch (aktualisiere sie lokal durch erneutes Ausführen von `Straßennetz.py` und pushen).
- Interaktiv/Server: Für eine komplette Web-App (mit Eingaben) eignen sich z.B. Streamlit/Render/Railway. Das erfordert aber eine Server-Umgebung mit `osmnx/geopandas`.

## Hinweise zu `Graphen.py`

`Graphen.py` ist eine Desktop-GUI (Tkinter). Für eine Web-Variante wäre eine Neuumsetzung mit z.B. Streamlit/Gradio oder eine JS-Portierung nötig. Sag Bescheid, wenn ich dir eine einfache Streamlit-Version bauen soll.
