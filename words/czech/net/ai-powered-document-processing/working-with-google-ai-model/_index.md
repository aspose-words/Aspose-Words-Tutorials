---
"description": "Zvyšte úroveň zpracování dokumentů s Aspose.Words pro .NET a Google AI, abyste mohli snadno vytvářet stručné souhrny."
"linktitle": "Práce s modelem umělé inteligence Google"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Práce s modelem umělé inteligence Google"
"url": "/cs/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Práce s modelem umělé inteligence Google

## Zavedení

V tomto článku se krok za krokem podíváme na to, jak shrnout dokumenty pomocí Aspose.Words a modelů umělé inteligence od Googlu. Ať už chcete zkrátit dlouhou zprávu nebo extrahovat poznatky z více zdrojů, máme pro vás vše.

## Předpoklady

Než se pustíme do praktické části, ujistěme se, že jste připraveni na úspěch. Zde je to, co budete potřebovat:

1. Základní znalost C# a .NET: Znalost programovacích konceptů vám pomůže lépe pochopit příklady.
   
2. Knihovna Aspose.Words pro .NET: Tato výkonná knihovna vám umožňuje bezproblémově vytvářet a manipulovat s dokumenty Wordu. Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).

3. Klíč API pro model umělé inteligence Google: Pro využití modelů umělé inteligence potřebujete klíč API pro ověřování. Bezpečně jej uložte do proměnných prostředí.

4. Vývojové prostředí: Ujistěte se, že máte nastavené funkční prostředí .NET (Visual Studio nebo jakékoli jiné IDE).

5. Ukázkový dokument: K otestování shrnutí budete potřebovat ukázkové dokumenty aplikace Word (např. „Velký dokument.docx“, „Dokument.docx“).

Teď, když jsme si probrali základy, pojďme se ponořit do kódu!

## Importovat balíčky

Pro práci s Aspose.Words a integraci modelů umělé inteligence Google je nutné importovat potřebné jmenné prostory. Zde je návod, jak to udělat:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Nyní, když máte importované potřebné balíčky, pojďme si krok za krokem rozebrat proces shrnování dokumentů.

## Krok 1: Nastavení adresáře dokumentů

Než budeme moci zpracovávat dokumenty, musíme určit, kde se naše soubory nacházejí. Tento krok je klíčový pro zajištění přístupu aplikace Aspose.Words k dokumentům.

```csharp
// Váš adresář dokumentů
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Váš adresář ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Nahradit `"YOUR_DOCUMENT_DIRECTORY"` a `"YOUR_ARTIFACTS_DIRECTORY"` se skutečnými cestami ve vašem systému, kde jsou vaše dokumenty uloženy. To bude sloužit jako základ pro čtení a ukládání dokumentů.

## Krok 2: Načítání dokumentů

Dále musíme načíst dokumenty, které chceme shrnout. V tomto případě načtete dva dokumenty, které jsme dříve specifikovali.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

Ten/Ta/To `Document` Třída z Aspose.Words umožňuje načítat soubory Wordu do paměti. Ujistěte se, že názvy souborů odpovídají skutečným dokumentům ve vašem adresáři, jinak se setkáte s chybou „soubor nebyl nalezen“!

## Krok 3: Získání klíče API

Abyste mohli využívat model umělé inteligence, budete muset získat klíč API. Ten slouží jako váš přístupový průkaz ke službám umělé inteligence od Googlu.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Tento řádek kódu načte klíč API, který jste uložili do proměnných prostředí. Z bezpečnostních důvodů je dobrým zvykem vyloučit z kódu citlivé informace, jako jsou klíče API.

## Krok 4: Vytvoření instance modelu AI

Nyní je čas vytvořit instanci modelu AI. Zde si můžete vybrat, který model chcete použít – v tomto příkladu volíme model GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Tento řádek nastavuje model umělé inteligence, který budete používat pro sumarizaci dokumentů. Nezapomeňte si přečíst [dokumentace](https://reference.aspose.com/words/net/) pro podrobnosti o různých modelech a jejich možnostech.

## Krok 5: Shrnutí jednoho dokumentu

Zaměřme se na shrnutí prvního dokumentu. Můžeme si zde zvolit krátké shrnutí.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

V tomto kroku použijeme `Summarize` z instance modelu AI pro získání zkrácené verze prvního dokumentu. Délka shrnutí je nastavena na krátkou, ale můžete ji přizpůsobit podle svých potřeb. Nakonec se shrnutý dokument uloží do adresáře s artefakty.

## Krok 6: Shrnutí více dokumentů

Chcete shrnout více dokumentů najednou? Aspose.Words to také usnadňuje!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Zde nazýváme `Summarize` Znovu použijte metodu, ale tentokrát s polem dokumentů. Získáte tak dlouhé shrnutí, které zapouzdřuje podstatu obou souborů. Stejně jako předtím je výsledek uložen do zadaného adresáře s artefakty.

## Závěr

tady to máte! Úspěšně jste nastavili prostředí pro shrnutí dokumentů pomocí Aspose.Words pro .NET a modelů umělé inteligence od Googlu. Od načítání dokumentů až po vytváření stručných shrnutí, tyto kroky poskytují zjednodušený přístup k efektivní správě velkých objemů textu.

## Často kladené otázky

### Co je Aspose.Words?
Aspose.Words je výkonná knihovna pro vytváření, úpravy a převod dokumentů Wordu pomocí .NET.

### Jak získám klíč API pro Google AI?
Klíč API obvykle získáte registrací do služby Google Cloud a povolením potřebných služeb API.

### Mohu shrnout více dokumentů najednou?
Ano! Jak bylo ukázáno, metodě sumarizace můžete předat pole dokumentů.

### Jaké typy souhrnů mohu vytvářet?
Můžete si vybrat mezi krátkým, středním a dlouhým shrnutím podle vašich potřeb.

### Kde najdu další zdroje o Aspose.Words?
Podívejte se na [dokumentace](https://reference.aspose.com/words/net/) pro další příklady a pokyny.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}