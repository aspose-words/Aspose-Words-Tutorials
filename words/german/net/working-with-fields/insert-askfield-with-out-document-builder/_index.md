---
title: ASKField ohne Document Builder einfügen
linktitle: ASKField ohne Document Builder einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie ein ASK-Feld einfügen, ohne Document Builder in Aspose.Words für .NET zu verwenden. Folgen Sie dieser Anleitung, um Ihre Word-Dokumente dynamisch zu verbessern.
weight: 10
url: /de/net/working-with-fields/insert-askfield-with-out-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ASKField ohne Document Builder einfügen

## Einführung

Möchten Sie die Dokumentenautomatisierung mit Aspose.Words für .NET meistern? Dann sind Sie hier genau richtig! Heute zeigen wir Ihnen, wie Sie ein ASK-Feld einfügen, ohne einen Dokumentgenerator zu verwenden. Dies ist eine praktische Funktion, wenn Sie möchten, dass Ihr Dokument Benutzer zu bestimmten Eingaben auffordert, wodurch Ihre Word-Dokumente interaktiver und dynamischer werden. Lassen Sie uns also loslegen und Ihre Dokumente intelligenter machen!

## Voraussetzungen

Bevor wir uns mit dem Code beschäftigen, stellen wir sicher, dass wir alles eingerichtet haben:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie diese Bibliothek installiert haben. Wenn nicht, können Sie sie hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine geeignete IDE wie Visual Studio.
3. .NET Framework: Stellen Sie sicher, dass Sie .NET Framework installiert haben.

Großartig! Jetzt, da alles bereit ist, beginnen wir mit dem Importieren der erforderlichen Namespaces.

## Namespaces importieren

Als Erstes müssen wir den Aspose.Words-Namespace importieren, um auf alle Funktionen von Aspose.Words für .NET zugreifen zu können. So geht's:

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Schritt 1: Neues Dokument erstellen

Bevor wir ein ASK-Feld einfügen können, benötigen wir ein Dokument, mit dem wir arbeiten können. So erstellen Sie ein neues Dokument:

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Dokumenterstellung.
Document doc = new Document();
```

Dieser Codeausschnitt richtet ein neues Word-Dokument ein, in das wir unser ASK-Feld einfügen.

## Schritt 2: Zugriff auf den Absatzknoten

In einem Word-Dokument ist der Inhalt in Knoten organisiert. Wir müssen auf den ersten Absatzknoten zugreifen, in den wir unser ASK-Feld einfügen:

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Diese Codezeile ruft den ersten Absatz im Dokument ab und ist bereit für die Einfügung unseres ASK-Felds.

## Schritt 3: Einfügen des ASK-Feldes

Kommen wir nun zum Hauptvorgang – dem Einfügen des ASK-Felds. Dieses Feld fordert den Benutzer beim Öffnen des Dokuments zur Eingabe auf.

```csharp
// Fügen Sie das ASK-Feld ein.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Hier fügen wir dem Absatz ein ASK-Feld hinzu. Einfach, oder?

## Schritt 4: Konfigurieren Sie das ASK-Feld

Wir müssen einige Eigenschaften festlegen, um das Verhalten des ASK-Felds zu definieren. Lassen Sie uns den Lesezeichennamen, den Eingabeaufforderungstext, die Standardantwort und das Serienbriefverhalten konfigurieren:

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName: Eine eindeutige Kennung für das ASK-Feld.
- PromptText: Der Text, der den Benutzer zur Eingabe auffordert.
- DefaultResponse: Die vorausgefüllte Antwort, die der Benutzer ändern kann.
- PromptOnceOnMailMerge: Legt fest, ob die Eingabeaufforderung während eines Serienbriefvorgangs nur einmal angezeigt wird.

## Schritt 5: Aktualisieren Sie das Feld

Nachdem wir das ASK-Feld konfiguriert haben, müssen wir es aktualisieren, um sicherzustellen, dass alle Einstellungen korrekt angewendet werden:

```csharp
field.Update();
```

Dieser Befehl stellt sicher, dass unser ASK-Feld bereit und im Dokument richtig eingerichtet ist.

## Schritt 6: Speichern Sie das Dokument

Zum Schluss speichern wir das Dokument in unserem angegebenen Verzeichnis:

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Diese Zeile speichert das Dokument mit dem eingefügten ASK-Feld. Und schon ist Ihr Dokument mit einem dynamischen ASK-Feld ausgestattet!

## Abschluss

Herzlichen Glückwunsch! Sie haben gerade mit Aspose.Words für .NET ohne den Document Builder ein ASK-Feld zu einem Word-Dokument hinzugefügt. Diese Funktion kann die Benutzerinteraktion mit Ihren Dokumenten erheblich verbessern und sie flexibler und benutzerfreundlicher machen. Experimentieren Sie weiter mit verschiedenen Feldern und Eigenschaften, um das volle Potenzial von Aspose.Words auszuschöpfen. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist ein ASK-Feld in Aspose.Words?
Ein ASK-Feld in Aspose.Words ist ein Feld, das den Benutzer beim Öffnen des Dokuments zur Eingabe bestimmter Eingaben auffordert und so eine dynamische Dateneingabe ermöglicht.

### Kann ich mehrere ASK-Felder in einem einzigen Dokument verwenden?
Ja, Sie können mehrere ASK-Felder in ein Dokument einfügen, jedes mit einzigartigen Eingabeaufforderungen und Antworten.

###  Was ist der Zweck der`PromptOnceOnMailMerge` property?
 Der`PromptOnceOnMailMerge` Die Eigenschaft legt fest, ob die ASK-Eingabeaufforderung während eines Serienbriefvorgangs nur einmal oder jedes Mal angezeigt wird.

### Muss ich das ASK-Feld aktualisieren, nachdem ich seine Eigenschaften festgelegt habe?
Ja, durch die Aktualisierung des ASK-Felds wird sichergestellt, dass alle Eigenschaften korrekt angewendet werden und das Feld wie erwartet funktioniert.

### Kann ich den Eingabeaufforderungstext und die Standardantwort anpassen?
Auf jeden Fall! Sie können benutzerdefinierte Eingabeaufforderungstexte und Standardantworten festlegen, um das ASK-Feld an Ihre spezifischen Anforderungen anzupassen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
