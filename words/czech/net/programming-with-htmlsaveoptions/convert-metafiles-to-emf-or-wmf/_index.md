---
"description": "Podrobný návod k převodu metasouborů do formátů EMF nebo WMF při převodu dokumentu do HTML pomocí Aspose.Words pro .NET."
"linktitle": "Převod metasouborů do formátu EMF nebo WMF"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Převod metasouborů do formátu EMF nebo WMF"
"url": "/cs/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Převod metasouborů do formátu EMF nebo WMF

## Zavedení

Vítejte u dalšího hlubokého ponoru do světa Aspose.Words pro .NET. Dnes se pustíme do šikovného triku: převodu obrázků SVG do formátů EMF nebo WMF ve vašich dokumentech Word. Může to znít trochu technicky, ale nebojte se. Po absolvování tohoto tutoriálu v tom budete profesionál. Ať už jste zkušený vývojář, nebo s Aspose.Words pro .NET teprve začínáte, tento průvodce vás krok za krokem provede vším, co potřebujete vědět.

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máme vše nastavené. Zde je to, co budete potřebovat:

1. Knihovna Aspose.Words pro .NET: Ujistěte se, že máte nejnovější verzi. Pokud ji nemáte, můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
3. Vývojové prostředí: IDE jako Visual Studio vám usnadní život.
4. Základní znalost C#: Nemusíte být expert, ale základní znalost vám pomůže.

Máte všechno? Skvělé! Pojďme na to.

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory. To je klíčové, protože to našemu programu říká, kde má najít třídy a metody, které budeme používat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tyto jmenné prostory pokrývají vše od základních systémových funkcí až po specifické funkce Aspose.Words, které potřebujeme pro tento tutoriál.

## Krok 1: Nastavení adresáře dokumentů

Začněme definováním cesty k adresáři s vašimi dokumenty. Sem bude uložen váš dokument Wordu po převodu metasouborů.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument uložit.

## Krok 2: Vytvořte HTML řetězec pomocí SVG

Dále potřebujeme řetězec HTML, který obsahuje obrázek SVG, který chceme převést. Zde je jednoduchý příklad:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg šířka='500' výška='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Tento úryvek HTML kódu obsahuje základní SVG kód s nápisem „Ahoj světe!“.

## Krok 3: Načtěte HTML s volbou ConvertSvgToEmf

Nyní používáme `HtmlLoadOptions` , abychom určili, jak chceme v HTML zacházet s obrázky SVG. Nastavení `ConvertSvgToEmf` na `true` zajišťuje, že obrázky SVG jsou převedeny do formátu EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Tento úryvek kódu vytvoří nový `Document` objekt načtením HTML řetězce do něj se zadanými možnostmi načítání.

## Krok 4: Nastavení HtmlSaveOptions pro formát metasouboru

Pro uložení dokumentu ve správném formátu metasouboru používáme `HtmlSaveOptions`Zde nastavíme `MetafileFormat` na `HtmlMetafileFormat.Png`, ale můžete to změnit na `Emf` nebo `Wmf` v závislosti na vašich potřebách.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Krok 5: Uložte dokument

Nakonec dokument uložíme s použitím zadaných možností ukládání.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Tím se dokument uloží do zadaného adresáře s formátem metasouboru převedeným dle definice.

## Závěr

je to! Dodržováním těchto kroků jste úspěšně převedli obrázky SVG do formátů EMF nebo WMF ve vašich dokumentech Word pomocí Aspose.Words pro .NET. Tato metoda je užitečná pro zajištění kompatibility a zachování vizuální integrity vašich dokumentů napříč různými platformami. Přeji vám šťastné programování!

## Často kladené otázky

### Mohu touto metodou převést i jiné obrazové formáty?
Ano, můžete převést různé formáty obrázků úpravou možností načítání a ukládání.

### Je nutné používat konkrétní verzi .NET Frameworku?
Aspose.Words pro .NET podporuje více verzí .NET Frameworku, ale pro nejlepší kompatibilitu a funkce je vždy dobré používat nejnovější verzi.

### Jaká je výhoda převodu SVG do EMF nebo WMF?
Převod SVG do EMF nebo WMF zajišťuje, že vektorová grafika bude zachována a správně vykreslena v prostředích, která nemusí plně podporovat SVG.

### Mohu tento proces automatizovat pro více dokumentů?
Rozhodně! Můžete procházet více HTML souborů a použít stejný proces k automatizaci převodu pro dávkové zpracování.

### Kde najdu další zdroje a podporu pro Aspose.Words pro .NET?
Najdete zde komplexní dokumentaci [zde](https://reference.aspose.com/words/net/) a získejte podporu od komunity Aspose [zde](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}