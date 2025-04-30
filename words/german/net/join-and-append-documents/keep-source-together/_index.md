---
"description": "Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET verhindern, dass Tabellen über mehrere Seiten hinweg umbrechen. Sorgen Sie für saubere, professionell aussehende Word-Dokumente."
"linktitle": "Tisch zusammenhalten"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Tisch zusammenhalten"
"url": "/de/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tisch zusammenhalten

## Einführung

Tabellen sind ein wesentlicher Bestandteil vieler Word-Dokumente. Manchmal kann es jedoch vorkommen, dass sich Ihre Tabelle über zwei Seiten erstreckt. Dies kann den Lesefluss Ihres Dokuments stören und dessen Lesbarkeit beeinträchtigen. Wäre es nicht schön, wenn es eine Möglichkeit gäbe, die gesamte Tabelle auf einer Seite zusammenzuhalten? Mit Aspose.Words für .NET gibt es eine einfache Lösung für dieses Problem! In diesem Tutorial erfahren Sie, wie Sie verhindern, dass Tabellen über mehrere Seiten verteilt werden, und so sicherstellen, dass Ihr Dokument ordentlich und professionell aussieht.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen, um problemlos mitmachen zu können.

### Aspose.Words für die .NET-Bibliothek

Zunächst müssen Sie Aspose.Words für .NET installieren. Dies ist die leistungsstarke Bibliothek, mit der Sie programmgesteuert mit Word-Dokumenten arbeiten können.

