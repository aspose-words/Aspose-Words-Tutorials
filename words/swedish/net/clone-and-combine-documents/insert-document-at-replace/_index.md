---
title: Infoga dokument vid ersätt
linktitle: Infoga dokument vid ersätt
second_title: Aspose.Words Document Processing API
description: Lär dig hur du sömlöst infogar ett Word-dokument i ett annat med Aspose.Words för .NET med vår detaljerade, steg-för-steg-guide. Perfekt för utvecklare som vill effektivisera dokumentbehandlingen.
weight: 10
url: /sv/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Infoga dokument vid ersätt

## Introduktion

Hej där, dokumentmästare! Har du någonsin funnit dig själv i koden och försökt ta reda på hur man infogar ett Word-dokument i ett annat sömlöst? Var inte rädd, för idag dyker vi in i Aspose.Words-världen för .NET för att göra den uppgiften till en lek. Vi går igenom en detaljerad, steg-för-steg-guide om hur du använder detta kraftfulla bibliotek för att infoga dokument vid specifika punkter under en sök- och ersättningsoperation. Är du redo att bli en Aspose.Words-guide? Låt oss komma igång!

## Förutsättningar

Innan vi går in i koden finns det några saker du måste ha på plats:

-  Visual Studio: Se till att du har Visual Studio installerat på din dator. Om du inte har det ännu kan du ladda ner det från[här](https://visualstudio.microsoft.com/).
-  Aspose.Words för .NET: Du behöver Aspose.Words-biblioteket. Du kan få det från[Aspose hemsida](https://releases.aspose.com/words/net/).
- Grundläggande C#-kunskap: En grundläggande förståelse för C# och .NET hjälper dig att följa med i denna handledning.

Okej, med de ur vägen, låt oss smutsa ner händerna med lite kod!

## Importera namnområden

Först och främst måste vi importera de nödvändiga namnrymden för att arbeta med Aspose.Words. Det här är som att samla alla dina verktyg innan du startar ett projekt. Lägg till dessa med hjälp av direktiv överst i din C#-fil:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nu när vi har våra förutsättningar på plats, låt oss dela upp processen i små steg. Varje steg är avgörande och kommer att föra oss närmare vårt mål.

## Steg 1: Konfigurera dokumentkatalogen

Först måste vi ange katalogen där våra dokument lagras. Det här är som att sätta scenen inför den stora föreställningen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersätta`"YOUR DOCUMENT DIRECTORY"` med sökvägen till din katalog. Det är här dina dokument kommer att leva och andas.

## Steg 2: Ladda huvuddokumentet

Därefter laddar vi huvuddokumentet som vi vill infoga ett annat dokument i. Se det här som vår huvudscen där all action kommer att ske.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Denna kod laddar huvuddokumentet från den angivna katalogen.

## Steg 3: Ställ in alternativ för Sök och ersätt

För att hitta den specifika platsen där vi vill infoga vårt dokument använder vi sök- och ersätt-funktionen. Det här är som att använda en karta för att hitta den exakta platsen för vårt nya tillskott.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Här ställer vi in riktningen till bakåt och anger en anpassad återuppringningshanterare som vi kommer att definiera härnäst.

## Steg 4: Utför Ersätt-operationen

Nu säger vi till vårt huvuddokument att leta efter en specifik platshållartext och ersätta den med ingenting, samtidigt som vi använder vår anpassade återuppringning för att infoga ett annat dokument.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Den här koden utför sök- och ersätt-operationen och sparar sedan det uppdaterade dokumentet.

## Steg 5: Skapa en anpassad ersättande återuppringningshanterare

Vår anpassade återuppringningshanterare är där magin händer. Denna hanterare kommer att definiera hur dokumentinsättningen utförs under sök- och ersätt-operationen.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Infoga ett dokument efter stycket som innehåller matchningstexten.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Ta bort stycket med matchningstexten.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Här laddar vi dokumentet som ska infogas och anropar sedan en hjälpmetod för att utföra infogningen.

## Steg 6: Definiera metoden Infoga dokument

Den sista biten i vårt pussel är metoden som faktiskt infogar dokumentet på den angivna platsen.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Kontrollera om insättningsdestinationen är ett stycke eller en tabell
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Skapa en NodeImporter för att importera noder från källdokumentet
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Gå igenom alla noder på blocknivå i källdokumentets avsnitt
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Hoppa över det sista tomma stycket i ett avsnitt
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importera och infoga noden i destinationen
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Denna metod tar hand om att importera noder från dokumentet som ska infogas och placera dem på rätt plats i huvuddokumentet.

## Slutsats

Och där har du det! En omfattande guide för att infoga ett dokument i ett annat med Aspose.Words för .NET. Genom att följa dessa steg kan du enkelt automatisera dokumentsammansättning och manipuleringsuppgifter. Oavsett om du bygger ett dokumenthanteringssystem eller bara behöver effektivisera ditt arbetsflöde för dokumentbearbetning är Aspose.Words din pålitliga medhjälpare.

## FAQ's

### Vad är Aspose.Words för .NET?
Aspose.Words för .NET är ett kraftfullt bibliotek för att manipulera Word-dokument programmatiskt. Det låter dig skapa, ändra, konvertera och bearbeta Word-dokument med lätthet.

### Kan jag infoga flera dokument samtidigt?
Ja, du kan modifiera återuppringningshanteraren för att hantera flera infogningar genom att iterera över en samling dokument.

### Finns det en gratis provperiod?
 Absolut! Du kan ladda ner en gratis testversion från[här](https://releases.aspose.com/).

### Hur får jag support för Aspose.Words?
 Du kan få stöd genom att besöka[Aspose.Words forum](https://forum.aspose.com/c/words/8).

### Kan jag behålla formateringen av det infogade dokumentet?
 Ja, den`NodeImporter` class låter dig ange hur formatering ska hanteras när du importerar noder från ett dokument till ett annat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
