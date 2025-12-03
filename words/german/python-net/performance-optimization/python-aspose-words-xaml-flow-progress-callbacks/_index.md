---
"date": "2025-03-29"
"description": "Erfahren Sie, wie Sie die Dokumentspeicherung mit Aspose.Words für Python mithilfe des XAML-Flow-Formats und Fortschrittsrückrufen optimieren. Steigern Sie die Effizienz bei der Dokumentenverwaltung."
"title": "Optimieren der Dokumentspeicherung in Python&#58; Aspose.Words XAML-Flow- und Fortschrittsrückrufe"
"url": "/de/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# So optimieren Sie das Speichern von Dokumenten in Python mit Aspose.Words: XAML-Flow- und Progress-Callbacks

## Einführung

Möchten Sie Dokumentkonvertierungen mit Python effizient verwalten? Haben Sie Probleme mit der Bildverarbeitung und der Fortschrittsverfolgung beim Speichern von Dokumenten? Dieses Tutorial führt Sie durch die Optimierung des Dokumentspeicherns mit Aspose.Words für Python und konzentriert sich dabei auf zwei leistungsstarke Funktionen: `XamlFlowSaveOptions` mit Rückruf zum Bildordner und zum Fortschritt der Dokumentspeicherung.

Dieser umfassende Leitfaden ist ideal für Entwickler, die ihre Dokumentverarbeitungs-Workflows mithilfe der Aspose.Words-Bibliothek verbessern möchten.

**Was Sie lernen werden:**
- So speichern Sie ein Dokument im XAML-Flow-Format, während Sie Bildressourcen verwalten.
- Implementieren von Fortschrittsrückrufen während des Speicherns von Dokumenten, um lange Vorgänge zu vermeiden.
- Einrichten und Konfigurieren von Aspose.Words für Python in Ihrer Entwicklungsumgebung.
- Praktische Anwendungen dieser Funktionen in Dokumentenmanagementsystemen.

Lassen Sie uns in die Voraussetzungen eintauchen, bevor wir mit dem Programmieren beginnen!

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

### Erforderliche Bibliotheken und Versionen
- **Aspose.Words für Python**: Stellen Sie sicher, dass Sie Version 23.3 oder höher haben.
- **Python**: Version 3.6 oder höher wird empfohlen.

### Anforderungen für die Umgebungseinrichtung
- Ein Code-Editor wie VSCode oder PyCharm.
- Grundkenntnisse der Python-Programmierung.

### Voraussetzungen
- Vertrautheit mit Konzepten der Dokumentenverarbeitung.
- Kenntnisse in der Dateiverwaltung und Verzeichnisverwaltung in Python.

## Einrichten von Aspose.Words für Python

Um Aspose.Words nutzen zu können, müssen Sie es über pip installieren. Öffnen Sie Ihr Terminal oder Ihre Eingabeaufforderung und führen Sie Folgendes aus:

```bash
pip install aspose-words
```

