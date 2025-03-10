---
title: Diagrammachsen in einem Word-Dokument ausblenden
linktitle: Diagrammachsen in einem Word-Dokument ausblenden
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserem ausführlichen Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET die Diagrammachsen in einem Word-Dokument ausblenden.
weight: 10
url: /de/net/programming-with-charts/hide-chart-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagrammachsen in einem Word-Dokument ausblenden

## Einführung

Beim Erstellen dynamischer und optisch ansprechender Word-Dokumente müssen häufig Diagramme und Grafiken eingefügt werden. In einem solchen Szenario kann es erforderlich sein, die Diagrammachsen für eine übersichtlichere Darstellung auszublenden. Aspose.Words für .NET bietet eine umfassende und benutzerfreundliche API für solche Aufgaben. Dieses Tutorial führt Sie durch die Schritte zum Ausblenden einer Diagrammachse in einem Word-Dokument mit Aspose.Words für .NET.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

-  Aspose.Words für .NET: Sie können es herunterladen von[Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Jede IDE, die .NET-Entwicklung unterstützt, z. B. Visual Studio.
- .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
- Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# ist von Vorteil.

## Namespaces importieren

Um mit Aspose.Words für .NET arbeiten zu können, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. So können Sie das tun:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

Lassen Sie uns den Prozess in einfache, leicht zu befolgende Schritte unterteilen.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Der erste Schritt umfasst das Erstellen eines neuen Word-Dokuments und das Initialisieren des DocumentBuilder-Objekts.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In diesem Schritt definieren wir den Pfad, in dem das Dokument gespeichert wird. Anschließend erstellen wir einen neuen`Document` Objekt und ein`DocumentBuilder` Objekt, um mit dem Erstellen unseres Dokuments zu beginnen.

## Schritt 2: Einfügen eines Diagramms

 Als nächstes fügen wir ein Diagramm in das Dokument ein, mit dem`DocumentBuilder` Objekt.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

 Hier fügen wir ein Säulendiagramm mit angegebenen Dimensionen ein.`InsertChart` Methode gibt einen`Shape` Objekt, das das Diagramm enthält.

## Schritt 3: Vorhandene Serien löschen

Bevor wir dem Diagramm neue Daten hinzufügen, müssen wir alle vorhandenen Reihen löschen.

```csharp
chart.Series.Clear();
```

Dieser Schritt stellt sicher, dass alle Standarddaten im Diagramm entfernt werden und Platz für die neuen Daten gemacht wird, die wir als Nächstes hinzufügen.

## Schritt 4: Seriendaten hinzufügen

Fügen wir nun dem Diagramm unsere eigene Datenreihe hinzu.

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

In diesem Schritt fügen wir eine Serie mit dem Titel „Aspose Series 1“ mit entsprechenden Kategorien und Werten hinzu.

## Schritt 5: Y-Achse ausblenden

 Um die Y-Achse des Diagramms auszublenden, setzen wir einfach die`Hidden` Eigenschaft der Y-Achse auf`true`.

```csharp
chart.AxisY.Hidden = true;
```

Diese Codezeile verbirgt die Y-Achse und macht sie im Diagramm unsichtbar.

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithCharts.HideChartAxis.docx");
```

Dieser Befehl speichert das Word-Dokument mit dem Diagramm im angegebenen Pfad.

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für .NET eine Diagrammachse in einem Word-Dokument ausblenden. Diese leistungsstarke Bibliothek erleichtert die programmgesteuerte Bearbeitung von Word-Dokumenten. Wenn Sie diese Schritte befolgen, können Sie mit minimalem Aufwand benutzerdefinierte und professionell aussehende Dokumente erstellen.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke API zum Erstellen, Bearbeiten, Konvertieren und Bearbeiten von Word-Dokumenten innerhalb von .NET-Anwendungen.

### Kann ich sowohl die X- als auch die Y-Achse in einem Diagramm ausblenden?
 Ja, Sie können beide Achsen ausblenden, indem Sie die`Hidden` Eigentum beider`AxisX` Und`AxisY` Zu`true`.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
 Ja, Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/).

### Wo finde ich weitere Dokumentation?
 Eine ausführliche Dokumentation finden Sie auf der Aspose.Words for .NET[Hier](https://reference.aspose.com/words/net/).

### Wie kann ich Support für Aspose.Words für .NET erhalten?
 Sie können Unterstützung von der Aspose-Community erhalten[Hier](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
