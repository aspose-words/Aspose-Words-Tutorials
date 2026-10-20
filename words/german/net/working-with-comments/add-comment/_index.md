---
title: Einen Comment zu einem bestimmten Absatz in einem Word‑Dokument mit Aspose.Words für .NET einfügen
weight: 210
limit:
description: Schritt‑für‑Schritt‑Anleitung zum Hinzufügen eines Autorenkommentars zu einem ausgewählten Absatz in einem Word‑Dokument und zum Speichern als DOCX mit Aspose.Words für .NET.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Schritt‑für‑Schritt‑Anleitung zum Hinzufügen eines Autorenkommentars
    zu einem ausgewählten Absatz in einem Word‑Dokument und zum Speichern als DOCX
    mit Aspose.Words für .NET.
  headline: Einen Comment zu einem bestimmten Absatz in einem Word‑Dokument mit Aspose.Words
    für .NET einfügen
  type: TechArticle
- description: Schritt‑für‑Schritt‑Anleitung zum Hinzufügen eines Autorenkommentars
    zu einem ausgewählten Absatz in einem Word‑Dokument und zum Speichern als DOCX
    mit Aspose.Words für .NET.
  name: Einen Comment zu einem bestimmten Absatz in einem Word‑Dokument mit Aspose.Words
    für .NET einfügen
  steps:
  - name: Instanziieren Sie ein neues Document und einen DocumentBuilder, um mit dem
      Erstellen der Word‑Datei zu beginnen.
    text: Instanziieren Sie ein neues Document und einen DocumentBuilder, um mit dem
      Erstellen der Word‑Datei zu beginnen.
  - name: Verwenden Sie DocumentBuilder.Writeln, um dem Dokument drei separate Textabsätze
      hinzuzufügen.
    text: Verwenden Sie DocumentBuilder.Writeln, um dem Dokument drei separate Textabsätze
      hinzuzufügen.
  - name: Rufen Sie den zweiten Absatz sicher ab und greifen Sie auf den ersten zurück,
      falls das Dokument weniger als zwei Absätze enthält.
    text: Rufen Sie den zweiten Absatz sicher ab und greifen Sie auf den ersten zurück,
      falls das Dokument weniger als zwei Absätze enthält.
  - name: Erstellen Sie einen Comment mit Autorendaten, setzen Sie dessen Text und
      hängen Sie ihn an den ausgewählten Absatz an.
    text: Erstellen Sie einen Comment mit Autorendaten, setzen Sie dessen Text und
      hängen Sie ihn an den ausgewählten Absatz an.
  - name: Speichern Sie das modifizierte Dokument als DOCX‑Datei mit dem Namen 'sample.docx'
      im aktuellen Ordner.
    text: Speichern Sie das modifizierte Dokument als DOCX‑Datei mit dem Namen 'sample.docx'
      im aktuellen Ordner.
  type: HowTo
- questions:
  - answer: Der `if`‑Block greift auf den ersten Absatz (`paraList[0]`) zurück, wenn
      `paraList.Count` kleiner als 2 ist, sodass der Kommentar an diesem einzigen
      Absatz angehängt wird statt an einem fehlenden zweiten.
    question: Was macht der Code, wenn das Dokument nur einen Absatz enthält?
  - answer: Sie werden dem `Comment`‑Konstruktor als zweites und drittes Argument
      übergeben – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – wobei
      \"Jordan\" der Autorenname und \"JH\" die Initialen sind.
    question: Wie werden im Beispiel der Name des Kommentar‑Autors und die Initialen
      festgelegt?
  - answer: In diesem Beispiel wird der Kommentar über `AppendChild` mit dem gesamten
      `Paragraph` verknüpft, aber um einen Textbereich zu kommentieren, müssten Sie
      ein `CommentRangeStart` und ein `CommentRangeEnd` um die gewünschten `Run`‑Knoten
      erstellen und dann den `Comment`‑Knoten dazwischen einfügen.
    question: Kann ich einen Kommentar an ein bestimmtes Textstück statt an den gesamten
      Absatz anhängen?
  - answer: '`AppendChild` fügt den `Comment`‑Knoten zur Kind‑Collection des Absatzes
      hinzu, und Aspose.Words erzeugt beim Speichern des Dokuments automatisch die
      erforderlichen Kommentar‑Start‑/End‑Marker.'
    question: Muss ich Kommentar‑Marker manuell einfügen, oder übernimmt das `AppendChild`
      das?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Einen Kommentar in einen Word‑Absatz einfügen
og_description: Fügen Sie einem bestimmten Absatz einen Autorenkommentar hinzu und exportieren Sie die Datei als DOCX mit Aspose.Words.
og_image_alt: Anleitung, die zeigt, wie man mit Aspose.Words für .NET einen Kommentar zu einem Absatz in einem Word‑Dokument hinzufügt
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Einen Comment zu einem bestimmten Absatz in einem Word‑Dokument mit Aspose.Words für .NET einfügen
Mit Aspose.Words für .NET können Sie programmgesteuert Kommentare zu Word‑Dateien hinzufügen. Dieses Tutorial führt Sie durch das Erstellen eines neuen Dokuments, das Einfügen von drei Absätzen, das Auffinden des zweiten Absatzes und das Anhängen eines Kommentars, der Autor‑ und Datumsinformationen enthält. Abschließend wird das Dokument als DOCX‑Datei gespeichert, wobei der Kommentar erhalten bleibt.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Was macht der Code, wenn das Dokument nur einen Absatz enthält?**  
A: Der `if`‑Block greift auf den ersten Absatz (`paraList[0]`) zurück, wenn `paraList.Count` kleiner als 2 ist, sodass der Kommentar an diesem einzigen Absatz angehängt wird statt an einem fehlenden zweiten.

**Q: Wie werden im Beispiel der Name des Kommentar‑Autors und die Initialen festgelegt?**  
A: Sie werden dem `Comment`‑Konstruktor als zweites und drittes Argument übergeben – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – wobei \"Jordan\" der Autorenname und \"JH\" die Initialen sind.

**Q: Kann ich einen Kommentar an ein bestimmtes Textstück statt an den gesamten Absatz anhängen?**  
A: In diesem Beispiel wird der Kommentar über `AppendChild` mit dem gesamten `Paragraph` verknüpft, aber um einen Textbereich zu kommentieren, müssten Sie ein `CommentRangeStart` und ein `CommentRangeEnd` um die gewünschten `Run`‑Knoten erstellen und dann den `Comment`‑Knoten dazwischen einfügen.

**Q: Muss ich Kommentar‑Marker manuell einfügen, oder übernimmt das `AppendChild` das?**  
A: `AppendChild` fügt den `Comment`‑Knoten zur Kind‑Collection des Absatzes hinzu, und Aspose.Words erzeugt beim Speichern des Dokuments automatisch die erforderlichen Kommentar‑Start‑/End‑Marker.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}