### Schritte zum Lizenzerwerb
1. **Kostenlose Testversion**: Zugriff auf eine temporäre Lizenz [Hier](https://purchase.aspose.com/temporary-license/) zu Testzwecken.
2. **Kaufen**: Für die langfristige Nutzung erwerben Sie eine Lizenz [Hier](https://purchase.aspose.com/buy).
3. **Grundlegende Initialisierung und Einrichtung**:
   - Laden Sie Ihr Dokument mit `aw.Document()`.
   - Konfigurieren Sie die Speicheroptionen nach Bedarf.

## Implementierungshandbuch

In diesem Abschnitt werden Sie durch die Implementierung der beiden Hauptfunktionen dieses Lernprogramms geführt: XamlFlowSaveOptions mit Bildordner und Rückruf für den Fortschritt beim Speichern von Dokumenten.

### Feature 1: XamlFlowSaveOptions mit Bildordner

#### Überblick
Mit dieser Funktion können Sie ein Dokument im XAML-Flow-Format speichern und dabei einen Bildordner und einen Alias angeben. Dies ist ideal für die effiziente Verwaltung großer Dokumente mit eingebetteten Bildern.

#### Implementierungsschritte

##### Schritt 1: Erforderliche Bibliotheken importieren
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Schritt 2: Definieren der ImageUriPrinter-Rückrufklasse
Diese Klasse zählt Bildströme und leitet sie während der Konvertierung in einen angegebenen Aliasordner um.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # Typ: Liste [str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Wichtige Konfigurationsoptionen:**
- `images_folder`: Gibt das Verzeichnis an, in dem Bilder gespeichert werden.
- `images_folder_alias`: Legt einen Aliaspfad fest, der während der Dokumentkonvertierung verwendet wird.

##### Tipps zur Fehlerbehebung
- Stellen Sie sicher, dass alle Verzeichnisse vorhanden sind, bevor Sie den Code ausführen, um Fehler aufgrund nicht gefundener Dateien zu vermeiden.
- Überprüfen Sie die Schreibberechtigungen in Ihrem Ausgabeverzeichnis.

### Funktion 2: Rückruf zum Fortschritt des Dokumentspeicherns

#### Überblick
Diese Funktion verwaltet den Speichervorgang mithilfe eines Fortschrittsrückrufs, sodass Sie lang andauernde Speichervorgänge abbrechen können.

#### Implementierungsschritte

##### Schritt 1: Definieren der SavingProgressCallback-Klasse
Die Klasse überwacht die Dauer der Dokumentspeicherung und bricht ab, wenn diese ein vorgegebenes Zeitlimit überschreitet.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Maximal zulässige Dauer in Sek.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Wichtige Konfigurationsoptionen:**
- `save_format`: Wählen Sie zwischen XAML_FLOW und XAML_FLOW_PACK.
- `progress_callback`: Überwacht den Speicherfortschritt, um lange Vorgänge zu bewältigen.

##### Tipps zur Fehlerbehebung
- Anpassen `max_duration` basierend auf Dokumentgröße und Komplexität.
- Behandeln Sie Ausnahmen ordnungsgemäß, um informative Fehlermeldungen bereitzustellen.

## Praktische Anwendungen

Hier sind einige Anwendungsfälle aus der Praxis für diese Funktionen:
1. **Dokumentenmanagementsysteme**: Verwalten Sie große Dokumente mit eingebetteten Bildern effizient, indem Sie Bildordner angeben und so Leistung und Organisation verbessern.
2. **Automatisierte Berichtstools**: Verwenden Sie Fortschrittsrückrufe, um sicherzustellen, dass Berichte innerhalb akzeptabler Zeiträume generiert werden, und verbessern Sie so die Benutzererfahrung.
3. **Content-Distributionsnetzwerke**: Optimieren Sie die Konvertierung von Dokumenten für die Verteilung im Internet und verwalten Sie gleichzeitig die Ressourcen effektiv.

## Überlegungen zur Leistung

So optimieren Sie die Leistung bei der Verwendung von Aspose.Words mit Python:
- **Speicherverwaltung**: Überwachen Sie die Ressourcennutzung und verwalten Sie den Speicher effizient, indem Sie Objekte nach der Verwendung entsorgen.
- **Datei-E/A-Vorgänge**: Minimieren Sie Dateilese-/Schreibvorgänge, um die Geschwindigkeit zu verbessern.
- **Stapelverarbeitung**: Verarbeiten Sie Dokumente nach Möglichkeit stapelweise, um den Aufwand zu reduzieren.

## Abschluss

In diesem Tutorial haben wir untersucht, wie Sie die Dokumentspeicherung mit Aspose.Words für Python mithilfe von XAML Flow und Fortschrittsrückrufen optimieren können. Durch die Implementierung dieser Funktionen können Sie die Effizienz Ihrer Dokumentverarbeitungs-Workflows steigern, Ressourcen effektiv verwalten und zeitnahe Abläufe sicherstellen.