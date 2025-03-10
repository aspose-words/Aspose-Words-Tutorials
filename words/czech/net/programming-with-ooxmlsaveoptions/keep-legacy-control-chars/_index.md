---
title: Udržujte starší ovládací znaky
linktitle: Udržujte starší ovládací znaky
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak zachovat starší řídicí znaky v dokumentech aplikace Word pomocí Aspose.Words for .NET, pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Udržujte starší ovládací znaky

## Zavedení

Byli jste někdy zmateni těmi podivnými, neviditelnými řídicími znaky ve vašich dokumentech aplikace Word? Jsou jako malí, skrytí gremlinové, kteří mohou zkazit formátování a funkčnost. Naštěstí Aspose.Words for .NET poskytuje šikovnou funkci, která tyto starší řídicí znaky při ukládání dokumentů uchová nedotčené. V tomto tutoriálu se ponoříme hluboko do toho, jak spravovat tyto řídicí znaky pomocí Aspose.Words for .NET. Rozebereme to krok za krokem a zajistíme, že po cestě pochopíte každý detail. Jste připraveni začít? Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Stáhněte a nainstalujte z[zde](https://releases.aspose.com/words/net/).
2.  Platná licence Aspose: Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).
3. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
4. Základní znalost C#: Užitečná bude znalost programovacího jazyka C#.

## Importovat jmenné prostory

Před napsáním kódu musíte importovat potřebné jmenné prostory. Přidejte následující řádky na začátek souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení vašeho projektu

Nejprve budete muset nastavit svůj projekt ve Visual Studiu (nebo preferovaném IDE). 

1. Vytvoření nového projektu C#: Otevřete Visual Studio a vytvořte nový projekt C# Console Application.
2. Instalace Aspose.Words pro .NET: K instalaci Aspose.Words pro .NET použijte Správce balíčků NuGet. Klikněte pravým tlačítkem na svůj projekt v Průzkumníku řešení, vyberte „Spravovat balíčky NuGet“, vyhledejte „Aspose.Words“ a nainstalujte jej.

## Krok 2: Vložte svůj dokument

Dále načtete dokument aplikace Word, který obsahuje starší řídicí znaky.

1. Zadejte cestu dokumentu: Nastavte cestu k adresáři dokumentů.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Vložte dokument: Použijte`Document` třídy k načtení dokumentu.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Krok 3: Nakonfigurujte možnosti uložení

Nyní nakonfigurujme možnosti uložení tak, aby zůstaly původní řídicí znaky nedotčené.

1.  Vytvořit možnosti uložení: Inicializace instance`OoxmlSaveOptions` a nastavte`KeepLegacyControlChars`majetek do`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Krok 4: Uložte dokument

Nakonec uložte dokument s nakonfigurovanými možnostmi uložení.

1.  Uložte dokument: Použijte`Save` metoda`Document` třídy k uložení dokumentu se zadanými možnostmi uložení.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Závěr

tady to máte! Pomocí těchto kroků můžete zajistit, že při práci s dokumenty aplikace Word v Aspose.Words for .NET budou zachovány vaše starší řídicí znaky. Tato funkce může být záchranou, zejména při práci se složitými dokumenty, kde hrají rozhodující roli řídící postavy. 

## FAQ

### Co jsou starší řídicí znaky?

Starší řídicí znaky jsou netisknutelné znaky používané ve starších dokumentech k řízení formátování a rozvržení.

### Mohu tyto řídicí znaky místo ponechání odstranit?

Ano, můžete použít Aspose.Words for .NET k odstranění nebo nahrazení těchto znaků v případě potřeby.

### Je tato funkce dostupná ve všech verzích Aspose.Words pro .NET?

Tato funkce je dostupná v posledních verzích. Ujistěte se, že používáte nejnovější verzi pro přístup ke všem funkcím.

### Potřebuji licenci k používání Aspose.Words pro .NET?

 Ano, potřebujete platnou licenci. Pro účely hodnocení můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Kde najdu další dokumentaci k Aspose.Words pro .NET?

 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
