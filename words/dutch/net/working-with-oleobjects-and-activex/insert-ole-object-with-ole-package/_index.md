---
title: Ole-object in Word invoegen met Ole-pakket
linktitle: Ole-object in Word invoegen met Ole-pakket
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u OLE-objecten in Word-documenten invoegt met Aspose.Words voor .NET. Volg onze gedetailleerde stapsgewijze handleiding om bestanden naadloos in te sluiten.
weight: 10
url: /nl/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ole-object in Word invoegen met Ole-pakket

## Invoering

Als u ooit een bestand in een Word-document wilde insluiten, bent u hier aan het juiste adres. Of het nu een ZIP-bestand, een Excel-sheet of een ander bestandstype is, het direct insluiten ervan in uw Word-document kan ongelooflijk nuttig zijn. Zie het als een geheim compartiment in uw document waar u allerlei schatten kunt verstoppen. En vandaag gaan we uitleggen hoe u dit kunt doen met Aspose.Words voor .NET. Klaar om een Word-wizard te worden? Laten we erin duiken!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Aspose.Words voor .NET: Als u dat nog niet gedaan hebt, download het dan hier[hier](https://releases.aspose.com/words/net/).
2. Een ontwikkelomgeving: Visual Studio of een andere .NET-ontwikkelomgeving.
3. Basiskennis van C#: u hoeft geen expert te zijn, maar het is wel handig als u al wat ervaring hebt met C#.
4. Een documentenmap: een map waarin u documenten kunt opslaan en ophalen.

## Naamruimten importeren

Laten we eerst onze namespaces op orde brengen. U moet de volgende namespaces in uw project opnemen:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Laten we het opsplitsen in kleine stapjes, zodat het makkelijk te volgen is.

## Stap 1: Stel uw document in

Stel je voor dat je een kunstenaar bent met een leeg canvas. Eerst hebben we ons lege canvas nodig, dat is ons Word-document. Zo stel je het in:

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Deze code initialiseert een nieuw Word-document en stelt een DocumentBuilder in, die we gebruiken om inhoud in ons document in te voegen.

## Stap 2: Lees je Ole Object

Laten we nu het bestand lezen dat u wilt embedden. Zie dit als het oppakken van de schat die u wilt verstoppen in uw geheime compartiment:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Deze regel leest alle bytes uit uw ZIP-bestand en slaat ze op in een byte-array.

## Stap 3: Het Ole-object invoegen

Nu komt het magische gedeelte. We gaan het bestand insluiten in ons Word-document:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Hier creëren we een geheugenstroom van de byte-array en gebruiken de`InsertOleObject` methode om het in het document te embedden. We stellen ook de bestandsnaam en weergavenaam in voor het embedde object.

## Stap 4: Sla uw document op

Laten we tot slot ons meesterwerk redden:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Hiermee wordt het document met uw ingesloten bestand in de opgegeven map opgeslagen.

## Conclusie

En daar heb je het! Je hebt met succes een OLE-object in een Word-document ingesloten met Aspose.Words voor .NET. Het is alsof je een verborgen juweel in je document hebt toegevoegd dat op elk moment kan worden onthuld. Deze techniek kan ongelooflijk nuttig zijn voor verschillende toepassingen, van technische documentatie tot dynamische rapporten. 

## Veelgestelde vragen

### Kan ik andere bestandstypen op deze manier insluiten?
Ja, u kunt verschillende bestandstypen insluiten, zoals Excel-sheets, PDF's en afbeeldingen.

### Heb ik een licentie nodig voor Aspose.Words?
 Ja, je hebt een geldige licentie nodig. Je kunt een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) voor evaluatie.

### Hoe kan ik de weergavenaam van het OLE-object aanpassen?
 U kunt de`DisplayName` eigendom van de`OlePackage` om het aan te passen.

### Is Aspose.Words compatibel met .NET Core?
Ja, Aspose.Words ondersteunt zowel .NET Framework als .NET Core.

### Kan ik het ingesloten OLE-object in het Word-document bewerken?
Nee, u kunt het OLE-object niet rechtstreeks in Word bewerken. U moet het openen in de oorspronkelijke toepassing.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
