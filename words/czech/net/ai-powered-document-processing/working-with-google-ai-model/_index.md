---
title: Práce s modelem Google AI
linktitle: Práce s modelem Google AI
second_title: Aspose.Words API pro zpracování dokumentů
description: Vylepšete své zpracování dokumentů pomocí Aspose.Words pro .NET a Google AI, abyste mohli snadno vytvářet stručné souhrny.
weight: 10
url: /cs/net/ai-powered-document-processing/working-with-google-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Práce s modelem Google AI

## Zavedení

tomto článku prozkoumáme, jak shrnout dokumenty pomocí Aspose.Words a modelů umělé inteligence Google krok za krokem. Ať už chcete zkrátit dlouhou zprávu nebo získat statistiky z více zdrojů, máme pro vás řešení.

## Předpoklady

Než se pustíme do praktické části, ujistíme se, že jste připraveni na úspěch. Zde je to, co budete potřebovat:

1. Základní znalost C# a .NET: Znalost programovacích konceptů vám pomůže lépe pochopit příklady.
   
2.  Aspose.Words for .NET Library: Tato výkonná knihovna vám umožňuje bezproblémově vytvářet a manipulovat s dokumenty Wordu. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).

3. Klíč API pro model Google AI: Chcete-li používat modely AI, potřebujete klíč API pro ověřování. Uložte jej bezpečně do proměnných prostředí.

4. Vývojové prostředí: Ujistěte se, že máte nastavené pracovní prostředí .NET (Visual Studio nebo jakékoli jiné IDE).

5. Vzorový dokument: K otestování shrnutí budete potřebovat vzorové dokumenty aplikace Word (např. „Velký dokument.docx“, „Dokument.docx“).

Nyní, když jsme probrali základy, pojďme se ponořit do kódu!

## Importujte balíčky

Chcete-li pracovat s Aspose.Words a integrovat modely Google AI, musíte importovat potřebné jmenné prostory. Můžete to udělat takto:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Nyní, když máte naimportovány potřebné balíčky, pojďme si rozebrat proces shrnutí dokumentů krok za krokem.

## Krok 1: Nastavení adresáře dokumentů

Než budeme moci zpracovat dokumenty, musíme určit, kde se naše soubory nacházejí. Tento krok je zásadní pro zajištění přístupu Aspose.Words k dokumentům.

```csharp
// Váš adresář dokumentů
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Váš adresář ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

 Nahradit`"YOUR_DOCUMENT_DIRECTORY"` a`"YOUR_ARTIFACTS_DIRECTORY"` se skutečnými cestami ve vašem systému, kde jsou uloženy vaše dokumenty. To bude sloužit jako základ pro čtení a ukládání dokumentů.

## Krok 2: Načtení dokumentů

Dále musíme načíst dokumenty, které chceme shrnout. V tomto případě načtete dva dokumenty, které jsme specifikovali dříve.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

 The`Document` třída z Aspose.Words umožňuje načíst soubory Wordu do paměti. Ujistěte se, že názvy souborů odpovídají skutečným dokumentům ve vašem adresáři, jinak narazíte na chyby nenalezen soubor!

## Krok 3: Načtení klíče API

Chcete-li použít model AI, budete muset získat svůj klíč API. Slouží jako váš přístupový průkaz ke službám Google AI.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Tento řádek kódu načte klíč API, který jste uložili do proměnných prostředí. Z bezpečnostních důvodů je dobré do kódu nevkládat citlivé informace, jako jsou klíče API.

## Krok 4: Vytvoření instance modelu AI

Nyní je čas vytvořit instanci modelu AI. Zde si můžete vybrat, který model chcete použít – v tomto příkladu jsme se rozhodli pro model GPT-4 Mini.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

 Tento řádek nastavuje model AI, který budete používat pro sumarizaci dokumentů. Určitě se poraďte[dokumentaci](https://reference.aspose.com/words/net/) podrobnosti o různých modelech a jejich možnostech.

## Krok 5: Shrnutí jednoho dokumentu

Zaměřme se na shrnutí prvního dokumentu. Zde si můžeme vybrat krátké shrnutí.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

 V tomto kroku použijeme`Summarize`metoda z instance modelu AI k získání kondenzace prvního dokumentu. Délka souhrnu je nastavena na krátkou, ale můžete ji upravit podle svých potřeb. Nakonec se shrnutý dokument uloží do vašeho adresáře artefaktů.

## Krok 6: Shrnutí více dokumentů

Chcete shrnout více dokumentů najednou? Aspose.Words to také usnadňuje!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

 Tady voláme`Summarize` metoda znovu, ale tentokrát s řadou dokumentů. Získáte tak dlouhé shrnutí, které shrnuje podstatu obou souborů. Stejně jako dříve se výsledek uloží do určeného adresáře artefaktů.

## Závěr

A tady to máte! Úspěšně jste nastavili prostředí pro shrnutí dokumentů pomocí Aspose.Words for .NET a modelů AI společnosti Google. Od načítání dokumentů až po vytváření stručných souhrnů, tyto kroky poskytují efektivní přístup k efektivní správě velkých objemů textu.

## FAQ

### Co je Aspose.Words?
Aspose.Words je výkonná knihovna pro vytváření, úpravu a převod dokumentů aplikace Word pomocí .NET.

### Jak získám klíč API pro Google AI?
Klíč API můžete obvykle získat registrací do služby Google Cloud a povolením nezbytných služeb API.

### Mohu shrnout více dokumentů najednou?
Ano! Jak bylo ukázáno, do metody sumarizace můžete předat řadu dokumentů.

### Jaké typy souhrnů mohu vytvořit?
Můžete si vybrat mezi krátkými, středními a dlouhými souhrny podle svých potřeb.

### Kde najdu další zdroje Aspose.Words?
 Podívejte se na[dokumentace](https://reference.aspose.com/words/net/) pro další příklady a návody.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
