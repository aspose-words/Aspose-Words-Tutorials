---
title: Escape-URI im PDF-Dokument
linktitle: Escape-URI im PDF-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET URIs in PDFs maskieren. Diese ausführliche Anleitung führt Sie Schritt für Schritt durch den Vorgang.
weight: 10
url: /de/net/programming-with-pdfsaveoptions/escape-uri/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Escape-URI im PDF-Dokument

## Einführung

Hallo! Haben Sie sich schon einmal gefragt, wie Sie mit URIs umgehen, wenn Sie ein Word-Dokument mit Aspose.Words für .NET als PDF speichern? Dann sind Sie hier richtig! Heute werden wir uns eingehend mit dem Escapen von URIs in PDF-Dokumenten befassen, um sicherzustellen, dass sie beim Konvertieren Ihres Dokuments korrekt funktionieren. Lassen Sie uns diese Reise gemeinsam Schritt für Schritt antreten und sicherstellen, dass Sie jedes Konzept auf dem Weg verstehen.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version haben. Sie können es herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
3. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie über Grundkenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Dies ist für den Zugriff auf die Aspose.Words-Funktionen von entscheidender Bedeutung.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Okay, lassen Sie uns den Prozess in leicht verständliche Schritte aufteilen. Folgen Sie den Anweisungen und Sie werden im Handumdrehen ein Profi im Escapen von URIs sein!

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Bevor Sie sich in den Code vertiefen, richten Sie den Pfad zu Ihrem Dokumentverzeichnis ein. Hier werden Ihre Dateien gespeichert.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Sie Ihr PDF-Dokument speichern möchten.

## Schritt 2: Neues Dokument erstellen

Als Nächstes erstellen wir mit Aspose.Words ein neues Dokument. Dieses Dokument dient uns als Leinwand zum Einfügen von Hyperlinks.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier,`Document` ist Ihr neues Word-Dokument und`DocumentBuilder` ist eine Hilfsklasse, die den Dokumenterstellungsprozess vereinfacht.

## Schritt 3: Einfügen eines Hyperlinks

Fügen wir nun einen Hyperlink in das Dokument ein. Dieser Hyperlink steht im Mittelpunkt unseres URI-Escape-Prozesses.

```csharp
builder.InsertHyperlink("Testlink", "https://www.google.com/search?q= aspose", false);
```

 In dieser Zeile`"Testlink"` ist der Anzeigetext für den Hyperlink und`"https://www.google.com/search?q= aspose"` ist die URL. Die`false` Der Parameter gibt an, dass der Link nicht als Hyperlink formatiert werden soll (d. h. er wird nicht unterstrichen und blau dargestellt).

## Schritt 4: Speichern Sie das Dokument als PDF

Speichern Sie das Dokument abschließend als PDF. Dabei kümmert sich Aspose.Words um das Escapen der URI in der PDF-Ausgabe.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EscapeUri.pdf");
```

 Diese Zeile speichert das Dokument im angegebenen Verzeichnis mit dem Dateinamen`WorkingWithPdfSaveOptions.EscapeUri.pdf`.

## Abschluss

Und da haben Sie es! Sie haben gerade gelernt, wie Sie URIs maskieren, wenn Sie ein Word-Dokument mit Aspose.Words für .NET als PDF speichern. Dieser Prozess stellt sicher, dass Ihre Hyperlinks im resultierenden PDF funktionsfähig und richtig formatiert bleiben. 

Denken Sie daran, dass die Beherrschung dieser kleinen, aber wichtigen Techniken die Qualität und Funktionalität Ihrer Dokumente erheblich verbessern kann. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?

Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente in .NET-Anwendungen erstellen, bearbeiten und konvertieren können.

### Warum ist die URI-Escape-Funktion in PDFs wichtig?

Durch das URI-Escaping wird sichergestellt, dass Sonderzeichen in URLs richtig interpretiert werden. Dadurch werden defekte Links verhindert und sichergestellt, dass sie wie vorgesehen funktionieren.

### Kann ich in Aspose.Words für .NET andere Linktypen verwenden?

Auf jeden Fall! Aspose.Words unterstützt verschiedene Arten von Links, darunter interne Dokumentlinks, Lesezeichen und externe URLs.

### Wie kann ich eine kostenlose Testversion von Aspose.Words für .NET erhalten?

 Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/).

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?

 Die ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
