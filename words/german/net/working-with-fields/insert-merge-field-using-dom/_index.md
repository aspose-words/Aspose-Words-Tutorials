---
title: Seriendruckfeld mit DOM einfügen
linktitle: Seriendruckfeld mit DOM einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem umfassenden Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET Seriendruckfelder in Word-Dokumente einfügen und konfigurieren.
weight: 10
url: /de/net/working-with-fields/insert-merge-field-using-dom/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Seriendruckfeld mit DOM einfügen

## Einführung

Wenn Sie mit der Dokumentverarbeitung in .NET arbeiten, sind Sie wahrscheinlich schon auf Aspose.Words gestoßen. Diese leistungsstarke Bibliothek bietet eine breite Palette von Funktionen zur programmgesteuerten Bearbeitung von Word-Dokumenten. In diesem Tutorial konzentrieren wir uns auf eine bestimmte Funktion: das Einfügen eines Seriendruckfelds mithilfe des Document Object Model (DOM) in Aspose.Words für .NET. Diese Anleitung führt Sie durch jeden Schritt, vom Einrichten Ihrer Umgebung bis zum Einfügen und Aktualisieren eines Seriendruckfelds in einem Word-Dokument.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen, um diesem Tutorial folgen zu können.

1. Grundkenntnisse in C#: Sie sollten mit der C#-Programmierung vertraut sein.
2. Visual Studio installiert: Stellen Sie sicher, dass Visual Studio oder eine andere C#-IDE auf Ihrem Computer installiert ist.
3.  Aspose.Words für .NET: Laden Sie die neueste Version von Aspose.Words für .NET herunter und installieren Sie sie von der[Veröffentlichungen](https://releases.aspose.com/words/net/).
4.  Gültige Lizenz: Wenn Sie keine Lizenz haben, können Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

## Schritt 1: Richten Sie Ihr Projekt ein

Lassen Sie uns zunächst ein neues Projekt in Visual Studio einrichten.

1. Öffnen Sie Visual Studio.
2. Neues Projekt erstellen: Gehen Sie zu Datei > Neu > Projekt. Wählen Sie eine C#-Konsolenanwendung aus.
3. Benennen Sie Ihr Projekt: Geben Sie Ihrem Projekt einen aussagekräftigen Namen und klicken Sie auf „Erstellen“.

## Schritt 2: Installieren Sie Aspose.Words

Um Aspose.Words zu verwenden, müssen Sie es zu Ihrem Projekt hinzufügen. Dies kann über den NuGet Package Manager erfolgen.

1. Öffnen Sie den NuGet-Paket-Manager: Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt und wählen Sie dann „NuGet-Pakete verwalten“ aus.
2. Suchen Sie nach Aspose.Words: Suchen Sie im NuGet-Paket-Manager nach „Aspose.Words“.
3. Installieren Sie das Paket: Klicken Sie auf „Installieren“, um Aspose.Words zu Ihrem Projekt hinzuzufügen.

## Schritt 3: Namespaces importieren

Um Aspose.Words verwenden zu können, müssen Sie die erforderlichen Namespaces in Ihr Projekt importieren. So können Sie das tun:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Schritt 4: Initialisieren Sie Ihr Dokument

Nachdem nun alles eingerichtet ist, erstellen wir ein neues Word-Dokument und initialisieren den DocumentBuilder.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Erstellen Sie das Dokument und den DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 5: Bewegen Sie den Cursor zu einem bestimmten Absatz

Als Nächstes müssen wir den Cursor zu einem bestimmten Absatz im Dokument bewegen, in den wir das Seriendruckfeld einfügen möchten.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Schritt 6: Fügen Sie das Seriendruckfeld ein

 Das Einfügen eines Seriendruckfelds ist unkompliziert. Wir verwenden das`InsertField` Methode der`DocumentBuilder` Klasse.

```csharp
// Seriendruckfeld einfügen.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Schritt 7: Konfigurieren Sie das Seriendruckfeld

Nach dem Einfügen des Seriendruckfelds können Sie verschiedene Eigenschaften festlegen, um es entsprechend Ihren Anforderungen zu konfigurieren.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Schritt 8: Aktualisieren und Speichern des Dokuments

Aktualisieren Sie abschließend das Feld, um sicherzustellen, dass alle Einstellungen angewendet werden, und speichern Sie das Dokument.

```csharp
// Aktualisieren Sie das Feld.
field.Update();

// Speichern Sie das Dokument.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Abschluss

Wenn Sie diese Schritte befolgen, können Sie mit Aspose.Words für .NET ganz einfach Seriendruckfelder in ein Word-Dokument einfügen und konfigurieren. Dieses Tutorial behandelt die wesentlichen Schritte vom Einrichten Ihrer Umgebung bis zum Speichern des endgültigen Dokuments. Mit Aspose.Words können Sie komplexe Dokumentverarbeitungsaufgaben automatisieren und so Ihre .NET-Anwendungen leistungsfähiger und effizienter machen.

## Häufig gestellte Fragen

###  Was ist ein Seriendruckfeld?
Ein Seriendruckfeld ist ein Platzhalter in einem Dokument, der dynamisch durch Daten aus einer Datenquelle, beispielsweise einer Datenbank oder einer CSV-Datei, ersetzt werden kann.

###  Kann ich Aspose.Words kostenlos nutzen?
 Aspose.Words bietet eine kostenlose Testversion an, die Sie herunterladen können[Hier](https://releases.aspose.com/)Für eine langfristige Nutzung müssen Sie eine Lizenz erwerben.

###  Wie erhalte ich eine temporäre Lizenz für Aspose.Words?
 Sie können eine temporäre Lizenz von der Aspose-Website erhalten[Hier](https://purchase.aspose.com/temporary-license/).

### Welche .NET-Versionen werden von Aspose.Words unterstützt?
Aspose.Words unterstützt mehrere Versionen von .NET, darunter .NET Framework, .NET Core und .NET Standard.

###  Wo finde ich die API-Dokumentation für Aspose.Words?
 Die API-Dokumentation ist verfügbar[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
