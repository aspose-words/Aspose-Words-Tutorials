---
title: Voeg dynamische kopdatum in Word‑document in met Aspose.Words for .NET
weight: 110
limit:
description: Leer hoe je een dynamisch DATE‑veld toevoegt aan de primaire koptekst van een Word‑document met Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Leer hoe je een dynamisch DATE‑veld toevoegt aan de primaire koptekst
    van een Word‑document met Aspose.Words for .NET.
  headline: Voeg dynamische kopdatum in Word‑document in met Aspose.Words for .NET
  type: TechArticle
- description: Leer hoe je een dynamisch DATE‑veld toevoegt aan de primaire koptekst
    van een Word‑document met Aspose.Words for .NET.
  name: Voeg dynamische kopdatum in Word‑document in met Aspose.Words for .NET
  steps:
  - name: Maak een nieuw Document en een DocumentBuilder aan om het te bewerken.
    text: Maak een nieuw Document en een DocumentBuilder aan om het te bewerken.
  - name: Verplaats de cursor van de builder naar de primaire koptekst zodat volgende
      invoegingen de koptekst beïnvloeden.
    text: Verplaats de cursor van de builder naar de primaire koptekst zodat volgende
      invoegingen de koptekst beïnvloeden.
  - name: Schrijf het statische label en voeg een DATE‑veld met de opmaak “MMMM d,
      yyyy” toe aan de koptekst, waarmee een dynamische datum wordt gecreëerd.
    text: Schrijf het statische label en voeg een DATE‑veld met de opmaak “MMMM d,
      yyyy” toe aan de koptekst, waarmee een dynamische datum wordt gecreëerd.
  - name: Keer terug naar de hoofdtekst en voeg een voorbeeldparagraaf toe, waarmee
      normale documentinhoud naast de koptekst wordt gedemonstreerd.
    text: Keer terug naar de hoofdtekst en voeg een voorbeeldparagraaf toe, waarmee
      normale documentinhoud naast de koptekst wordt gedemonstreerd.
  - name: Sla het document op als een .docx‑bestand.
    text: Sla het document op als een .docx‑bestand.
  type: HowTo
- questions:
  - answer: De aanroep `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` plaatst
      de builder op de bestaande primaire koptekst, en `Write`/`InsertField` voegen
      simpelweg tekst toe aan wat er al staat; ze verwijderen geen bestaande inhoud.
    question: Wat gebeurt er als het document al een primaire koptekst heeft – zal
      mijn code die overschrijven?
  - answer: Ja – wijzig het switch‑formaat in de veldcode die aan `InsertField` wordt
      doorgegeven, bijv. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\")` geeft
      een datum als 2026-09-22.
    question: Kan ik het datumformaat dat door het DATE‑veld wordt gebruikt wijzigen,
      en zo ja, hoe?
  - answer: Vervang `HeaderFooterType.HeaderPrimary` door `HeaderFooterType.HeaderFirst`
      bij het aanroepen van `MoveToHeaderFooter`; de rest van de code werkt op dezelfde
      manier.
    question: Als ik het datumveld in de koptekst van de eerste pagina wil in plaats
      van de primaire koptekst, wat moet ik dan doen?
  - answer: Het veld wordt alleen ingevoegd met de `\@`‑switch, die Word vertelt de
      huidige datum weer te geven elke keer dat het veld wordt vernieuwd (bijv. bij
      het openen van het bestand of wanneer je Ctrl+Alt+F9 indrukt).
    question: Werkt het DATE‑veld automatisch bij wanneer het document later wordt
      geopend?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Voeg een dynamische datum toe aan een Word‑koptekst
og_description: Stapsgewijze gids om een live datumveld in je Word‑koptekst in te sluiten met Aspose.Words.
og_image_alt: Schermafbeelding die laat zien hoe je een dynamisch DATE‑veld in de koptekst van een Word‑document invoegt met Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg dynamische kopdatum in Word‑document in met Aspose.Words
Deze tutorial toont hoe je de Document- en DocumentBuilder-klassen in Aspose.Words for .NET gebruikt om een dynamisch DATE‑veld in de primaire koptekst van een Word‑document in te voegen. Het toegevoegde veld werkt automatisch bij naar de huidige datum elke keer dat het document wordt geopend, zodat je koptekst altijd de laatste datum weergeeft. Volg de stap‑voor‑stap‑code om het veld toe te voegen en het bijgewerkte bestand op te slaan.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wat gebeurt er als het document al een primaire koptekst heeft – zal mijn code die overschrijven?**  
A: De aanroep `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` plaatst de builder op de bestaande primaire koptekst, en `Write`/`InsertField` voegen simpelweg tekst toe aan wat er al staat; ze verwijderen geen bestaande inhoud.

**Q: Kan ik het datumformaat dat door het DATE‑veld wordt gebruikt wijzigen, en zo ja, hoe?**  
A: Ja – wijzig het switch‑formaat in de veldcode die aan `InsertField` wordt doorgegeven, bijv. `builder.InsertField(\"DATE \\\\@ \"yyyy-MM-dd\")` geeft een datum als 2026-09-22.

**Q: Als ik het datumveld in de koptekst van de eerste pagina wil in plaats van de primaire koptekst, wat moet ik dan doen?**  
A: Vervang `HeaderFooterType.HeaderPrimary` door `HeaderFooterType.HeaderFirst` bij het aanroepen van `MoveToHeaderFooter`; de rest van de code werkt op dezelfde manier.

**Q: Werkt het DATE‑veld automatisch bij wanneer het document later wordt geopend?**  
A: Het veld wordt alleen ingevoegd met de `\@`‑switch, die Word vertelt de huidige datum weer te geven elke keer dat het veld wordt vernieuwd (bijv. bij het openen van het bestand of wanneer je Ctrl+Alt+F9 indrukt).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}