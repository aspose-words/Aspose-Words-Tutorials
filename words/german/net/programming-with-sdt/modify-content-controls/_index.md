---
title: Inhaltssteuerelemente ändern
linktitle: Inhaltssteuerelemente ändern
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie strukturierte Dokument-Tags in Word mit Aspose.Words für .NET ändern. Aktualisieren Sie Text, Dropdowns und Bilder Schritt für Schritt.
weight: 10
url: /de/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inhaltssteuerelemente ändern

## Einführung

Wenn Sie schon einmal mit Word-Dokumenten gearbeitet und strukturierte Inhaltssteuerelemente – wie einfachen Text, Dropdown-Listen oder Bilder – mit Aspose.Words für .NET ändern mussten, sind Sie hier richtig! Structured Document Tags (SDTs) sind leistungsstarke Tools, die die Dokumentautomatisierung einfacher und flexibler machen. In diesem Tutorial erfahren Sie, wie Sie diese SDTs an Ihre Bedürfnisse anpassen können. Egal, ob Sie Text aktualisieren, Dropdown-Auswahlen ändern oder Bilder austauschen, diese Anleitung führt Sie Schritt für Schritt durch den Vorgang.

## Voraussetzungen

Bevor wir uns in die Einzelheiten der Änderung von Inhaltssteuerelementen stürzen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET installiert: Stellen Sie sicher, dass Sie die Aspose.Words-Bibliothek installiert haben. Wenn nicht, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).

2. Grundkenntnisse in C#: Dieses Tutorial setzt voraus, dass Sie mit den grundlegenden Konzepten der C#-Programmierung vertraut sind.

3. Eine .NET-Entwicklungsumgebung: Sie sollten eine IDE wie Visual Studio zum Ausführen von .NET-Anwendungen eingerichtet haben.

4. Ein Beispieldokument: Wir verwenden ein Beispiel-Word-Dokument mit verschiedenen SDT-Typen. Sie können das aus dem Beispiel verwenden oder Ihr eigenes erstellen.

5.  Zugriff auf die Aspose-Dokumentation: Ausführlichere Informationen finden Sie in der[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/).

## Namespaces importieren

Um mit Aspose.Words arbeiten zu können, müssen Sie die relevanten Namespaces in Ihr C#-Projekt importieren. So geht's:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Über diese Namespaces erhalten Sie Zugriff auf die Klassen und Methoden, die zum Bearbeiten strukturierter Dokument-Tags in Ihren Word-Dokumenten erforderlich sind.

## Schritt 1: Richten Sie Ihren Dokumentpfad ein

 Bevor Sie Änderungen vornehmen, müssen Sie den Pfad zu Ihrem Dokument angeben. Ersetzen Sie`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Ihr Dokument gespeichert ist.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Schritt 2: Durchlaufen strukturierter Dokument-Tags

 Um SDTs zu ändern, müssen Sie zunächst alle SDTs im Dokument durchlaufen. Dies geschieht mit dem`GetChildNodes` Methode zum Abrufen aller Knoten vom Typ`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // SDTs basierend auf ihrem Typ ändern
}
```

## Schritt 3: Ändern von SDTs im Klartext

Wenn das SDT ein einfacher Texttyp ist, können Sie seinen Inhalt ersetzen. Löschen Sie zuerst den vorhandenen Inhalt und fügen Sie dann neuen Text hinzu.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Erläuterung: Hier`RemoveAllChildren()`löscht den vorhandenen Inhalt des SDT. Anschließend erstellen wir ein neues`Paragraph` Und`Run` Objekt, um den neuen Text einzufügen.

## Schritt 4: Dropdown-Liste SDTs ändern

 Bei Dropdown-Listen-SDTs können Sie das ausgewählte Element ändern, indem Sie auf das`ListItems` Sammlung. Hier wählen wir das dritte Element in der Liste aus.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Erklärung: Dieser Codeausschnitt wählt das Element am Index 2 (drittes Element) aus der Dropdown-Liste aus. Passen Sie den Index Ihren Anforderungen entsprechend an.

## Schritt 5: Bild-SDTs ändern

Um ein Bild innerhalb eines Bild-SDT zu aktualisieren, können Sie das vorhandene Bild durch ein neues ersetzen.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Erklärung: Dieser Code prüft, ob die Form ein Bild enthält und ersetzt es dann durch ein neues Bild an der`ImagesDir`.

## Schritt 6: Speichern Sie Ihr geändertes Dokument

Nachdem Sie alle erforderlichen Änderungen vorgenommen haben, speichern Sie das geänderte Dokument unter einem neuen Namen, um Ihr Originaldokument intakt zu halten.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Erklärung: Dadurch wird das Dokument unter einem neuen Dateinamen gespeichert, sodass Sie es leicht vom Original unterscheiden können.

## Abschluss

Das Ändern von Inhaltssteuerelementen in einem Word-Dokument mit Aspose.Words für .NET ist unkompliziert, wenn Sie die erforderlichen Schritte erst einmal verstanden haben. Egal, ob Sie Text aktualisieren, Dropdown-Auswahlen ändern oder Bilder austauschen, Aspose.Words bietet eine robuste API für diese Aufgaben. Indem Sie diesem Tutorial folgen, können Sie die strukturierten Inhaltssteuerelemente Ihres Dokuments effektiv verwalten und anpassen und so Ihre Dokumente dynamischer und auf Ihre Bedürfnisse zugeschnitten gestalten.

## FAQs

1. Was ist ein Structured Document Tag (SDT)?

SDTs sind Elemente in Word-Dokumenten, die bei der Verwaltung und Formatierung von Dokumentinhalten wie Textfeldern, Dropdown-Listen oder Bildern helfen.

2. Wie kann ich einem SDT ein neues Dropdown-Element hinzufügen?

 Um ein neues Element hinzuzufügen, verwenden Sie das`ListItems` Eigenschaft und fügen Sie eine neue`SdtListItem` zur Sammlung.

3. Kann ich Aspose.Words verwenden, um SDTs aus einem Dokument zu entfernen?

Ja, Sie können SDTs entfernen, indem Sie auf die Knoten des Dokuments zugreifen und das gewünschte SDT löschen.

4. Wie gehe ich mit SDTs um, die in anderen Elementen verschachtelt sind?

 Verwenden Sie die`GetChildNodes` Methode mit entsprechenden Parametern für den Zugriff auf verschachtelte SDTs.

5. Was soll ich tun, wenn das SDT, das ich ändern muss, im Dokument nicht sichtbar ist?

Stellen Sie sicher, dass das SDT nicht ausgeblendet oder geschützt ist. Überprüfen Sie die Dokumenteinstellungen und stellen Sie sicher, dass Ihr Code den richtigen SDT-Typ anspricht.


### Beispielquellcode zum Ändern von Inhaltssteuerelementen mit Aspose.Words für .NET 

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

Das ist es! Sie haben erfolgreich verschiedene Arten von Inhaltssteuerelementen in Ihrem Word-Dokument mit Aspose.Words für .NET geändert.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
