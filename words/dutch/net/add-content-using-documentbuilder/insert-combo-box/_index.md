---
title: Voeg een Combo Box Form Field toe aan een Word-document met Aspose.Words for .NET
weight: 310
limit:
description: Leer hoe je een combo‑box-formulierveld met vooraf gedefinieerde items toevoegt aan een Word-document met Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Voeg een Combo Box Form Field toe aan een Word-document met Aspose.Words
Deze tutorial laat zien hoe je Aspose.Words for .NET's DocumentBuilder gebruikt om een nieuw Word-document te maken en een combo‑box-formulierveld in te voegen dat is gevuld met vooraf gedefinieerde items. Door de stap‑voor‑stap code te volgen, zie je hoe je de opties van de combo‑box configureert en vervolgens het document opslaat voor gebruik in interactieve formulieren.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Wat stelt de `items`‑array die aan `InsertComboBox` wordt doorgegeven voor?**
A: Het definieert de lijst van strings die verschijnen als selecteerbare opties in de dropdown van de combo‑box.

**Q: Hoe kan ik wijzigen welk item standaard geselecteerd is wanneer het document wordt geopend?**
A: Stel het derde argument (`selectedIndex`) van `InsertComboBox` in op de nul‑gebaseerde index van het gewenste standaarditem (bijv. `2` voor "Three").

**Q: Is het mogelijk om de combo‑box op een specifieke locatie in het document te plaatsen?**
A: Ja—verplaats de cursor van de `DocumentBuilder` naar de gewenste plek met methoden zoals `MoveToParagraph`, `InsertParagraph` of `Write` voordat je `InsertComboBox` aanroept.

**Q: Welk bestandsformaat wordt door deze code aangemaakt en kan het geopend worden in oudere versies van Word?**
A: De code slaat een `.docx`‑bestand op, dat geopend kan worden door Word 2007 en later, evenals elke applicatie die het OpenXML‑formaat ondersteunt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}