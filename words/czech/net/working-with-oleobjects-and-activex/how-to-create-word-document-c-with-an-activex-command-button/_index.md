---
category: general
date: 2026-10-26
description: Naučte se, jak vytvořit dokument Word v C# a programově přidat ActiveX
  tlačítko. Tento krok‑za‑krokem průvodce zahrnuje vložení příkazového tlačítka, jeho
  skrytí v návrhovém režimu a uložení souboru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: cs
lastmod: 2026-10-26
og_description: Vytvořte dokument Word v C# a programově přidejte ActiveX tlačítko.
  Postupujte podle tohoto kompletního tutoriálu, jak vložit příkazové tlačítko, které
  se zobrazí pouze během běhu.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Vytvořte Word dokument v C# s tlačítkem ActiveX – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Jak vytvořit Word dokument v C# s ActiveX tlačítkem příkazu
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument C# s ActiveX tlačítkem příkazu

Pokud potřebujete **vytvořit Word dokument C#**, který obsahuje interaktivní tlačítko, tento průvodce vám přesně ukáže, jak na to. Po přečtení prvních dvou vět budete znát celkový přístup a následující kroky vás provedou každým řádkem kódu, který musíte napsat.

Naučíte se, jak přidat ActiveX tlačítko, skrýt jej během návrhu a zobrazit jej pouze při otevření souboru uživatelem. Tutoriál také pokrývá běžné úskalí, jako jsou bezpečnostní varování a kompatibilita verzí, takže můžete dodávat spolehlivé dokumenty.

## Požadavky

* .NET 6.0 nebo novější nainstalováno  
* Licencovaná kopie **Aspose.Words for .NET** (bezplatná zkušební verze funguje pro experimentování)  
* Základní znalost C# a Visual Studio (jakékoli IDE podporující .NET bude stačit)

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Krok 1: Vytvořit Word dokument C# a inicializovat DocumentBuilder

