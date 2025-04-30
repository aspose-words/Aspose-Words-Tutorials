---
"description": "Lär dig hur du infogar dokument i fält för koppling av dokument med Aspose.Words för .NET i den här omfattande steg-för-steg-handledningen."
"linktitle": "Infoga dokument vid dokumentkoppling"
"second_title": "Aspose.Words dokumentbehandlings-API"
"title": "Infoga dokument vid dokumentkoppling"
"url": "/sv/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Infoga dokument vid dokumentkoppling

## Introduktion

Välkommen till dokumentautomationens värld med Aspose.Words för .NET! Har du någonsin undrat hur du dynamiskt infogar dokument i specifika fält i ett huvuddokument under en dokumentkoppling? Då har du kommit rätt. Den här handledningen guidar dig steg för steg genom processen att infoga dokument i dokumentkopplingsfält med Aspose.Words för .NET. Det är som att lägga ett pussel, där varje bit faller perfekt på plats. Så, låt oss dyka in!

## Förkunskapskrav

Innan vi börjar, se till att du har följande:

1. Aspose.Words för .NET: Du kan [ladda ner den senaste versionen här](https://releases.aspose.com/words/net/)Om du behöver köpa en licens kan du göra det [här](https://purchase.aspose.com/buy)Alternativt kan du skaffa en [tillfällig licens](https://purchase.aspose.com/temporary-license/) eller prova det med en [gratis provperiod](https://releases.aspose.com/).
2. Utvecklingsmiljö: Visual Studio eller annan C# IDE.
3. Grundläggande kunskaper i C#: Bekantskap med C#-programmering gör den här handledningen till en barnlek.

## Importera namnrymder

Först och främst måste du importera de nödvändiga namnrymderna. Dessa är som byggstenarna i ditt projekt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Låt oss dela upp processen i hanterbara steg. Varje steg bygger på det föregående och leder dig till en komplett lösning.

## Steg 1: Konfigurera din katalog

Innan du kan börja infoga dokument måste du ange sökvägen till din dokumentkatalog. Det är här dina dokument lagras.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Steg 2: Ladda huvuddokumentet

Nästa steg är att läsa in huvuddokumentet. Det här dokumentet innehåller kopplingsfälten där andra dokument kommer att infogas.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Steg 3: Ställa in återanropet för fältsammanslagning

För att hantera sammanslagningsprocessen måste du ställa in en callback-funktion. Denna funktion ansvarar för att infoga dokument i de angivna sammanslagningsfälten.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Steg 4: Utföra dokumentkopplingen

Nu är det dags att köra dokumentkopplingen. Det är här magin händer. Du anger kopplingsfältet och dokumentet som ska infogas i det här fältet.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Steg 5: Spara dokumentet

När dokumentkopplingen är klar sparar du det ändrade dokumentet. Det nya dokumentet kommer att ha det infogade innehållet precis där du vill ha det.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Steg 6: Skapa återuppringningshanteraren

Återanropshanteraren är en klass som utför specialbearbetning för mergefältet. Den laddar dokumentet som anges i fältvärdet och infogar det i det aktuella mergefältet.

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

Och där har du det! Du har lyckats infoga dokument i specifika fält under en dokumentkoppling med Aspose.Words för .NET. Den här kraftfulla funktionen kan spara dig massor av tid och ansträngning, särskilt när du hanterar stora mängder dokument. Tänk dig det som att ha en personlig assistent som tar hand om allt det tunga arbetet åt dig. Så fortsätt och testa. Lycka till med kodningen!

## Vanliga frågor

### Kan jag infoga flera dokument i olika kopplingsfält?
Ja, det kan du. Ange bara lämpliga kopplingsfält och motsvarande dokumentsökvägar i `MailMerge.Execute` metod.

### Är det möjligt att formatera det infogade dokumentet annorlunda än huvuddokumentet?
Absolut! Du kan använda `ImportFormatMode` parametern i `NodeImporter` för att kontrollera formateringen.

### Vad händer om namnet på kopplingsfältet är dynamiskt?
Du kan hantera namn på dynamiska kopplingsfält genom att skicka dem som parametrar till återanropshanteraren.

### Kan jag använda den här metoden med olika filformat?
Ja, Aspose.Words stöder olika filformat, inklusive DOCX, PDF och mer.

### Hur hanterar jag fel under dokumentinsättningsprocessen?
Implementera felhantering i din callback-hanterare för att hantera eventuella undantag som kan uppstå.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}