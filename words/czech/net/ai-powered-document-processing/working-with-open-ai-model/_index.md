---
"description": "Získejte efektivní sumarizaci dokumentů pomocí Aspose.Words pro .NET s výkonnými modely OpenAI. Ponořte se do tohoto komplexního průvodce hned teď."
"linktitle": "Práce s modelem otevřené umělé inteligence"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Práce s modelem otevřené umělé inteligence"
"url": "/cs/net/ai-powered-document-processing/working-with-open-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Práce s modelem otevřené umělé inteligence

## Zavedení

V dnešním digitálním světě je obsah klíčový. Ať už jste student, obchodní profesionál nebo vášnivý spisovatel, schopnost efektivně manipulovat s dokumenty, shrnovat je a generovat je neocenitelná. A právě zde přichází na řadu knihovna Aspose.Words pro .NET, která vám umožní spravovat dokumenty jako profesionál. V tomto komplexním tutoriálu se ponoříme do toho, jak využít Aspose.Words ve spojení s modely OpenAI k efektivnímu shrnování dokumentů. Jste připraveni odemknout svůj potenciál správy dokumentů? Pojďme na to!

## Předpoklady

Než si vyhrneme rukávy a pustíme se do kódu, je třeba mít připraveno několik základních věcí:

### .NET Framework
Ujistěte se, že používáte verzi frameworku .NET, která je kompatibilní s Aspose.Words. Obecně by .NET 5.0 a vyšší měl fungovat perfektně.

### Knihovna Aspose.Words pro .NET
Budete si muset stáhnout a nainstalovat knihovnu Aspose.Words. Můžete si ji stáhnout z [tento odkaz](https://releases.aspose.com/words/net/).

### Klíč API OpenAI
Pro integraci jazykových modelů OpenAI pro sumarizaci dokumentů budete potřebovat klíč API. Získáte ho registrací na platformě OpenAI a jeho načtením z nastavení účtu.

### IDE pro vývoj
Pro vývoj aplikací .NET je ideální mít nainstalované integrované vývojové prostředí (IDE), jako je Visual Studio.

### Základní znalosti programování
Základní znalost jazyka C# a objektově orientovaného programování vám pomůže snáze pochopit dané koncepty.

## Importovat balíčky

Nyní, když máme vše připravené, pojďme importovat naše balíčky. Otevřete projekt Visual Studia a přidejte potřebné knihovny. Zde je návod, jak to udělat:

### Přidat balíček Aspose.Words

Balíček Aspose.Words můžete přidat pomocí Správce balíčků NuGet. Postupujte takto:
- Přejděte do nabídky Nástroje -> Správce balíčků NuGet -> Spravovat balíčky NuGet pro řešení.
- Vyhledejte „Aspose.Words“ a klikněte na tlačítko Instalovat.

### Přidat systémové prostředí

Nezapomeňte zahrnout `System` jmenný prostor pro zpracování proměnných prostředí:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Přidat Aspose.Words

Pak do souboru C# zahrňte jmenný prostor Aspose.Words:
```csharp
using Aspose.Words;
```

### Přidat knihovnu OpenAI

Pokud používáte knihovnu pro propojení s OpenAI (například REST klienta), nezapomeňte ji také zahrnout. Možná ji budete muset přidat přes NuGet stejným způsobem, jako jsme přidali Aspose.Words.

Nyní, když jsme si připravili prostředí a importovali potřebné balíčky, pojďme si krok za krokem rozebrat proces sumarizace dokumentů.

## Krok 1: Definujte adresáře dokumentů

Než začnete pracovat se svými dokumenty, musíte si nastavit adresáře, kde budou vaše dokumenty a artefakty uloženy:

```csharp
// Váš adresář dokumentů
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Váš adresář artefaktů
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
Díky tomu je váš kód lépe spravovatelný, protože v případě potřeby můžete snadno změnit cesty. `MyDir` je místo, kde jsou uloženy vaše vstupní dokumenty, zatímco `ArtifactsDir` je místo, kam budete ukládat vygenerované souhrny.

## Krok 2: Vložte dokumenty

Dále načtete dokumenty, které chcete shrnout. S Aspose.Words je to jednoduché:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Ujistěte se, že názvy vašich dokumentů odpovídají těm, které chcete použít, jinak narazíte na chyby!

## Krok 3: Získejte svůj klíč API

Nyní, když máte načtené dokumenty, je čas načíst klíč OpenAI API. Pro jeho bezpečnost ho načtete z proměnných prostředí:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Je nezbytné bezpečně spravovat klíč API, abyste zabránili přístupu neoprávněných uživatelů.

## Krok 4: Vytvořte instanci modelu OpenAI

připraveným klíčem API můžete nyní vytvořit instanci modelu OpenAI. Pro sumarizaci dokumentů použijeme model Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Tento krok v podstatě připraví mozkovou kapacitu potřebnou k shrnutí vašich dokumentů a poskytne vám přístup k shrnutí řízenému umělou inteligencí.

## Krok 5: Shrnutí jednoho dokumentu

Nejprve si shrňme první dokument. Tady se děje ta zázrak:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
Zde používáme `Summarize` metoda modelu. `SummaryLength.Short` Parametr určuje, že chceme krátké shrnutí – ideální pro rychlý přehled!

## Krok 6: Shrnutí více dokumentů

Máte ambice? Můžete shrnout více dokumentů najednou. Podívejte se, jak je to snadné:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Tato funkce je obzvláště užitečná pro porovnávání více souborů. Možná se připravujete na schůzku a potřebujete stručné poznámky z několika dlouhých zpráv. Toto je váš nový nejlepší přítel!

## Závěr

Shrnutí dokumentů pomocí Aspose.Words pro .NET a OpenAI není jen prospěšná dovednost, je to i velmi posilující. Dodržováním tohoto návodu jste proměnili dlouhé a složité texty ve stručná shrnutí, čímž si ušetříte čas a úsilí. Ať už zajišťujete srozumitelnost pro klienty nebo se připravujete na důležitou prezentaci, nyní máte nástroje, jak to udělat efektivně.

Tak na co ještě čekáte? Pusťte se do svých dokumentů s důvěrou a nechte technologie udělat těžkou práci!

## Často kladené otázky

### Co je Aspose.Words pro .NET?  
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty.

### Potřebuji API klíč pro OpenAI?  
Ano, pro přístup k funkcím sumarizace pomocí jejich modelů musíte mít platný klíč OpenAI API.

### Mohu shrnout více dokumentů najednou?  
Rozhodně! V jednom hovoru můžete shrnout více dokumentů, což je ideální pro rozsáhlé zprávy.

### Jak nainstaluji Aspose.Words?  
Můžete si jej nainstalovat pomocí Správce balíčků NuGet ve Visual Studiu vyhledáním „Aspose.Words“.

### Existuje bezplatná zkušební verze pro Aspose.Words?  
Ano, můžete si zdarma vyzkoušet Aspose.Words prostřednictvím jejich [webové stránky](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}