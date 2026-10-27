---
category: general
date: 2026-09-05
description: Vytvořte Word dokument pomocí Aspose.Words, nastavte zástupný text, přidejte
  ovládací prvek a uložte dokument jako docx v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: cs
lastmod: 2026-09-05
og_description: Vytvořte dokument Word pomocí Aspose.Words pro .NET, nastavte zástupný
  text, přidejte ovládací prvek a uložte dokument jako docx. Postupujte podle tohoto
  kompletního tutoriálu.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Vytvořte dokument Word s ovládacími prvky obsahu v C# – průvodce krok za
  krokem
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Jak vytvořit dokument Word s obsahovými ovládacími prvky v C#
url: /cs/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit Word dokument s ovládacími prvky obsahu v C#

Pokud potřebujete **vytvořit Word dokument**, který obsahuje strukturované ovládací prvky obsahu, tento průvodce vám ukáže, jak přidat značku prostého textu, **nastavit zástupný text** a **uložit dokument jako docx** pomocí Aspose.Words pro .NET. Příklad je plně spustitelný a demonstruje doporučený přístup k programové tvorbě Word dokumentů.

Dozvíte se, jak:

* Inicializovat prázdný Word soubor pomocí `Document` a `DocumentBuilder`.
* **Jak přidat ovládací prvek** (a `StructuredDocumentTag`) do těla dokumentu.
* **Jak vytvořit značku** s názvem a zástupným textem, který vede koncového uživatele.
* Uložit výsledek pomocí `document.Save`, aby byl soubor platným `.docx`.

Tutoriál předpokládá, že máte základní vývojové prostředí C# a licenci pro Aspose.Words (bezplatná zkušební verze funguje pro výukové účely).

---

## Požadavky

| Požadavek | Důvod |
|-------------|--------|
| .NET 6.0 nebo novější | Poskytuje runtime pro Aspose.Words pro .NET. |
| Aspose.Words pro .NET NuGet balíček | Obsahuje třídy `Document`, `DocumentBuilder` a `StructuredDocumentTag`. |
| IDE jako Visual Studio 2022 | Umožňuje snadné spuštění a ladění ukázky. |

Instalujte balíček pomocí .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Krok 1: Nastavte projekt pro **vytvoření Word dokumentu**

Vytvořte nový konzolový projekt (nebo přidejte kód do existujícího). První řádky vytvoří prázdný Word soubor a `DocumentBuilder`, který vám umožní zapisovat obsah.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` představuje strukturu souboru, zatímco `DocumentBuilder` sleduje bod vkládání. Tento vzor je základem pro jakýkoli scénář generování Word dokumentů.

---

## Krok 2: **Jak přidat ovládací prvek** – vytvořte prostý textový ovládací prvek (značku)

Ovládací prvek ve Wordu se nazývá *structured document tag* (SDT). Následující kód vytvoří prostý textový SDT, přiřadí mu název a definuje zástupný text, který se zobrazí po otevření dokumentu.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Proč je to důležité:**  
* Vlastnost `Title` funguje jako stabilní identifikátor, který vám umožní později ovládací prvek programově najít nebo nahradit.  
* `PlaceholderName` poskytuje vizuální vodítko uživateli dokumentu, aniž by bylo potřeba další UI kód.

![Vytvořte Word dokument s ovládacím prvkem, který zobrazuje zástupný text](image.png)

*Alt text obrázku: Vytvořte Word dokument s ovládacím prvkem, který zobrazuje zástupný text.*

---

## Krok 3: Přesuňte kurzor dovnitř ovládacího prvku a napište výchozí text

Po vložení ovládacího prvku kurzor builderu stále ukazuje mimo něj. Přesuňte kurzor do značky, aby následné zápisy byly součástí obsahu ovládacího prvku.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Pokud chcete ovládací prvek nechat prázdný, vynechte volání `Write`. Zástupný text zůstane viditelný, dokud uživatel nezadá hodnotu.

---

## Krok 4: **Nastavit zástupný text** (alternativní přístup)

Někdy potřebujete změnit zástupný text po vytvoření značky. Můžete přímo upravit vlastnost `PlaceholderName`:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Změna zástupného textu **neovlivní** existující obsah, což umožňuje bezpečně aktualizovat UI nápovědy bez zásahu do uživatelem zadaných dat.

---

## Krok 5: **Uložit dokument jako docx**

Uložte dokument v paměti do fyzického souboru. Metoda `Save` automaticky určí formát podle přípony souboru.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Pokud potřebujete jiný formát (např. PDF nebo HTML), zadejte hodnotu výčtu `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Krok 6: Kompletní, spustitelný příklad

Sestavením všech částí získáte stručný program, který demonstruje **jak vytvořit značku**, nastavit její zástupný text a **uložit dokument jako docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Očekávaný výstup:**  
Spuštěním programu se vytvoří `SdtExample.docx`, který obsahuje jeden odstavec s prostým textovým ovládacím prvkem pojmenovaným *CustomerName*. Ovládací prvek zobrazuje „John Doe“ jako počáteční obsah; pokud je výchozí text odstraněn, zástupný text „Enter name“ se objeví světle šedě, když je soubor otevřen v Microsoft Word.

---

## Běžné varianty a okrajové případy

| Scénář | Doporučené úpravy |
|----------|------------------------|
| **Více ovládacích prvků** | Opakujte kroky 2‑4 pro každé pole a dejte každému unikátní `Title`. |
| **Rich‑text ovládací prvek** | Použijte `SdtType.RichText` místo `PlainText`. |
| **Opakující se sekce** | Vyberte `SdtType.RepeatingSection` a přidejte podřízené ovládací prvky uvnitř sekce. |
| **Existující dokument** | Načtěte existující soubor pomocí `new Document("template.docx")` a vložte ovládací prvky na požadované místo. |
| **Unicode zástupný text** | Nastavte `PlaceholderName` na libovolný Unicode řetězec; Word jej vykreslí správně. |
| **Velké dokumenty** | Po použití uvolněte `DocumentBuilder` (`builder.Dispose();`) pro uvolnění paměti. |

**Pro tip:** Když potřebujete později získat hodnotu zadanou uživatelem, zavolejte `StructuredDocumentTag.GetText()` po uložení a opětovném otevření dokumentu. Tato metoda vrací vnitřní text bez zástupného textu.

**Dejte si pozor:** Použití zástupného textu, který se shoduje s výchozím textem, může způsobit zmatek, protože Word zástupný text skryje, jakmile je v dokumentu jakýkoli text. Udržujte je odlišné.

---

## Závěr

Nyní víte, jak **vytvořit Word dokument** programově, **jak přidat ovládací prvek**, **jak vytvořit značku**, **nastavit zástupný text** a **uložit dokument jako docx** pomocí Aspose.Words pro .NET. Kompletní příklad můžete zkopírovat do libovolného C# projektu a rozšířit o další typy ovládacích prvků, opakující se sekce nebo integraci s datovými zdroji.

Další kroky, které můžete prozkoumat, zahrnují:

* Přidání **obrázkových ovládacích prvků** (`SdtType.Picture`) pro vložení uživatelem poskytnutých grafik.  
* Použití **vazby** k mapování SDT na XML data pro scénáře hromadné korespondence.  
* Převod vygenerovaného DOCX do PDF (`SaveFormat.Pdf`) pro distribuci.

Experimentujte s různými typy značek a zástupnými zprávami, aby odpovídaly workflow vaší aplikace. Šťastné kódování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, která vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Vytvořit Word dokument pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Vytvořit Word dokument s tabulkou pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Vytvořit Word dokument s hlavičkou a patičkou pomocí Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}