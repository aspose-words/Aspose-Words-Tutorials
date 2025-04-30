---
"description": "Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie benutzerdefinierte Schriftartenordner in Aspose.Words für .NET einrichten. Ideal für Entwickler, die Dokumentschriftarten verbessern möchten."
"linktitle": "Schriftartenordner festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Schriftartenordner festlegen"
"url": "/de/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Schriftartenordner festlegen

## Einführung

Hallo! Bereit, in die Welt der benutzerdefinierten Schriftarten in Aspose.Words für .NET einzutauchen? Los geht’s! Dieses Tutorial führt Sie durch die Einrichtung benutzerdefinierter Schriftartenordner und stellt sicher, dass Ihre Dokumente genau Ihren Wünschen entsprechen. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, diese Anleitung führt Sie Schritt für Schritt durch die einzelnen Schritte. Also, lassen Sie uns Ihre Schriftarten fantastisch aussehen!

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

- Aspose.Words für .NET: Sie können [herunterladen](https://releases.aspose.com/words/net/) es, falls Sie das nicht bereits getan haben.
- Visual Studio: Jede Version funktioniert, aber die neueste ist immer die beste.
- Ein Dokument: Für dieses Tutorial verwenden wir ein Word-Dokument. Sie können ein eigenes erstellen oder ein vorhandenes verwenden.
- Benutzerdefinierte Schriftarten: Halten Sie einige benutzerdefinierte Schriftarten bereit. Wir verwenden diese, um das Einrichten von Schriftartenordnern zu demonstrieren.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Dies ist wichtig für den Zugriff auf die benötigten Klassen und Methoden von Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nachdem diese Namespaces importiert wurden, können wir mit der Einrichtung unserer benutzerdefinierten Schriftartordner beginnen.

## Schritt 1: Definieren Sie Ihr Dokumentverzeichnis

Beginnen wir mit der Definition des Pfads zu Ihrem Dokumentverzeichnis. Hier wird Ihr Word-Dokument gespeichert. Wir verwenden eine Variable namens `dataDir` um diesen Pfad zu speichern.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad zu Ihrem Verzeichnis. Dies ist wichtig, da Aspose.Words wissen muss, wo Ihr Dokument zu finden ist.

## Schritt 2: Schriftartquellen festlegen

Als nächstes müssen wir die Schriftartenquellen einrichten. Hier teilen wir Aspose.Words mit, wo unsere benutzerdefinierten Schriftarten zu finden sind. Wir verwenden die `FontSettings.DefaultInstance.SetFontsSources` Methode, um dies zu erreichen.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Folgendes tun wir:

- SystemFontSource: Dies weist Aspose.Words an, die Standardschriftarten des Systems zu verwenden.
- FolderFontSource: Hier geben wir den Ordner an, der unsere benutzerdefinierten Schriftarten enthält. Ersetzen Sie `"C:\\MyFonts\\"` mit dem Pfad zu Ihrem benutzerdefinierten Schriftartenverzeichnis. Die `true` Der Parameter gibt an, dass auch Unterverzeichnisse einbezogen werden sollen.

## Schritt 3: Laden Sie Ihr Dokument

Nachdem wir nun unsere Schriftquellen eingerichtet haben, ist es an der Zeit, das Dokument zu laden, mit dem wir arbeiten möchten. Wir verwenden die `Document` Klasse von Aspose.Words hierfür.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Stellen Sie sicher, dass `"Rendering.docx"` ist der Name Ihres Word-Dokuments. Wenn Ihr Dokument einen anderen Namen hat, aktualisieren Sie diesen bitte entsprechend.

## Schritt 4: Speichern Sie Ihr Dokument als PDF

Speichern wir unser Dokument als PDF, um die benutzerdefinierten Schriftarten in Aktion zu sehen. Wir verwenden die `Save` Methode der `Document` Klasse.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Dadurch wird Ihr Dokument als PDF im angegebenen Verzeichnis gespeichert, wobei die zuvor eingerichteten benutzerdefinierten Schriftarten verwendet werden.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich benutzerdefinierte Schriftartenordner in Aspose.Words für .NET eingerichtet und Ihr Dokument mit diesen benutzerdefinierten Schriftarten als PDF gespeichert. Ziemlich cool, oder? Das Anpassen von Schriftarten kann das Erscheinungsbild Ihrer Dokumente erheblich verbessern, und jetzt wissen Sie genau, wie es geht. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Wie installiere ich Aspose.Words für .NET?

Du kannst [herunterladen](https://releases.aspose.com/words/net/) die neueste Version von Aspose.Words für .NET von der Website.

### Kann ich mehrere benutzerdefinierte Schriftartenordner verwenden?

Ja, Sie können mehrere hinzufügen `FolderFontSource` Instanzen zum `SetFontsSources` Methode zum Verwenden von Schriftarten aus verschiedenen Verzeichnissen.

### Ist es notwendig, Systemschriftarten einzubinden?

Das Einbinden von Systemschriftarten ist optional, wird aber empfohlen, um sicherzustellen, dass alle Standardschriftarten verfügbar sind.

### Welche Dateitypen werden von Aspose.Words unterstützt?

Aspose.Words unterstützt eine Vielzahl von Dateiformaten, darunter DOCX, DOC, PDF, TXT, HTML und viele mehr.

### Wie kann ich eine temporäre Lizenz für Aspose.Words erhalten?

Sie erhalten eine [vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) von der Aspose-Website, um alle Funktionen von Aspose.Words auszuprobieren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}