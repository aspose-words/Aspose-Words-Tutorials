---
"description": "Naučte se, jak vložit plovoucí obrázek do dokumentu Wordu pomocí Aspose.Words pro .NET s tímto podrobným návodem krok za krokem. Ideální pro vylepšení vašich dokumentů."
"linktitle": "Vložit plovoucí obrázek do dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit plovoucí obrázek do dokumentu Word"
"url": "/cs/net/add-content-using-documentbuilder/insert-floating-image/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit plovoucí obrázek do dokumentu Word

## Zavedení

Představte si, že vytváříte úžasnou zprávu nebo návrh, kde jsou obrázky dokonale umístěny tak, aby doplňovaly váš text. S Aspose.Words pro .NET toho dosáhnete bez námahy. Tato knihovna poskytuje výkonné funkce pro manipulaci s dokumenty, což z ní dělá užitečné řešení pro vývojáře. V tomto tutoriálu se zaměříme na vkládání plovoucího obrázku pomocí třídy DocumentBuilder. Ať už jste zkušený vývojář, nebo teprve začínáte, tento průvodce vás provede jednotlivými kroky.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máte vše, co potřebujete k zahájení:

1. Aspose.Words pro .NET: Knihovnu si můžete stáhnout z [Stránka s vydáním Aspose](https://releases.aspose.com/words/net/).
2. Visual Studio: Jakákoli verze, která podporuje vývoj v .NET.
3. Základní znalost C#: Pochopení základů programování v C# bude užitečné.
4. Soubor obrázku: Soubor obrázku, který chcete vložit, například logo nebo obrázek.

## Importovat jmenné prostory

Chcete-li ve svém projektu použít Aspose.Words, je nutné importovat potřebné jmenné prostory. To se provede přidáním následujících řádků na začátek vašeho souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

S těmito předpoklady a jmennými prostory jsme připraveni začít s naším tutoriálem.

Pojďme si rozebrat proces vkládání plovoucího obrázku do dokumentu Wordu na snadno zvládnutelné kroky. Každý krok bude podrobně vysvětlen, abyste ho mohli bez problémů sledovat.

## Krok 1: Nastavení projektu

Nejprve si v aplikaci Visual Studio vytvořte nový projekt C#. Pro zjednodušení si můžete vybrat konzolovou aplikaci.

1. Otevřete Visual Studio a vytvořte nový projekt.
2. Vyberte „Konzolová aplikace (.NET Core)“ a klikněte na „Další“.
3. Pojmenujte svůj projekt a vyberte umístění pro jeho uložení. Klikněte na tlačítko „Vytvořit“.
4. Nainstalujte Aspose.Words pro .NET pomocí Správce balíčků NuGet. V Průzkumníku řešení klikněte pravým tlačítkem myši na svůj projekt, vyberte možnost „Spravovat balíčky NuGet“ a vyhledejte „Aspose.Words“. Nainstalujte nejnovější verzi.

## Krok 2: Inicializace dokumentu a DocumentBuilderu

Nyní, když je váš projekt nastavený, inicializujme objekty Document a DocumentBuilder.

1. Vytvořte novou instanci `Document` třída:

```csharp
Document doc = new Document();
```

2. Inicializace objektu DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ten/Ta/To `Document` objekt představuje dokument aplikace Word a `DocumentBuilder` pomáhá s přidáváním obsahu.

## Krok 3: Definování cesty k obrázku

Dále zadejte cestu k souboru s obrázkem. Ujistěte se, že je k obrázku přístupný z adresáře vašeho projektu.

Definujte adresář s obrázky a název souboru s obrázkem:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je váš obrázek uložen.

## Krok 4: Vložení plovoucího obrázku

Jakmile je vše nastaveno, vložme plovoucí obrázek do dokumentu.

Použijte `InsertImage` metoda `DocumentBuilder` třída pro vložení obrázku:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Zde je význam jednotlivých parametrů:
- `imagePath`: Cesta k souboru s obrázkem.
- `RelativeHorizontalPosition.Margin`: Horizontální poloha vzhledem k okraji.
- `100`: Horizontální odsazení od okraje (v bodech).
- `RelativeVerticalPosition.Margin`Svislá poloha vzhledem k okraji.
- `100`Svislé odsazení od okraje (v bodech).
- `200`Šířka obrázku (v bodech).
- `100`Výška obrázku (v bodech).
- `WrapType.Square`Styl obtékání textu kolem obrázku.

## Krok 5: Uložte dokument

Nakonec dokument uložte na požadované místo.

1. Zadejte cestu k výstupnímu souboru:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Uložte dokument:

```csharp
doc.Save(outputPath);
```

Váš dokument Wordu s plovoucím obrázkem je nyní připraven!

## Závěr

Vložení plovoucího obrázku do dokumentu Word pomocí Aspose.Words pro .NET je jednoduchý proces, pokud jej rozdělíte na snadno zvládnutelné kroky. Dodržováním tohoto návodu můžete do svých dokumentů přidat profesionálně vypadající obrázky a vylepšit tak jejich vizuální atraktivitu. Aspose.Words poskytuje robustní API, které usnadňuje manipulaci s dokumenty, ať už pracujete na zprávách, návrzích nebo jakémkoli jiném typu dokumentu.

## Často kladené otázky

### Mohu vložit více obrázků pomocí Aspose.Words pro .NET?

Ano, můžete vložit více obrázků opakováním `InsertImage` metodu pro každý obrázek s požadovanými parametry.

### Jak změním polohu obrázku?

Můžete upravit `RelativeHorizontalPosition`, `RelativeVerticalPosition`a parametry posunutí pro umístění obrázku podle potřeby.

### Jaké další typy obtékání jsou k dispozici pro obrázky?

Aspose.Words podporuje různé typy zalamování, jako například `Inline`, `TopBottom`, `Tight`, `Through`další. Můžete si vybrat ten, který nejlépe odpovídá rozvržení vašeho dokumentu.

### Mohu použít různé formáty obrázků?

Ano, Aspose.Words podporuje širokou škálu obrazových formátů včetně JPEG, PNG, BMP a GIF.

### Jak získám bezplatnou zkušební verzi Aspose.Words pro .NET?

Bezplatnou zkušební verzi můžete získat od [Zkušební stránka Aspose zdarma](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}