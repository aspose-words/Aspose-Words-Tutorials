---
title: Relative horizontale oder vertikale Position festlegen
linktitle: Relative horizontale oder vertikale Position festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET relative horizontale und vertikale Positionen für Tabellen in Word-Dokumenten festlegen.
weight: 10
url: /de/net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Relative horizontale oder vertikale Position festlegen

## Einführung

Haben Sie sich jemals gefragt, wie Sie Tabellen in Ihren Word-Dokumenten genau so positionieren können, wie Sie es möchten? Nun, Sie sind nicht allein. Egal, ob Sie einen professionellen Bericht oder eine stilvolle Broschüre erstellen, das Ausrichten von Tabellen kann einen großen Unterschied machen. Hier kommt Aspose.Words für .NET ins Spiel. Dieses Tutorial führt Sie Schritt für Schritt durch das Festlegen der relativen horizontalen oder vertikalen Positionen für Tabellen in Ihren Word-Dokumenten. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Falls noch nicht geschehen, können Sie es herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit den Grundlagen der C#-Programmierung vertraut sind.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Dies ist für den Zugriff auf die Aspose.Words-Funktionen unerlässlich.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Laden Sie Ihr Dokument

Um zu beginnen, müssen Sie Ihr Word-Dokument in das Programm laden. So geht's:

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Dieser Codeausschnitt richtet den Pfad zu Ihrem Dokumentverzeichnis ein und lädt das spezifische Dokument, an dem Sie arbeiten möchten. Stellen Sie sicher, dass Ihr Dokumentpfad korrekt ist, um Ladeprobleme zu vermeiden.

## Schritt 2: Zugriff auf die Tabelle

Als nächstes müssen wir auf die Tabelle im Dokument zugreifen. Normalerweise möchten Sie mit der ersten Tabelle im Hauptteil arbeiten.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Diese Codezeile holt die erste Tabelle aus dem Hauptteil des Dokuments. Wenn Ihr Dokument mehrere Tabellen hat, können Sie den Index entsprechend anpassen.

## Schritt 3: Horizontale Position festlegen

Nun legen wir die horizontale Position der Tabelle relativ zu einem bestimmten Element fest. In diesem Beispiel positionieren wir es relativ zur Spalte.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

 Durch die Einstellung der`HorizontalAnchor` Zu`RelativeHorizontalPosition.Column`sagen Sie der Tabelle, dass sie sich horizontal in Bezug auf die Spalte ausrichten soll, in der sie sich befindet.

## Schritt 4: Vertikale Position festlegen

Ähnlich wie bei der horizontalen Positionierung können Sie auch die vertikale Position festlegen. Hier positionieren wir es relativ zur Seite.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

 Einstellen der`VerticalAnchor` Zu`RelativeVerticalPosition.Page` sorgt dafür, dass die Tabelle vertikal entsprechend der Seite ausgerichtet ist.

## Schritt 5: Speichern Sie Ihr Dokument

Speichern Sie abschließend Ihre Änderungen in einem neuen Dokument. Dies ist ein wichtiger Schritt, um sicherzustellen, dass Ihre Änderungen erhalten bleiben.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Dieser Befehl speichert das geänderte Dokument unter einem neuen Namen und stellt sicher, dass Sie Ihre Originaldatei nicht überschreiben.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich die relativen horizontalen und vertikalen Positionen für eine Tabelle in einem Word-Dokument mit Aspose.Words für .NET festgelegt. Mit dieser neu erworbenen Fähigkeit können Sie das Layout und die Lesbarkeit Ihrer Dokumente verbessern und ihnen ein professionelleres und eleganteres Aussehen verleihen. Experimentieren Sie weiter mit verschiedenen Positionen und finden Sie heraus, was für Ihre Anforderungen am besten geeignet ist.

## Häufig gestellte Fragen

### Kann ich Tabellen relativ zu anderen Elementen positionieren?  
Ja, Aspose.Words ermöglicht Ihnen, Tabellen relativ zu verschiedenen Elementen wie Rändern, Seiten, Spalten und mehr zu positionieren.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?  
 Ja, Sie können eine Lizenz erwerben[Hier](https://purchase.aspose.com/buy) oder holen Sie sich eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?  
 Auf jeden Fall! Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.aspose.com/).

### Kann ich Aspose.Words mit anderen Programmiersprachen verwenden?  
Aspose.Words ist in erster Linie für .NET konzipiert, es sind jedoch Versionen für Java, Python und andere Plattformen verfügbar.

### Wo finde ich ausführlichere Dokumentation?  
AusführlicHier Informationen finden Sie in der Aspose.Words-Dokumentation.[here](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
