---
"description": "Erfahren Sie in einer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET ActiveX-Steuerelementeigenschaften aus Word-Dateien lesen. Verbessern Sie Ihre Fähigkeiten zur Dokumentautomatisierung."
"linktitle": "Active XControl-Eigenschaften aus Word-Datei lesen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Active XControl-Eigenschaften aus Word-Datei lesen"
"url": "/de/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Active XControl-Eigenschaften aus Word-Datei lesen

## Einführung

Im digitalen Zeitalter ist Automatisierung der Schlüssel zur Produktivitätssteigerung. Wenn Sie mit Word-Dokumenten arbeiten, die ActiveX-Steuerelemente enthalten, müssen Sie deren Eigenschaften möglicherweise für verschiedene Zwecke lesen. ActiveX-Steuerelemente wie Kontrollkästchen und Schaltflächen können wichtige Daten enthalten. Mit Aspose.Words für .NET können Sie diese Daten effizient programmgesteuert extrahieren und bearbeiten.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
2. Visual Studio oder eine beliebige C#-IDE: Zum Schreiben und Ausführen Ihres Codes.
3. Ein Word-Dokument mit ActiveX-Steuerelementen: Zum Beispiel „ActiveX-Steuerelemente.docx“.
4. Grundkenntnisse in C#: Um den Kurs erfolgreich absolvieren zu können, sind Kenntnisse in der C#-Programmierung erforderlich.

## Namespaces importieren

Importieren wir zunächst die erforderlichen Namespaces, um mit Aspose.Words für .NET zu arbeiten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Schritt 1: Laden Sie das Word-Dokument

Zu Beginn müssen Sie das Word-Dokument laden, das die ActiveX-Steuerelemente enthält.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Schritt 2: Initialisieren einer Zeichenfolge zum Speichern von Eigenschaften

Initialisieren Sie als Nächstes eine leere Zeichenfolge, um die Eigenschaften der ActiveX-Steuerelemente zu speichern.

```csharp
string properties = "";
```

## Schritt 3: Durch die Formen im Dokument iterieren

Wir müssen alle Formen im Dokument durchlaufen, um die ActiveX-Steuerelemente zu finden.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Verarbeiten des ActiveX-Steuerelements
    }
}
```

## Schritt 4: Eigenschaften aus ActiveX-Steuerelementen extrahieren

Überprüfen Sie innerhalb der Schleife, ob das Steuerelement ein Forms2OleControl ist. Wenn ja, konvertieren Sie es und extrahieren Sie die Eigenschaften.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Schritt 5: Gesamtzahl der ActiveX-Steuerelemente zählen

Zählen Sie nach dem Durchlaufen aller Formen die Gesamtzahl der gefundenen ActiveX-Steuerelemente.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Schritt 6: Anzeigen der Eigenschaften

Drucken Sie abschließend die extrahierten Eigenschaften auf der Konsole aus.

```csharp
Console.WriteLine("\n" + properties);
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie ActiveX-Steuerelementeigenschaften aus einem Word-Dokument mit Aspose.Words für .NET lesen. Dieses Tutorial behandelte das Laden eines Dokuments, das Durchlaufen von Formen und das Extrahieren von Eigenschaften aus ActiveX-Steuerelementen. Mit diesen Schritten können Sie die Extraktion wichtiger Daten aus Ihren Word-Dokumenten automatisieren und so Ihre Workflow-Effizienz steigern.

## Häufig gestellte Fragen

### Was sind ActiveX-Steuerelemente in Word-Dokumenten?
ActiveX-Steuerelemente sind interaktive Objekte, die in Word-Dokumente eingebettet sind, wie etwa Kontrollkästchen, Schaltflächen und Textfelder, die zum Erstellen von Formularen und Automatisieren von Aufgaben verwendet werden.

### Kann ich die Eigenschaften von ActiveX-Steuerelementen mit Aspose.Words für .NET ändern?
Ja, mit Aspose.Words für .NET können Sie die Eigenschaften von ActiveX-Steuerelementen programmgesteuert ändern.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
Aspose.Words für .NET bietet eine kostenlose Testversion an, für die weitere Nutzung ist jedoch eine Lizenz erforderlich. Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/).

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen außer C# verwenden?
Ja, Aspose.Words für .NET kann mit jeder .NET-Sprache verwendet werden, einschließlich VB.NET und F#.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
Eine ausführliche Dokumentation finden Sie [Hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}