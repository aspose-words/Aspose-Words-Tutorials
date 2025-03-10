---
title: Vergleichsgranularität im Word-Dokument
linktitle: Vergleichsgranularität im Word-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie mehr über die Funktion „Granularität vergleichen“ in Word-Dokumenten von Aspose.Words für .NET, mit der Dokumente Zeichen für Zeichen verglichen und die vorgenommenen Änderungen gemeldet werden können.
weight: 10
url: /de/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vergleichsgranularität im Word-Dokument

Hier ist eine Schritt-für-Schritt-Anleitung zur Erläuterung des folgenden C#-Quellcodes, der die Funktion „Granularität in Word-Dokumenten vergleichen“ von Aspose.Words für .NET verwendet.

## Schritt 1: Einführung

Mit der Funktion „Granularität vergleichen“ von Aspose.Words für .NET können Sie Dokumente auf Zeichenebene vergleichen. Dies bedeutet, dass jedes Zeichen verglichen wird und Änderungen entsprechend gemeldet werden.

## Schritt 2: Einrichten der Umgebung

Bevor Sie beginnen, müssen Sie Ihre Entwicklungsumgebung für die Arbeit mit Aspose.Words für .NET einrichten. Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben und über ein geeignetes C#-Projekt verfügen, in das Sie den Code einbetten können.

## Schritt 3: Erforderliche Assemblys hinzufügen

Um die Funktion „Granularität vergleichen“ von Aspose.Words für .NET zu verwenden, müssen Sie Ihrem Projekt die erforderlichen Assemblys hinzufügen. Stellen Sie sicher, dass Ihr Projekt über die richtigen Verweise auf Aspose.Words verfügt.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Schritt 4: Dokumente erstellen

In diesem Schritt erstellen wir mit der Klasse DocumentBuilder zwei Dokumente. Diese Dokumente werden für den Vergleich verwendet.

```csharp
// Erstellen Sie Dokument A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Erstellen Sie Dokument B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Schritt 5: Vergleichsoptionen konfigurieren

In diesem Schritt konfigurieren wir die Vergleichsoptionen, um die Vergleichsgranularität anzugeben. Hier verwenden wir die Granularität auf Zeichenebene.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Schritt 6: Dokumentenvergleich

Vergleichen wir nun die Dokumente mit der Compare-Methode der Document-Klasse. Änderungen werden im Dokument A gespeichert.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 Der`Compare`Methode vergleicht Dokument A mit Dokument B und speichert die Änderungen an Dokument A. Sie können den Namen des Autors und das Datum des Vergleichs als Referenz angeben.

## Abschluss

In diesem Artikel haben wir die Funktion „Granularität vergleichen“ von Aspose.Words für .NET untersucht. Mit dieser Funktion können Sie Dokumente auf Zeichenebene vergleichen und Änderungen melden. Sie können dieses Wissen nutzen, um in Ihren Projekten detaillierte Dokumentvergleiche durchzuführen.

### Beispielquellcode für Vergleichsgranularität mit Aspose.Words für .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Abschluss

In diesem Tutorial haben wir die Funktion „Vergleichsgranularität“ von Aspose.Words für .NET untersucht. Mit dieser Funktion können Sie den Detaillierungsgrad beim Vergleichen von Dokumenten festlegen. Durch die Auswahl verschiedener Granularitätsstufen können Sie je nach Ihren spezifischen Anforderungen detaillierte Vergleiche auf Zeichen-, Wort- oder Blockebene durchführen. Aspose.Words für .NET bietet eine flexible und leistungsstarke Funktion zum Vergleichen von Dokumenten, mit der sich Unterschiede in Dokumenten mit unterschiedlichen Granularitätsstufen leicht erkennen lassen.

### Häufig gestellte Fragen

#### F: Was ist der Zweck der Verwendung der Vergleichsgranularität in Aspose.Words für .NET?

A: Die Vergleichsgranularität in Aspose.Words für .NET ermöglicht es Ihnen, den Detaillierungsgrad beim Vergleichen von Dokumenten festzulegen. Mit dieser Funktion können Sie Dokumente auf verschiedenen Ebenen vergleichen, z. B. auf Zeichenebene, Wortebene oder sogar Blockebene. Jede Granularitätsebene bietet einen anderen Detaillierungsgrad in den Vergleichsergebnissen.

#### F: Wie verwende ich die Vergleichsgranularität in Aspose.Words für .NET?

A: Um die Vergleichsgranularität in Aspose.Words für .NET zu verwenden, folgen Sie diesen Schritten:
1. Richten Sie Ihre Entwicklungsumgebung mit der Aspose.Words-Bibliothek ein.
2. Fügen Sie Ihrem Projekt die erforderlichen Assemblys hinzu, indem Sie auf Aspose.Words verweisen.
3.  Erstellen Sie die zu vergleichenden Dokumente mit dem`DocumentBuilder` Klasse.
4.  Konfigurieren Sie die Vergleichsoptionen durch die Erstellung eines`CompareOptions` Objekt und Festlegen der`Granularity` Eigenschaft auf das gewünschte Niveau (z. B.`Granularity.CharLevel` für den Vergleich auf Zeichenebene).
5.  Verwenden Sie die`Compare`Methode auf einem Dokument, Übergabe des anderen Dokuments und der`CompareOptions` Objekt als Parameter. Diese Methode vergleicht die Dokumente basierend auf der angegebenen Granularität und speichert die Änderungen im ersten Dokument.

#### F: Welche Vergleichsgranularitätsebenen sind in Aspose.Words für .NET verfügbar?

A: Aspose.Words für .NET bietet drei Ebenen der Vergleichsgranularität:
- `Granularity.CharLevel`: Vergleicht Dokumente auf Zeichenebene.
- `Granularity.WordLevel`: Vergleicht Dokumente auf Wortebene.
- `Granularity.BlockLevel`: Vergleicht Dokumente auf Blockebene.

#### F: Wie kann ich die Vergleichsergebnisse mit Granularität auf Zeichenebene interpretieren?

A: Bei der Granularität auf Zeichenebene wird jedes Zeichen in den verglichenen Dokumenten auf Unterschiede analysiert. Die Vergleichsergebnisse zeigen Änderungen auf der Ebene der einzelnen Zeichen, einschließlich Hinzufügungen, Löschungen und Änderungen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
