---
title: Bidi-Markierungen in Word-Dokument einfügen
linktitle: Bidi-Markierungen in Word-Dokument einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Handbuch, wie Sie mit Aspose.Words für .NET bidirektionale (Bidi) Markierungen in Word-Dokumente einfügen. Stellen Sie bei mehrsprachigen Inhalten die richtige Textrichtung sicher.
weight: 10
url: /de/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bidi-Markierungen in Word-Dokument einfügen

## Einführung

In der Welt der Dokumentenverarbeitung kann bidirektionaler (Bidi) Text oft etwas schwierig zu handhaben sein. Dies gilt insbesondere bei Sprachen mit unterschiedlichen Textrichtungen, wie Arabisch oder Hebräisch. Glücklicherweise erleichtert Aspose.Words für .NET die Handhabung solcher Szenarien. In diesem Tutorial zeigen wir Ihnen, wie Sie mit Aspose.Words für .NET Bidi-Markierungen zu einem Word-Dokument hinzufügen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET: Sie müssen Aspose.Words für .NET installiert haben. Sie können es herunterladen von der[Aspose Downloads-Seite](https://releases.aspose.com/words/net/).
2. .NET Framework oder .NET Core: Stellen Sie sicher, dass Sie zum Ausführen der Beispiele eine kompatible .NET-Umgebung eingerichtet haben.
3. Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# und den grundlegenden Vorgängen in .NET.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. So können Sie sie in Ihr Projekt einbinden:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang des Hinzufügens von Bidi-Markierungen in einem Word-Dokument in klare Schritte unterteilen. Jeder Schritt führt Sie durch den Code und seinen Zweck.

## Schritt 1: Richten Sie Ihr Dokument ein

 Erstellen Sie zunächst eine neue Instanz des`Document` Klasse und eine`DocumentBuilder` , um dem Dokument Inhalt hinzuzufügen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und fügen Sie Inhalt hinzu
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Schritt initialisieren Sie ein neues Word-Dokument und richten eine`DocumentBuilder` um das Einfügen von Inhalten zu erleichtern.

## Schritt 2: Fügen Sie Ihrem Dokument Inhalt hinzu

Fügen Sie als Nächstes Text zu Ihrem Dokument hinzu. Hier fügen wir Text in verschiedenen Sprachen hinzu, um die Verarbeitung von Bidi-Text zu veranschaulichen.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Hier fügen wir zunächst eine standardmäßige englische Phrase hinzu. Dann aktivieren wir die Bidi-Textformatierung für den nachfolgenden Text, der auf Hebräisch und Arabisch geschrieben ist. Dies zeigt, wie bidirektionaler Text integriert wird.

## Schritt 3: Speicheroptionen für Bidi-Marken konfigurieren

 Um sicherzustellen, dass die Bidi-Marken korrekt im Dokument gespeichert werden, müssen Sie die`TxtSaveOptions` und aktivieren Sie die`AddBidiMarks` Option.

```csharp
// Bidi-Markierungen hinzufügen
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 In diesem Schritt erstellen wir eine Instanz von`TxtSaveOptions` und legen Sie die`AddBidiMarks`Eigentum an`true`. Dadurch wird sichergestellt, dass die Bidi-Markierungen beim Speichern des Dokuments als Textdatei berücksichtigt werden.

## Abschluss

Das Hinzufügen von Bidi-Markierungen zu Ihren Word-Dokumenten kann ein entscheidender Schritt sein, wenn Sie mit mehrsprachigen Inhalten arbeiten, die Sprachen mit unterschiedlichen Textrichtungen enthalten. Mit Aspose.Words für .NET ist dieser Vorgang unkompliziert und effizient. Indem Sie die oben beschriebenen Schritte befolgen, können Sie sicherstellen, dass Ihre Dokumente Bidi-Text korrekt darstellen, was die Lesbarkeit und Genauigkeit verbessert.

## Häufig gestellte Fragen

### Was sind Bidi-Marken und warum sind sie wichtig?
Bidi-Markierungen sind Sonderzeichen, mit denen die Textrichtung in Dokumenten gesteuert wird. Sie sind wichtig für die korrekte Anzeige von Sprachen, die von rechts nach links gelesen werden, wie Arabisch und Hebräisch.

### Kann ich Aspose.Words für .NET verwenden, um andere Arten von Textrichtungsproblemen zu behandeln?
Ja, Aspose.Words für .NET bietet umfassende Unterstützung für verschiedene Textrichtungs- und Formatierungsanforderungen, einschließlich Sprachen, die von rechts nach links und von links nach rechts verlaufen.

### Ist es möglich, die Bidi-Formatierung nur auf bestimmte Teile eines Dokuments anzuwenden?
Ja, Sie können die Bidi-Formatierung nach Bedarf auf bestimmte Absätze oder Abschnitte Ihres Dokuments anwenden.

### In welchen Formaten kann ich das Dokument mit Bidi-Markierungen speichern?
Im angegebenen Beispiel wird das Dokument als Textdatei gespeichert. Aspose.Words unterstützt jedoch auch das Speichern von Dokumenten in verschiedenen Formaten unter Beibehaltung von Bidi-Markierungen.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?
 Weitere Informationen zu Aspose.Words für .NET finden Sie im[Aspose-Dokumentation](https://reference.aspose.com/words/net/) und greifen Sie auf die[Support Forum](https://forum.aspose.com/c/words/8) für weitere Hilfe.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
