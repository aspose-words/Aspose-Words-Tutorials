---
title: Zeilenabstand für Schriftart abrufen
linktitle: Zeilenabstand für Schriftart abrufen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET den Zeilenabstand von Schriftarten festlegen. Perfekt für Entwickler.
weight: 10
url: /de/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zeilenabstand für Schriftart abrufen

## Einführung

Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Sie Word-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können. Eine häufige Aufgabe, die Sie möglicherweise ausführen müssen, ist das Abrufen des Zeilenabstands einer bestimmten Schriftart in einem Dokument. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess und stellen sicher, dass Sie mit Aspose.Words für .NET problemlos den Zeilenabstand einer Schriftart ermitteln können. 

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1.  Aspose.Words für .NET-Bibliothek: Laden Sie die neueste Version herunter und installieren Sie sie von[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine IDE wie Visual Studio eingerichtet haben.
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über Grundkenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Diese Namespaces ermöglichen Ihnen den Zugriff auf die Aspose.Words-Funktionen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns den Vorgang zum Festlegen des Zeilenabstands einer Schrift in einfache, überschaubare Schritte aufteilen.

## Schritt 1: Neues Dokument erstellen

Der erste Schritt besteht darin, mit Aspose.Words für .NET eine neue Word-Dokumentinstanz zu erstellen.

```csharp
Document doc = new Document();
```

## Schritt 2: DocumentBuilder initialisieren

Als nächstes müssen wir den`DocumentBuilder` Objekt. Dieses Objekt hilft uns, den Dokumentinhalt zu erstellen und zu bearbeiten.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 3: Festlegen der Schrifteigenschaften

Nun legen wir die Schrifteigenschaften für den Text fest, den wir einfügen möchten. Für dieses Beispiel verwenden wir die Schriftart „Calibri“.

```csharp
builder.Font.Name = "Calibri";
```

## Schritt 4: Text in das Dokument schreiben

 Mit dem`DocumentBuilder` Objekt, schreiben Sie einen Text in das Dokument. Dieser Text verwendet die Schrifteigenschaften, die wir im vorherigen Schritt festgelegt haben.

```csharp
builder.Writeln("Sample Text");
```

## Schritt 5: Abrufen des Font-Objekts

Um den Zeilenabstand zu erhalten, müssen wir auf das Schriftobjekt des gerade hinzugefügten Textes zugreifen. Dies können wir tun, indem wir durch die Dokumentstruktur bis zum ersten Absatzlauf navigieren.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Schritt 6: Den Zeilenabstand ermitteln

Schließlich rufen wir den Zeilenabstand aus dem Schriftobjekt ab und drucken ihn auf der Konsole.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Abschluss

Und da haben Sie es! Das Abrufen des Schriftzeilenabstands mit Aspose.Words für .NET ist unkompliziert, wenn Sie es in diese einfachen Schritte aufteilen. Egal, ob Sie ein neues Dokument erstellen oder mit einem vorhandenen arbeiten, Aspose.Words bietet alle Tools, die Sie zum effizienten Verwalten von Schrifteigenschaften benötigen.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert mit C# zu erstellen, zu bearbeiten und zu konvertieren.

### Kann ich Aspose.Words für .NET in anderen .NET-Sprachen verwenden?
Ja, Sie können Aspose.Words für .NET mit jeder .NET-Sprache verwenden, einschließlich VB.NET und F#.

### Wie kann ich Aspose.Words für .NET herunterladen?
 Sie können die neueste Version von Aspose.Words für .NET herunterladen von[Hier](https://releases.aspose.com/words/net/).

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
 Ja, Sie können eine kostenlose Testversion erhalten von[Hier](https://releases.aspose.com/).

### Wo finde ich die Dokumentation für Aspose.Words für .NET?
 Die Dokumentation für Aspose.Words für .NET ist verfügbar[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
