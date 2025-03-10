---
title: Převést metasoubory na EMF nebo WMF
linktitle: Převést metasoubory na EMF nebo WMF
second_title: Aspose.Words API pro zpracování dokumentů
description: Podrobný průvodce převodem metasouborů do formátu EMF nebo WMF při převodu dokumentu do HTML pomocí Aspose.Words for .NET.
weight: 10
url: /cs/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Převést metasoubory na EMF nebo WMF

## Zavedení

Vítejte u dalšího hlubokého ponoru do světa Aspose.Words pro .NET. Dnes řešíme úhledný trik: převod obrázků SVG do formátů EMF nebo WMF v dokumentech aplikace Word. Může to znít trochu technicky, ale nebojte se. Na konci tohoto tutoriálu v tom budete profík. Ať už jste zkušený vývojář nebo s Aspose.Words pro .NET teprve začínáte, tento průvodce vás krok za krokem provede vším, co potřebujete vědět.

## Předpoklady

Než se ponoříme do kódu, ujistíme se, že máme vše nastaveno. Zde je to, co potřebujete:

1.  Aspose.Words for .NET Library: Ujistěte se, že máte nejnovější verzi. Pokud jej nemáte, můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
3. Vývojové prostředí: IDE jako Visual Studio vám usnadní život.
4. Základní znalost C#: Nemusíte být expert, ale základní znalost vám pomůže.

Máš všechno? Velký! Začněme.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. To je zásadní, protože to našemu programu říká, kde najde třídy a metody, které budeme používat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tyto jmenné prostory pokrývají vše od základních systémových funkcí až po specifickou funkci Aspose.Words, kterou potřebujeme pro tento tutoriál.

## Krok 1: Nastavte adresář dokumentů

Začněme definováním cesty k adresáři dokumentů. Zde se uloží váš dokument aplikace Word poté, co převedeme metasoubory.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument uložit.

## Krok 2: Vytvořte HTML řetězec pomocí SVG

Dále potřebujeme řetězec HTML, který obsahuje obrázek SVG, který chceme převést. Zde je jednoduchý příklad:

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Tento úryvek HTML obsahuje základní SVG s nápisem „Ahoj světe!“.

## Krok 3: Načtěte HTML pomocí možnosti ConvertSvgToEmf

 Nyní používáme`HtmlLoadOptions` specifikovat, jak chceme zacházet s obrázky SVG v HTML. Nastavení`ConvertSvgToEmf` na`true` zajišťuje převod obrázků SVG do formátu EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Tento fragment kódu vytvoří nový`Document` objekt načtením řetězce HTML do něj se zadanými možnostmi načtení.

## Krok 4: Nastavte HtmlSaveOptions pro formát metasouboru

 Pro uložení dokumentu ve správném formátu metasouboru používáme`HtmlSaveOptions` . Tady jsme nastavili`MetafileFormat` na`HtmlMetafileFormat.Png` , ale můžete to změnit na`Emf` nebo`Wmf` v závislosti na vašich potřebách.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Krok 5: Uložte dokument

Nakonec dokument uložíme pomocí zadaných možností uložení.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Tím se dokument uloží do zadaného adresáře s formátem metasouboru převedeným podle definice.

## Závěr

tady to máte! Pomocí těchto kroků jste úspěšně převedli obrázky SVG do formátů EMF nebo WMF v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tato metoda je užitečná pro zajištění kompatibility a zachování vizuální integrity vašich dokumentů na různých platformách. Šťastné kódování!

## FAQ

### Mohu pomocí této metody převést jiné formáty obrázků?
Ano, můžete převádět různé formáty obrázků úpravou zatížení a možností uložení.

### Je nutné použít konkrétní verzi .NET Framework?
Aspose.Words for .NET podporuje více verzí .NET Framework, ale vždy je dobré použít nejnovější verzi pro nejlepší kompatibilitu a funkce.

### Jaká je výhoda převodu SVG na EMF nebo WMF?
Převod SVG do EMF nebo WMF zajišťuje zachování a správné vykreslení vektorové grafiky v prostředích, která nemusí plně podporovat SVG.

### Mohu tento proces automatizovat pro více dokumentů?
Absolutně! Můžete procházet více soubory HTML a použít stejný proces k automatizaci převodu pro dávkové zpracování.

### Kde najdu další zdroje a podporu pro Aspose.Words pro .NET?
 Můžete najít komplexní dokumentaci[zde](https://reference.aspose.com/words/net/) a získat podporu od komunity Aspose[zde](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
