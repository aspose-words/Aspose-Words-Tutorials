---
category: general
date: 2026-04-04
description: Zachyťte varování o nahrazení písma při načítání dokumentů Word pomocí
  Aspose.Words pro Java a automaticky detekujte chybějící písma. Postupujte podle
  tohoto krok‑za‑krokem průvodce.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: cs
og_description: Zachyťte upozornění na nahrazení fontů při načítání dokumentů Word
  pomocí Aspose.Words pro Java a zjistěte chybějící fonty během několika jednoduchých
  kroků.
og_title: Zachytit varování o substituci fontů – Detekovat chybějící fonty
tags:
- Aspose.Words
- Java
- Document Processing
title: Zachytit varování o nahrazení písma – Detekovat chybějící písma
url: /cs/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zachycení varování o nahrazení písma – Detekce chybějících písem

Už jste někdy potřebovali **zachytit varování o nahrazení písma** při otevírání souboru Word a zjistili, že chybí klíčové písmo? Nejste v tom sami. V mnoha podnikových pracovních postupech může chybějící písmo proměnit perfektně naformátovanou zprávu v nečitelný chaos a jedinou stopu, kterou dostanete, je tiché varování, které většina vývojářů nikdy nevidí.

Dobré zprávy jsou, že Aspose.Words for Java vám umožňuje zasáhnout do procesu načítání a **detekovat chybějící písma** dříve, než vám způsobí problémy. V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který vypíše každé varování o nahrazení přímo do konzole, takže můžete rozhodnout, zda vložíte správné písmo, nahradíte ho nebo upozorníte uživatele.

Na konci tohoto průvodce budete vědět, jak:

* Nastavit objekt `LoadOptions` s vlastním callbackem pro varování.
* Filtrovat callback tak, aby reagoval jen na události nahrazení písma.
* Načíst libovolný soubor `.docx` a okamžitě zobrazit varování.
* Rozšířit řešení o logování varování, vyvolání výjimek nebo dokonce automatickou instalaci chybějících písem.

Žádná externí dokumentace není potřeba – stačí pár řádků Java a Aspose.Words JAR.

## Požadavky

Než se pustíme dál, ujistěte se, že máte:

* Java 8 nebo novější nainstalovanou (nejlépe poslední LTS verzi).
* Aspose.Words for Java 23.11 nebo novější – můžete si stáhnout Maven artefakt nebo prostý JAR z webu Aspose.
* Dokument Word, který odkazuje na písmo, které nemáte na svém vývojovém počítači (např. „MyFancyFont”).  
* IDE nebo textový editor podle vaší volby – já používám IntelliJ IDEA, ale Eclipse nebo VS Code budou také v pořádku.

Pokud vám některá z položek není známá, zastavte se a nejprve je nainstalujte; zbytek tutoriálu předpokládá, že jsou připravené.

---

## Zachycení varování o nahrazení písma pomocí Aspose.Words

Jádro řešení spočívá v instanci `LoadOptions`. Přiřazením `IWarningCallback` můžeme zachytit každé varování, které knihovna během fáze načítání vyprodukuje.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Proč to funguje:**  
`LoadOptions` říká Aspose.Words, jak má zacházet s načítaným souborem. Rozhraní `IWarningCallback` je háček, který přijímá objekt `WarningInfo` pro *každé* varování. Kontrolou `info.getWarningType()` filtrujeme vše kromě `SUBSTITUTED_FONT`. Vlastnost `description` obsahuje čitelnou zprávu jako „Font 'MyFancyFont' was substituted with 'Arial'“.

### Očekávaný výstup do konzole

Pokud zdrojový dokument odkazuje na písmo, které není nainstalováno, uvidíte něco jako:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Pokud dokument používá pouze písma, která jsou na stroji nainstalována, callback zůstane tichý a zobrazí se pouze poslední řádek „Document loaded successfully.“.

---

## Detekce chybějících písem ve vašem dokumentu

