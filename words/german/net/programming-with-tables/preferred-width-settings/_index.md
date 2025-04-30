---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie Tabellen mit absoluten, relativen und automatischen Breiteneinstellungen in Aspose.Words für .NET erstellen."
"linktitle": "Bevorzugte Breiteneinstellungen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Bevorzugte Breiteneinstellungen"
"url": "/de/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bevorzugte Breiteneinstellungen

## Einführung

Tabellen bieten eine leistungsstarke Möglichkeit, Informationen in Ihren Word-Dokumenten zu organisieren und zu präsentieren. Beim Arbeiten mit Tabellen in Aspose.Words für .NET haben Sie verschiedene Möglichkeiten, die Breite von Tabellenzellen so einzustellen, dass sie perfekt in das Layout Ihres Dokuments passen. Diese Anleitung führt Sie durch die Erstellung von Tabellen mit bevorzugten Breiteneinstellungen mit Aspose.Words für .NET und konzentriert sich dabei auf absolute, relative und automatische Größenanpassungsoptionen. 

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Aspose.Words für .NET in Ihrer Entwicklungsumgebung installiert ist. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).

2. .NET-Entwicklungsumgebung: Richten Sie eine .NET-Entwicklungsumgebung wie Visual Studio ein.

3. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie die Codeausschnitte und Beispiele besser verstehen.

4. Aspose.Words Dokumentation: Siehe die [Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/) für ausführliche API-Informationen und weiterführende Literatur.

## Namespaces importieren

Bevor Sie mit dem Codieren beginnen, müssen Sie die erforderlichen Namespaces in Ihr C#-Projekt importieren:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Diese Namespaces bieten Zugriff auf die Kernfunktionen von Aspose.Words und dem Table-Objekt und ermöglichen Ihnen die Bearbeitung von Dokumenttabellen.

Lassen Sie uns den Vorgang zum Erstellen einer Tabelle mit unterschiedlichen bevorzugten Breiteneinstellungen in klare, überschaubare Schritte unterteilen.

## Schritt 1: Initialisieren Sie das Dokument und den DocumentBuilder

Überschrift: Erstellen eines neuen Dokuments und DocumentBuilder

Erklärung: Beginnen Sie mit der Erstellung eines neuen Word-Dokuments und einer `DocumentBuilder` Instanz. Die `DocumentBuilder` Die Klasse bietet eine einfache Möglichkeit, Ihrem Dokument Inhalte hinzuzufügen.

```csharp
// Definieren Sie den Pfad zum Speichern des Dokuments.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Erstellen Sie ein neues Dokument.
Document doc = new Document();

// Erstellen Sie einen DocumentBuilder für dieses Dokument.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Hier geben Sie das Verzeichnis an, in dem das Dokument gespeichert wird und initialisieren die `Document` Und `DocumentBuilder` Objekte.

## Schritt 2: Einfügen der ersten Tabellenzelle mit absoluter Breite

Fügen Sie die erste Zelle mit einer festen Breite von 40 Punkt in die Tabelle ein. Dadurch wird sichergestellt, dass diese Zelle unabhängig von der Tabellengröße immer eine Breite von 40 Punkt beibehält.

```csharp
// Fügen Sie eine Zelle mit absoluter Größe ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In diesem Schritt beginnen Sie mit der Erstellung der Tabelle und fügen eine Zelle mit einer absoluten Breite ein. Die `PreferredWidth.FromPoints(40)` Die Methode setzt die Zellenbreite auf 40 Punkte und `Shading.BackgroundPatternColor` wendet eine hellgelbe Hintergrundfarbe an.

## Schritt 3: Einfügen einer Zelle mit relativer Größe

Fügen Sie eine weitere Zelle mit einer Breite von 20 % der Gesamtbreite der Tabelle ein. Diese relative Größenanpassung stellt sicher, dass sich die Zelle proportional an die Tabellenbreite anpasst.

```csharp
// Fügen Sie eine Zelle mit relativer (prozentualer) Größe ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Die Breite dieser Zelle beträgt 20 % der Gesamtbreite der Tabelle, sodass sie an unterschiedliche Bildschirmgrößen oder Dokumentlayouts angepasst werden kann.

### Schritt 4: Einfügen einer Zelle mit automatischer Größe

Fügen Sie abschließend eine Zelle ein, deren Größe sich automatisch an den verbleibenden verfügbaren Platz in der Tabelle anpasst.

```csharp
// Fügen Sie eine Zelle mit automatischer Größenanpassung ein.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. Der size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` Mit dieser Einstellung kann diese Zelle je nach dem verbleibenden Platz nach Berücksichtigung der anderen Zellen erweitert oder verkleinert werden. Dadurch wird ein ausgewogenes und professionelles Tabellenlayout gewährleistet.

## Schritt 5: Dokument fertigstellen und speichern

Nachdem Sie alle Zellen eingefügt haben, vervollständigen Sie die Tabelle und speichern Sie das Dokument im angegebenen Pfad.

```csharp
// Speichern Sie das Dokument.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Dieser Schritt schließt die Tabelle ab und speichert das Dokument unter dem Dateinamen „WorkingWithTables.PreferredWidthSettings.docx“ in Ihrem angegebenen Verzeichnis.

## Abschluss

Das Erstellen von Tabellen mit bevorzugten Breiteneinstellungen in Aspose.Words für .NET ist unkompliziert, sobald Sie die verschiedenen verfügbaren Größenoptionen kennen. Ob feste, relative oder automatische Zellenbreiten – Aspose.Words bietet die Flexibilität, verschiedene Tabellenlayout-Szenarien effizient zu bewältigen. Mit den in dieser Anleitung beschriebenen Schritten stellen Sie sicher, dass Ihre Tabellen in Ihren Word-Dokumenten gut strukturiert und optisch ansprechend sind.

## Häufig gestellte Fragen

### Was ist der Unterschied zwischen absoluter und relativer Zellenbreite?
Absolute Zellenbreiten sind fest und ändern sich nicht, während relative Breiten basierend auf der Gesamtbreite der Tabelle angepasst werden.

### Kann ich negative Prozentsätze für relative Breiten verwenden?
Nein, negative Prozentwerte sind für die Zellenbreite nicht gültig. Nur positive Prozentwerte sind zulässig.

### Wie funktioniert die automatische Größenanpassung?
Bei der automatischen Größenanpassung wird die Breite der Zelle so angepasst, dass der verbleibende Platz in der Tabelle ausgefüllt wird, nachdem die Größe anderer Zellen angepasst wurde.

### Kann ich Zellen mit unterschiedlichen Breiteneinstellungen unterschiedliche Stile zuweisen?
Ja, Sie können den Zellen unabhängig von ihren Breiteneinstellungen verschiedene Stile und Formatierungen zuweisen.

### Was passiert, wenn die Gesamtbreite der Tabelle kleiner ist als die Summe aller Zellenbreiten?
Die Tabelle passt die Breite der Zellen automatisch an den verfügbaren Platz an, was dazu führen kann, dass einige Zellen kleiner werden.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}