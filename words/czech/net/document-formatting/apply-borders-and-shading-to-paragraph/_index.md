---
title: Použít ohraničení a stínování na odstavec v dokumentu aplikace Word
linktitle: Použít ohraničení a stínování na odstavec v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Použijte ohraničení a stínování na odstavce v dokumentech aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce pro vylepšení formátování dokumentu.
weight: 10
url: /cs/net/document-formatting/apply-borders-and-shading-to-paragraph/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použít ohraničení a stínování na odstavec v dokumentu aplikace Word

## Zavedení

Ahoj, přemýšleli jste někdy nad tím, jak docílit toho, aby vaše dokumenty ve Wordu vynikly efektními okraji a stínováním? Tak to jste na správném místě! Dnes se ponoříme do světa Aspose.Words for .NET, abychom oživili naše odstavce. Představte si, že váš dokument vypadá stejně elegantně jako práce profesionálního návrháře s pouhými několika řádky kódu. Jste připraveni začít? Jdeme na to!

## Předpoklady

Než si vyhrneme rukávy a vrhneme se na kódování, ujistíme se, že máme vše, co potřebujeme. Zde je váš rychlý kontrolní seznam:

-  Aspose.Words for .NET: Tuto knihovnu musíte mít nainstalovanou. Můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
- Základní znalost C#: Stačí jen porozumět a vyladit úryvky kódu.
- Platná licence: Buď a[dočasná licence](https://purchase.aspose.com/temporary-license/) nebo zakoupenou od[Aspose](https://purchase.aspose.com/buy).

## Importovat jmenné prostory

Než skočíme do kódu, musíme se ujistit, že máme do našeho projektu importované potřebné jmenné prostory. To nám zpřístupňuje všechny skvělé funkce Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Nyní si tento proces rozdělíme na malé kroky. Každý krok bude mít nadpis a podrobné vysvětlení. Připraveni? Jdeme na to!

## Krok 1: Nastavte adresář dokumentů

Nejprve potřebujeme místo pro uložení našeho krásně naformátovaného dokumentu. Nastavíme cestu k vašemu adresáři dokumentů.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Tento adresář je místem, kde bude uložen váš konečný dokument. Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou na vašem počítači.

## Krok 2: Vytvořte nový dokument a DocumentBuilder

 Dále musíme vytvořit nový dokument a`DocumentBuilder` objekt. The`DocumentBuilder` je naše kouzelná hůlka, která nám umožňuje manipulovat s dokumentem.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 The`Document` objekt představuje celý náš dokument aplikace Word a`DocumentBuilder` nám pomáhá přidávat a formátovat obsah.

## Krok 3: Definujte ohraničení odstavců

Nyní do našeho odstavce přidáme stylové ohraničení. Definujeme vzdálenost od textu a nastavíme různé styly ohraničení.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Zde nastavíme 20bodovou vzdálenost mezi textem a ohraničením. Ohraničení na všech stranách (vlevo, vpravo, nahoře, dole) jsou nastaveny na dvojité čáry. Efektní, že?

## Krok 4: Použijte stínování na odstavec

Hranice jsou skvělé, ale pojďme to trochu posouvat stínováním. Aby náš odstavec vynikl, použijeme vzor diagonálního kříže se směsí barev.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

V tomto kroku jsme použili diagonální křížovou texturu se světlou korálovou jako barvou pozadí a světle lososovou jako barvou popředí. Je to jako oblékat svůj odstavec do značkového oblečení!

## Krok 5: Přidejte text do odstavce

Co je to odstavec bez textu? Přidejme ukázkovou větu, abychom viděli naše formátování v akci.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Tento řádek vloží náš text do dokumentu. Jednoduché, ale nyní je zabaleno do stylového rámu a stínovaného pozadí.

## Krok 6: Uložte dokument

Konečně je čas zachránit naši práci. Uložme dokument do zadaného adresáře s popisným názvem.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

 Tím se náš dokument uloží s názvem`DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` v adresáři, který jsme uvedli dříve.

## Závěr

A tady to máte! Pomocí několika řádků kódu jsme přeměnili prostý odstavec na vizuálně přitažlivý obsah. Aspose.Words for .NET neuvěřitelně usnadňuje přidání profesionálně vyhlížejícího formátování do vašich dokumentů. Ať už připravujete zprávu, dopis nebo jakýkoli dokument, tyto triky vám pomohou udělat skvělý dojem. Takže jděte do toho, vyzkoušejte to a sledujte, jak vaše dokumenty ožívají!

## FAQ

### Mohu pro každé ohraničení použít různé styly čar?  
 Absolutně! Aspose.Words for .NET vám umožňuje přizpůsobit každý okraj individuálně. Stačí nastavit`LineStyle` pro každý typ ohraničení, jak je uvedeno v průvodci.

### Jaké další stínovací textury jsou k dispozici?  
 Můžete použít několik textur, například plný, vodorovný pruh, svislý pruh a další. Zkontrolujte[Založte dokumentaci](https://reference.aspose.com/words/net/) pro úplný seznam.

### Jak mohu změnit barvu okraje?  
 Barvu ohraničení můžete nastavit pomocí`Color` vlastnost pro každou hranici. Například,`borders[BorderType.Left].Color = Color.Red;`.

### Je možné použít ohraničení a stínování na konkrétní část textu?  
 Ano, můžete použít ohraničení a stínování na konkrétní úseky textu pomocí`Run` objekt uvnitř`DocumentBuilder`.

### Mohu tento proces automatizovat pro více odstavců?  
Rozhodně! Můžete procházet odstavce a programově použít stejná nastavení ohraničení a stínování.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
