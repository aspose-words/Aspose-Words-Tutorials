---
title: Detecteer documentbestandsformaat
linktitle: Detecteer documentbestandsformaat
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u documentbestandsindelingen kunt detecteren met Aspose.Words voor .NET met deze uitgebreide, stapsgewijze handleiding.
weight: 10
url: /nl/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detecteer documentbestandsformaat

## Invoering

In de digitale wereld van vandaag is het cruciaal om verschillende documentformaten efficiënt te beheren. Of u nu Word, PDF, HTML of andere formaten gebruikt, het correct kunnen detecteren en verwerken van deze bestanden kan u veel tijd en moeite besparen. In deze tutorial onderzoeken we hoe u documentbestandsformaten kunt detecteren met Aspose.Words voor .NET. Deze gids leidt u door alles wat u moet weten, van vereisten tot een gedetailleerde stapsgewijze handleiding.

## Vereisten

Voordat we in de code duiken, controleren we of je alles hebt wat je nodig hebt:

-  Aspose.Words voor .NET: U kunt het downloaden van[hier](https://releases.aspose.com/words/net/) . Zorg ervoor dat u een geldige licentie hebt. Zo niet, dan kunt u een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Elke recente versie werkt prima.
- .NET Framework: Zorg ervoor dat u de juiste versie hebt geïnstalleerd.

## Naamruimten importeren

Om te beginnen moet u de benodigde naamruimten in uw project importeren:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Laten we het voorbeeld opsplitsen in meerdere stappen, zodat het makkelijker te volgen is.

## Stap 1: Mappen instellen

Eerst moeten we de mappen instellen waarin de bestanden worden gesorteerd op basis van hun formaat.

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Maak de mappen aan als ze nog niet bestaan.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Stap 2: Haal de lijst met bestanden op

Vervolgens krijgen we een lijst met bestanden uit de map, exclusief beschadigde documenten.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Stap 3: Bestandsindelingen detecteren

Nu doorlopen we elk bestand en detecteren we de opmaak ervan met behulp van Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Geef het documenttype weer
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Conclusie

Het detecteren van documentbestandsformaten met Aspose.Words voor .NET is een eenvoudig proces. Door uw mappen in te stellen, uw lijst met bestanden op te halen en Aspose.Words te gebruiken om bestandsformaten te detecteren, kunt u uw documenten efficiënt organiseren en beheren. Deze aanpak bespaart niet alleen tijd, maar zorgt er ook voor dat u verschillende documentformaten correct verwerkt.

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?
Aspose.Words voor .NET is een krachtige bibliotheek voor het programmatisch werken met Word-documenten. Hiermee kunnen ontwikkelaars documenten in verschillende formaten maken, wijzigen en converteren.

### Kan Aspose.Words versleutelde documenten detecteren?
Ja, Aspose.Words kan detecteren of een document is gecodeerd en u kunt dergelijke documenten dienovereenkomstig verwerken.

### Welke formaten kan Aspose.Words detecteren?
Aspose.Words kan een breed scala aan formaten detecteren, waaronder DOC, DOCX, RTF, HTML, MHTML, ODT en nog veel meer.

### Hoe kan ik een tijdelijke licentie voor Aspose.Words krijgen?
 U kunt een tijdelijke vergunning krijgen bij de[Aspose Aankoop](https://purchase.aspose.com/temporary-license/) pagina.

### Waar kan ik de documentatie voor Aspose.Words vinden?
 De documentatie voor Aspose.Words is te vinden[hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