- [Laden Sie Aspose.Words für .NET herunter](https://releases.aspose.com/words/net/)

### Entwicklungsumgebung

Sie sollten eine Entwicklungsumgebung zum Ausführen von C#-Code eingerichtet haben, beispielsweise:

- Visual Studio (jede aktuelle Version)
- .NET Framework 2.0 oder höher

### Ein Word-Dokument mit einer Tabelle

Sie benötigen ein Word-Dokument mit einer Tabelle. In diesem Tutorial arbeiten wir mit einem Beispieldokument namens `"Table spanning two pages.docx"`. Diese Datei enthält eine Tabelle, die sich derzeit über zwei Seiten erstreckt.

### Temporäre Lizenz (optional)

Während Aspose.Words mit einer kostenlosen Testversion kommt, möchten Sie vielleicht eine [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) um das volle Potenzial der Bibliothek auszuschöpfen.

## Pakete importieren

Bevor wir Code schreiben, müssen wir die erforderlichen Namespaces für die Arbeit mit Aspose.Words für .NET importieren. Fügen Sie die folgenden Importe oben in Ihre Codedatei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Diese Namespaces ermöglichen Ihnen den Zugriff auf Klassen wie `Document`, `Table`, `Cell`, und andere, die wir in diesem Tutorial verwenden werden.

## Schritt 1: Laden Sie das Dokument

Als erstes müssen wir das Word-Dokument laden, das die Tabelle enthält. Dazu verwenden wir die `Document` Klasse von Aspose.Words. Mit dieser Klasse können Sie Word-Dateien programmgesteuert öffnen und bearbeiten.

```csharp
// Der Pfad zum Dokumentenverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

In diesem Codeausschnitt geben wir den Speicherort unseres Dokuments an. Ersetzen Sie `"YOUR DOCUMENTS DIRECTORY"` mit dem tatsächlichen Verzeichnis, in dem Ihr Dokument gespeichert ist.

## Schritt 2: Zugriff auf die Tabelle

Sobald das Dokument geladen ist, besteht der nächste Schritt darin, auf die Tabelle zuzugreifen, die wir zusammenhalten möchten. In diesem Beispiel gehen wir davon aus, dass es sich bei der Tabelle um die erste Tabelle im Dokument handelt.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Diese Codezeile findet die erste Tabelle im Dokument. Die `GetChild` Methode ruft einen bestimmten Knotentyp ab, der in diesem Fall ist `NodeType.Table`. Der `0` zeigt an, dass wir die erste Tabelle wollen, und die `true` Das Flag stellt sicher, dass wir alle untergeordneten Knoten rekursiv durchsuchen.

## Schritt 3: Durchlaufen der Tabellenzellen

Nun müssen wir jede Zelle der Tabelle durchlaufen. Da eine Tabelle mehrere Zeilen und jede Zeile mehrere Zellen enthält, durchlaufen wir jede Zelle und stellen sicher, dass sie nicht über mehrere Seiten hinweg umbricht.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Hier, `GetChildNodes` ruft alle Zellen der Tabelle ab und wir durchlaufen jede einzelne. Die `EnsureMinimum()` Bei dieser Methode wird sichergestellt, dass jede Zelle mindestens einen Absatz enthält, da eine leere Zelle später zu Problemen führen könnte.

## Schritt 4: KeepWithNext-Eigenschaft festlegen

Um zu verhindern, dass die Tabelle über mehrere Seiten hinweg umbricht, müssen wir Folgendes festlegen: `KeepWithNext` -Eigenschaft für jeden Absatz in der Tabelle. Diese Eigenschaft stellt sicher, dass der Absatz mit dem nächsten Absatz verbunden bleibt, wodurch Seitenumbrüche zwischen ihnen effektiv verhindert werden.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Diese Schleife prüft jeden Absatz in jeder Zelle. Die Bedingung stellt sicher, dass wir nicht die `KeepWithNext` -Eigenschaft auf den letzten Absatz in der letzten Zeile. Andernfalls hätte die Eigenschaft keine Auswirkung, da kein nächster Absatz vorhanden ist.

## Schritt 5: Speichern Sie das Dokument

Schließlich, nach der Anwendung der `KeepWithNext` Eigenschaft müssen wir das geänderte Dokument speichern.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Diese Zeile speichert das aktualisierte Dokument unter einem neuen Namen, wobei die Originaldatei erhalten bleibt. Sie können nun die resultierende Datei öffnen und sehen, dass die Tabelle nicht mehr auf zwei Seiten verteilt ist!

## Abschluss

Und da haben Sie es! Mit diesen einfachen Schritten können Sie mit Aspose.Words für .NET ganz einfach verhindern, dass Tabellen in Word-Dokumenten über mehrere Seiten verteilt werden. Ob Sie an Berichten, Verträgen oder anderen Dokumenten arbeiten – intakte Tabellen sorgen für ein eleganteres und professionelleres Erscheinungsbild.

Das Besondere an Aspose.Words ist seine Flexibilität und Benutzerfreundlichkeit. Sie können Word-Dokumente programmgesteuert bearbeiten, ohne dass Microsoft Word auf Ihrem Rechner installiert sein muss. Nachdem Sie nun den Dreh raus haben, Tabellen zusammenzuhalten, erkunden Sie die weiteren Funktionen der Bibliothek, um Ihre Fähigkeiten in der Dokumentenverarbeitung auf das nächste Level zu heben!

## Häufig gestellte Fragen

### Warum ist meine Tabelle nach Verwendung dieses Codes immer noch seitenübergreifend?

Wenn Ihr Tisch immer noch bricht, stellen Sie sicher, dass Sie die `KeepWithNext` -Eigenschaft korrekt. Überprüfen Sie noch einmal, ob diese Eigenschaft für alle Absätze außer dem letzten in jeder Zelle festgelegt ist.

### Kann ich nur bestimmte Zeilen zusammenhalten?

Ja, Sie können selektiv anwenden die `KeepWithNext` -Eigenschaft auf bestimmte Zeilen oder Absätze innerhalb der Tabelle, um zu steuern, welche Teile zusammenbleiben sollen.

### Funktioniert diese Methode mit großen Tabellen?

Bei sehr großen Tabellen kann Word diese dennoch auf mehrere Seiten aufteilen, wenn nicht genügend Platz vorhanden ist, um die gesamte Tabelle auf einer Seite unterzubringen. Passen Sie die Formatierung oder die Ränder Ihrer Tabelle an größere Tabellen an.

### Kann ich diese Methode mit anderen Dokumentformaten verwenden?

Ja! Aspose.Words für .NET unterstützt viele Formate wie DOC, DOCX, PDF und andere. Dieselbe Methode funktioniert für alle Formate, die Tabellen unterstützen.

### Ist Aspose.Words für .NET eine kostenlose Bibliothek?

Aspose.Words für .NET bietet eine kostenlose Testversion an. Für den vollen Zugriff auf alle Funktionen ist jedoch eine Lizenz erforderlich. Weitere Lizenzoptionen finden Sie auf der [Aspose-Kaufseite](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}