Můžete se ptát, *„Je varování o nahrazení stejné jako chybějící písmo?“* Ve většině případů ano – Aspose.Words nahradí chybějící písmo náhradním a nahlásí to pomocí `SUBSTITUTED_FONT`. Existují však okrajové případy, kdy je písmo nainstalováno, ale konkrétní styl (tučně‑kurzíva, specifické OpenType funkce) není, což vede k jemnému nahrazení.

Aby byl jistý, že jste zachytili každý nedostatek, můžete kombinovat callback varování s kontrolou po načtení:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Tip:** Pokud najdete jakékoli běhy (runs), které stále odkazují na chybějící písmo, můžete je nahradit za běhu:

```java
font.setName("Arial"); // fallback
```

Tím zajistíte konzistentní vizuální výsledek, i když bylo původní varování potlačeno.

---

## Časté úskalí a jak se jim vyhnout

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Zapomenutí nastavit callback** | `LoadOptions` má ve výchozím nastavení nečinný callback, takže varování zmizí. | Vždy před načtením zavolejte `loadOptions.setWarningCallback(...)`. |
| **Použití nesprávného typu varování** | `WarningType.SUBSTITUTED_FONT` je jediný enum, který signalizuje chybějící písma. | Filtrujte přesně na `WarningType.SUBSTITUTED_FONT`; ostatní typy (např. `UNKNOWN_FILE_FORMAT`) nejsou relevantní. |
| **Pevně zakódované cesty k souborům** | Funguje lokálně, ale selže v CI/CD pipelinech. | Použijte relativní cestu nebo předávejte umístění souboru jako argument příkazové řádky. |
| **Ignorování Unicode písem** | Některá chybějící písma jsou problém jen pro určité znaky. | Otestujte dokument, který obsahuje celý znakový set, který očekáváte podporovat. |
| **Spouštění na headless serveru bez konfigurace písem** | Server může postrádat jakékoli náhradní písma, což způsobuje neočekávaná nahrazení. | Nainstalujte na server minimální sadu běžných písem (Arial, Times New Roman). |

---

## Rozšíření řešení

Nyní, když můžete **zachytit varování o nahrazení písma**, můžete chtít:

* **Logovat varování do souboru** – nahradit `System.out.println` loggerem jako SLF4J.
* **Vyvolat výjimku** – užitečné v automatizovaných pipelinech, kde by chybějící písmo mělo selhat sestavení:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Automaticky instalovat chybějící písma** – stáhnout požadovaný TTF/OTF za běhu a přidat jej do Java `GraphicsEnvironment`. Jedná se o pokročilejší scénář, ale naprosto možný.

## Diagram (volitelný)

![Diagram zachycení varování o nahrazení písma ukazující, jak Aspose.Words směruje varování o chybějícím písmu do vlastního callbacku](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Diagram zachycení varování o nahrazení písma ukazující, jak Aspose.Words směruje varování o chybějícím písmu do vlastního callbacku.”

---

## Závěr

Právě jsme si prošli, jak **zachytit varování o nahrazení písma** a **detekovat chybějící písma** při načítání dokumentů Word pomocí Aspose.Words pro Java. Nastavením objektu `LoadOptions` a implementací malého `IWarningCallback` získáte úplnou přehlednost o procesu náhradního písma, což vám umožní logovat, nahrazovat nebo přerušit při chybějících typech písma.

Stručně řečeno: nastavte callback, filtrujte na `SUBSTITUTED_FONT`, načtěte dokument a zpracujte výstup podle potřeb vaší aplikace. Odtud můžete rozšířit na logovací frameworky, CI kontroly nebo dokonce automatické poskytování písem.

Chcete jít dál? Vyzkoušejte:

* **Vkládání písem** přímo do uloženého dokumentu (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` s `FontEmbeddingMode.EMBED_ALL`).
* **Generování PDF** po opravě písem, aby finální výstup vypadal přesně podle očekávání.
* **Prohledání celé složky** dokumentů pro chybějící písma a vytvoření souhrnné zprávy.

To je prozatím vše – šťastné programování a ať se vaše dokumenty vždy zobrazují se správným písmem!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}