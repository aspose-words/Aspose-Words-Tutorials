---
category: general
date: 2026-10-07
description: Naučte se, jak přidat ovládací prvek obsahu do dokumentu Word pomocí
  Aspose.Words. Tento průvodce také vysvětluje, jak vytvořit ovládací prvek obsahu
  pro pole s identifikátorem zaměstnance.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: cs
lastmod: 2026-10-07
og_description: Přidejte obsahový ovládací prvek do dokumentu Word pomocí Aspose.Words.
  Sledujte tento kompletní tutoriál a naučte se, jak vytvořit obsahový ovládací prvek
  a přidat pole s ID zaměstnance.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Přidejte obsahový ovládací prvek do Wordu pomocí Aspose.Words – krok za
  krokem
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Jak přidat obsahový ovládací prvek do dokumentu Word pomocí Aspose.Words
url: /cs/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat obsahový ovládací prvek do dokumentu Word pomocí Aspose.Words

Pokud potřebujete **přidat obsahový ovládací prvek** do souboru Word, tento tutoriál vám přesně ukáže, jak to provést pomocí knihovny Aspose.Words pro .NET. Ať už vytváříte dokument podobný formuláři nebo automatizujete zadávání dat, naučíte se **jak vytvořit obsahový ovládací prvek**, který zachytí ID zaměstnance v jediném kroku.

V tomto průvodci se dozvíte:

* Programově vytvořit prázdný dokument Word.  
* Vložit prostý textový Structured Document Tag (SDT), který funguje jako obsahový ovládací prvek.  
* Naplnit ovládací prvek ID zaměstnance a soubor uložit.  

Jediné předpoklady jsou aktuální verze .NET (doporučeno 4.6+) a licence Aspose.Words (nebo bezplatná zkušební verze). Žádné další NuGet balíčky nejsou potřeba kromě `Aspose.Words`.

## Přidání obsahového ovládacího prvku pomocí Aspose.Words

Prvním hlavním krokem je vytvořit samotný obsahový ovládací prvek. V Aspose.Words je **obsahový ovládací prvek** reprezentován třídou `StructuredDocumentTag`. Přidáním SDT do dokumentu v podstatě **přidáte obsahový ovládací prvek**, který lze později upravovat v Microsoft Word nebo zpracovávat programově.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité*: `DocumentBuilder` poskytuje rozhraní podobné kurzoru, které vám umožňuje vkládat uzly (odstavce, tabulky, SDT atd.) na aktuální pozici. Začátek s čistým dokumentem zajišťuje, že se obsahový ovládací prvek objeví přesně tam, kde chcete.

## Jak vytvořit obsahový ovládací prvek pro pole ID zaměstnance

Dále nakonfigurujte SDT tak, aby fungoval jako prostý textový obsahový ovládací prvek, který bude uchovávat identifikátor zaměstnance. Vlastnost `Title` je to, co Word zobrazuje v panelu **Properties**, zatímco `PlaceholderName` poskytuje uživateli nápovědu.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Proč je to důležité*: Nastavení `Title` na **EmployeeID** dělá ovládací prvek samodeskriptivní, což je užitečné, když později získáváte hodnoty pomocí `StructuredDocumentTag.GetText()`. Zástupný text zlepšuje uživatelský zážitek tím, že naznačuje očekávaný formát.

### Přidání pole ID zaměstnance do obsahového ovládacího prvku

Nyní vložte SDT do dokumentu na aktuální pozici builderu a zapište výchozí číslo zaměstnance.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Proč je to důležité*: `InsertNode` umístí SDT do stromu dokumentu. Následující `Writeln` zapisuje obsah **uvnitř** ovládacího prvku, protože kurzor builderu je stále uvnitř uzlu SDT. Kdybyste volali `Writeln` před vložením SDT, text by se objevil mimo ovládací prvek.

## Uložení dokumentu a ověření obsahového ovládacího prvku

Nakonec dokument uložte na disk. Uložený soubor `.docx` bude obsahovat obsahový ovládací prvek, který můžete otevřít v Microsoft Word a zobrazit zástupný text i výchozí ID zaměstnance.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Proč je to důležité*: Použití absolutní nebo relativní cesty vám umožňuje kontrolovat, kam se soubor uloží. Aspose.Words automaticky zapíše potřebné XML části pro obsahový ovládací prvek, takže nejsou potřeba žádné další kroky.

### Rychlé ověřovací kroky

1. Otevřete `EmployeeForm.docx` ve Wordu.  
2. Klikněte na šedé pole s textem **Enter ID** – mělo by být nahrazeno **12345**.  
3. Otevřete kartu **Developer** → **Design Mode** a podívejte se na vlastnosti ovládacího prvku (Title = *EmployeeID*).

Pokud se ovládací prvek nezobrazí, zkontrolujte, že používáte Aspose.Words ≥ 23.10; starší verze měly odlišný konstruktor pro `StructuredDocumentTag`.

## Volitelné varianty a okrajové případy

| Scénář | Jak upravit kód |
|----------|-----------------------|
| **Použít ovládací prvek bohatého textu** místo prostého textu | Změňte `SdtType.PlainText` na `SdtType.RichText`. |
| **Přidat ovládací prvek do existujícího dokumentu** | Načtěte soubor pomocí `new Document("Existing.docx")` a umístěte builder na požadovanou záložku před vložením SDT. |
| **Uzamknout obsahový ovládací prvek, aby uživatelé nemohli hodnotu upravovat** | Nastavte `sdt.LockContentControl = true;` po vytvoření SDT. |
| **Použít vlastní značku pro pozdější extrakci** | Použijte `sdt.Tag = "EmpIdTag";` a později ji načtěte pomocí `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Nastavit opakující se obsahový ovládací prvek (více ID)** | Vytvořte SDT uvnitř řádku tabulky a řádek podle potřeby duplikujte. |

**Pro tip**: Vždy uvolněte objekt `Document` (nebo jej zabalte do `using` bloku), když pracujete v dlouho běžící službě, aby se nativní zdroje rychle uvolnily.

## Závěr

Nyní víte, jak **přidat obsahový ovládací prvek** do dokumentu Word pomocí Aspose.Words, jak **vytvořit obsahový ovládací prvek**, který zachytí identifikátor zaměstnance, a jak **programově přidat pole ID zaměstnance**. Dodržením výše uvedených kroků můžete do libovolného generovaného dokumentu vložit strukturovaná, editovatelná pole, což usnadní sběr nebo zobrazení dat v jednotném formátu.

Dále prozkoumejte související témata, jako je **vazba obsahových ovládacích prvků na XML data**, **vytváření opakujících se obsahových ovládacích prvků pro tabulky** nebo **použití Aspose.Words API k extrakci hodnot z vyplněných ovládacích prvků**. Tyto rozšíření vám umožní postavit plnohodnotné, datově řízené formuláře Word bez nutnosti ručního otevírání souboru. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní přístupy ve vašich projektech.

- [Přidání obsahu pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)
- [Přidání rozbalovacího seznamu (Combo Box) do formulářového pole v dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Přidání zaškrtávacího políčka (Check Box) do formulářového pole v dokumentu Word s Aspose.Words pro .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}