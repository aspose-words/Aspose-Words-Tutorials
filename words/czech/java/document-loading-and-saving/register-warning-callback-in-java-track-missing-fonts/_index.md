---
category: general
date: 2026-05-30
description: Zaregistrujte varovný callback v Javě pro sledování chybějících fontů
  a přizpůsobení načítání dokumentu pomocí Aspose.Words. Naučte se kompletní krok‑za‑krokem
  řešení.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: cs
og_description: Zaregistrujte varovný callback v Javě pro sledování chybějících fontů
  a přizpůsobení načítání dokumentu. Kompletní průvodce s kódem a vysvětleními.
og_title: Zaregistrovat varovný callback v Javě – Sledovat chybějící fonty
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Zaregistrovat varovný callback v Javě – Sledovat chybějící fonty
url: /cs/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zaregistrovat varovné zpětné volání v Javě – Sledovat chybějící písma

Už jste se někdy zamysleli, jak **sledovat chybějící písma** při načítání Word dokumentu pomocí Aspose.Words pro Java? Možná jste viděli ty tiché nahrazení písem a pomysleli si: „Co se stalo s mým rozvržením?“ Dobrou zprávou je, že nemusíte hádat. **Zaregistrováním varovného zpětného volání** můžete zachytit každou událost nahrazení písma v okamžiku, kdy je dokument načten, a také můžete **přizpůsobit načítání dokumentu**, aby vyhovovalo vašemu pipeline.

> **Co získáte:**  
> • Kompletní Java program používající Aspose.Words  
> • Postupné vysvětlení každého řádku  
> • Tipy pro řešení okrajových případů, jako jsou šifrované soubory nebo velké dávky  
> • Rychlá kontrola, kterou můžete spustit na libovolném souboru `.docx`

## Požadavky

Než se pustíme, ujistěte se, že máte:

- **Java 17** (nebo jakýkoli recentní JDK) nainstalovaný a nastavený `JAVA_HOME`.  
- **Aspose.Words for Java** JAR ve vaší classpath. Nejnovější verzi můžete získat z Maven Central repozitáře:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Vzorek Word dokumentu (`input.docx`), o kterém se domníváte, že obsahuje písma, která nejsou nainstalována na vašem počítači.  
- IDE nebo nástroj pro sestavování z příkazové řádky (Maven/Gradle), se kterým jste obeznámeni.

To je vše. Žádná další písma, žádné další služby – jen čistá Java a Aspose.Words.

## Proč zaregistrovat varovné zpětné volání?

Vnímejte **varovné zpětné volání** jako bezpečnostní kameru pro proces načítání dokumentu. Když Aspose.Words narazí na chybějící glyfu, nevyhodí výjimku; tiše nahradí písmo náhradním. Toto tiché nahrazení může rozbít vaše rozvržení, zejména v PDF nebo fakturách, kde je branding kritický. Zaregistrováním zpětného volání získáte:

1. **Získat informace v reálném čase** – každé varování `FONT_SUBSTITUTION` je doručeno okamžitě.  
2. **Zaznamenat nebo reagovat** – můžete zaznamenat do souboru, vyvolat upozornění nebo dokonce programově nahradit písmo.  
3. **Udržet čistý výstup** – znalost chybějících písem vám umožní opravit zdrojový dokument před publikací.

Stručně řečeno, zpětné volání promění skrytý problém na viditelný, čímž učiní váš pipeline dokumentů mnohem spolehlivějším.

## Krok 1 – Vytvořte `LoadOptions` pro přizpůsobení načítání dokumentu

Prvním krokem je vytvořit instanci `LoadOptions`. Tento objekt je vstupní bránou pro každé ladění během načítání, které můžete potřebovat, od zpracování hesla po naši funkci **zaregistrovat varovné zpětné volání**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Proč nevolat jen `new Document("file.docx")`? Protože bez `LoadOptions` ztratíte možnost zachytit události načítání. `LoadOptions` je jediné místo, kde Aspose.Words umožňuje **přizpůsobit načítání dokumentu**.

## Krok 2 – Zaregistrujte varovné zpětné volání pro sledování chybějících písem

Nyní přichází hvězda představení: **zaregistrujeme varovné zpětné volání**, které implementuje `IWarningCallback`. V metodě `warning` filtrujeme na `WarningType.FONT_SUBSTITUTION` a vypíšeme užitečnou zprávu.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Několik věcí, na které je třeba si dát pozor:

- **Proč `IWarningCallback`?** Je to rozhraní, které Aspose.Words používá pro všechny typy varování, poskytující vám jeden vstupní bod pro mnoho možných problémů.  
- **Filtrování je klíčové** – bez kontroly `if` byste viděli varování o chybějících obrázcích, zastaralých funkcích atd., což by zaplnilo vaše logy.  
- **Bezpečnost vláken** – zpětné volání běží ve stejném vlákně, které načítá dokument, takže můžete bezpečně aktualizovat sdílené struktury, pokud potřebujete později agregovat výsledky.

