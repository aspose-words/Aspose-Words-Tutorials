---
"description": "Erfahren Sie, wie Sie Listennummern in Word-Dokumenten mit Aspose.Words für .NET neu starten. Diese ausführliche, 2000 Wörter umfassende Anleitung deckt alles ab, was Sie wissen müssen – von der Einrichtung bis zur erweiterten Anpassung."
"linktitle": "Neustartlistennummer"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Neustartlistennummer"
"url": "/de/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Neustartlistennummer

## Einführung

Möchten Sie die Kunst der Listenmanipulation in Ihren Word-Dokumenten mit Aspose.Words für .NET meistern? Dann sind Sie hier genau richtig! In diesem Tutorial tauchen wir tief in das Neustarten von Listennummern ein – eine praktische Funktion, die Ihre Fähigkeiten zur Dokumentenautomatisierung auf die nächste Stufe hebt. Schnall dich an und los geht’s!

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET: Sie müssen Aspose.Words für .NET installiert haben. Falls Sie es noch nicht installiert haben, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Stellen Sie sicher, dass Sie über eine geeignete Entwicklungsumgebung wie Visual Studio verfügen.
3. Grundkenntnisse in C#: Ein grundlegendes Verständnis von C# wird Ihnen helfen, dem Tutorial zu folgen.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Diese sind für den Zugriff auf die Aspose.Words-Funktionen von entscheidender Bedeutung.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Lassen Sie uns den Prozess nun in leicht verständliche Schritte unterteilen. Wir behandeln alles, vom Erstellen einer Liste bis zum Neustart der Nummerierung.

## Schritt 1: Richten Sie Ihr Dokument und Ihren Builder ein

Bevor Sie mit der Bearbeitung von Listen beginnen können, benötigen Sie ein Dokument und einen DocumentBuilder. Der DocumentBuilder ist Ihr zentrales Tool zum Hinzufügen von Inhalten zu Ihrem Dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Erstellen und Anpassen Ihrer ersten Liste

Als Nächstes erstellen wir eine Liste basierend auf einer Vorlage und passen ihr Erscheinungsbild an. In diesem Beispiel verwenden wir das arabische Zahlenformat mit Klammern.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Hier haben wir die Schriftfarbe auf Rot eingestellt und den Text rechtsbündig ausgerichtet.

## Schritt 3: Fügen Sie Ihrer ersten Liste Elemente hinzu

Wenn Ihre Liste fertig ist, ist es Zeit, einige Elemente hinzuzufügen. Der DocumentBuilder `ListFormat.List` Die Eigenschaft hilft beim Anwenden des Listenformats auf den Text.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Schritt 4: Listennummerierung neu starten

Um die Liste wiederzuverwenden und ihre Nummerierung neu zu starten, müssen Sie eine Kopie der Originalliste erstellen. So können Sie die neue Liste unabhängig bearbeiten.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

In diesem Beispiel beginnt die neue Liste bei Nummer 10.

## Schritt 5: Elemente zur neuen Liste hinzufügen

Fügen Sie wie zuvor Elemente zu Ihrer neuen Liste hinzu. Dies zeigt, wie die Liste bei der angegebenen Nummer neu gestartet wird.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Schritt 6: Speichern Sie Ihr Dokument

Speichern Sie Ihr Dokument abschließend im angegebenen Verzeichnis.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Abschluss

Das Neustarten von Listennummern in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert und unglaublich nützlich. Egal, ob Sie Berichte erstellen, strukturierte Dokumente erstellen oder einfach nur eine bessere Kontrolle über Ihre Listen benötigen – diese Technik ist die richtige Lösung für Sie.

## Häufig gestellte Fragen

### Kann ich neben NumberArabicParenthesis auch andere Listenvorlagen verwenden?

Absolut! Aspose.Words bietet verschiedene Listenvorlagen wie Aufzählungszeichen, Buchstaben, römische Ziffern und mehr. Sie können diejenige auswählen, die Ihren Anforderungen am besten entspricht.

### Wie ändere ich die Listenebene?

Sie können die Listenebene ändern, indem Sie die `ListLevels` Eigenschaft. Beispielsweise `list1.ListLevels[1]` würde sich auf die zweite Ebene der Liste beziehen.

### Kann ich die Nummerierung bei jeder beliebigen Nummer neu starten?

Ja, Sie können die Startnummer auf einen beliebigen ganzzahligen Wert setzen, indem Sie `StartAt` Eigenschaft der Listenebene.

### Ist es möglich, für unterschiedliche Listenebenen unterschiedliche Formatierungen zu verwenden?

Tatsächlich! Jede Listenebene kann eigene Formatierungseinstellungen wie Schriftart, Ausrichtung und Nummerierungsstil haben.

### Was ist, wenn ich die Nummerierung einer vorherigen Liste fortsetzen und nicht neu starten möchte?

Wenn Sie die Nummerierung fortsetzen möchten, müssen Sie keine Kopie der Liste erstellen. Fügen Sie einfach weiterhin Elemente zur ursprünglichen Liste hinzu.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}