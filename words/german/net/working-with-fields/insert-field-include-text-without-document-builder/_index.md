---
title: Feld einfügen, Text einschließen ohne Dokumentgenerator
linktitle: FieldIncludeText ohne Document Builder einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie mit unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie in Aspose.Words für .NET einen FieldIncludeText einfügen, ohne DocumentBuilder zu verwenden.
weight: 10
url: /de/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Feld einfügen, Text einschließen ohne Dokumentgenerator

## Einführung

In der Welt der Dokumentenautomatisierung und -bearbeitung ist Aspose.Words für .NET ein leistungsstarkes Tool. Heute tauchen wir in eine detaillierte Anleitung ein, wie Sie einen FieldIncludeText einfügen, ohne DocumentBuilder zu verwenden. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess und stellt sicher, dass Sie jeden Teil des Codes und seinen Zweck verstehen.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version installiert haben. Sie können sie herunterladen von[Hier](https://releases.aspose.com/words/net/).
2. .NET-Entwicklungsumgebung: Jede .NET-kompatible IDE wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung erleichtern Ihnen den Lernprozess.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren. Diese Namespaces bieten Zugriff auf die Klassen und Methoden, die zum Bearbeiten von Word-Dokumenten erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Lassen Sie uns nun das Beispiel in mehrere Schritte unterteilen. Jeder Schritt wird zur Gewährleistung der Klarheit ausführlich erklärt.

## Schritt 1: Verzeichnispfad festlegen

Der erste Schritt besteht darin, den Pfad zu Ihrem Dokumentverzeichnis zu definieren. Hier werden Ihre Word-Dokumente gespeichert und abgerufen.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Schritt 2: Erstellen Sie das Dokument und den Absatz

Als nächstes erstellen wir ein neues Dokument und einen Absatz innerhalb dieses Dokuments. Dieser Absatz enthält das Feld FieldIncludeText.

```csharp
// Erstellen Sie das Dokument und den Absatz.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Schritt 3: FieldIncludeText-Feld einfügen

Nun fügen wir das Feld FieldIncludeText in den Absatz ein. Mit diesem Feld können Sie Text aus einem anderen Dokument einfügen.

```csharp
// Fügen Sie das Feld FieldIncludeText ein.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Schritt 4: Feldeigenschaften festlegen

Wir müssen die Eigenschaften für das Feld FieldIncludeText angeben. Dazu gehört das Festlegen des Lesezeichennamens und des vollständigen Pfads des Quelldokuments.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Schritt 5: Absatz zum Dokument hinzufügen

Nachdem das Feld eingerichtet ist, fügen wir den Absatz an den ersten Abschnittstext des Dokuments an.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Schritt 6: Feld aktualisieren

Bevor wir das Dokument speichern, müssen wir FieldIncludeText aktualisieren, um sicherzustellen, dass der richtige Inhalt aus dem Quelldokument übernommen wird.

```csharp
fieldIncludeText.Update();
```

## Schritt 7: Speichern Sie das Dokument

Abschließend speichern wir das Dokument im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie problemlos einen FieldIncludeText einfügen, ohne DocumentBuilder in Aspose.Words für .NET zu verwenden. Dieser Ansatz bietet eine optimierte Möglichkeit, Inhalte aus einem Dokument in ein anderes einzufügen, wodurch Ihre Aufgaben zur Dokumentautomatisierung erheblich vereinfacht werden.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?  
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die Arbeit mit Word-Dokumenten in .NET-Anwendungen. Sie ermöglicht das programmgesteuerte Erstellen, Bearbeiten und Konvertieren von Dokumenten.

### Warum FieldIncludeText verwenden?  
FieldIncludeText ist nützlich, um Inhalte dynamisch aus einem Dokument in ein anderes einzufügen und so modularere und wartbarere Dokumente zu ermöglichen.

### Kann ich mit dieser Methode Text aus anderen Dateiformaten einfügen?  
FieldIncludeText funktioniert speziell mit Word-Dokumenten. Für andere Formate benötigen Sie möglicherweise andere Methoden oder Klassen, die von Aspose.Words bereitgestellt werden.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?  
Ja, Aspose.Words für .NET unterstützt .NET Framework, .NET Core und .NET 5/6.

### Wie kann ich eine kostenlose Testversion von Aspose.Words für .NET erhalten?  
 Eine kostenlose Testversion erhalten Sie bei[Hier](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
