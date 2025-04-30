---
"description": "Erfahren Sie in diesem ausführlichen Tutorial, wie Sie Schriftarten mit Aspose.Words für .NET als Base64 exportieren. Stellen Sie sicher, dass Schriftarten in HTML-Dateien korrekt eingebettet und angezeigt werden."
"linktitle": "Schriftarten als Base 64 exportieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Schriftarten als Base 64 exportieren"
"url": "/de/net/programming-with-htmlsaveoptions/export-fonts-as-base-64/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Schriftarten als Base 64 exportieren

## Einführung

Wenn es um die programmgesteuerte Bearbeitung von Word-Dokumenten geht, ist Aspose.Words für .NET ein echtes Kraftpaket. Eine seiner praktischen Funktionen ist der Export von Schriftarten als Base64 in HTML-Dateien. Dadurch wird sichergestellt, dass Schriftarten in verschiedenen Browsern und Systemen korrekt eingebettet und angezeigt werden. In diesem Tutorial erfahren Sie, wie Sie dies erreichen können. Sind Sie bereit, Ihre Word-Dokument-Schriftarten webfreundlich zu gestalten? Los geht’s!

## Voraussetzungen

Bevor wir mit der Codierung beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

- Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von der [Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) Seite.
- .NET-Entwicklungsumgebung: Jede IDE wie Visual Studio funktioniert einwandfrei.
- Grundkenntnisse in C#: Sie müssen kein Profi sein, aber ein grundlegendes Verständnis ist hilfreich.

## Namespaces importieren

Um Aspose.Words für .NET zu verwenden, müssen Sie die erforderlichen Namespaces in Ihren C#-Code importieren. Dadurch stehen alle Klassen und Methoden zur Verfügung.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Richten Sie Ihr Projekt ein

Als Erstes richten wir Ihr Projekt ein und installieren die Aspose.Words-Bibliothek.

### 1.1 Neues Projekt erstellen

Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolen-App-Projekt. Geben Sie ihm einen aussagekräftigen Namen, z. B. „ExportFontsBase64“.

### 1.2 Installieren Sie Aspose.Words

Sie können Aspose.Words für .NET über den NuGet-Paket-Manager installieren:

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt.
2. Wählen Sie „NuGet-Pakete verwalten“ aus.
3. Suchen Sie nach „Aspose.Words“ und installieren Sie es.

Alternativ können Sie den folgenden Befehl in der Paket-Manager-Konsole ausführen:

```sh
Install-Package Aspose.Words
```

## Schritt 2: Laden Sie Ihr Word-Dokument

Nachdem Ihr Projekt nun eingerichtet ist, laden wir das Word-Dokument, aus dem Sie Schriftarten exportieren möchten.

### 2.1 Definieren des Dokumentverzeichnisses

Legen Sie zunächst das Verzeichnis fest, in dem sich Ihr Word-Dokument befindet:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis.

### 2.2 Laden Sie das Dokument

Laden Sie anschließend Ihr Dokument mit dem `Document` Klasse:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Stellen Sie sicher, dass sich „Rendering.docx“ in Ihrem angegebenen Verzeichnis befindet.

## Schritt 3: Konfigurieren Sie die HTML-Speicheroptionen

Um Schriftarten als Base64 zu exportieren, müssen wir die `HtmlSaveOptions`.


Erstellen Sie eine Instanz von `HtmlSaveOptions` und legen Sie die `ExportFontsAsBase64` Eigentum zu `true`:

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { ExportFontsAsBase64 = true };
```

## Schritt 4: Speichern Sie das Dokument als HTML

Abschließend speichern wir das Dokument mit den konfigurierten Optionen.


Verwenden Sie die `Save` Methode der `Document` Klasse zum Speichern Ihres Dokuments:

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
```

Diese Zeile speichert Ihr Dokument als HTML-Datei mit als Base64 exportierten Schriftarten und stellt sicher, dass sie in das HTML eingebettet sind.

## Abschluss

Herzlichen Glückwunsch! Sie haben Schriftarten erfolgreich als Base64 aus einem Word-Dokument mit Aspose.Words für .NET exportiert. Dadurch wird sichergestellt, dass Ihre Schriftarten auf verschiedenen Plattformen erhalten bleiben und korrekt angezeigt werden. Egal, ob Sie Dokumente für die Anzeige im Web vorbereiten oder einfach nur die Kompatibilität sicherstellen möchten – diese Funktion ist unglaublich nützlich.

## Häufig gestellte Fragen

### Was ist Base64-Kodierung?
Base64 ist eine Methode zur Kodierung binärer Daten (wie Schriftarten) in ein Textformat. Dies gewährleistet die Kompatibilität mit textbasierten Formaten wie HTML.

### Warum sollte ich Base64 für Schriftarten in HTML verwenden?
Durch die Verwendung von Base64 wird sichergestellt, dass Schriftarten direkt in das HTML eingebettet werden. Dadurch werden Probleme mit fehlenden Schriftdateien vermieden und eine konsistente Anzeige gewährleistet.

### Kann ich diese Methode für andere Ressourcen wie Bilder verwenden?
Absolut! Mit Aspose.Words für .NET können Sie verschiedene Ressourcen, einschließlich Bilder, als Base64 in Ihre HTML-Dateien einbetten.

### Was ist, wenn mein Dokument mehrere Schriftarten enthält?
Kein Problem! Aspose.Words für .NET bettet alle in Ihrem Dokument verwendeten Schriftarten als Base64 in die resultierende HTML-Datei ein.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
Aspose.Words für .NET ist eine kommerzielle Bibliothek. Sie können jedoch eine kostenlose Testversion von der [Aspose-Veröffentlichungen](https://releases.aspose.com/) Seite.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}