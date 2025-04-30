---
"description": "Naučte se, jak povolit nebo zakázat nahrazování písem v dokumentech Word pomocí Aspose.Words pro .NET. Zajistěte, aby vaše dokumenty vypadaly konzistentně na všech platformách."
"linktitle": "Povolit Zakázat nahrazování písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Povolit Zakázat nahrazování písem"
"url": "/cs/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Povolit Zakázat nahrazování písem

## Zavedení

Už jste se někdy ocitli v situaci, kdy se vámi pečlivě vybraná písma v dokumentu Wordu při prohlížení na jiném počítači nahradí? Nepříjemné, že? Děje se to kvůli substituci písem, což je proces, při kterém systém nahradí chybějící písmo dostupným. Ale nebojte se! S Aspose.Words pro .NET můžete snadno spravovat a ovládat substituci písem. V tomto tutoriálu vás provedeme kroky, jak povolit nebo zakázat substituci písem ve vašich dokumentech Wordu, a zajistíme tak, aby vaše dokumenty vždy vypadaly přesně tak, jak chcete.

## Předpoklady

Než se pustíme do jednotlivých kroků, ujistěte se, že máte vše, co potřebujete:

- Aspose.Words pro .NET: Stáhněte si nejnovější verzi [zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli verze podporující .NET.
- Základní znalost C#: To vám pomůže sledovat příklady kódování.

## Importovat jmenné prostory

Nejprve se ujistěte, že máte v projektu importovány potřebné jmenné prostory. Přidejte je na začátek souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Nyní si celý proces rozdělme na jednoduché a zvládnutelné kroky.

## Krok 1: Nastavení projektu

Nejprve si v aplikaci Visual Studio vytvořte nový projekt a přidejte odkaz na knihovnu Aspose.Words pro .NET. Pokud jste tak ještě neučinili, stáhněte si ji z... [Webové stránky Aspose](https://releases.aspose.com/words/net/).

## Krok 2: Vložte dokument

Dále načtěte dokument, se kterým chcete pracovat. Postupujte takto:

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k adresáři s dokumenty. Tento kód načte dokument do paměti, abyste s ním mohli manipulovat.

## Krok 3: Konfigurace nastavení písma

Nyní si vytvořme `FontSettings` objekt pro správu nastavení nahrazování písem:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Krok 4: Nastavení výchozí substituce písma

Nastavte výchozí náhradní písmo na písmo dle vašeho výběru. Toto písmo bude použito, pokud původní písmo není k dispozici:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

tomto příkladu používáme jako výchozí písmo Arial.

## Krok 5: Zakázat nahrazování informací o písmu

Chcete-li zakázat nahrazování informací o písmu, které systému brání v nahrazování chybějících písem dostupnými, použijte následující kód:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Krok 6: Použití nastavení písma v dokumentu

Nyní použijte na dokument tato nastavení:

```csharp
doc.FontSettings = fontSettings;
```

## Krok 7: Uložte dokument

Nakonec upravený dokument uložte. Můžete jej uložit v libovolném formátu. V tomto tutoriálu jej uložíme jako PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Závěr

A tady to máte! Dodržováním těchto kroků můžete snadno ovládat nahrazování písem ve svých dokumentech Word pomocí Aspose.Words pro .NET. Tím zajistíte, že si vaše dokumenty zachovají zamýšlený vzhled a dojem bez ohledu na to, kde si je prohlížíte.

## Často kladené otázky

### Mohu pro nahrazení použít jiná písma než Arial?

Rozhodně! Můžete zadat libovolné písmo dostupné ve vašem systému změnou názvu písma v `DefaultFontName` vlastnictví.

### Co se stane, když zadané výchozí písmo není k dispozici?

Pokud výchozí písmo není k dispozici, Aspose.Words použije systémový záložní mechanismus k nalezení vhodné náhrady.

### Mohu po vypnutí nahrazování písem znovu povolit?

Ano, můžete přepínat `Enabled` majetek `FontInfoSubstitution` zpět k `true` pokud chcete znovu povolit nahrazování písem.

### Existuje způsob, jak zkontrolovat, která písma se nahrazují?

Ano, Aspose.Words poskytuje metody pro zaznamenávání a sledování nahrazování písem, což vám umožňuje vidět, která písma jsou nahrazována.

### Mohu tuto metodu použít i pro jiné formáty dokumentů než DOCX?

Rozhodně! Aspose.Words podporuje různé formáty a tato nastavení písma můžete použít na jakýkoli podporovaný formát.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}