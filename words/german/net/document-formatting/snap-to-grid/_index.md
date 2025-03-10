---
title: Im Word-Dokument am Raster ausrichten
linktitle: Im Word-Dokument am Raster ausrichten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET die Funktion „Am Raster ausrichten“ in Word-Dokumenten aktivieren. Dieses ausführliche Tutorial behandelt Voraussetzungen, eine Schritt-für-Schritt-Anleitung und häufig gestellte Fragen.
weight: 10
url: /de/net/document-formatting/snap-to-grid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Im Word-Dokument am Raster ausrichten

## Einführung

Beim Arbeiten mit Word-Dokumenten ist die Beibehaltung eines konsistenten und strukturierten Layouts von entscheidender Bedeutung, insbesondere bei komplexen Formatierungen oder mehrsprachigen Inhalten. Eine nützliche Funktion, die dabei helfen kann, ist die Funktion „Am Raster ausrichten“. In diesem Tutorial erfahren Sie ausführlich, wie Sie die Funktion „Am Raster ausrichten“ in Ihren Word-Dokumenten mit Aspose.Words für .NET aktivieren und verwenden können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

-  Aspose.Words für .NET-Bibliothek: Sie können sie herunterladen[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
- Grundkenntnisse in C#: Das Verständnis der Grundlagen der C#-Programmierung wird Ihnen helfen, den Beispielen zu folgen.
-  Aspose-Lizenz: Eine temporäre Lizenz kann erworben werden[Hier](https://purchase.aspose.com/temporary-license/), die Verwendung einer Volllizenz gewährleistet den Zugriff auf alle Funktionen ohne Einschränkungen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Dadurch können Sie die Funktionen der Aspose.Words-Bibliothek in Ihrem Projekt verwenden.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

Lassen Sie uns den Vorgang zum Aktivieren der Funktion „Am Raster ausrichten“ in einem Word-Dokument Schritt für Schritt durchgehen. Jeder Schritt enthält eine Überschrift und eine ausführliche Erklärung.

## Schritt 1: Richten Sie Ihr Projekt ein

Zuerst müssen Sie Ihr .NET-Projekt einrichten und die Aspose.Words-Bibliothek einbinden.

Einrichten des Projekts

1. Neues Projekt erstellen:
   - Öffnen Sie Visual Studio.
   - Erstellen Sie ein neues Konsolen-App-Projekt (.NET Framework).

2. Installieren Sie Aspose.Words:
   - Öffnen Sie den NuGet-Paket-Manager (Tools > NuGet-Paket-Manager > NuGet-Pakete für Lösung verwalten).
   - Suchen Sie nach „Aspose.Words“ und installieren Sie es.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Diese Zeile legt das Verzeichnis fest, in dem Ihre Dokumente gespeichert werden. Ersetzen Sie`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

## Schritt 2: Initialisieren Sie das Dokument und den DocumentBuilder

 Als nächstes müssen Sie ein neues Word-Dokument erstellen und das`DocumentBuilder` Klasse, die beim Erstellen des Dokuments hilft.

Erstellen eines neuen Dokuments

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document doc = new Document();`erstellt ein neues Word-Dokument.
- `DocumentBuilder builder = new DocumentBuilder(doc);` initialisiert den DocumentBuilder mit dem erstellten Dokument.

## Schritt 3: Aktivieren Sie die Funktion „Am Raster ausrichten“ für Absätze

Aktivieren wir nun die Option „Am Raster ausrichten“ für einen Absatz in Ihrem Dokument.

Optimieren des Absatzlayouts

```csharp
// Optimieren Sie das Layout beim Eintippen asiatischer Schriftzeichen.
Paragraph par = doc.FirstSection.Body.FirstParagraph;
par.ParagraphFormat.SnapToGrid = true;
```

- `Paragraph par = doc.FirstSection.Body.FirstParagraph;` ruft den ersten Absatz des Dokuments ab.
- `par.ParagraphFormat.SnapToGrid = true;` aktiviert die Funktion „Am Raster ausrichten“ für den Absatz und stellt sicher, dass der Text am Raster ausgerichtet wird.

## Schritt 4: Dem Dokument Inhalt hinzufügen

Fügen wir dem Dokument einige Textinhalte hinzu, um zu sehen, wie die Funktion „Am Raster ausrichten“ in der Praxis funktioniert.

Schreiben von Texten

```csharp
builder.Writeln("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.");
```

- `builder.Writeln("Lorem ipsum dolor sit amet...");` schreibt den angegebenen Text in das Dokument und wendet dabei die Einstellung „Am Raster ausrichten“ an.

## Schritt 5: Am Raster ausrichten für Schriftarten aktivieren

Darüber hinaus können Sie die Funktion „Am Raster ausrichten“ für Schriftarten innerhalb eines Absatzes aktivieren, um eine einheitliche Zeichenausrichtung beizubehalten.

Festlegen der Schriftartausrichtung am Raster

```csharp
par.Runs[0].Font.SnapToGrid = true;
```

- `par.Runs[0].Font.SnapToGrid = true;` stellt sicher, dass die im Absatz verwendete Schriftart am Raster ausgerichtet ist.

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

Speichern des Dokuments

```csharp
doc.Save(dataDir + "Paragraph.SnapToGrid.docx");
```

- `doc.Save(dataDir + "Paragraph.SnapToGrid.docx");` speichert das Dokument unter dem angegebenen Namen im angegebenen Verzeichnis.

## Abschluss

Mit diesen Schritten haben Sie die Funktion „Am Raster ausrichten“ in einem Word-Dokument mithilfe von Aspose.Words für .NET erfolgreich aktiviert. Diese Funktion hilft dabei, ein ordentliches und organisiertes Layout beizubehalten, was besonders bei komplexen Dokumentstrukturen oder mehrsprachigen Inhalten nützlich ist.

## Häufig gestellte Fragen

### Was ist die Funktion „Am Raster ausrichten“?
Mit der Funktion „Am Raster ausrichten“ werden Text und Elemente an einem vordefinierten Raster ausgerichtet, wodurch eine einheitliche und strukturierte Dokumentformatierung gewährleistet wird.

### Kann ich „Am Raster ausrichten“ nur für bestimmte Abschnitte verwenden?
Ja, Sie können die Funktion „Am Raster ausrichten“ für bestimmte Absätze oder Abschnitte in Ihrem Dokument aktivieren.

### Ist für die Nutzung von Aspose.Words eine Lizenz erforderlich?
Ja. Sie können zwar eine temporäre Lizenz zur Evaluierung verwenden, für den vollständigen Zugriff wird jedoch eine Volllizenz empfohlen.

### Beeinträchtigt die Funktion „Am Raster ausrichten“ die Dokumentleistung?
Nein, die Aktivierung der Funktion „Am Raster ausrichten“ hat keine nennenswerten Auswirkungen auf die Dokumentleistung.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?
 Besuchen Sie die[Dokumentation](https://reference.aspose.com/words/net/) für detaillierte Informationen und Beispiele.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
