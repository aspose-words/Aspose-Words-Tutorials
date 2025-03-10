---
title: In Word-Dokument zu Kopf- und Fußzeilen verschieben
linktitle: In Word-Dokument zu Kopf- und Fußzeilen verschieben
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET zu Kopf- und Fußzeilen in einem Word-Dokument wechseln. Verbessern Sie Ihre Fähigkeiten zur Dokumenterstellung.
weight: 10
url: /de/net/add-content-using-documentbuilder/move-to-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# In Word-Dokument zu Kopf- und Fußzeilen verschieben

## Einführung

Wenn es um die programmgesteuerte Erstellung und Verwaltung von Word-Dokumenten geht, ist Aspose.Words für .NET ein leistungsstarkes Tool, das Ihnen viel Zeit und Mühe ersparen kann. In diesem Artikel erfahren Sie, wie Sie mit Aspose.Words für .NET zu Kopf- und Fußzeilen in einem Word-Dokument wechseln. Diese Funktion ist wichtig, wenn Sie den Kopf- oder Fußzeilenabschnitten Ihres Dokuments bestimmte Inhalte hinzufügen müssen. Egal, ob Sie einen Bericht, eine Rechnung oder ein anderes Dokument erstellen, das eine professionelle Note erfordert, das Verständnis der Bearbeitung von Kopf- und Fußzeilen ist von entscheidender Bedeutung.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles eingerichtet haben:

1. **Aspose.Words for .NET** : Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET haben. Sie können sie von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. **Development Environment**Sie benötigen eine Entwicklungsumgebung wie Visual Studio.
3. **Basic Knowledge of C#**: Das Verständnis der Grundlagen der C#-Programmierung wird Ihnen helfen, den Schritten zu folgen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Dieser Schritt ist entscheidend für den Zugriff auf die von Aspose.Words für .NET bereitgestellten Klassen und Methoden.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System;
```

Lassen Sie uns den Prozess in einfache Schritte unterteilen. Jeder Schritt wird klar erklärt, damit Sie verstehen, was der Code macht und warum.

## Schritt 1: Initialisieren Sie das Dokument

Der erste Schritt besteht darin, ein neues Dokument und ein DocumentBuilder-Objekt zu initialisieren. Mit der DocumentBuilder-Klasse können Sie das Dokument erstellen und bearbeiten.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Schritt erstellen Sie eine neue Instanz des`Document` Klasse und die`DocumentBuilder` Klasse. Die`dataDir` Die Variable wird verwendet, um das Verzeichnis anzugeben, in dem Sie das Dokument speichern möchten.

## Schritt 2: Seiteneinrichtung konfigurieren

Als nächstes müssen wir angeben, dass die Kopf- und Fußzeilen für die erste sowie die geraden und ungeraden Seiten unterschiedlich sein sollen.

```csharp
//Geben Sie an, dass Kopf- und Fußzeilen für die erste sowie die geraden und ungeraden Seiten unterschiedlich sein sollen.
builder.PageSetup.DifferentFirstPageHeaderFooter = true;
builder.PageSetup.OddAndEvenPagesHeaderFooter = true;
```

Diese Einstellungen stellen sicher, dass Sie für unterschiedliche Seitentypen eindeutige Kopf- und Fußzeilen haben können.

## Schritt 3: Zur Kopf-/Fußzeile wechseln und Inhalt hinzufügen

Gehen wir nun zu den Kopf- und Fußzeilenabschnitten und fügen etwas Inhalt hinzu.

```csharp
// Erstellen Sie die Kopfzeilen.
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.Write("Header for the first page");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderEven);
builder.Write("Header for even pages");
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);
builder.Write("Header for all other pages");
```

 In diesem Schritt verwenden wir die`MoveToHeaderFooter` -Methode, um zum gewünschten Kopf- oder Fußzeilenabschnitt zu navigieren. Die`Write` Die Methode wird dann verwendet, um diesen Abschnitten Text hinzuzufügen.

## Schritt 4: Inhalt zum Dokumenttext hinzufügen

Um die Kopf- und Fußzeilen zu demonstrieren, fügen wir dem Hauptteil des Dokuments etwas Inhalt hinzu und erstellen ein paar Seiten.

```csharp
// Erstellen Sie zwei Seiten im Dokument.
builder.MoveToSection(0);
builder.Writeln("Page1");
builder.InsertBreak(BreakType.PageBreak);
builder.Writeln("Page2");
```

Hier fügen wir dem Dokument Text hinzu und fügen einen Seitenumbruch ein, um eine zweite Seite zu erstellen.

## Schritt 5: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx");
```

Diese Codezeile speichert das Dokument mit dem Namen "AddContentUsingDocumentBuilder.MoveToHeadersFooters.docx" im angegebenen Verzeichnis.

## Abschluss

 Wenn Sie diese Schritte befolgen, können Sie Kopf- und Fußzeilen in einem Word-Dokument mit Aspose.Words für .NET ganz einfach bearbeiten. Dieses Tutorial behandelt die Grundlagen, aber Aspose.Words bietet eine breite Palette an Funktionen für komplexere Dokumentbearbeitungen. Zögern Sie nicht, die[Dokumentation](https://reference.aspose.com/words/net/) für erweiterte Funktionen.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert mit C# zu erstellen, zu ändern und zu konvertieren.

### Kann ich Kopf- und Fußzeilen Bilder hinzufügen?
 Ja, Sie können Bilder zu Kopf- und Fußzeilen hinzufügen, indem Sie`DocumentBuilder.InsertImage` Verfahren.

### Ist es möglich, für jeden Abschnitt unterschiedliche Kopf- und Fußzeilen zu haben?
 Absolut! Sie können für jeden Abschnitt einzigartige Kopf- und Fußzeilen haben, indem Sie verschiedene`HeaderFooterType` für jeden Abschnitt.

### Wie erstelle ich komplexere Layouts in Kopf- und Fußzeilen?
Sie können Tabellen, Bilder und verschiedene Formatierungsoptionen von Aspose.Words verwenden, um komplexe Layouts zu erstellen.

### Wo finde ich weitere Beispiele und Tutorials?
 Schauen Sie sich die[Dokumentation](https://reference.aspose.com/words/net/) und die[Support-Forum](https://forum.aspose.com/c/words/8) für weitere Beispiele und Community-Unterstützung.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
