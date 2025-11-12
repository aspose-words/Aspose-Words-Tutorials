---
date: '2025-11-12'
description: Naučte se krok za krokem, jak pomocí Aspose.Words pro Java vkládat konce
  stránek, tabulátory, nezlomitelné mezery a rozvržení do více sloupců – zvyšte automatizaci
  dokumentů ještě dnes.
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: cs
title: Vložení řídicích znaků pomocí Aspose.Words pro Javu
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vkládání řídicích znaků pomocí Aspose.Words pro Java

## Proč jsou řídicí znaky důležité v dokumentech Java
Když programově generujete faktury, zprávy nebo newslettery, je přesné rozložení textu nevyjednatelné. Řídicí znaky, jako jsou **zalomení stránky**, **tabulátory** a **nedělitelné mezery**, vám umožňují přesně určit, kde se obsah objeví, bez ruční úpravy. V tomto tutoriálu uvidíte, jak spravovat tyto znaky pomocí API Aspose.Words pro Java, aby vaše dokumenty vypadaly profesionálně hned při prvním vytvoření.

**Co v tomto průvodci dosáhnete**
1. Vložit a ověřit návraty vozíku, konce řádků a zalomení stránky.  
2. Přidat mezery, tabulátory a nedělitelné mezery pro zarovnání textu.  
3. Vytvořit více‑sloupcové rozvržení pomocí zalomení sloupce.  
4. Použít osvědčené tipy pro výkon u velkých dokumentů.

## Požadavky
Než začneme, ujistěte se, že máte připraveno následující:

| Požadavek | Detaily |
|-------------|---------|
| **Aspose.Words pro Java** | Verze 25.3 nebo novější (API je zpětně kompatibilní). |
| **JDK** | 8 nebo vyšší. |
| **IDE** | IntelliJ IDEA, Eclipse nebo libovolné Java IDE podle vaší preference. |
| **Nástroj pro sestavení** | Maven **nebo** Gradle pro správu závislostí. |
| **Licence** | Dočasná nebo zakoupená licenční soubor Aspose.Words (`aspose.words.lic`). |

### Kontrolní seznam nastavení prostředí
1. Nainstalujte Maven **nebo** Gradle.  
2. Přidejte závislost Aspose.Words (viz další sekce).  
3. Umístěte licenční soubor na zabezpečené místo a poznamenejte si cestu.

## Přidání Aspose.Words do vašeho projektu

### Maven
Vložte následující úryvek do souboru `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
Přidejte tento řádek do souboru `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Inicializace licence
Po získání licence ji inicializujte na začátku vaší aplikace:

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Poznámka:** Bez licence knihovna běží v režimu hodnocení, který vkládá vodoznaky.

## Implementační průvodce

Probereme dvě hlavní funkce: **zpracování návratu vozíku** a **vkládání různých řídicích znaků**. Každá funkce je rozdělena do číslovaných kroků a před každým blokem kódu je krátký vysvětlující odstavec.

### Funkce 1 – Zpracování návratu vozíku a zalomení stránky
Řídicí znaky jako `ControlChar.CR` (návrat vozíku) a `ControlChar.PAGE_BREAK` definují logický tok dokumentu. Následující příklad ukazuje, jak ověřit, že jsou tyto znaky umístěny správně.

#### Krok za krokem

1. **Vytvořte nový Document a DocumentBuilder**  
   Objekt `Document` je kontejner pro veškerý obsah; `DocumentBuilder` poskytuje plynulé API pro přidávání textu.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Vložte dva jednoduché odstavce**  
   Každé volání `writeln` automaticky přidá zalomení odstavce.

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **Sestavte očekávaný řetězec s řídicími znaky**  
   Použijeme `MessageFormat` k vložení `ControlChar.CR` a `ControlChar.PAGE_BREAK` do očekávaného textu.

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **Ořízněte text dokumentu a znovu ověřte**  
   Oříznutí odstraní koncové mezery a zachová úmyslná zalomení řádků.

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **Výsledek:** Aserce potvrzují, že interní textová reprezentace dokumentu obsahuje přesně ty návraty vozíku a zalomení stránky, které očekáváte.

### Funkce 2 – Vkládání různých řídicích znaků
Nyní se podíváme, jak přímo do dokumentu vložit mezery, tabulátory, konce řádků, zalomení