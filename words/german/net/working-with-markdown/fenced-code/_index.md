---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET geschützten Code und Infostrings in Word-Dokumente einfügen. Schritt-für-Schritt-Anleitung inklusive. Verbessern Sie Ihre Kenntnisse zur Dokumentformatierung."
"linktitle": "Eingezäunter Code"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Eingezäunter Code"
"url": "/de/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eingezäunter Code

## Einführung

Hallo Programmierer! Heute tauchen wir in die Welt von Aspose.Words für .NET ein, um die Kunst zu meistern, Ihren Word-Dokumenten Fence Code und Fence Code mit Infostrings hinzuzufügen. Stellen Sie sich Ihr Word-Dokument als Leinwand vor, und Sie, der Künstler, malen mit der Präzision eines erfahrenen Entwicklers. Mit Aspose.Words können Sie Ihre Dokumente programmatisch mit strukturierten, formatierten Codeblöcken erweitern und Ihren technischen Dokumenten Professionalität und Klarheit verleihen.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

- Grundkenntnisse in C#: Ein allgemeines Verständnis von C# hilft Ihnen, die Konzepte schnell zu erfassen.
- Aspose.Words für .NET: Sie benötigen Aspose.Words für .NET. Falls Sie es noch nicht haben, laden Sie es herunter. [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder jede andere C#-IDE, mit der Sie vertraut sind.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren. Das ist so, als würden Sie vor dem Start eines Projekts alle Ihre Werkzeuge zusammensuchen.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Lassen Sie uns den Prozess nun Schritt für Schritt aufschlüsseln.

## Schritt 1: Einrichten Ihres Projekts

Bevor wir schöne, formatierte Codeblöcke in unserem Word-Dokument erstellen können, müssen wir in Visual Studio ein neues Projekt einrichten.

1. Erstellen Sie ein neues Projekt: Öffnen Sie Visual Studio und erstellen Sie eine neue C#-Konsolenanwendung.
2. Aspose.Words-Referenz hinzufügen: Installieren Sie Aspose.Words über den NuGet-Paketmanager. Klicken Sie dazu im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“ und suchen Sie nach Aspose.Words.

## Schritt 2: Initialisieren Sie den DocumentBuilder

Nachdem Ihr Projekt nun eingerichtet ist, initialisieren wir den DocumentBuilder, der unser Haupttool zum Hinzufügen von Inhalten zum Word-Dokument sein wird.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 3: Erstellen Sie einen Stil für eingezäunten Code

Um eingezäunten Code hinzuzufügen, müssen wir zunächst einen Stil erstellen. Stellen Sie sich das so vor, als würden Sie das Design für unseren Codeblock festlegen.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Schritt 4: Fügen Sie dem Dokument abgeschirmten Code hinzu

Da unser Stil nun fertig ist, können wir dem Dokument einen eingezäunten Codeblock hinzufügen.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Schritt 5: Erstellen Sie einen Stil für eingezäunten Code mit Info-String

Manchmal möchten Sie möglicherweise die Programmiersprache angeben oder Ihrem Codeblock zusätzliche Informationen hinzufügen. Lassen Sie uns dafür einen Stil erstellen.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Schritt 6: Fügen Sie dem Dokument eingezäunten Code mit Info-String hinzu

Fügen wir nun einen eingezäunten Codeblock mit einer Infozeichenfolge hinzu, um anzuzeigen, dass es sich um C#-Code handelt.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Abschluss

Herzlichen Glückwunsch! Sie haben Ihren Word-Dokumenten mit Aspose.Words für .NET soeben Codeblöcke und Code mit Infostrings hinzugefügt. Das ist nur die Spitze des Eisbergs. Mit Aspose.Words können Sie Ihre Dokumentenverarbeitung automatisieren und optimieren. Entdecken Sie weiter und viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können.

### Kann ich Aspose.Words mit anderen Programmiersprachen verwenden?
Aspose.Words unterstützt hauptsächlich .NET-Sprachen, es sind jedoch Versionen für Java, Python und andere Sprachen verfügbar.

### Ist die Nutzung von Aspose.Words kostenlos?
Aspose.Words ist ein kommerzielles Produkt, aber Sie können eine kostenlose Testversion herunterladen [Hier](https://releases.aspose.com/) um seine Funktionen zu erkunden.

### Wie kann ich Support für Aspose.Words erhalten?
Sie können Unterstützung von der Aspose-Community und den Entwicklern erhalten [Hier](https://forum.aspose.com/c/words/8).

### Welche weiteren Funktionen bietet Aspose.Words?
Aspose.Words bietet eine breite Palette an Funktionen, darunter Dokumentkonvertierung, vorlagenbasierte Dokumenterstellung, Berichterstellung und vieles mehr.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}