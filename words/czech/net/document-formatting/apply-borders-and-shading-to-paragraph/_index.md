---
"description": "Okraje a stínování odstavců v dokumentech Wordu můžete použít pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu a vylepšete formátování dokumentu."
"linktitle": "Použití ohraničení a stínování na odstavec v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Použití ohraničení a stínování na odstavec v dokumentu Word"
"url": "/cs/net/document-formatting/apply-borders-and-shading-to-paragraph/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použití ohraničení a stínování na odstavec v dokumentu Word

## Zavedení

Ahoj, přemýšleli jste někdy, jak vylepšit dokumenty Wordu pomocí ozdobných okrajů a stínování? Tak jste na správném místě! Dnes se ponoříme do světa Aspose.Words pro .NET, abychom oživili naše odstavce. Představte si, že váš dokument bude vypadat elegantně jako práce profesionálního designéra jen s několika řádky kódu. Jste připraveni začít? Pojďme na to!

## Předpoklady

Než si vyhrneme rukávy a pustíme se do programování, ujistěme se, že máme vše, co potřebujeme. Zde je váš stručný kontrolní seznam:

- Aspose.Words pro .NET: Musíte mít tuto knihovnu nainstalovanou. Můžete si ji stáhnout z [Webové stránky Aspose](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
- Základní znalost C#: Dostatečná znalost kódu pro pochopení a úpravu úryvků kódu.
- Platný řidičský průkaz: Buď [dočasná licence](https://purchase.aspose.com/temporary-license/) nebo zakoupený od [Aspose](https://purchase.aspose.com/buy).

## Importovat jmenné prostory

Než se pustíme do kódování, musíme se ujistit, že máme do našeho projektu importované potřebné jmenné prostory. Díky tomu budeme mít přístup ke všem skvělým funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using Aspose.Words.Drawing;
using System.Drawing;
```

Nyní si celý proces rozdělme na několik kroků. Každý krok bude mít nadpis a podrobné vysvětlení. Jste připraveni? Jdeme na to!

## Krok 1: Nastavení adresáře dokumentů

Nejdříve potřebujeme místo, kam uložíme náš krásně naformátovaný dokument. Nastavme cestu k adresáři s dokumenty.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Do tohoto adresáře bude uložen váš finální dokument. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou na vašem počítači.

## Krok 2: Vytvořte nový dokument a nástroj DocumentBuilder

Dále musíme vytvořit nový dokument a `DocumentBuilder` Objekt. Ten `DocumentBuilder` je naše kouzelná hůlka, která nám umožňuje manipulovat s dokumentem.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten/Ta/To `Document` objekt představuje celý náš dokument Word a `DocumentBuilder` pomáhá nám přidávat a formátovat obsah.

## Krok 3: Definování ohraničení odstavců

Nyní přidáme k našemu odstavci stylové ohraničení. Definujeme vzdálenost od textu a nastavíme různé styly ohraničení.

```csharp
BorderCollection borders = builder.ParagraphFormat.Borders;
borders.DistanceFromText = 20;
borders[BorderType.Left].LineStyle = LineStyle.Double;
borders[BorderType.Right].LineStyle = LineStyle.Double;
borders[BorderType.Top].LineStyle = LineStyle.Double;
borders[BorderType.Bottom].LineStyle = LineStyle.Double;
```

Zde nastavíme vzdálenost mezi textem a okraji 20 bodů. Okraje na všech stranách (vlevo, vpravo, nahoře, dole) jsou nastaveny na dvojité čáry. To je skvělé, že?

## Krok 4: Použití stínování na odstavec

Okraje jsou skvělé, ale pojďme to vylepšit stínováním. Použijeme diagonální křížový vzor s prolínáním barev, abychom náš odstavec zvýraznili.

```csharp
Shading shading = builder.ParagraphFormat.Shading;
shading.Texture = TextureIndex.TextureDiagonalCross;
shading.BackgroundPatternColor = System.Drawing.Color.LightCoral;
shading.ForegroundPatternColor = System.Drawing.Color.LightSalmon;
```

V tomto kroku jsme použili diagonální křížovou texturu se světle korálovou barvou pozadí a světle lososovou barvou popředí. Je to jako obléknout váš odstavec do značkového oblečení!

## Krok 5: Přidání textu do odstavce

Co je to odstavec bez textu? Přidejme ukázkovou větu, abychom viděli, jak naše formátování funguje.

```csharp
builder.Write("I'm a formatted paragraph with double border and nice shading.");
```

Tento řádek vloží náš text do dokumentu. Jednoduché, ale nyní je zabalený ve stylovém rámečku a se stínovaným pozadím.

## Krok 6: Uložte dokument

Konečně je čas uložit naši práci. Uložme dokument do zadaného adresáře s popisným názvem.

```csharp
doc.Save(dataDir + "DocumentFormatting.ApplyBordersAndShadingToParagraph.doc");
```

Tím se náš dokument uloží s názvem `DocumentFormatting.ApplyBordersAndShadingToParagraph.doc` v adresáři, který jsme dříve uvedli.

## Závěr

tady to máte! S pouhými několika řádky kódu jsme proměnili obyčejný odstavec ve vizuálně přitažlivý obsah. Aspose.Words pro .NET neuvěřitelně usnadňuje přidávání profesionálně vypadajícího formátování do vašich dokumentů. Ať už připravujete zprávu, dopis nebo jakýkoli jiný dokument, tyto triky vám pomohou udělat skvělý dojem. Tak do toho, vyzkoušejte to a sledujte, jak vaše dokumenty ožívají!

## Často kladené otázky

### Mohu pro každý okraj použít různé styly čar?  
Rozhodně! Aspose.Words pro .NET umožňuje individuálně přizpůsobit každý okraj. Stačí nastavit `LineStyle` pro každý typ ohraničení, jak je uvedeno v průvodci.

### Jaké další textury stínování jsou k dispozici?  
Můžete použít několik textur, například plnou, vodorovný pruh, svislý pruh a další. Zkontrolujte [Dokumentace Aspose](https://reference.aspose.com/words/net/) pro úplný seznam.

### Jak mohu změnit barvu okraje?  
Barvu ohraničení můžete nastavit pomocí `Color` vlastnost pro každou hranici. Například `borders[BorderType.Left].Color = Color.Red;`.

### Je možné použít ohraničení a stínování na určitou část textu?  
Ano, můžete použít ohraničení a stínování na konkrétní úseky textu pomocí `Run` objekt uvnitř `DocumentBuilder`.

### Mohu tento proces automatizovat pro více odstavců?  
Rozhodně! Můžete procházet odstavce a programově aplikovat stejná nastavení ohraničení a stínování.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}