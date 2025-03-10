---
title: Inline-Code
linktitle: Inline-Code
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Inline-Codestile in Word-Dokumenten anwenden. Dieses Tutorial behandelt einzelne und mehrere Backticks zur Codeformatierung.
weight: 10
url: /de/net/working-with-markdown/inline-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inline-Code

## Einführung

Wenn Sie Word-Dokumente programmgesteuert erstellen oder bearbeiten, müssen Sie Text möglicherweise so formatieren, dass er Code ähnelt. Ob für Dokumentationen oder Codeausschnitte in einem Bericht, Aspose.Words für .NET bietet eine robuste Möglichkeit, Textformatierungen zu handhaben. In diesem Tutorial konzentrieren wir uns darauf, wie Sie mit Aspose.Words Inline-Codeformatierungen auf Text anwenden. Wir werden untersuchen, wie Sie benutzerdefinierte Formatierungen für einzelne und mehrere Backticks definieren und verwenden, damit Ihre Codesegmente in Ihren Dokumenten deutlich hervorstechen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie Aspose.Words in Ihrer .NET-Umgebung installiert haben. Sie können es von der[Aspose.Words für .NET-Releases-Seite](https://releases.aspose.com/words/net/).

2. Grundlegende Kenntnisse der .NET-Programmierung: Dieses Handbuch setzt voraus, dass Sie über grundlegende Kenntnisse der C#- und .NET-Programmierung verfügen.

3. Entwicklungsumgebung: Sie sollten eine .NET-Entwicklungsumgebung wie Visual Studio eingerichtet haben, in der Sie C#-Code schreiben und ausführen können.

## Namespaces importieren

Um Aspose.Words in Ihrem Projekt verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. So gehen Sie dabei vor:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Lassen Sie uns den Prozess in klare Schritte unterteilen:

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

 Zuerst müssen Sie ein neues Dokument erstellen und ein`DocumentBuilder` Instanz. Die`DocumentBuilder`Klasse hilft Ihnen, Inhalte hinzuzufügen und in einem Word-Dokument zu formatieren.

```csharp
// Initialisieren Sie DocumentBuilder mit dem neuen Dokument.
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 2: Inline-Code-Stil mit einem Backtick hinzufügen

In diesem Schritt definieren wir einen Stil für Inline-Code mit einem einzelnen Backtick. Dieser Stil formatiert Text so, dass er wie Inline-Code aussieht.

### Definieren Sie den Stil

```csharp
// Definieren Sie einen neuen Zeichenstil für Inline-Code mit einem Backtick.
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; // Eine typische Schriftart für Code.
inlineCode1BackTicks.Font.Size = 10.5; // Schriftgröße für den Inline-Code.
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; // Codetextfarbe.
inlineCode1BackTicks.Font.Bold = true; // Machen Sie den Codetext fett.
```

### Anwenden des Stils

Jetzt können Sie diesen Stil auf den Text in Ihrem Dokument anwenden.

```csharp
// Verwenden Sie den DocumentBuilder, um Text im Inline-Code-Stil einzufügen.
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## Schritt 3: Inline-Code-Stil mit drei Backticks hinzufügen

Als Nächstes definieren wir einen Stil für Inline-Code mit drei Backticks, der normalerweise für mehrzeilige Codeblöcke verwendet wird.

### Definieren Sie den Stil

```csharp
// Definieren Sie einen neuen Zeichenstil für Inline-Code mit drei Backticks.
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; // Einheitliche Schriftart für Code.
inlineCode3BackTicks.Font.Size = 10.5; // Schriftgröße für den Codeblock.
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; //Andere Farbe für bessere Sichtbarkeit.
inlineCode3BackTicks.Font.Bold = true; // Halten Sie es zur Hervorhebung fett.
```

### Anwenden des Stils

Wenden Sie diesen Stil auf Text an, um ihn als mehrzeiligen Codeblock zu formatieren.

```csharp
// Wenden Sie den Stil für den Codeblock an.
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## Abschluss

Das Formatieren von Text als Inline-Code in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert, wenn Sie die Schritte kennen. Indem Sie benutzerdefinierte Stile mit einzelnen oder mehreren Backticks definieren und anwenden, können Sie Ihre Codeausschnitte deutlich hervorheben. Diese Methode ist besonders nützlich für technische Dokumentationen oder alle Dokumente, bei denen die Lesbarkeit des Codes von entscheidender Bedeutung ist.

Experimentieren Sie mit verschiedenen Stilen und Formatierungsoptionen, um das für Ihre Anforderungen am besten geeignete Format zu finden. Aspose.Words bietet umfassende Flexibilität, sodass Sie das Erscheinungsbild Ihres Dokuments weitgehend anpassen können.

## Häufig gestellte Fragen

### Kann ich für Inline-Codestile unterschiedliche Schriftarten verwenden?
Ja, Sie können jede Schriftart verwenden, die Ihren Anforderungen entspricht. Schriftarten wie „Courier New“ werden aufgrund ihrer monospaceden Natur normalerweise für Code verwendet.

### Wie ändere ich die Farbe des Inline-Codetextes?
 Sie können die Farbe ändern, indem Sie die`Font.Color` Eigenschaft des Stils auf`System.Drawing.Color`.

### Kann ich mehrere Stile auf denselben Text anwenden?
In Aspose.Words können Sie immer nur einen Stil gleichzeitig anwenden. Wenn Sie Stile kombinieren müssen, sollten Sie einen neuen Stil erstellen, der alle gewünschten Formatierungen enthält.

### Wie wende ich Stile auf vorhandenen Text in einem Dokument an?
 Um Stile auf vorhandenen Text anzuwenden, müssen Sie zuerst den Text auswählen und dann den gewünschten Stil mithilfe der`Font.Style` Eigentum.

### Kann ich Aspose.Words für andere Dokumentformate verwenden?
Aspose.Words wurde speziell für Word-Dokumente entwickelt. Für andere Formate müssen Sie möglicherweise andere Bibliotheken verwenden oder die Dokumente in ein kompatibles Format konvertieren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
