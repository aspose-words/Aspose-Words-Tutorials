---
title: Anpassen der Diagrammdatenbeschriftung
linktitle: Anpassen der Diagrammdatenbeschriftung
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in einer Schritt-für-Schritt-Anleitung, wie Sie Diagrammdatenbeschriftungen mit Aspose.Words für .NET anpassen. Perfekt für .NET-Entwickler.
weight: 10
url: /de/net/programming-with-charts/chart-data-label/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Anpassen der Diagrammdatenbeschriftung

## Einführung

Möchten Sie Ihre .NET-Anwendungen mit dynamischen und benutzerdefinierten Dokumentverarbeitungsfunktionen aufpeppen? Aspose.Words für .NET könnte genau die Antwort für Sie sein! In diesem Handbuch werden wir uns eingehend mit der Anpassung von Diagrammdatenbeschriftungen mithilfe von Aspose.Words für .NET befassen, einer leistungsstarken Bibliothek zum Erstellen, Ändern und Konvertieren von Word-Dokumenten. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieses Tutorial führt Sie durch jeden Schritt und stellt sicher, dass Sie verstehen, wie Sie dieses Tool effektiv nutzen können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Visual Studio: Installieren Sie Visual Studio 2019 oder höher.
2. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework 4.0 oder höher haben.
3.  Aspose.Words für .NET: Laden Sie Aspose.Words für .NET herunter und installieren Sie es von der[Downloadlink](https://releases.aspose.com/words/net/).
4. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind unbedingt erforderlich.
5.  Eine gültige Lizenz: Besorgen Sie sich eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) oder kaufen Sie eines im[Kauflink](https://purchase.aspose.com/buy).

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren. Dieser Schritt ist entscheidend, da er sicherstellt, dass Sie Zugriff auf alle von Aspose.Words bereitgestellten Klassen und Methoden haben.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Charts;
```

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Um Word-Dokumente zu erstellen und zu bearbeiten, müssen wir zunächst eine Instanz des`Document` Klasse und eine`DocumentBuilder` Objekt.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Erläuterung

- Dokument doc: Erstellt eine neue Instanz der Dokumentklasse.
- DocumentBuilder-Builder: Der DocumentBuilder hilft beim Einfügen von Inhalten in das Dokumentobjekt.

## Schritt 2: Einfügen eines Diagramms

 Als nächstes fügen wir ein Balkendiagramm in das Dokument ein. Dazu verwenden wir`DocumentBuilder` Objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Bar, 432, 252);
Chart chart = shape.Chart;
```

### Erläuterung

- Formform: Stellt das Diagramm als Form im Dokument dar.
- builder.InsertChart(ChartType.Bar, 432, 252): Fügt ein Balkendiagramm mit angegebenen Dimensionen ein.

## Schritt 3: Zugriff auf die Diagrammserie

Um die Datenbeschriftungen anzupassen, müssen wir zuerst auf die Reihen im Diagramm zugreifen.

```csharp
ChartSeries series0 = shape.Chart.Series[0];
```

### Erläuterung

- ChartSeries series0: Ruft die erste Serie des Diagramms ab, die wir anpassen werden.

## Schritt 4: Datenbeschriftungen anpassen

Datenbeschriftungen können angepasst werden, um verschiedene Informationen anzuzeigen. Wir konfigurieren die Beschriftungen so, dass der Legendenschlüssel, der Serienname und der Wert angezeigt werden, während der Kategoriename und der Prozentsatz ausgeblendet werden.

```csharp
ChartDataLabelCollection labels = series0.DataLabels;
labels.ShowLegendKey = true;
labels.ShowLeaderLines = true;
labels.ShowCategoryName = false;
labels.ShowPercentage = false;
labels.ShowSeriesName = true;
labels.ShowValue = true;
labels.Separator = "/";
```

### Erläuterung

- ChartDataLabelCollection-Beschriftungen: Greift auf die Datenbeschriftungen der Reihe zu.
- labels.ShowLegendKey: Zeigt den Legendenschlüssel an.
- labels.ShowLeaderLines: Zeigt Führungslinien für Datenbeschriftungen an, die weit außerhalb der Datenpunkte positioniert sind.
- labels.ShowCategoryName: Blendet den Kategorienamen aus.
- labels.ShowPercentage: Blendet den Prozentwert aus.
- labels.ShowSeriesName: Zeigt den Seriennamen an.
- labels.ShowValue: Zeigt den Wert der Datenpunkte an.
- labels.Separator: Legt das Trennzeichen für die Datenbeschriftungen fest.

## Schritt 5: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithCharts.ChartDataLabel.docx");
```

### Erläuterung

- doc.Save: Speichert das Dokument unter dem angegebenen Namen im angegebenen Verzeichnis.

## Abschluss

 Herzlichen Glückwunsch! Sie haben Diagrammdatenbeschriftungen erfolgreich mit Aspose.Words für .NET angepasst. Diese Bibliothek bietet eine robuste Lösung für die programmgesteuerte Verarbeitung von Word-Dokumenten und erleichtert Entwicklern die Erstellung anspruchsvoller und dynamischer Anwendungen zur Dokumentverarbeitung. Tauchen Sie ein in die[Dokumentation](https://reference.aspose.com/words/net/) um weitere Funktionen und Möglichkeiten zu entdecken.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Dokumentverarbeitungsbibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, ändern und konvertieren können.

### Wie installiere ich Aspose.Words für .NET?
 Sie können es herunterladen und installieren von der[Downloadlink](https://releases.aspose.com/words/net/). Befolgen Sie die bereitgestellten Installationsanweisungen.

### Kann ich Aspose.Words für .NET kostenlos testen?
 Ja, Sie können eine[Kostenlose Testversion](https://releases.aspose.com/) oder ein[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/)um das Produkt zu bewerten.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?
Ja, Aspose.Words für .NET ist mit .NET Core, .NET Standard und .NET Framework kompatibel.

### Wo erhalte ich Support für Aspose.Words für .NET?
 Besuchen Sie die[Support-Forum](https://forum.aspose.com/c/words/8) für Hilfe und Unterstützung durch die Aspose-Community und Experten.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
