---
"description": "Entdecken Sie, wie Sie mit Aspose.Words für .NET Nummerierungen mit Leerzeichen in Klartextdokumenten erkennen und sicherstellen, dass Ihre Listen richtig erkannt werden."
"linktitle": "Nummerierung mit Leerzeichen erkennen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Nummerierung mit Leerzeichen erkennen"
"url": "/de/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nummerierung mit Leerzeichen erkennen

## Einführung

Aspose.Words für .NET-Enthusiasten! Heute tauchen wir in eine faszinierende Funktion ein, die die Handhabung von Listen in Klartextdokumenten zum Kinderspiel macht. Haben Sie schon einmal mit Textdateien gearbeitet, in denen einige Zeilen Listen sein sollten, aber beim Laden in ein Word-Dokument einfach nicht richtig aussehen? Nun, wir haben einen tollen Trick auf Lager: die Erkennung von Nummerierungen mit Leerzeichen. Dieses Tutorial führt Sie durch die Verwendung von `DetectNumberingWithWhitespaces` Option in Aspose.Words für .NET, um sicherzustellen, dass Ihre Listen richtig erkannt werden, auch wenn zwischen den Zahlen und dem Text Leerzeichen stehen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- Aspose.Words für .NET: Sie können es herunterladen von der [Aspose-Veröffentlichungen](https://releases.aspose.com/words/net/) Seite.
- Entwicklungsumgebung: Visual Studio oder eine andere C#-IDE.
- .NET Framework auf Ihrem Computer installiert.
- Grundkenntnisse in C#: Das Verständnis der Grundlagen hilft Ihnen, den Beispielen zu folgen.

## Namespaces importieren

Bevor Sie mit dem Code beginnen, stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Hier ist ein kurzer Codeausschnitt für den Einstieg:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Wir unterteilen den Prozess in einfache, überschaubare Schritte. Jeder Schritt führt Sie durch den erforderlichen Code und erklärt, was passiert.

## Schritt 1: Definieren Sie Ihr Dokumentverzeichnis

Als Erstes richten wir den Pfad zu Ihrem Dokumentverzeichnis ein. Hier werden Ihre Eingabe- und Ausgabedateien gespeichert.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Erstellen Sie ein Klartextdokument

Als Nächstes erstellen wir ein Klartextdokument als Zeichenfolge. Dieses Dokument enthält Teile, die als Listen interpretiert werden können.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Schritt 3: LoadOptions konfigurieren

Um Nummerierungen mit Leerzeichen zu erkennen, müssen wir die `DetectNumberingWithWhitespaces` Möglichkeit, `true` in einem `TxtLoadOptions` Objekt.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Schritt 4: Laden Sie das Dokument

Laden wir nun das Dokument mit dem `TxtLoadOptions` als Parameter. Dadurch wird sichergestellt, dass die vierte Liste (mit Leerzeichen) korrekt erkannt wird.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis. Dadurch wird ein Word-Dokument mit korrekt erkannten Listen ausgegeben.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen beherrschen Sie die Kunst, Nummerierungen mit Leerzeichen in Klartextdokumenten mit Aspose.Words für .NET zu erkennen. Diese Funktion ist unglaublich praktisch, wenn Sie mit verschiedenen Textformaten arbeiten und sicherstellen möchten, dass Ihre Listen in Ihren Word-Dokumenten korrekt dargestellt werden. Wenn Sie also das nächste Mal auf diese kniffligen Listen stoßen, wissen Sie genau, was zu tun ist.

## Häufig gestellte Fragen

### Was ist `DetectNumberingWithWhitespaces` in Aspose.Words für .NET?
`DetectNumberingWithWhitespaces` ist eine Option in `TxtLoadOptions` Dadurch kann Aspose.Words Listen auch dann erkennen, wenn zwischen der Nummerierung und dem Text des Listenelements Leerzeichen vorhanden sind.

### Kann ich diese Funktion für andere Trennzeichen wie Aufzählungszeichen und Klammern verwenden?
Ja, Aspose.Words erkennt automatisch Listen mit gängigen Trennzeichen wie Aufzählungszeichen und Klammern. Die `DetectNumberingWithWhitespaces` hilft insbesondere bei Listen mit Leerzeichen.

### Was passiert, wenn ich nicht benutze `DetectNumberingWithWhitespaces`?
Ohne diese Option werden Listen mit Leerzeichen zwischen der Nummerierung und dem Text möglicherweise nicht als Listen erkannt und die Elemente könnten als einfache Absätze erscheinen.

### Ist diese Funktion in anderen Aspose-Produkten verfügbar?
Diese spezielle Funktion ist auf Aspose.Words für .NET zugeschnitten und für die Verarbeitung von Word-Dokumenten konzipiert.

### Wie kann ich eine temporäre Lizenz für Aspose.Words für .NET erhalten?
Eine vorläufige Lizenz erhalten Sie bei der [Aspose Temporäre Lizenz](https://purchase.aspose.com/temporary-license/) Seite.




{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}