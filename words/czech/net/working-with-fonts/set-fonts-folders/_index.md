---
"description": "Naučte se, jak nastavit vlastní složky písem v Aspose.Words pro .NET s tímto komplexním návodem krok za krokem. Ideální pro vývojáře, kteří chtějí vylepšit písma v dokumentech."
"linktitle": "Nastavení složek písem"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení složek písem"
"url": "/cs/net/working-with-fonts/set-fonts-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení složek písem

## Zavedení

Ahoj! Jste připraveni ponořit se do světa vlastních písem v Aspose.Words pro .NET? Pojďme na to. Tento tutoriál vás provede procesem nastavení vlastních složek písem a zajistí, aby vaše dokumenty vypadaly přesně tak, jak chcete. Ať už jste zkušený vývojář, nebo teprve začínáte, tento průvodce vás provede každým krokem. Takže, pojďme zajistit, aby vaše písma vypadala skvěle!

## Předpoklady

Než se do toho pustíme, ujistěme se, že máte vše potřebné:

- Aspose.Words pro .NET: Můžete [stáhnout](https://releases.aspose.com/words/net/) to, pokud jste to ještě neudělali.
- Visual Studio: Fungovat bude jakákoli verze, ale ta nejnovější je vždy nejlepší.
- Dokument: V tomto tutoriálu použijeme dokument aplikace Word. Můžete si vytvořit vlastní nebo použít existující.
- Vlastní písma: Mějte připravená nějaká vlastní písma. Použijeme je k demonstraci nastavení složek písem.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. To je nezbytné pro přístup ke třídám a metodám, které potřebujeme z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Po importu těchto jmenných prostorů jsme připraveni začít s nastavením vlastních složek písem.

## Krok 1: Definujte adresář dokumentů

Začněme definováním cesty k adresáři s vašimi dokumenty. Zde je uložen váš dokument Wordu. Použijeme proměnnou s názvem `dataDir` pro uložení této cesty.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu adresáři. To je zásadní, protože Aspose.Words bude potřebovat vědět, kde má váš dokument najít.

## Krok 2: Nastavení zdrojů písem

Dále musíme nastavit zdroje písem. Zde sdělíme Aspose.Words, kde má najít naše vlastní písma. Použijeme `FontSettings.DefaultInstance.SetFontsSources` metoda, jak toho dosáhnout.

```csharp
FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
	new SystemFontSource(), new FolderFontSource("C:\\MyFonts\\", true)
});
```

Zde je to, co děláme:

- SystemFontSource: Toto říká Aspose.Words, aby použil výchozí písma systému.
- ZdrojFotbalovéhoSouboru: Zde určujeme složku obsahující naše vlastní fonty. Nahradit `"C:\\MyFonts\\"` s cestou k adresáři s vlastními fonty. `true` Parametr označuje, že by měly být zahrnuty i podadresáře.

## Krok 3: Vložte dokument

Nyní, když jsme nastavili zdroje písem, je čas načíst dokument, se kterým chceme pracovat. Použijeme `Document` třída z Aspose. Slova pro toto.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Zajistěte, aby `"Rendering.docx"` je název vašeho dokumentu Word. Pokud má váš dokument jiný název, nezapomeňte jej odpovídajícím způsobem aktualizovat.

## Krok 4: Uložte dokument jako PDF

Nakonec si uložme dokument jako PDF, abychom viděli, jak vlastní písma fungují. Použijeme `Save` metoda `Document` třída.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFolders.pdf");
```

Tím se váš dokument uloží jako PDF do zadaného adresáře s použitím vlastních písem, které jsme nastavili dříve.

## Závěr

tady to máte! Úspěšně jste si nastavili vlastní složky s fonty v Aspose.Words pro .NET a uložili dokument jako PDF s těmito vlastními fonty. Docela skvělé, že? Úprava fontů může výrazně ovlivnit vzhled vašich dokumentů a teď přesně víte, jak na to. Přeji vám šťastné programování!

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro .NET?

Můžeš [stáhnout](https://releases.aspose.com/words/net/) nejnovější verzi Aspose.Words pro .NET z webových stránek.

### Mohu použít více vlastních složek s písmy?

Ano, můžete jich přidat více `FolderFontSource` případy k `SetFontsSources` metoda pro použití fontů z různých adresářů.

### Je nutné zahrnout systémové fonty?

Zahrnutí systémových písem je volitelné, ale doporučuje se, aby byla zajištěna dostupnost všech standardních písem.

### Jaké typy souborů podporuje Aspose.Words?

Aspose.Words podporuje širokou škálu formátů souborů, včetně DOCX, DOC, PDF, TXT, HTML a mnoha dalších.

### Jak mohu získat dočasnou licenci pro Aspose.Words?

Můžete získat [dočasná licence](https://purchase.aspose.com/temporary-license/) z webových stránek Aspose a vyzkoušejte si všechny funkce Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}