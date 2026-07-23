---
category: general
date: 2026-07-23
description: Naučte se, jak přidat Forms2OleControl do DOCX pomocí Aspose.Words. Tento
  krok‑za‑krokem průvodce ukazuje vložení ActiveX ovládacího prvku CommandButton v
  Javě.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add forms2olecontrol to docx
- insert ActiveX control in DOCX
- Aspose.Words Forms2OleControl example
- embed CommandButton in Word document
- Java DocumentBuilder ActiveX
language: cs
lastmod: 2026-07-23
og_description: Přidejte Forms2OleControl do DOCX okamžitě. Postupujte podle tohoto
  praktického návodu, jak vložit ActiveX CommandButton pomocí Aspose.Words pro Javu.
og_image_alt: Screenshot of Java code that adds Forms2OleControl to DOCX using Aspose.Words
og_title: Přidání Forms2OleControl do DOCX – Kompletní tutoriál Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  headline: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to add Forms2OleControl to DOCX using Aspose.Words. This
    step‑by‑step guide shows inserting an ActiveX CommandButton control in Java.
  name: Add Forms2OleControl to DOCX – Complete Aspose.Words Guide
  steps:
  - name: Using a Different ActiveX Control
    text: 'If you want a checkbox instead of a button, just change the control type:'
  - name: Embedding Multiple Controls
    text: Call `builder.insertForms2OleControl()` multiple times, moving the cursor
      with `builder.moveTo()` or inserting text between calls. Each call adds a new
      OLE container, so you can build complex forms inside a single DOCX.
  - name: Working with .NET
    text: The same logic applies to C#—the method names are identical (`DocumentBuilder.InsertForms2OleControl()`).
      If you’re on .NET, replace the Java syntax with its C# counterpart, but the
      **embed CommandButton in Word document** concept stays unchanged.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Java
- DOCX
title: Přidejte Forms2OleControl do DOCX – Kompletní průvodce Aspose.Words
url: /cs/java/using-document-elements/add-forms2olecontrol-to-docx-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidání Forms2OleControl do DOCX – Kompletní průvodce Aspose.Words

Už jste se někdy zamýšleli, jak **add Forms2OleControl to DOCX** bez toho, abyste si trhali vlasy? Nejste v tom sami. Ať už vytváříte report založený na šabloně nebo potřebujete klikací tlačítko uvnitř souboru Word, vložení ActiveX ovládacího prvku je tajná ingredience.

V tomto tutoriálu projdeme konkrétním příkladem, který **adds Forms2OleControl to DOCX** pomocí Aspose.Words pro Java. Uvidíte celý kód, pochopíte, proč je každá řádka důležitá, a získáte tipy, jak zvládnout drobné problémy, které často vývojáře zaskočí.

## Co se naučíte

- Jak nastavit Aspose.Words v Java projektu  
- Přesné kroky k **insert an ActiveX control in DOCX** (ano, hlavní klíčové slovo znovu)  
- Konfigurace vlastností CommandButtonu, aby se choval jako skutečný UI prvek  
- Uložení dokumentu a ověření, že ovládací prvek je skutečně vložen  

Předchozí zkušenost s ActiveX není vyžadována, ale základní znalost Javy a Maven/Gradle vám usnadní práci. Připravení? Ponořme se.

---

## Krok 1: Nastavení Aspose.Words ve vašem projektu

Než budete moci **add Forms2OleControl to DOCX**, potřebujete knihovnu Aspose.Words na classpathu. Nejjednodušší způsob je přes Maven:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

> **Tip:** Pokud používáte Gradle, ekvivalent je `implementation 'com.aspose:aspose-words:24.9'`.  

Proč je to důležité: Aspose.Words poskytuje metodu `DocumentBuilder.insertForms2OleControl()`, na kterou se budeme spoléhat při **insert an ActiveX control in DOCX**. Bez knihovny by kompilátor netušil, co je `Forms2OleControl`.

---

## Krok 2: Přidání Forms2OleControl do DOCX

Nyní přichází jádro tutoriálu – zde skutečně **add Forms2OleControl to DOCX**. Vytvoříme nový dokument, spustíme `DocumentBuilder` a zavoláme metodu pro vložení.

