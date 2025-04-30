---
"description": "Leer hoe je een bestaande handtekeningregel in een Word-document kunt ondertekenen met Aspose.Words voor .NET met onze gedetailleerde stapsgewijze handleiding. Perfect voor ontwikkelaars."
"linktitle": "Bestaande handtekeningregel in Word-document ondertekenen"
"second_title": "Aspose.Words API voor documentverwerking"
"title": "Bestaande handtekeningregel in Word-document ondertekenen"
"url": "/nl/net/programming-with-digital-signatures/signing-existing-signature-line/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Bestaande handtekeningregel in Word-document ondertekenen

## Invoering

Hallo! Heb je ooit een digitaal document moeten ondertekenen, maar vond je het een beetje omslachtig? Dan heb je geluk, want vandaag duiken we in hoe je moeiteloos een bestaande handtekeningregel in een Word-document kunt ondertekenen met Aspose.Words voor .NET. Deze tutorial leidt je stap voor stap door het proces, zodat je deze taak in een mum van tijd onder de knie hebt.

## Vereisten

Voordat we in de details duiken, willen we eerst controleren of we alles hebben wat we nodig hebben:

1. Aspose.Words voor .NET: Zorg ervoor dat je de Aspose.Words voor .NET-bibliotheek hebt geïnstalleerd. Als je dat nog niet hebt gedaan, kun je deze downloaden. [hier](https://releases.aspose.com/words/net/).
2. Ontwikkelomgeving: Visual Studio of een andere C#-compatibele IDE.
3. Document en certificaat: Een Word-document met een handtekeningregel en een digitaal certificaat (PFX-bestand).
4. Basiskennis van C#: Kennis van C#-programmering is een pré.

## Naamruimten importeren

Voordat u de klassen en methoden van Aspose.Words kunt gebruiken, moet u de benodigde naamruimten importeren. Hier is een fragment van de vereiste imports:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

## Stap 1: Laad uw document

Allereerst moet u het Word-document met de handtekeningregel laden. Deze stap is cruciaal omdat het de basis vormt voor het hele proces.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

## Stap 2: Toegang tot de handtekeningregel

Nu het document is geladen, is de volgende stap het vinden en openen van de handtekeningregel in het document.

```csharp
SignatureLine signatureLine = ((Shape) doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

## Stap 3: Stel de opties voor het ondertekenen in

Het instellen van de ondertekeningsopties is essentieel. Dit omvat het specificeren van de ID van de handtekeningregel en het opgeven van de afbeelding die als handtekening wordt gebruikt.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes("YOUR IMAGE DIRECTORY" + "signature_image.emf")
};
```

## Stap 4: Certificaathouder aanmaken

Om het document digitaal te ondertekenen, hebt u een digitaal certificaat nodig. Zo maakt u een certificaathouder aan vanuit uw PFX-bestand.

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "your_password");
```

## Stap 5: Onderteken het document

Nu combineren we alle componenten om het document te ondertekenen. Dit is waar de magie gebeurt!

```csharp
DigitalSignatureUtil.Sign(
    dataDir + "Digitally signed.docx",
    dataDir + "Signature line.docx",
    certHolder,
    signOptions
);
```

## Conclusie

En voilà! Je hebt met succes een bestaande handtekeningregel in een Word-document ondertekend met Aspose.Words voor .NET. Niet zo moeilijk, toch? Met deze stappen kun je nu documenten digitaal ondertekenen en zo een extra laagje authenticiteit en professionaliteit toevoegen. Dus de volgende keer dat iemand je een document ter ondertekening stuurt, weet je precies wat je moet doen!

## Veelgestelde vragen

### Wat is Aspose.Words voor .NET?

Aspose.Words voor .NET is een krachtige bibliotheek voor het werken met Word-documenten in .NET-applicaties. Hiermee kunt u Word-documenten programmatisch maken, wijzigen en converteren.

### Waar kan ik een gratis proefversie van Aspose.Words voor .NET krijgen?

U kunt een gratis proefversie downloaden [hier](https://releases.aspose.com/).

### Kan ik elk afbeeldingsformaat gebruiken voor de handtekening?

Aspose.Words ondersteunt verschillende afbeeldingsformaten, maar door gebruik te maken van een Enhanced Metafile (EMF) is de kwaliteit van handtekeningen beter.

### Hoe kan ik een digitaal certificaat verkrijgen?

U kunt digitale certificaten online bij verschillende aanbieders kopen. Zorg ervoor dat het certificaat in PFX-formaat is en dat u het wachtwoord kent.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?

Uitgebreide documentatie is beschikbaar [hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}