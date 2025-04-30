---
"description": "Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Text durchgestrichen formatieren. Verbessern Sie Ihre Fähigkeiten zur Dokumentverarbeitung."
"linktitle": "Durchgestrichen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Durchgestrichen"
"url": "/de/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Durchgestrichen

## Einführung

Willkommen zu dieser ausführlichen Anleitung zum Anwenden von Durchstreichformatierungen auf Text mit Aspose.Words für .NET. Wenn Sie Ihre Fähigkeiten zur Dokumentverarbeitung verbessern und Ihrem Text eine einzigartige Note verleihen möchten, sind Sie hier genau richtig. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Aspose.Words für .NET: Laden Sie es herunter [Hier](https://releases.aspose.com/words/net/).
- .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem System installiert ist.
- Entwicklungsumgebung: Eine IDE wie Visual Studio.
- Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind erforderlich.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces importieren. Diese sind für den Zugriff auf die Aspose.Words-Bibliothek und ihre Funktionen unerlässlich.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Initialisieren Sie den DocumentBuilder

Der `DocumentBuilder` Die Klasse ist ein leistungsstarkes Tool in Aspose.Words, mit dem Sie Ihrem Dokument problemlos Inhalte hinzufügen können.

```csharp
// Initialisieren Sie einen DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Schritt 2: Durchgestrichene Eigenschaft festlegen

Wenden wir nun die Durchstreichungseigenschaft auf unseren Text an. Dazu setzen wir die `StrikeThrough` Eigentum der `Font` Einwände erheben gegen `true`.

```csharp
// Machen Sie den Text durchgestrichen.
builder.Font.StrikeThrough = true;
```

## Schritt 3: Text durchgestrichen schreiben

Nachdem wir die Durchstreichungseigenschaft festgelegt haben, können wir nun unseren Text hinzufügen. Die `Writeln` Die Methode fügt den Text zum Dokument hinzu.

```csharp
// Schreiben Sie Text mit Durchgestrichen.
builder.Writeln("This text will be StrikeThrough");
```

## Abschluss

Und fertig! Sie haben Ihrem Text mit Aspose.Words für .NET erfolgreich Durchstreichungsformatierungen hinzugefügt. Diese leistungsstarke Bibliothek eröffnet Ihnen unzählige Möglichkeiten zur Dokumentenverarbeitung und -anpassung. Ob Sie Berichte, Briefe oder andere Dokumente erstellen – die Beherrschung dieser Funktionen steigert zweifellos Ihre Produktivität und die Qualität Ihrer Ergebnisse.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Dokumentverarbeitungsbibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können.

### Kann ich Aspose.Words für .NET in einem kommerziellen Projekt verwenden?
Ja, Sie können Aspose.Words für .NET in kommerziellen Projekten verwenden. Informationen zu Kaufoptionen finden Sie im [Kaufseite](https://purchase.aspose.com/buy).

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
Ja, Sie können eine kostenlose Testversion herunterladen [Hier](https://releases.aspose.com/).

### Wie erhalte ich Unterstützung für Aspose.Words für .NET?
Sie erhalten Unterstützung von der Aspose-Community und Experten auf dem [Support-Forum](https://forum.aspose.com/c/words/8).

### Kann ich mit Aspose.Words für .NET andere Textformatierungsoptionen anwenden?
Absolut! Aspose.Words für .NET unterstützt eine Vielzahl von Textformatierungsoptionen, darunter Fettdruck, Kursivschrift, Unterstrichenheit und mehr.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}