---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET relative horizontale und vertikale Positionen für Tabellen in Word-Dokumenten festlegen."
"linktitle": "Relative horizontale oder vertikale Position festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Relative horizontale oder vertikale Position festlegen"
"url": "/de/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Relative horizontale oder vertikale Position festlegen

## Einführung

Haben Sie schon einmal versucht, Tabellen in Ihren Word-Dokumenten optimal zu positionieren? Damit sind Sie nicht allein. Ob professioneller Bericht oder elegante Broschüre – die Ausrichtung von Tabellen kann einen großen Unterschied machen. Hier kommt Aspose.Words für .NET ins Spiel. Dieses Tutorial zeigt Ihnen Schritt für Schritt, wie Sie die relative horizontale oder vertikale Position von Tabellen in Ihren Word-Dokumenten festlegen. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Falls noch nicht geschehen, können Sie es herunterladen [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit den Grundlagen der C#-Programmierung vertraut sind.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces importieren. Dies ist für den Zugriff auf die Aspose.Words-Funktionen unerlässlich.

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

Dieser Codeausschnitt richtet den Pfad zu Ihrem Dokumentverzeichnis ein und lädt das gewünschte Dokument. Stellen Sie sicher, dass der Dokumentpfad korrekt ist, um Ladeprobleme zu vermeiden.

## Schritt 2: Zugriff auf die Tabelle

Als Nächstes müssen wir auf die Tabelle im Dokument zugreifen. Normalerweise möchten Sie mit der ersten Tabelle im Hauptteil arbeiten.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Diese Codezeile ruft die erste Tabelle aus dem Dokument ab. Wenn Ihr Dokument mehrere Tabellen enthält, können Sie den Index entsprechend anpassen.

## Schritt 3: Horizontale Position einstellen

Legen wir nun die horizontale Position der Tabelle relativ zu einem bestimmten Element fest. In diesem Beispiel positionieren wir sie relativ zur Spalte.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Durch die Einstellung der `HorizontalAnchor` Zu `RelativeHorizontalPosition.Column`, weisen Sie die Tabelle an, sich horizontal in Bezug auf die Spalte auszurichten, in der sie sich befindet.

## Schritt 4: Vertikale Position einstellen

Ähnlich wie bei der horizontalen Positionierung können Sie auch die vertikale Position festlegen. Hier positionieren wir es relativ zur Seite.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Einstellen der `VerticalAnchor` Zu `RelativeVerticalPosition.Page` sorgt dafür, dass die Tabelle vertikal entsprechend der Seite ausgerichtet ist.

## Schritt 5: Speichern Sie Ihr Dokument

Speichern Sie abschließend Ihre Änderungen in einem neuen Dokument. Dies ist ein wichtiger Schritt, um sicherzustellen, dass Ihre Änderungen erhalten bleiben.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Dieser Befehl speichert das geänderte Dokument unter einem neuen Namen und stellt sicher, dass Sie Ihre Originaldatei nicht überschreiben.

## Abschluss

Und da haben Sie es! Sie haben die relativen horizontalen und vertikalen Positionen einer Tabelle in einem Word-Dokument mit Aspose.Words für .NET erfolgreich festgelegt. Mit dieser neu erworbenen Fähigkeit können Sie das Layout und die Lesbarkeit Ihrer Dokumente verbessern und ihnen ein professionelleres und eleganteres Aussehen verleihen. Experimentieren Sie weiter mit verschiedenen Positionen und finden Sie heraus, was für Ihre Anforderungen am besten geeignet ist.

## Häufig gestellte Fragen

### Kann ich Tabellen relativ zu anderen Elementen positionieren?  
Ja, mit Aspose.Words können Sie Tabellen relativ zu verschiedenen Elementen wie Rändern, Seiten, Spalten und mehr positionieren.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?  
Ja, Sie können eine Lizenz erwerben [Hier](https://purchase.aspose.com/buy) oder eine temporäre Lizenz erhalten [Hier](https://purchase.aspose.com/temporary-license/).

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?  
Absolut! Sie können eine kostenlose Testversion herunterladen [Hier](https://releases.aspose.com/).

### Kann ich Aspose.Words mit anderen Programmiersprachen verwenden?  
Aspose.Words ist hauptsächlich für .NET konzipiert, es sind jedoch Versionen für Java, Python und andere Plattformen verfügbar.

### Wo finde ich ausführlichere Dokumentation?  
Ausführlichere Informationen finden Sie in der Aspose.Words-Dokumentation. [Hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}