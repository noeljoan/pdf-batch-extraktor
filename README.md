# 📄 Universal KI Pdf-Batch-Extraktor (Local-LLM)

![Python](https://shields.io)
![Ollama](https://shields.io)
![Privacy](https://shields.io)
![Platform](https://shields.io)

Ein hochpräzises, vollständig datenschutzkonformes Desktop-Werkzeug zur automatisierten Metadaten-Extraktion aus pdf Dokumenten. 

Durch die Kombination aus hochauflösender Bild-Vorschaltung (PyMuPDF + Tesseract) und einem **lokalen Sprachmodell** verarbeitet und versteht das Programm Dokumente wie ein menschliches Auge und Gehirn – komplett ohne Internetverbindung und lauffähig als eigenständige Windows-Anwendung (`.exe`).

---

## ✨ Features & Optimierungen (Version 14)

- **🧠 Lokale KI-Intelligenz (Qwen2.5:1.5b):** Nutzt ein hocheffizientes Small Language Model direkt auf Ihrem PC. Die KI liest den erfassten Text im Kontext, isoliert echte Bautitel und ignoriert rechtlichen Standard-Zeichensalat.
- **🔒 100% Offline-Sicherheit (Kein Cloud-Datenabfluss):** Das Skript funktioniert nach dem ersten Modell-Download vollständig im Flugmodus. Es werden **keine** Daten an Drittanbieter (wie OpenAI oder Claude) gesendet oder für das KI-Training missbraucht.
- **📦 Eigenständige Windows-App (.EXE):** Kann direkt als eigenständiges Programm kompiliert und ohne Terminal oder sichtbare Python-Konsole per Doppelklick gestartet werden.
- **⚡ Extrem ressourcenschonend:** Das Modell benötigt nur ca. 1 GB Arbeitsspeicher. Die CPU-Last ist minimal – der PC friert während der Verarbeitung nicht ein, und das Tool läuft im Sekundentakt flüssig durch.
- **🖼️ Robustes Bild-OCR:** Wandelt die erste PDF-Seite in eine hochauflösende Grafik um. Dadurch werden auch extrem verrauschte, alte Scans oder fehlerhaft codierte Schriften exakt digitalisiert.
- **📊 Smarte Excel-Formatierung:** Automatischer Filter für illegale Unicode-Steuerzeichen (Excel-Crash-Schutz) und dynamische Anpassung der Spaltenbreiten nach dem Export.

---

## 🛠️ System-Voraussetzungen & Installation

### 1. Lokale KI-Umgebung (Ollama)
Das Skript benötigt die kostenlose Laufzeitumgebung **Ollama** zur Ausführung du Sprachmodells:
1. Laden Sie Ollama für Windows herunter und installieren Sie es: [ollama.com](https://ollama.com).
2. Öffnen Sie Ihre Windows-Eingabeaufforderung (CMD) und laden Sie das Modell mit folgendem Befehl herunter:
   ```cmd
   ollama run qwen2.5:1.5b
   ```
3. Sobald der Download abgeschlossen ist, können Sie das Fenster mit `/bye` wieder schließen.

### 2. Texterkennungs-Engine (Tesseract OCR)
Für die visuelle Digitalisierung von gescannten Bild-PDFs:
1. Laden Sie den Windows-Installer herunter: [UB Mannheim Tesseract Wiki](https://github.com).
2. **Wichtig:** Setzen Sie während der Installation das Häkchen bei **"German" (Deutsch)** unter *Additional language data*, um deutsche Umlaute korrekt zu erfassen.
3. Das Skript greift standardmäßig auf den Pfad `C:\Program Files\Tesseract-OCR\tesseract.exe` zu.

### 3. Python-Bibliotheken (Nur für Entwickler / Kompilierung)
Installieren Sie die benötigten Pakete über Ihr Python-Terminal:
```bash
pip install openpyxl pymupdf pytesseract pillow ollama pyinstaller
```

---

## 📦 Anwendung als .EXE kompilieren

Um die eigenständige Windows-Anwendung ohne Terminal-Zwang selbst zu generieren, führen Sie folgenden Befehl im Projektordner aus:

```bash
pyinstaller --noconfirm --onedir --windowed --name "Normen_Extraktor" pdf_extraktor.py
```

Nach Abschluss des Vorgangs finden Sie Ihre einsatzbereite Anwendung im Ordner **`dist/PDF_Extraktor/PDF_Extraktor.exe`**. Sie können von dieser Datei einfach eine Verknüpfung auf Ihrem Desktop erstellen.

---

## 🚀 Verwendung

1. Starten Sie die Anwendung per Doppelklick auf die **`PDF_Extraktor.exe`** (oder via Terminal mit `python pdf_extraktor.py`).
2. **Schritt 1:** Wählen Sie über den oberen "Durchsuchen"-Button den Ordner aus, der Ihre PDFs enthält.
3. **Schritt 2:** Wählen Sie über "Speichern unter" den Zielpfad und einen neuen Namen für Ihre Excel-Datei aus (z. B. `Pdf_Uebersicht.xlsx`).
4. Klicken Sie auf **"KI-Extraktion starten"**. Der Fortschrittsbalken zählt flüssig nach oben.

---

## 📋 Struktur des Excel-Exports

Das Tool bereinigt Klassifizierungs-Rauschen (ICS-Nummern) am Anfang und fehlerhafte Anhängsel vollautomatisch:

| Spalte | Extraktions-Quelle | Beispiel-Ergebnis |
| :--- | :--- | :--- |
| **Dateiname** | Name der verarbeiteten Datei | `XXXXXXX.pdf` |
| **Normnummer** | Erkannte Normbezeichnung (isoliert) | `DIN 13` |
| **Ausgabedatum** | Veröffentlichungsdatum (mehrsprachig) | `August 1968` |
| **Titel (DE)** | Bereinigter, offizieller Bautitel | `Metrisches ISO-Gewinde` |
| **Status** | Platzhalter für interne Workflows | `Unbekannt` |

---

## 📄 Lizenz & Autor

- **Autor:** Noel Joan
- **Lizenz:** MIT-Lizenz – Freie Verwendung, Modifikation und Weitergabe für private sowie kommerzielle Zwecke.
