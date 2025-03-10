---
title: Infoga dokument vid brevkoppling
linktitle: Infoga dokument vid brevkoppling
second_title: Aspose.Words Document Processing API
description: Lär dig hur du infogar dokument vid sammanslagningsfält med Aspose.Words för .NET i denna omfattande, steg-för-steg handledning.
weight: 10
url: /sv/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga dokument vid brevkoppling

## Introduktion

Välkommen till en värld av dokumentautomatisering med Aspose.Words för .NET! Har du någonsin undrat hur man dynamiskt infogar dokument i specifika fält i ett huvuddokument under en sammankopplingsoperation? Tja, du är på rätt plats. Denna handledning guidar dig steg-för-steg genom processen att infoga dokument vid sammanslagningsfält med Aspose.Words för .NET. Det är som att lägga ihop ett pussel, där varje bit faller perfekt på plats. Så, låt oss dyka in!

## Förutsättningar

Innan vi börjar, se till att du har följande:

1.  Aspose.Words för .NET: Du kan[ladda ner den senaste versionen här](https://releases.aspose.com/words/net/) . Om du behöver köpa en licens kan du göra det[här](https://purchase.aspose.com/buy) . Alternativt kan du få en[tillfällig licens](https://purchase.aspose.com/temporary-license/) eller prova med en[gratis provperiod](https://releases.aspose.com/).
2. Utvecklingsmiljö: Visual Studio eller någon annan C# IDE.
3. Grundläggande kunskaper om C#: Bekantskap med C#-programmering kommer att göra denna handledning till en lek.

## Importera namnområden

Först och främst måste du importera de nödvändiga namnrymden. Dessa är som byggstenarna i ditt projekt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Låt oss dela upp processen i hanterbara steg. Varje steg kommer att bygga på det föregående, vilket leder dig till en komplett lösning.

## Steg 1: Konfigurera din katalog

Innan du kan börja infoga dokument måste du definiera sökvägen till din dokumentkatalog. Det är här dina dokument lagras.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda huvuddokumentet

Därefter laddar du huvuddokumentet. Detta dokument innehåller sammanslagningsfälten där andra dokument kommer att infogas.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Steg 3: Ställa in återuppringning för fältsammanslagning

För att hantera sammanslagningen måste du ställa in en återuppringningsfunktion. Denna funktion kommer att ansvara för att infoga dokument vid de angivna sammanslagningsfälten.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Steg 4: Kör sammankopplingen av brev

Nu är det dags att köra sammanslagningen. Det är här magin händer. Du anger kopplingsfältet och dokumentet som ska infogas i detta fält.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Steg 5: Spara dokumentet

När sammanslagningen är klar sparar du det ändrade dokumentet. Det här nya dokumentet kommer att ha infogat innehåll precis där du vill ha det.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Steg 6: Skapa återuppringningshanteraren

Callback-hanteraren är en klass som gör speciell bearbetning för sammanslagningsfältet. Den laddar dokumentet som anges i fältvärdet och infogar det i det aktuella sammanslagningsfältet.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Steg 7: Infoga dokumentet

Den här metoden infogar det angivna dokumentet i det aktuella stycket eller tabellcellen.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Slutsats

Och där har du det! Du har framgångsrikt infogat dokument i specifika fält under en kopplingsoperation med Aspose.Words för .NET. Denna kraftfulla funktion kan spara massor av tid och ansträngning, särskilt när du hanterar stora volymer dokument. Se det som att ha en personlig assistent som tar hand om alla tunga lyft åt dig. Så fortsätt och prova. Glad kodning!

## FAQ's

### Kan jag infoga flera dokument i olika sammanslagningsfält?
Ja, det kan du. Ange helt enkelt lämpliga sammanslagningsfält och motsvarande dokumentsökvägar i`MailMerge.Execute` metod.

### Är det möjligt att formatera det infogade dokumentet annorlunda än huvuddokumentet?
 Absolut! Du kan använda`ImportFormatMode` parametern i`NodeImporter` för att styra formateringen.

### Vad händer om sammanslagningsfältets namn är dynamiskt?
Du kan hantera dynamiska sammanslagningsfältnamn genom att skicka dem som parametrar till återuppringningshanteraren.

### Kan jag använda den här metoden med olika filformat?
Ja, Aspose.Words stöder olika filformat inklusive DOCX, PDF och mer.

### Hur hanterar jag fel under dokumentinsättningsprocessen?
Implementera felhantering i din callback-hanterare för att hantera eventuella undantag som kan uppstå.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
