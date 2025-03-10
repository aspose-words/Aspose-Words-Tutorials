---
title: Mehrstufige Listenformatierung im Word-Dokument
linktitle: Mehrstufige Listenformatierung im Word-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET mehrstufige Listenformatierungen in Word-Dokumenten meistern. Verbessern Sie mühelos die Dokumentstruktur.
weight: 10
url: /de/net/document-formatting/multilevel-list-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mehrstufige Listenformatierung im Word-Dokument

## Einführung

Wenn Sie Entwickler sind und die Erstellung und Formatierung von Word-Dokumenten automatisieren möchten, ist Aspose.Words für .NET eine bahnbrechende Neuerung. Heute werden wir uns damit befassen, wie Sie mit dieser leistungsstarken Bibliothek die mehrstufige Listenformatierung meistern können. Ob Sie strukturierte Dokumente erstellen, Berichte skizzieren oder technische Dokumentationen generieren, mehrstufige Listen können die Lesbarkeit und Organisation Ihrer Inhalte verbessern.

## Voraussetzungen

Bevor wir uns in die Einzelheiten stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen, um diesem Tutorial folgen zu können.

1. Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine Entwicklungsumgebung eingerichtet haben. Visual Studio ist eine gute Wahl.
2.  Aspose.Words für .NET: Laden Sie die Bibliothek Aspose.Words für .NET herunter und installieren Sie sie. Sie erhalten sie[Hier](https://releases.aspose.com/words/net/).
3.  Lizenz: Besorgen Sie sich eine temporäre Lizenz, wenn Sie keine Volllizenz haben.[Hier](https://purchase.aspose.com/temporary-license/).
4. Grundlegende C#-Kenntnisse: Vertrautheit mit C# und dem .NET-Framework ist von Vorteil.

## Namespaces importieren

Um Aspose.Words für .NET in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. So gehen Sie dabei vor:

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## Schritt 1: Initialisieren Sie Ihr Dokument und Ihren Builder

Zunächst erstellen wir ein neues Word-Dokument und initialisieren den DocumentBuilder. Die DocumentBuilder-Klasse bietet Methoden zum Einfügen von Inhalten in das Dokument.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Standardnummerierung anwenden

 Um mit einer nummerierten Liste zu beginnen, verwenden Sie die`ApplyNumberDefault` Methode. Dadurch wird die Standardformatierung für nummerierte Listen eingerichtet.

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

 In diesen Zeilen`ApplyNumberDefault` beginnt die nummerierte Liste und`Writeln` fügt Elemente zur Liste hinzu.

## Schritt 3: Einrückung für Unterebenen

 Um als nächstes Unterebenen innerhalb Ihrer Liste zu erstellen, verwenden Sie die`ListIndent` -Methode. Diese Methode rückt das Listenelement ein, sodass es eine Unterebene des vorherigen Elements darstellt.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

Dieser Codeausschnitt rückt die Elemente ein und erstellt so eine Liste zweiter Ebene.

## Schritt 4: Weitere Einrückung für tiefere Ebenen

Sie können mit weiteren Einrückungen tiefere Ebenen in Ihrer Liste erstellen. Hier erstellen wir eine dritte Ebene.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

Nun haben Sie eine Liste der dritten Ebene unter „Punkt 2.2“.

## Schritt 5: Ausrücken, um zu höheren Ebenen zurückzukehren

 Um zu einer höheren Ebene zurückzukehren, verwenden Sie die`ListOutdent` -Methode. Dadurch wird das Element auf die vorherige Listenebene zurückversetzt.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

Damit gelangt der „Punkt 2.3“ wieder auf die zweite Ebene.

## Schritt 6: Nummerierung entfernen

Wenn Sie mit Ihrer Liste fertig sind, können Sie die Nummerierung entfernen, um mit normalem Text oder einer anderen Formatierungsart fortzufahren.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

Dieser Codeschnipsel vervollständigt die Liste und beendet die Nummerierung.

## Schritt 7: Speichern Sie Ihr Dokument

Speichern Sie das Dokument abschließend im gewünschten Verzeichnis.

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

Dadurch wird Ihr schön formatiertes Dokument mit mehrstufigen Listen gespeichert.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich eine mehrstufige Liste in einem Word-Dokument mit Aspose.Words für .NET erstellt. Mit dieser leistungsstarken Bibliothek können Sie komplexe Dokumentformatierungsaufgaben mühelos automatisieren. Denken Sie daran, dass die Beherrschung dieser Tools nicht nur Zeit spart, sondern auch Konsistenz und Professionalität bei der Dokumenterstellung gewährleistet.

## Häufig gestellte Fragen

### Kann ich den Stil der Listennummerierung anpassen?
 Ja, Aspose.Words für .NET ermöglicht Ihnen die Anpassung des Listennummerierungsstils mithilfe der`ListTemplate` Klasse.

### Wie füge ich Aufzählungspunkte anstelle von Zahlen hinzu?
 Sie können Aufzählungszeichen hinzufügen, indem Sie das`ApplyBulletDefault` Methode anstelle von`ApplyNumberDefault`.

### Ist es möglich, die Nummerierung einer vorherigen Liste fortzusetzen?
 Ja, Sie können die Nummerierung fortsetzen, indem Sie`ListFormat.List` Eigenschaft zum Verknüpfen mit einer vorhandenen Liste.

### Wie ändere ich die Einrückungsebene dynamisch?
 Sie können die Einrückungsebene dynamisch ändern, indem Sie`ListIndent` Und`ListOutdent` Methoden nach Bedarf.

### Kann ich mehrstufige Listen in anderen Dokumentformaten wie PDF erstellen?
Ja, Aspose.Words unterstützt das Speichern von Dokumenten in verschiedenen Formaten, einschließlich PDF, unter Beibehaltung der Formatierung.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