```java
import com.aspose.words.*;

public class ActiveXExample {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2.2: Insert an ActiveX Forms2OleControl (CommandButton)
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Step 2.3: Configure the CommandButton properties
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setName("MyButton");
        commandButton.setCaption("Click Me");

        // Step 2.4: Save the document with the embedded control
        String outPath = "output/ActiveXButton.docx";
        document.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**What’s happening here?**  

- `new Document()` nám dává čisté plátno. Představte si to jako čerstvý list papíru připravený na **insert ActiveX control in DOCX**.  
- `builder.insertForms2OleControl()` vytvoří nízkoúrovňový OLE kontejner, který Aspose.Words nazývá *Forms2OleControl*. Toto je jediná API metoda, která skutečně **adds Forms2OleControl to DOCX**.  
- Nastavením `OleControlType.COMMANDBUTTON` říkáme Wordu, že OLE objekt má fungovat jako klasické CommandButton – přesně jako tlačítko, které byste přetáhli na formulář v UI designeru.  
- Nakonec `document.save(...)` zapíše .docx soubor a uloží vložený ActiveX.

---

## Krok 3: Konfigurace vlastností CommandButtonu (Proč je to důležité)

Pouhé vložení ovládacího prvku vám poskytne prázdné místo. Aby byl užitečný, musíte nastavit několik vlastností:

| Vlastnost | Účel | Typická hodnota |
|----------|------|-----------------|
| `setOleControlType` | Definuje typ ActiveX ovládacího prvku (Button, CheckBox, atd.) | `OleControlType.COMMANDBUTTON` |
| `setName` | Interní identifikátor používaný makry Wordu nebo VBA skripty | `"MyButton"` |
| `setCaption` | Text zobrazený na povrchu tlačítka | `"Click Me"` |

Pokud je vynecháte, tlačítko se zobrazí s generickým názvem a bez popisku – nic, co by uživatel klikl. Také si pamatujte, že ActiveX ovládací prvky jsou **platform‑specific**; fungují jen na Windows strojích s nainstalovanými odpovídajícími COM knihovnami.  

> **Pozor:** Když otevřete vygenerovaný DOCX na ne‑Windows platformě (např. macOS), Word zobrazí místo skutečného tlačítka placeholder obrázek. Jedná se o běžné omezení ActiveX, ne o chybu ve vašem kódu.

---

## Krok 4: Uložení a ověření dokumentu

Volání `document.save(...)` zapíše standardní DOCX soubor, který může otevřít jakákoliv moderní verze Microsoft Word. Po spuštění programu otevřete `ActiveXButton.docx`:

1. Najděte tlačítko “Click Me”, kde jste jej vložili.  
2. Klikněte pravým tlačítkem na tlačítko → **Properties** pro potvrzení názvu a popisku.  
3. Klikněte na tlačítko; Word zobrazí jednoduché dialogové okno, pokud jste připojili makro (mimo rozsah tohoto návodu).  

Pokud tlačítko chybí, zkontrolujte, že jste správně použili **Aspose.Words Forms2OleControl example** a že výstupní složka existuje.  

> **Speciální případ:** Pokud potřebujete, aby tlačítko spouštělo makro, musíte po uložení dokumentu přidat VBA kód. Aspose.Words může vložit VBA pomocí API `Document.getBuiltInDocumentProperties()`, ale to je už samostatný tutoriál.

---

## Běžné varianty a úskalí

### Použití jiného ActiveX ovládacího prvku
Pokud chcete místo tlačítka zaškrtávací políčko, stačí změnit typ ovládacího prvku:

```java
commandButton.setOleControlType(OleControlType.CHECKBOX);
commandButton.setCaption("Accept Terms");
```

### Vkládání více ovládacích prvků
Zavolejte `builder.insertForms2OleControl()` vícekrát, posuňte kurzor pomocí `builder.moveTo()` nebo vložte text mezi voláními. Každé volání přidá nový OLE kontejner, takže můžete vytvořit složité formuláře v jednom DOCX.

### Práce s .NET
Stejná logika platí pro C# – názvy metod jsou identické (`DocumentBuilder.InsertForms2OleControl()`). Pokud pracujete v .NET, nahraďte Java syntaxi její C# ekvivalentou, ale koncept **embed CommandButton in Word document** zůstává stejný.

---

## Závěr

Nyní máte funkční, kompletní příklad, který **adds Forms2OleControl to DOCX** pomocí Aspose.Words pro Java. Vytvořením prázdného dokumentu, vložením ActiveX ovládacího prvku, nastavením jeho vlastností a uložením souboru jste zvládli základní kroky k **insert ActiveX control in DOCX** a můžete tento vzor rozšířit na další typy ovládacích prvků.

Co dál? Zkuste kombinovat tuto techniku s Aspose.Words mail‑merge pro generování personalizovaných formulářů, nebo prozkoumejte přidání VBA maker, aby tlačítko skutečně něco dělalo. Možnosti jsou neomezené, když spojíte kód **Aspose.Words Forms2OleControl example** s vaší vlastní obchodní logikou.

Šťastné programování a neváhejte zanechat komentář, pokud narazíte na potíže!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Přidání záložek do Wordu s Aspose.Words pro Java – Vložení, aktualizace, smazání](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)
- [Jak přidat vodoznak do dokumentů pomocí Aspose.Words pro Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}