Prvním krokem je vytvořit objekt `Document` a `DocumentBuilder`. `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje plynulé metody pro přidávání obsahu.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Proč je to důležité:** Bez `DocumentBuilder` byste museli ručně manipulovat s OpenXML DOM, což je náchylné k chybám a těžší na čtení. Builder abstrahuje tyto detaily a zaručuje dobře vytvořený Word soubor.

## Krok 2: Jak přidat ActiveX tlačítko – vložit ovládací prvek CommandButton

Nyní vložíme **ActiveX ovládací prvek CommandButton** na konkrétní místo. Obdélník určuje pozici tlačítka (X, Y) a velikost (šířka, výška) v bodech.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Proč je to důležité:** `InsertForms2OleControl` je jediná metoda Aspose.Words, která vytváří skutečný ActiveX OLE objekt. Hodnota výčtu `Forms2OleControlType.CommandButton` říká Wordu, aby vložil klikatelné tlačítko místo obecného OLE kontejneru.

## Krok 3: Programově přidat tlačítko příkazu – skrýt jej do doby běhu

Word považuje jakýkoli vložený tvar za viditelný ve výchozím nastavení. Aby tlačítko zůstalo neviditelné během návrhu šablony, nastavte vlastnost `Hidden` na tvar, který builder právě vytvořil.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Proč je to důležité:** Nastavení `Hidden = true` zabraňuje tomu, aby tlačítko zaplňovalo návrhové zobrazení. Když je dokument otevřen ve Wordu, běhové prostředí automaticky odhalí ovládací prvek, čímž zachová zamýšlený uživatelský zážitek.

## Krok 4: Uložit soubor – vytvořit Word dokument s tlačítkem příkazu

Nakonec zapíšete dokument na disk. Vyberte cestu, do které může vaše aplikace zapisovat, a použijte příponu `.docx`, aby byla zajištěna moderní kompatibilita.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Proč je to důležité:** Ukládání jako `.docx` zaručuje, že vložený ActiveX ovládací prvek splňuje standard Office Open XML, který podporuje Word 2007 a novější. Pokud potřebujete podporu staršího formátu `.doc`, změňte příponu a použijte `SaveFormat.Doc`.

## Kompletní funkční příklad

Když spojíme vše dohromady, zde je kompletní program, který můžete zkopírovat, vložit a spustit:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Očekávaný výstup:** Po spuštění programu otevřete `C:\Temp\ActiveX.docx` v Microsoft Word. Uvidíte prázdný dokument; tlačítko není viditelné v režimu návrhu. Stiskněte **Alt + F9** pro přepnutí kódů polí, poté klikněte na oblast tlačítka — Word vykreslí ActiveX ovládací prvek a můžete s ním interagovat (např. dvojklikem zobrazíte jeho vlastnosti).

## Okrajové případy a tipy nejlepších postupů

| Situace | Na co si dát pozor | Doporučené řešení |
|-----------|-------------------|-----------------|
| **Uživatel zakáže ActiveX** | Word může zobrazit bezpečnostní varování nebo blokovat ovládací prvek. | Uveďte koncovým uživatelům, aby v Trust Center povolili „ActiveX controls“, nebo poskytněte alternativu podepsanou makrem. |
| **Dokument otevřen ve Word Online** | Word Online nepodporuje ActiveX; tlačítko bude vynecháno. | Použijte záložní hypertextový odkaz nebo obsahový ovládací prvek, pokud potřebujete kompatibilitu s cloudem. |
| **Různé nastavení DPI** | Velikost obdélníku se může na displejích s vysokým DPI jevit větší nebo menší. | Použijte `GraphicsUnit.Point` (výchozí) a testujte na běžných nastaveních DPI (96 dpi, 120 dpi). |
| **Více tlačítek** | Volání `GetChildNodes(NodeType.Shape, true)[0]` získá pouze první tvar. | Procházejte `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` a nastavte `Hidden` pro každý tvar, který přidáte. |
| **Starší formát .doc** | Některé vlastnosti ActiveX se při ukládání jako `.doc` ztratí. | Upřednostněte `.docx`, pokud nemáte přísnou požadavek na starší formát. |

**Tip:** Po vložení tlačítka můžete přiřadit makro k jeho vlastnosti `OnAction` přes uživatelské rozhraní Wordu. To vám umožní definovat vlastní chování při kliknutí bez psaní dalšího C# kódu.

## Často kladené otázky

* **Funguje to s .NET Core?**  
  Ano. Aspose.Words for .NET je plně kompatibilní s .NET 5, .NET 6 a novějšími. Stačí odkazovat na stejný balíček NuGet.

* **Mohu změnit popisek tlačítka po vygenerování dokumentu?**  
  Popisek nastavený v `InsertForms2OleControl` se stane výchozím textem během návrhu. Uživatelé jej mohou ve Wordu upravit, ale můžete také aktualizovat popisek programově přístupem k vlastnostem OLE objektu přes API `Shape.OleFormat`.

* **Co když potřebuji jinou velikost tlačítka?**  
  Upravit hodnoty `RectangleF`. První dva parametry jsou souřadnice X a Y; poslední dva jsou šířka a výška v bodech (1 pt = 1/72 palce).

## Závěr

Nyní víte, jak **vytvořit Word dokument C#** a **programově přidat tlačítko příkazu** pomocí Aspose.Words. Tutoriál pokryl inicializaci dokumentu, vložení ActiveX tlačítka, jeho skrytí do doby běhu a uložení finálního souboru. S těmito stavebními kameny můžete vložit interaktivní ovládací prvky do libovolné Word šablony, kterou generujete.

Dále prozkoumejte související témata, jako je **jak přidat ActiveX tlačítko** a zpracování událostí, **vytvořit stylování tlačítka příkazu ve Wordu** pomocí VBA a **programově přidat tlačítko příkazu** do existujících dokumentů. Rozšíření tohoto vzoru na zaškrtávací políčka, rozbalovací seznamy nebo vlastní OLE objekty následuje stejné kroky — stačí změnit hodnotu výčtu `Forms2OleControlType`.

Začněte experimentovat: nahraďte popisek, upravte pozici nebo spojte více ovládacích prvků dohromady. Čím více budete cvičit, tím plynulejší budete při dodávání bohatých, interaktivních Word dokumentů z C#. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak programově přidat tlačítko příkazu v dokumentu Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Jak přidat ActiveX tlačítko do Word dokumentu s Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Vytvořit Word dokument s ActiveX tlačítkem – průvodce C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}