Tento úryvek **zaregistruje varovné zpětné volání** a od tohoto okamžiku bude každá událost chybějícího písma vytištěna na `stdout`. To je jádro **sledování chybějících písem**.

## Krok 3 – Načtěte dokument pomocí nakonfigurovaných `LoadOptions`

S zpětným voláním na místě konečně načteme soubor. Pokud dokument odkazuje na písmo, které nemáte, zpětné volání se spustí před tím, než je objekt dokumentu plně vytvořen.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Nahraďte `YOUR_DIRECTORY` skutečnou cestou na vašem počítači. Konstruktor `Document` načte soubor, použije případné heslo (pokud jste ho nastavili v `loadOptions`), a spustí varovné zpětné volání pro každé chybějící písmo. Uvidíte výstup jako:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Tento řádek dokazuje, že jste úspěšně **sledovali chybějící písma**.

## Krok 4 – Pokračujte ve zpracování dokumentu (volitelné)

V tomto okamžiku můžete s dokumentem manipulovat, jak chcete – nahradit text, vložit obrázky nebo dokonce programově vyměnit nahrazená písma. Zpětné volání vám již poskytlo seznam problematických písem, takže můžete například vložit náhradní písmo:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Klidně tento blok přeskočte, pokud potřebujete jen **sledovat chybějící písma**. Klíčové je, že nyní máte informace potřebné k informovanému rozhodnutí.

## Krok 5 – Uložte zpracovaný dokument

Nakonec dokument uložte. Můžete přepsat originál, uložit na nové místo nebo exportovat do PDF – vše bez ztráty varovných dat, která jste dříve zachytili.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Spuštění celé třídy vytvoří výstup na konzoli pro každé chybějící písmo a nový soubor s názvem `processed.docx` ve stejném adresáři.

## Kompletní funkční příklad

Níže je kompletní Java třída, kterou můžete zkopírovat a vložit do svého IDE. Obsahuje vše, o čem jsme mluvili, plus malý obalovací `main` metod.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Očekávaný výstup

Když spustíte program na dokumentu, který používá písmo neinstalované ve vašem systému, uvidíte něco jako:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Pokud dokument neobsahuje **žádná chybějící písma**, konzole zůstane tichá až do posledního řádku „Document saved successfully.“ – přesně to, co očekáváte od dobře fungující implementace **zaregistrovat varovné zpětné volání**.

## Profesionální tipy a běžné úskalí

- **Více zpětných volání?** Aspose.Words umožňuje pouze jeden varovný handler. Pokud potřebujete logovat jak do souboru, tak na konzoli, implementujte kompozitní zpětné volání, které přeposílá varování na více cílů.  
- **Velké dávky** – při zpracování stovek souborů zvažte opětovné použití jedné instance `LoadOptions`; vytváření nové pro každý soubor přidává zbytečnou režii.  
- **Šifrované dokumenty** – nastavte heslo v `LoadOptions` před načtením, jinak získáte `IncorrectPasswordException` dříve, než se zpětné volání vůbec spustí.  
- **Výkon** – zpětné volání běží synchronně. Pokud logujete do vzdálené služby, bufferujte zprávy a vyprázdněte je po dokončení načítání, abyste se vyhnuli I/O úzkým hrdlům.  
- **Náhrada písma** – můžete také poskytnout vlastní kolekci `FontSource`, pokud máte proprietární písma, která chcete, aby Aspose.Words zvažoval před návratem k systémovým písmům.

## Závěr

Nyní jste se naučili, jak **zaregistrovat varovné zpětné volání** v Javě, efektivně **sledovat chybějící písma** a **přizpůsobit načítání dokumentu** pomocí Aspose.Words. Řešení je samostatné, běží s jednou metodou `main` a poskytuje okamžitý přehled o jakémkoli nahrazení písma, které by jinak zůstalo nepovšimnuté.

Další kroky? Zkuste rozšířit zpětné volání tak, aby zapisovalo varování do CSV souboru pro auditní účely, nebo jej zkombinujte s dávkovým procesorem, který automaticky vloží chybějící písma. Můžete také prozkoumat další typy varování, jako `IMAGE_SUBSTITUTION` nebo `DEPRECATED_FEATURE` – stejný vzor platí.

Šťastné programování a ať se vaše dokumenty vždy vykreslují přesně tak, jak jste zamýšleli!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")


## Co byste se měli naučit dál?

- [Varovné zpětné volání ve Word dokumentu](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Přizpůsobení barev motivu a písem v Aspose.Words Java: Komplexní průvodce](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Sledování změn ve Word dokumentech pomocí Aspose.Words Java: Kompletní průvodce revizemi dokumentů](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}