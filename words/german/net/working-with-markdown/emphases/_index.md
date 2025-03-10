---
title: Schwerpunkte
linktitle: Schwerpunkte
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET hervorgehobenen Text in Markdown erstellen. Dieses Handbuch behandelt Fett-, Kursiv- und kombinierte Stile mit schrittweisen Anweisungen.
weight: 10
url: /de/net/working-with-markdown/emphases/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schwerpunkte

## Einführung

Markdown ist eine leichtgewichtige Auszeichnungssprache, mit der Sie Textdokumenten mit Formatierungselementen versehen können. In diesem Handbuch werden wir uns mit den Einzelheiten der Verwendung von Aspose.Words für .NET befassen, um Markdown-Dateien mit hervorgehobenem Text, z. B. Fett- und Kursivschrift, zu erstellen. Egal, ob Sie eine Dokumentation, einen Blogbeitrag oder einen beliebigen Text erstellen, der etwas Flair braucht, dieses Tutorial führt Sie durch jeden Schritt des Prozesses.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass wir alles haben, was wir zum Starten brauchen:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version von Aspose.Words für .NET installiert haben. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine geeignete .NET-Entwicklungsumgebung, beispielsweise Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind von Vorteil.
4. Markdown-Grundlagen: Die Vertrautheit mit der Markdown-Syntax hilft Ihnen, den Kontext besser zu verstehen.

## Namespaces importieren

Um mit Aspose.Words für .NET zu arbeiten, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer Codedatei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten des Dokuments und des DocumentBuilder

Als erstes müssen wir ein neues Word-Dokument erstellen und ein`DocumentBuilder` um mit dem Hinzufügen von Inhalten zu beginnen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Der`dataDir` Die Variable ist ein Platzhalter für das Verzeichnis, in dem Sie Ihre Markdown-Datei speichern. Achten Sie darauf, „IHR DOKUMENTVERZEICHNIS“ durch den tatsächlichen Pfad zu ersetzen.

## Schritt 2: Normalen Text schreiben

Fügen wir nun unserem Dokument einen einfachen Text hinzu. Dies dient als Grundlage für die Demonstration der Texthervorhebung.

```csharp
builder.Writeln("Markdown treats asterisks (*) and underscores (_) as indicators of emphases.");
builder.Write("You can write ");
```

 Hier,`Writeln` fügt eine neue Zeile nach dem Text hinzu, während`Write` wird auf derselben Linie fortgesetzt.

## Schritt 3: Fettgedruckten Text hinzufügen

 Um fetten Text in Markdown hinzuzufügen, umschließen Sie den gewünschten Text mit doppelten Sternchen (``). In Aspose.Words für .NET können Sie dies erreichen, indem Sie den`Bold` Eigentum der`Font` Einwände erheben gegen`true`.

```csharp
builder.Font.Bold = true;
builder.Write("bold");
builder.Font.Bold = false;
builder.Write(" or ");
```

Dieser Codeausschnitt setzt den Text „fett“ in Fettschrift und wechselt dann für das Wort „oder“ zurück zum normalen Text.

## Schritt 4: Kursiver Text hinzufügen

Kursiver Text in Markdown wird in einzelne Sternchen (`*` ). Stellen Sie auf ähnliche Weise die`Italic` Eigentum der`Font` Einwände erheben gegen`true`.

```csharp
builder.Font.Italic = true;
builder.Write("italic");
builder.Font.Italic = false;
builder.Writeln(" text.");
```

Dadurch wird „kursiv“ im Kursivstil wiedergegeben, gefolgt vom normalen Text.

## Schritt 5: Fetten und kursiven Text kombinieren

Sie können Fett- und Kursivschrift kombinieren, indem Sie den Text in drei Sternchen (`*` ). Stellen Sie beide`Bold` Und`Italic` Eigenschaften zu`true`.

```csharp
builder.Write("You can also write ");
builder.Font.Bold = true;
builder.Font.Italic = true;
builder.Write("BoldItalic");
builder.Font.Bold = false;
builder.Font.Italic = false;
builder.Write(" text.");
```

Dieser Codeausschnitt zeigt, wie Sie auf „Fett/Kursiv“ sowohl Fett- als auch Kursivschrift anwenden.

## Schritt 6: Speichern des Dokuments als Markdown

Nachdem Sie den gesamten hervorgehobenen Text hinzugefügt haben, ist es an der Zeit, das Dokument als Markdown-Datei zu speichern.

```csharp
builder.Document.Save(dataDir + "WorkingWithMarkdown.Emphases.md");
```

Diese Zeile speichert das Dokument im angegebenen Verzeichnis unter dem Dateinamen „WorkingWithMarkdown.Emphases.md“.

## Abschluss

Und da haben Sie es! Sie wissen jetzt, wie Sie mit Aspose.Words für .NET hervorgehobenen Text in Markdown erstellen. Diese leistungsstarke Bibliothek erleichtert die programmgesteuerte Bearbeitung von Word-Dokumenten und deren Export in verschiedene Formate, einschließlich Markdown. Indem Sie die in diesem Handbuch beschriebenen Schritte befolgen, können Sie Ihre Dokumente mit fettem und kursivem Text aufwerten und sie ansprechender und lesbarer machen.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET andere Textstile in Markdown verwenden?
Ja, Sie können andere Stile wie Überschriften, Listen und Codeblöcke verwenden. Aspose.Words für .NET unterstützt eine breite Palette von Markdown-Formatierungsoptionen.

### Wie kann ich Aspose.Words für .NET installieren?
 Sie können die Bibliothek herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/)und befolgen Sie die bereitgestellten Installationsanweisungen.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
 Ja, Sie können ein[Kostenlose Testversion](https://releases.aspose.com/) um die Funktionen von Aspose.Words für .NET zu testen.

### Kann ich Support erhalten, wenn ich auf Probleme stoße?
 Auf jeden Fall! Sie können die[Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8) um Hilfe von der Community und dem Aspose-Team zu erhalten.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words für .NET?
 Sie erhalten eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) um die gesamten Fähigkeiten der Bibliothek zu bewerten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
