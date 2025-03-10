---
title: Práce s modelem AI
linktitle: Práce s modelem AI
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se používat Aspose.Words pro .NET ke shrnutí dokumentů pomocí AI. Snadné kroky pro zlepšení správy dokumentů.
weight: 10
url: /cs/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Práce s modelem AI

## Zavedení

Vítejte v podmanivém světě Aspose.Words pro .NET! Pokud jste někdy chtěli posunout správu dokumentů na další úroveň, jste na správném místě. Představte si, že máte schopnost automaticky sumarizovat velké dokumenty pomocí pouhých několika řádků kódu. Zní to úžasně, že? V této příručce se ponoříme hluboko do používání Aspose.Words ke generování souhrnů dokumentů pomocí výkonných jazykových modelů AI, jako je GPT OpenAI. Ať už jste vývojář, který chce vylepšit své aplikace, nebo technický nadšenec, který se chce naučit něco nového, tento tutoriál vám pomůže.

## Předpoklady

Než si vyhrneme rukávy a pustíme se do kódování, je potřeba mít připraveno několik náležitostí:

1. Nainstalované Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Můžete si ji zdarma stáhnout, pokud ji ještě nemáte.
  
2. .NET Framework: Ujistěte se, že používáte kompatibilní verzi rozhraní .NET Framework pro Aspose.Words. Podporuje jak .NET Framework, tak .NET Core.

3.  Aspose.Words for .NET: Budete si muset stáhnout a nainstalovat Aspose.Words. Můžete si vzít nejnovější verzi[zde](https://releases.aspose.com/words/net/).

4. Klíč API pro modely umělé inteligence: Chcete-li využít sumarizaci umělé inteligence, budete potřebovat přístup k modelu umělé inteligence. Získejte svůj API klíč z platforem jako OpenAI nebo Google.

5. Základní znalost C#: Základní znalost programování v C# je nezbytná k tomu, abyste z tohoto tutoriálu vytěžili maximum.

Máš všechno? Děsivý! Pojďme se vrhnout na zábavnější část – import našich požadovaných balíčků.

## Importujte balíčky

Abychom mohli využít schopnosti Aspose.Words a pracovat s modely AI, začneme importem potřebných balíčků. Jak na to:

### Vytvořit nový projekt

Nejprve spusťte Visual Studio a vytvořte nový projekt aplikace konzoly.

1. Otevřete Visual Studio.
2. Klikněte na „Vytvořit nový projekt“.
3. Vyberte „Console App (.NET Framework)“ nebo „Console App (.NET Core)“ podle vašeho nastavení.
4. Pojmenujte svůj projekt a určete umístění.

### Nainstalujte balíčky Aspose.Words a AI Model Packages

Chcete-li používat Aspose.Words, musíte balíček nainstalovat přes NuGet.

1. Klikněte pravým tlačítkem na svůj projekt v Průzkumníku řešení a vyberte „Spravovat balíčky NuGet“.
2. Vyhledejte „Aspose.Words“ a klikněte na „Instalovat“.
3. Pokud používáte nějaké konkrétní balíčky modelů AI (jako OpenAI), ujistěte se, že jsou také nainstalovány.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
gratuluji! Když jsou balíčky připraveny, pojďme se hlouběji ponořit do naší implementace.

## Krok 1: Nastavte adresáře dokumentů

našem kódu definujeme adresáře, abychom mohli spravovat, kde jsou naše dokumenty uloženy a kam půjde náš výstup. 

```csharp
// Váš adresář dokumentů
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Váš adresář ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Tady, vyměňte`YOUR_DOCUMENT_DIRECTORY` s místem, kde jsou uloženy vaše dokumenty, a`YOUR_ARTIFACTS_DIRECTORY` kam chcete uložit souhrnné soubory.

## Krok 2: Vložte dokumenty

Dále do našeho programu načteme dokumenty, které chceme shrnout. Je to snadné jako facka! Zde je postup:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Upravte názvy souborů podle toho, co jste si uložili. Příklad předpokládá, že máte dva dokumenty s názvem „Big document.docx“ a „Document.docx“.

## Krok 3: Inicializujte model AI

Naším dalším krokem je navázání spojení s modelem AI. Zde vstupuje do hry klíč API, který jste získali dříve.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Ujistěte se, že máte klíč API uložený jako proměnná prostředí. Je to jako udržovat svou tajnou omáčku v bezpečí!

## Krok 4: Vygenerujte souhrn pro první dokument

Nyní vytvoříme shrnutí pro náš první dokument. Nastavíme také parametry pro definování délky souhrnu.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Tento úryvek shrnuje první dokument a uloží výstup do vámi zadaného adresáře artefaktů. Délku souhrnu si klidně změňte podle svého!

## Krok 5: Vygenerujte souhrn pro více dokumentů

Cítíte se dobrodružně? Můžete také shrnout více dokumentů najednou! Postup je následující:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Přesně tak, shrnujete dva dokumenty současně! Mluvte o účinnosti, že?

## Závěr

A tady to máte! Podle tohoto průvodce jste zvládli umění sumarizace dokumentů pomocí Aspose.Words pro .NET a výkonných modelů umělé inteligence. Je to vzrušující funkce, která vám může ušetřit spoustu času, ať už pro osobní použití nebo integraci do profesionálních aplikací. Nyní pokračujte, uvolněte sílu automatizace a sledujte, jak vaše produktivita stoupá!

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, upravovat, převádět a vykreslovat dokumenty aplikace Word programově.

### Jak získám klíč API pro modely AI?
Klíč API můžete získat od poskytovatelů AI, jako je OpenAI nebo Google. Nezapomeňte si vytvořit účet a podle jejich pokynů vygenerujte klíč.

### Mohu použít Aspose.Words pro jiné formáty souborů?
Ano! Aspose.Words podporuje různé formáty souborů, včetně DOCX, RTF a HTML, a poskytuje rozsáhlé možnosti nad rámec textových dokumentů.

### Existuje bezplatná verze Aspose.Words?
Aspose nabízí bezplatnou zkušební verzi, která vám umožní vyzkoušet její funkce. Můžete si jej stáhnout z jejich stránek.

### Kde najdu další zdroje pro Aspose.Words?
 Můžete zkontrolovat dokumentaci[zde](https://reference.aspose.com/words/net/) pro komplexní průvodce a postřehy.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
