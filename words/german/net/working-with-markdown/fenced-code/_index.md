---
title: Eingezäunter Code
linktitle: Eingezäunter Code
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET umzäunten Code und Info-Strings zu Word-Dokumenten hinzufügen. Schritt-für-Schritt-Anleitung enthalten. Verbessern Sie Ihre Fähigkeiten zur Dokumentformatierung.
weight: 10
url: /de/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eingezäunter Code

## Einführung

Hallo, Programmiererkollege! Heute tauchen wir in die Welt von Aspose.Words für .NET ein, um die Kunst zu meistern, Ihren Word-Dokumenten umzäunten Code und umzäunten Code mit Info-Strings hinzuzufügen. Stellen Sie sich Ihr Word-Dokument als Leinwand vor, und Sie, der Künstler, malen mit der Präzision eines erfahrenen Entwicklers. Mit Aspose.Words erhalten Sie die Möglichkeit, Ihre Dokumente programmgesteuert mit strukturierten, formatierten Codeblöcken zu verbessern, sodass Ihre technischen Dokumente vor Professionalität und Klarheit erstrahlen.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

- Grundkenntnisse in C#: Allgemeine Kenntnisse in C# helfen Ihnen, die Konzepte schnell zu erfassen.
-  Aspose.Words für .NET: Sie müssen Aspose.Words für .NET installiert haben. Wenn Sie es noch nicht haben, holen Sie es sich[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder jede andere C#-IDE, mit der Sie vertraut sind.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Das ist so, als würden Sie alle Ihre Werkzeuge zusammentragen, bevor Sie ein Projekt starten.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Lassen Sie uns den Prozess nun Schritt für Schritt aufschlüsseln.

## Schritt 1: Einrichten Ihres Projekts

Bevor wir in unserem Word-Dokument schöne, formatierte Codeblöcke erstellen können, müssen wir in Visual Studio ein neues Projekt einrichten.

1. Erstellen Sie ein neues Projekt: Öffnen Sie Visual Studio und erstellen Sie eine neue C#-Konsolenanwendung.
2. Aspose.Words-Referenz hinzufügen: Installieren Sie Aspose.Words über den NuGet-Paket-Manager. Sie können dies tun, indem Sie im Solution Explorer mit der rechten Maustaste auf Ihr Projekt klicken, „NuGet-Pakete verwalten“ auswählen und nach Aspose.Words suchen.

## Schritt 2: Initialisieren Sie den DocumentBuilder

Nachdem Ihr Projekt nun eingerichtet ist, initialisieren wir den DocumentBuilder, der unser Haupttool zum Hinzufügen von Inhalten zum Word-Dokument sein wird.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 3: Erstellen Sie einen Stil für eingezäunten Code

Um umzäunten Code hinzuzufügen, müssen wir zuerst einen Stil erstellen. Betrachten Sie dies als Festlegen des Designs für unseren Codeblock.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Schritt 4: Fügen Sie dem Dokument abgeschirmten Code hinzu

Nachdem unser Stil fertig ist, können wir dem Dokument jetzt einen eingezäunten Codeblock hinzufügen.

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

Herzlichen Glückwunsch! Sie haben gerade mithilfe von Aspose.Words für .NET umzäunte Codeblöcke und umzäunten Code mit Info-Strings zu Ihren Word-Dokumenten hinzugefügt. Dies ist nur die Spitze des Eisbergs. Mit Aspose.Words können Sie Ihre Dokumentverarbeitung auf ein neues Niveau automatisieren und verbessern. Erkunden Sie weiter und viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können.

### Kann ich Aspose.Words mit anderen Programmiersprachen verwenden?
Aspose.Words unterstützt hauptsächlich .NET-Sprachen, es sind jedoch Versionen für Java, Python und andere Sprachen verfügbar.

### Ist die Nutzung von Aspose.Words kostenlos?
 Aspose.Words ist ein kommerzielles Produkt, aber Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.aspose.com/)um seine Funktionen zu erkunden.

### Wie kann ich Support für Aspose.Words erhalten?
 Sie können Unterstützung von der Aspose-Community und den Entwicklern erhalten[Hier](https://forum.aspose.com/c/words/8).

### Welche weiteren Funktionen bietet Aspose.Words?
Aspose.Words bietet eine breite Palette an Funktionen, darunter Dokumentkonvertierung, vorlagenbasierte Dokumenterstellung, Berichterstellung und vieles mehr.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
