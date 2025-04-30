---
"description": "Naučte se, jak používat Aspose.Words pro .NET k shrnování dokumentů pomocí umělé inteligence. Snadné kroky pro vylepšení správy dokumentů."
"linktitle": "Práce s modelem umělé inteligence"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Práce s modelem umělé inteligence"
"url": "/cs/net/ai-powered-document-processing/working-with-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Práce s modelem umělé inteligence

## Zavedení

Vítejte v podmanivém světě Aspose.Words pro .NET! Pokud jste si někdy přáli posunout správu dokumentů na další úroveň, jste na správném místě. Představte si, že máte možnost automaticky shrnovat velké dokumenty pomocí několika řádků kódu. Zní to úžasně, že? V této příručce se ponoříme do hloubky používání Aspose.Words ke generování shrnutí dokumentů pomocí výkonných jazykových modelů umělé inteligence, jako je GPT od OpenAI. Ať už jste vývojář, který chce vylepšit své aplikace, nebo technologický nadšenec, který se chce naučit něco nového, tento tutoriál vás bude bavit.

## Předpoklady

Než si vyhrneme rukávy a pustíme se do programování, je třeba mít připraveno několik základních věcí:

1. Nainstalované Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Pokud ho ještě nemáte, můžete si ho zdarma stáhnout.
  
2. .NET Framework: Ujistěte se, že používáte kompatibilní verzi .NET Frameworku pro Aspose.Words. Podporuje .NET Framework i .NET Core.

3. Aspose.Words pro .NET: Budete si muset stáhnout a nainstalovat Aspose.Words. Nejnovější verzi si můžete stáhnout [zde](https://releases.aspose.com/words/net/).

4. Klíč API pro modely umělé inteligence: Abyste mohli využívat sumarizaci umělé inteligence, budete potřebovat přístup k modelu umělé inteligence. Získejte klíč API z platforem, jako je OpenAI nebo Google.

5. Základní znalost C#: Pro co nejlepší využití tohoto tutoriálu je nezbytná základní znalost programování v C#.

Máte všechno? Paráda! Pojďme se pustit do té zábavné části – importu požadovaných balíčků.

## Importovat balíčky

Abychom mohli využít sílu Aspose.Words a pracovat s modely umělé inteligence, začneme importem potřebných balíčků. Zde je návod, jak to udělat:

### Vytvořit nový projekt

Nejprve spusťte Visual Studio a vytvořte nový projekt konzolové aplikace.

1. Otevřete Visual Studio.
2. Klikněte na „Vytvořit nový projekt“.
3. V závislosti na nastavení vyberte možnost „Konzolová aplikace (.NET Framework)“ nebo „Konzolová aplikace (.NET Core)“.
4. Pojmenujte svůj projekt a uveďte jeho umístění.

### Instalace balíčků Aspose.Words a AI Model

Chcete-li používat Aspose.Words, musíte si balíček nainstalovat přes NuGet.

1. V Průzkumníku řešení klikněte pravým tlačítkem myši na svůj projekt a vyberte možnost „Spravovat balíčky NuGet“.
2. Vyhledejte „Aspose.Words“ a klikněte na „Instalovat“.
3. Pokud používáte nějaké specifické balíčky modelů umělé inteligence (například OpenAI), ujistěte se, že jsou také nainstalovány.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Gratulujeme! S připravenými balíčky se pojďme hlouběji ponořit do naší implementace.

## Krok 1: Nastavení adresářů dokumentů

V našem kódu definujeme adresáře pro správu toho, kam se naše dokumenty ukládají a kam se bude ukládat náš výstup. 

```csharp
// Váš adresář dokumentů
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Váš adresář ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

- Zde nahraďte `YOUR_DOCUMENT_DIRECTORY` s místem, kde jsou vaše dokumenty uloženy, a `YOUR_ARTIFACTS_DIRECTORY` kam chcete uložit shrnuté soubory.

## Krok 2: Vložení dokumentů

Dále načteme do našeho programu dokumenty, které chceme shrnout. Je to hračka! Postupujte takto:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Upravte názvy souborů podle uložených názvů. Příklad předpokládá, že máte dva dokumenty s názvem „Velký dokument.docx“ a „Dokument.docx“.

## Krok 3: Inicializace modelu umělé inteligence

Naším dalším krokem je navázání spojení s modelem umělé inteligence. Zde se uplatní klíč API, který jste získali dříve.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Ujistěte se, že máte klíč API uložený jako proměnnou prostředí. Je to jako chránit svou tajnou přísadu!

## Krok 4: Vytvořte souhrn pro první dokument

Nyní si vytvořme shrnutí pro náš první dokument. Nastavíme také parametry pro definování délky shrnutí.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Tento úryvek shrnuje první dokument a ukládá výstup do vámi zadaného adresáře s artefakty. Délku shrnutí si můžete libovolně upravit!

## Krok 5: Vygenerování souhrnu pro více dokumentů

Máte chuť na dobrodružství? Můžete také shrnout více dokumentů najednou! Zde je návod, jak to udělat:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Prostě takhle shrnujete dva dokumenty současně! To je ale efektivita, že?

## Závěr

A tady to máte! Dodržováním tohoto návodu jste zvládli umění shrnování dokumentů pomocí Aspose.Words pro .NET a výkonných modelů umělé inteligence. Je to skvělá funkce, která vám může ušetřit spoustu času, ať už pro osobní použití nebo pro integraci do profesionálních aplikací. A teď se do toho pusťte, uvolněte sílu automatizace a sledujte, jak vaše produktivita prudce stoupá!

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat, převádět a vykreslovat dokumenty Wordu.

### Jak získám API klíč pro modely umělé inteligence?
Klíč API můžete získat od poskytovatelů umělé inteligence, jako je OpenAI nebo Google. Nezapomeňte si vytvořit účet a postupovat podle jejich pokynů k vygenerování klíče.

### Mohu použít Aspose.Words pro jiné formáty souborů?
Ano! Aspose.Words podporuje různé formáty souborů, včetně DOCX, RTF a HTML, a poskytuje tak rozsáhlé možnosti nad rámec pouhých textových dokumentů.

### Existuje bezplatná verze Aspose.Words?
Aspose nabízí bezplatnou zkušební verzi, která vám umožní otestovat jeho funkce. Můžete si ji stáhnout z jejich webových stránek.

### Kde najdu další zdroje pro Aspose.Words?
Můžete si prohlédnout dokumentaci [zde](https://reference.aspose.com/words/net/) pro komplexní průvodce a informace.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}