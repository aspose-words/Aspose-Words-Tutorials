---
title: Gruppenform hinzufügen
linktitle: Gruppenform hinzufügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem umfassenden Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET Gruppenformen zu Word-Dokumenten hinzufügen.
weight: 10
url: /de/net/programming-with-shapes/add-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppenform hinzufügen

## Einführung

Das Erstellen komplexer Dokumente mit reichhaltigen visuellen Elementen kann manchmal eine gewaltige Aufgabe sein, insbesondere wenn es um Gruppenformen geht. Aber keine Angst! Aspose.Words für .NET vereinfacht diesen Prozess und macht ihn kinderleicht. In diesem Tutorial führen wir Sie durch die Schritte zum Hinzufügen von Gruppenformen zu Ihren Word-Dokumenten. Bereit, loszulegen? Dann legen wir los!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET: Sie können es herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede andere mit .NET kompatible IDE.
3. Grundlegende Kenntnisse in C#: Kenntnisse in der C#-Programmierung sind von Vorteil.

## Namespaces importieren

Zu Beginn müssen wir die erforderlichen Namespaces in unser Projekt importieren. Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten mit Aspose.Words erforderlich sind.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Schritt 1: Initialisieren Sie das Dokument

Zunächst einmal initialisieren wir ein neues Word-Dokument. Stellen Sie sich das so vor, als würden Sie eine leere Leinwand erstellen, auf der wir unsere Gruppenformen hinzufügen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
doc.EnsureMinimum();
```

 Hier,`EnsureMinimum()` fügt einen minimalen Satz an Knoten hinzu, die für das Dokument erforderlich sind.

## Schritt 2: Erstellen des GroupShape-Objekts

 Als nächstes müssen wir ein`GroupShape`Objekt. Dieses Objekt dient als Container für andere Formen und ermöglicht es uns, diese zu gruppieren.

```csharp
GroupShape groupShape = new GroupShape(doc);
```

## Schritt 3: Formen zur Gruppenform hinzufügen

 Fügen wir nun einzelne Formen zu unserem`GroupShape` Container. Wir beginnen mit einer Akzentrahmenform und fügen dann eine Aktionsschaltflächenform hinzu.

### Hinzufügen einer Akzent-Rahmenform

```csharp
Shape accentBorderShape = new Shape(doc, ShapeType.AccentBorderCallout1)
{
    Width = 100,
    Height = 100
};
groupShape.AppendChild(accentBorderShape);
```

 Dieser Codeausschnitt erstellt eine Akzentrahmenform mit einer Breite und Höhe von 100 Einheiten und fügt sie dem`GroupShape`.

### Hinzufügen einer Aktionsschaltflächenform

```csharp
Shape actionButtonShape = new Shape(doc, ShapeType.ActionButtonBeginning)
{
    Left = 100,
    Width = 100,
    Height = 200
};
groupShape.AppendChild(actionButtonShape);
```

 Hier erstellen wir eine Aktionsschaltflächenform, positionieren sie und fügen sie zu unserem`GroupShape`.

## Schritt 4: Definieren Sie die GroupShape-Dimensionen

 Um sicherzustellen, dass unsere Formen gut in die Gruppe passen, müssen wir die Abmessungen der`GroupShape`.

```csharp
groupShape.Width = 200;
groupShape.Height = 200;
groupShape.CoordSize = new Size(200, 200);
```

 Dies definiert die Breite und Höhe des`GroupShape` als 200 Einheiten und stellt die Koordinatengröße entsprechend ein.

## Schritt 5: Fügen Sie die Gruppenform in das Dokument ein

 Nun fügen wir unsere`GroupShape` in das Dokument mit`DocumentBuilder`.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.InsertNode(groupShape);
```

`DocumentBuilder` bietet eine einfache Möglichkeit, dem Dokument Knoten, einschließlich Formen, hinzuzufügen.

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddGroupShape.docx");
```

Und da haben Sie es! Ihr Dokument mit Gruppenformen ist fertig.

## Abschluss

Das Hinzufügen von Gruppenformen zu Ihren Word-Dokumenten muss kein komplizierter Vorgang sein. Mit Aspose.Words für .NET können Sie Formen ganz einfach erstellen und bearbeiten und so Ihre Dokumente optisch ansprechender und funktionaler gestalten. Befolgen Sie die in diesem Tutorial beschriebenen Schritte und Sie werden im Handumdrehen zum Profi!

## Häufig gestellte Fragen

### Kann ich einer Gruppenform mehr als zwei Formen hinzufügen?
 Ja, Sie können beliebig viele Formen zu einem`GroupShape` . Benutzen Sie einfach die`AppendChild` Methode für jede Form.

### Ist es möglich, die Formen innerhalb einer Gruppenform zu gestalten?
 Absolut! Jede Form kann individuell gestaltet werden, indem man die Eigenschaften verwendet, die im`Shape` Klasse.

### Wie positioniere ich die Gruppenform innerhalb des Dokuments?
 Sie können die`GroupShape` durch Einstellen seiner`Left` Und`Top` Eigenschaften.

### Kann ich den Formen innerhalb der Gruppenform Text hinzufügen?
 Ja, Sie können Text zu Formen hinzufügen mit dem`AppendChild` Methode zum Hinzufügen eines`Paragraph` enthaltend`Run` Knoten mit Text.

### Ist es möglich, Formen dynamisch basierend auf Benutzereingaben zu gruppieren?
Ja, Sie können Formen dynamisch basierend auf Benutzereingaben erstellen und gruppieren, indem Sie die Eigenschaften und Methoden entsprechend anpassen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
