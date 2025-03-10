---
title: Bevorzugte Breiteneinstellungen
linktitle: Bevorzugte Breiteneinstellungen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie in Aspose.Words für .NET Tabellen mit absoluten, relativen und automatischen Breiteneinstellungen erstellen.
weight: 10
url: /de/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bevorzugte Breiteneinstellungen

## Einführung

Tabellen sind eine leistungsstarke Möglichkeit, Informationen in Ihren Word-Dokumenten zu organisieren und darzustellen. Wenn Sie mit Tabellen in Aspose.Words für .NET arbeiten, haben Sie mehrere Möglichkeiten, die Breite von Tabellenzellen festzulegen, um sicherzustellen, dass sie perfekt in das Layout Ihres Dokuments passen. Diese Anleitung führt Sie durch den Prozess der Erstellung von Tabellen mit bevorzugten Breiteneinstellungen mit Aspose.Words für .NET und konzentriert sich dabei auf absolute, relative und automatische Größenoptionen. 

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET in Ihrer Entwicklungsumgebung installiert haben. Sie können es herunterladen[Hier](https://releases.aspose.com/words/net/).

2. .NET-Entwicklungsumgebung: Richten Sie eine .NET-Entwicklungsumgebung wie beispielsweise Visual Studio ein.

3. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, verstehen Sie die Codeausschnitte und Beispiele besser.

4.  Aspose.Words Dokumentation: Siehe die[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) für detaillierte API-Informationen und weiterführende Literatur.

## Namespaces importieren

Bevor Sie mit dem Codieren beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Diese Namespaces bieten Zugriff auf die Kernfunktionen von Aspose.Words und dem Table-Objekt und ermöglichen Ihnen die Bearbeitung von Dokumenttabellen.

Lassen Sie uns den Vorgang zum Erstellen einer Tabelle mit unterschiedlichen bevorzugten Breiteneinstellungen in klare, überschaubare Schritte aufteilen.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Überschrift: Erstellen eines neuen Dokuments und DocumentBuilder

 Erläuterung: Erstellen Sie zunächst ein neues Word-Dokument und ein`DocumentBuilder` Instanz. Die`DocumentBuilder` Klasse bietet eine einfache Möglichkeit, Ihrem Dokument Inhalt hinzuzufügen.

```csharp
// Definieren Sie den Pfad zum Speichern des Dokuments.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Erstellen Sie ein neues Dokument.
Document doc = new Document();

// Erstellen Sie einen DocumentBuilder für dieses Dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier geben Sie das Verzeichnis an, in dem das Dokument gespeichert wird und initialisieren den`Document` Und`DocumentBuilder` Objekte.

## Schritt 2: Einfügen der ersten Tabellenzelle mit absoluter Breite

Fügen Sie die erste Zelle mit einer festen Breite von 40 Punkt in die Tabelle ein. Dadurch wird sichergestellt, dass diese Zelle unabhängig von der Tabellengröße immer eine Breite von 40 Punkt beibehält.

```csharp
// Fügen Sie eine Zelle mit absoluter Größe ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In diesem Schritt beginnen Sie mit dem Erstellen der Tabelle und fügen eine Zelle mit absoluter Breite ein. Die`PreferredWidth.FromPoints(40)` Die Methode setzt die Breite der Zelle auf 40 Punkte und`Shading.BackgroundPatternColor` wendet eine hellgelbe Hintergrundfarbe an.

## Schritt 3: Einfügen einer Zelle mit relativer Größe

Fügen Sie eine weitere Zelle mit einer Breite von 20 % der Gesamtbreite der Tabelle ein. Diese relative Größenanpassung stellt sicher, dass sich die Zelle proportional an die Breite der Tabelle anpasst.

```csharp
// Fügen Sie eine Zelle mit relativer (prozentueller) Größe ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Die Breite dieser Zelle beträgt 20 % der Gesamtbreite der Tabelle, sodass sie an unterschiedliche Bildschirmgrößen oder Dokumentlayouts angepasst werden kann.

### Schritt 4: Einfügen einer Zelle mit automatischer Größenanpassung

Fügen Sie abschließend eine Zelle ein, deren Größe sich automatisch an den verbleibenden verfügbaren Platz in der Tabelle anpasst.

```csharp
// Fügen Sie eine Zelle mit automatischer Größenanpassung ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 Der`PreferredWidth.Auto` Mit dieser Einstellung kann diese Zelle je nach dem verbleibenden Platz nach Berücksichtigung der anderen Zellen erweitert oder verkleinert werden. Dadurch wird sichergestellt, dass das Tabellenlayout ausgewogen und professionell aussieht.

## Schritt 5: Dokument fertigstellen und speichern

Wenn Sie alle Zellen eingefügt haben, vervollständigen Sie die Tabelle und speichern Sie das Dokument im angegebenen Pfad.

```csharp
// Speichern Sie das Dokument.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Dieser Schritt finalisiert die Tabelle und speichert das Dokument unter dem Dateinamen „WorkingWithTables.PreferredWidthSettings.docx“ im von Ihnen angegebenen Verzeichnis.

## Abschluss

Das Erstellen von Tabellen mit bevorzugten Breiteneinstellungen in Aspose.Words für .NET ist unkompliziert, wenn Sie die verschiedenen verfügbaren Größenoptionen kennen. Unabhängig davon, ob Sie feste, relative oder automatische Zellenbreiten benötigen, bietet Aspose.Words die Flexibilität, verschiedene Tabellenlayout-Szenarien effizient zu handhaben. Indem Sie die in diesem Handbuch beschriebenen Schritte befolgen, können Sie sicherstellen, dass Ihre Tabellen in Ihren Word-Dokumenten gut strukturiert und optisch ansprechend sind.

## Häufig gestellte Fragen

### Was ist der Unterschied zwischen absoluter und relativer Zellenbreite?
Absolute Zellenbreiten sind fest und ändern sich nicht, während relative Breiten basierend auf der Gesamtbreite der Tabelle angepasst werden.

### Kann ich für relative Breiten negative Prozentsätze verwenden?
Nein, negative Prozentwerte sind für die Zellenbreite nicht gültig. Nur positive Prozentwerte sind zulässig.

### Wie funktioniert die automatische Größenanpassung?
Bei der automatischen Größenanpassung wird die Breite der Zelle so angepasst, dass der verbleibende Platz in der Tabelle ausgefüllt wird, nachdem die Größe anderer Zellen angepasst wurde.

### Kann ich Zellen mit unterschiedlichen Breiteneinstellungen unterschiedliche Stile zuweisen?
Ja, Sie können den Zellen unabhängig von ihren Breiteneinstellungen verschiedene Stile und Formatierungen zuweisen.

### Was passiert, wenn die Gesamtbreite der Tabelle kleiner ist als die Summe aller Zellenbreiten?
Die Breite der Zellen wird von der Tabelle automatisch so angepasst, dass sie in den verfügbaren Platz passt. Dies kann dazu führen, dass einige Zellen schrumpfen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
