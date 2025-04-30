---
"description": "Erfahren Sie in dieser Anleitung, wie Sie mit Aspose.Words für .NET bidirektionale (Bidi) Markierungen in Word-Dokumenten hinzufügen. Stellen Sie die korrekte Textrichtung für mehrsprachige Inhalte sicher."
"linktitle": "Bidi-Markierungen in Word-Dokumente einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Bidi-Markierungen in Word-Dokumente einfügen"
"url": "/de/net/programming-with-txtsaveoptions/add-bidi-marks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bidi-Markierungen in Word-Dokumente einfügen

## Einführung

In der Dokumentenverarbeitung ist bidirektionaler (Bidi) Text oft schwierig zu handhaben. Dies gilt insbesondere für Sprachen mit unterschiedlichen Textrichtungen, wie Arabisch oder Hebräisch. Glücklicherweise erleichtert Aspose.Words für .NET die Handhabung solcher Szenarien. In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET Bidi-Markierungen zu einem Word-Dokument hinzufügen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET: Sie müssen Aspose.Words für .NET installiert haben. Sie können es von der [Aspose-Downloadseite](https://releases.aspose.com/words/net/).
2. .NET Framework oder .NET Core: Stellen Sie sicher, dass Sie zum Ausführen der Beispiele eine kompatible .NET-Umgebung eingerichtet haben.
3. Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# und den grundlegenden Vorgängen in .NET.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. So können Sie sie in Ihr Projekt einbinden:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Wir unterteilen den Prozess des Hinzufügens von Bidi-Markierungen in ein Word-Dokument in klare Schritte. Jeder Schritt führt Sie durch den Code und seinen Zweck.

## Schritt 1: Richten Sie Ihr Dokument ein

Beginnen Sie mit der Erstellung einer neuen Instanz des `Document` Klasse und eine `DocumentBuilder` um dem Dokument Inhalt hinzuzufügen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und fügen Sie Inhalte hinzu
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In diesem Schritt initialisieren Sie ein neues Word-Dokument und richten eine `DocumentBuilder` um das Einfügen von Inhalten zu erleichtern.

## Schritt 2: Fügen Sie Ihrem Dokument Inhalt hinzu

Fügen Sie als Nächstes Text zu Ihrem Dokument hinzu. Hier fügen wir Text in verschiedenen Sprachen hinzu, um die Verarbeitung von Bidi-Text zu veranschaulichen.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Hier fügen wir zunächst eine englische Standardphrase hinzu. Anschließend aktivieren wir die Bidi-Formatierung für den nachfolgenden Text, der auf Hebräisch und Arabisch verfasst ist. Dies zeigt, wie bidirektionaler Text integriert wird.

## Schritt 3: Konfigurieren Sie die Speicheroptionen für Bidi-Marken

Um sicherzustellen, dass die Bidi-Marken korrekt im Dokument gespeichert werden, müssen Sie die `TxtSaveOptions` und aktivieren Sie die `AddBidiMarks` Option.

```csharp
// Bidi-Markierungen hinzufügen
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

In diesem Schritt erstellen wir eine Instanz von `TxtSaveOptions` und legen Sie die `AddBidiMarks` Eigentum zu `true`Dadurch wird sichergestellt, dass die Bidi-Markierungen beim Speichern des Dokuments als Textdatei berücksichtigt werden.

## Abschluss

Das Hinzufügen von Bidi-Markierungen zu Ihren Word-Dokumenten kann ein entscheidender Schritt sein, wenn Sie mehrsprachige Inhalte mit unterschiedlichen Textrichtungen bearbeiten. Mit Aspose.Words für .NET ist dieser Prozess unkompliziert und effizient. Indem Sie die oben beschriebenen Schritte befolgen, stellen Sie sicher, dass Ihre Dokumente Bidi-Text korrekt darstellen und so Lesbarkeit und Genauigkeit verbessern.

## Häufig gestellte Fragen

### Was sind Bidi-Marken und warum sind sie wichtig?
Bidi-Markierungen sind Sonderzeichen zur Steuerung der Textrichtung in Dokumenten. Sie sind wichtig für die korrekte Darstellung von Sprachen, die von rechts nach links gelesen werden, wie Arabisch und Hebräisch.

### Kann ich Aspose.Words für .NET verwenden, um andere Arten von Textrichtungsproblemen zu behandeln?
Ja, Aspose.Words für .NET bietet umfassende Unterstützung für verschiedene Textrichtungs- und Formatierungsanforderungen, einschließlich Sprachen, die von rechts nach links und von links nach rechts geschrieben werden.

### Ist es möglich, die Bidi-Formatierung nur auf bestimmte Teile eines Dokuments anzuwenden?
Ja, Sie können die Bidi-Formatierung nach Bedarf auf bestimmte Absätze oder Abschnitte Ihres Dokuments anwenden.

### In welchen Formaten kann ich das Dokument mit Bidi-Markierungen speichern?
Im angegebenen Beispiel wird das Dokument als Textdatei gespeichert. Aspose.Words unterstützt jedoch auch das Speichern von Dokumenten in verschiedenen Formaten unter Beibehaltung der Bidi-Markierungen.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?
Sie können mehr über Aspose.Words für .NET erfahren durch die [Aspose-Dokumentation](https://reference.aspose.com/words/net/) und greifen Sie auf die [Support-Forum](https://forum.aspose.com/c/words/8) für zusätzliche Hilfe.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}