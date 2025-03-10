---
title: Bauen Sie einen Tisch mit Stil
linktitle: Bauen Sie einen Tisch mit Stil
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Tabellen in Word-Dokumenten erstellen und formatieren.
weight: 10
url: /de/net/programming-with-table-styles-and-formatting/build-table-with-style/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bauen Sie einen Tisch mit Stil

## Einführung

Zum Erstellen stilvoller, professioneller Dokumente ist oft mehr als nur einfacher Text erforderlich. Tabellen sind eine fantastische Möglichkeit, Daten zu organisieren, aber sie ansprechend aussehen zu lassen, ist eine ganz andere Herausforderung. Hier kommt Aspose.Words für .NET ins Spiel! In diesem Tutorial erfahren Sie, wie Sie eine stilvolle Tabelle erstellen, die Ihren Word-Dokumenten ein elegantes und professionelles Aussehen verleiht.

## Voraussetzungen

Bevor wir mit der Schritt-für-Schritt-Anleitung beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie herunter und installieren Sie[Aspose.Words für .NET](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Sie sollten eine Entwicklungsumgebung eingerichtet haben. Visual Studio ist eine gute Option für dieses Tutorial.
3. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie den Anweisungen leichter folgen.

## Namespaces importieren

Um zu beginnen, müssen Sie die erforderlichen Namespaces importieren. Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Neues Dokument und DocumentBuilder erstellen

 Als erstes müssen Sie ein neues Dokument erstellen und ein`DocumentBuilder` Objekt. Dieses`DocumentBuilder` hilft Ihnen beim Erstellen der Tabelle in Ihrem Dokument.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Beginnen Sie mit dem Erstellen der Tabelle

Nachdem unser Dokument und der Builder nun bereit sind, beginnen wir mit der Erstellung der Tabelle.

```csharp
Table table = builder.StartTable();
```

## Schritt 3: Einfügen der ersten Zeile

Eine Tabelle ohne Zeilen ist nur eine leere Struktur. Wir müssen mindestens eine Zeile einfügen, bevor wir die Tabelle formatieren können.

```csharp
builder.InsertCell();
```

## Schritt 4: Legen Sie den Tabellenstil fest

 Nachdem wir die erste Zelle eingefügt haben, ist es an der Zeit, unserer Tabelle etwas Stil zu verleihen. Wir verwenden die`StyleIdentifier` , um einen vordefinierten Stil anzuwenden.

```csharp
// Legen Sie den verwendeten Tabellenstil basierend auf der eindeutigen Stilkennung fest
table.StyleIdentifier = StyleIdentifier.MediumShading1Accent1;
```

## Schritt 5: Stiloptionen definieren

Die Tabellenstiloptionen definieren, welche Teile der Tabelle gestaltet werden. Wir können beispielsweise wählen, ob wir die erste Spalte, Zeilenbänder und die erste Zeile gestalten möchten.

```csharp
// Anwenden, welche Funktionen durch den Stil formatiert werden sollen
table.StyleOptions = TableStyleOptions.FirstColumn | TableStyleOptions.RowBands | TableStyleOptions.FirstRow;
```

## Schritt 6: Tabelle an Inhalt anpassen

Um sicherzustellen, dass unser Tisch ordentlich und aufgeräumt aussieht, können wir die`AutoFit` Methode, um die Tabelle an ihren Inhalt anzupassen.

```csharp
table.AutoFit(AutoFitBehavior.AutoFitToContents);
```

## Schritt 7: Daten in die Tabelle einfügen

Jetzt ist es an der Zeit, unsere Tabelle mit einigen Daten zu füllen. Wir beginnen mit der Kopfzeile und fügen dann einige Beispieldaten hinzu.

### Kopfzeile einfügen

```csharp
builder.Writeln("Item");
builder.CellFormat.RightPadding = 40;
builder.InsertCell();
builder.Writeln("Quantity (kg)");
builder.EndRow();
```

#### Einfügen von Datenzeilen

```csharp
builder.InsertCell();
builder.Writeln("Apples");
builder.InsertCell();
builder.Writeln("20");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Bananas");
builder.InsertCell();
builder.Writeln("40");
builder.EndRow();

builder.InsertCell();
builder.Writeln("Carrots");
builder.InsertCell();
builder.Writeln("50");
builder.EndRow();
```

## Schritt 8: Speichern Sie das Dokument

Nach der Eingabe aller Daten erfolgt im letzten Schritt das Speichern des Dokuments.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.BuildTableWithStyle.docx");
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine stilvolle Tabelle in einem Word-Dokument mit Aspose.Words für .NET erstellt. Diese leistungsstarke Bibliothek erleichtert die Automatisierung und Anpassung von Word-Dokumenten an Ihre genauen Anforderungen. Egal, ob Sie Berichte, Rechnungen oder andere Dokumenttypen erstellen, Aspose.Words bietet alles.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, Word-Dokumente programmgesteuert mit C# zu erstellen, zu bearbeiten und zu bearbeiten.

### Kann ich Aspose.Words für .NET verwenden, um vorhandene Tabellen zu formatieren?
Ja, Aspose.Words für .NET kann zum Formatieren sowohl neuer als auch vorhandener Tabellen in Ihren Word-Dokumenten verwendet werden.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, Aspose.Words für .NET erfordert eine Lizenz für die volle Funktionalität. Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) oder kaufe ein volles[Hier](https://purchase.aspose.com/buy).

### Kann ich mit Aspose.Words für .NET andere Dokumenttypen automatisieren?
Absolut! Aspose.Words für .NET unterstützt verschiedene Dokumenttypen, darunter DOCX, PDF, HTML und mehr.

### Wo finde ich weitere Beispiele und Dokumentation?
 Ausführliche Dokumentationen und Beispiele finden Sie auf der[Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
