---
title: Seznam s odrážkami
linktitle: Seznam s odrážkami
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vytvářet a přizpůsobovat seznamy s odrážkami v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/working-with-markdown/bulleted-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Seznam s odrážkami

## Zavedení

Jste připraveni ponořit se do světa Aspose.Words pro .NET? Dnes si projdeme vytvořením seznamu s odrážkami ve vašich dokumentech aplikace Word. Ať už organizujete nápady, vypisujete položky nebo jen přidáváte do dokumentu trochu struktury, seznamy s odrážkami jsou super praktické. Takže, pojďme začít!

## Předpoklady

Než se vrhneme na zábavu s kódováním, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ho ještě nemáte, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vývojové prostředí AC# jako Visual Studio.
3. Základní znalosti C#: Základní znalost programování v C# vám pomůže pokračovat.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. Je to jako připravit půdu pro hladký chod našeho kódu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Nyní si tento proces rozdělíme na jednoduché, zvládnutelné kroky.

## Krok 1: Vytvořte nový dokument

Dobře, začněme vytvořením nového dokumentu. Tady se bude dít všechna kouzla.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Krok 2: Použijte formát seznamu odrážek

Dále použijeme formát seznamu odrážek. To říká dokumentu, že se chystáme spustit seznam s odrážkami.

```csharp
builder.ListFormat.ApplyBulletDefault();
```

## Krok 3: Přizpůsobte seznam odrážek

Zde si přizpůsobíme seznam odrážek podle našich představ. V tomto příkladu použijeme jako odrážku pomlčku (-).

```csharp
builder.ListFormat.List.ListLevels[0].NumberFormat = "-";
```

## Krok 4: Přidejte položky seznamu

Nyní přidáme některé položky do našeho seznamu s odrážkami. Zde můžete být kreativní a přidat jakýkoli obsah, který potřebujete.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

## Krok 5: Přidejte podpoložky

Aby to bylo zajímavější, přidejte některé podpoložky pod „Položka 2“. To pomáhá při organizaci dílčích bodů.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
builder.ListFormat.ListOutdent(); // Návrat na úroveň hlavního seznamu
```

## Závěr

A tady to máte! Právě jste vytvořili seznam s odrážkami v dokumentu aplikace Word pomocí Aspose.Words for .NET. Je to přímočarý proces, ale neuvěřitelně výkonný pro organizaci vašich dokumentů. Ať už vytváříte jednoduché seznamy nebo složité vnořené seznamy, Aspose.Words vás pokryje.

Nebojte se experimentovat s různými styly a formáty seznamů, aby vyhovovaly vašim potřebám. Šťastné kódování!

## FAQ

### Mohu v seznamu použít různé symboly odrážek?
    Ano, můžete upravit symboly odrážek změnou`NumberFormat` vlastnictví.

### Jak přidám další úrovně odsazení?
    Použijte`ListIndent` způsob přidání dalších úrovní a`ListOutdent` vrátit se na vyšší úroveň.

### Je možné kombinovat seznamy odrážek a čísel?
   Absolutně! Mezi formáty odrážek a čísel můžete přepínat pomocí`ApplyNumberDefault` a`ApplyBulletDefault` metody.

### Mohu upravit styl textu v položkách seznamu?
    Ano, na text v položkách seznamu můžete použít různé styly, fonty a formátování pomocí`Font` vlastnictvím`DocumentBuilder`.

### Jak mohu vytvořit vícesloupcový seznam s odrážkami?
   Formátování tabulky můžete použít k vytvoření vícesloupcových seznamů, kde každá buňka obsahuje samostatný seznam s odrážkami.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
