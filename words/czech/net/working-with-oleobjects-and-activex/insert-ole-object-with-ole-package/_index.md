---
title: Vložit Ole Objekt Do Wordu S Balíčkem Ole
linktitle: Vložit Ole Objekt Do Wordu S Balíčkem Ole
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vkládat objekty OLE do dokumentů aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce krok za krokem pro bezproblémové vkládání souborů.
weight: 10
url: /cs/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit Ole Objekt Do Wordu S Balíčkem Ole

## Zavedení

Pokud jste někdy chtěli vložit soubor do dokumentu aplikace Word, jste na správném místě. Ať už se jedná o soubor ZIP, list aplikace Excel nebo jakýkoli jiný typ souboru, vložení přímo do dokumentu aplikace Word může být neuvěřitelně užitečné. Představte si to, jako byste měli v dokumentu tajnou přihrádku, kam můžete schovat nejrůznější poklady. A dnes si projdeme, jak to udělat pomocí Aspose.Words for .NET. Jste připraveni stát se průvodcem aplikace Word? Pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words for .NET: Pokud jste to ještě neudělali, stáhněte si ji z[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí .NET.
3. Základní porozumění C#: Nemusíte být expert, ale znalost C# vám pomůže.
4. Adresář dokumentů: Složka, do které můžete ukládat a načítat dokumenty.

## Importovat jmenné prostory

Nejprve si udělejme pořádek ve jmenných prostorech. Do projektu musíte zahrnout následující jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Pojďme si to rozdělit do malých kroků, takže je snadné je sledovat.

## Krok 1: Nastavte svůj dokument

Představte si, že jste umělec s prázdným plátnem. Nejprve potřebujeme naše prázdné plátno, což je náš dokument Word. Postup nastavení:

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tento kód inicializuje nový dokument Word a nastaví DocumentBuilder, který použijeme k vložení obsahu do našeho dokumentu.

## Krok 2: Přečtěte si svůj Ole Object

Dále si přečteme soubor, který chcete vložit. Berte to jako vyzvednutí pokladu, který chcete ukrýt ve své tajné přihrádce:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Tento řádek přečte všechny bajty ze souboru ZIP a uloží je do bajtového pole.

## Krok 3: Vložte objekt Ole

Nyní přichází ta kouzelná část. Tento soubor vložíme do dokumentu aplikace Word:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

 Zde vytvoříme paměťový proud z bajtového pole a použijeme`InsertOleObject` způsob, jak jej vložit do dokumentu. Nastavíme také název souboru a zobrazovaný název pro vložený objekt.

## Krok 4: Uložte dokument

Nakonec si uložme naše mistrovské dílo:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Tím se dokument s vloženým souborem uloží do určeného adresáře.

## Závěr

A tady to máte! Úspěšně jste vložili objekt OLE do dokumentu aplikace Word pomocí Aspose.Words for .NET. Je to jako přidat do dokumentu skrytý klenot, který lze kdykoli odhalit. Tato technika může být neuvěřitelně užitečná pro různé aplikace, od technické dokumentace po dynamické zprávy. 

## FAQ

### Mohu pomocí této metody vložit jiné typy souborů?
Ano, můžete vložit různé typy souborů, jako jsou listy aplikace Excel, soubory PDF a obrázky.

### Potřebuji licenci pro Aspose.Words?
 Ano, potřebujete platnou licenci. Můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Jak mohu upravit zobrazovaný název objektu OLE?
 Můžete nastavit`DisplayName` vlastnictvím`OlePackage` jej přizpůsobit.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words podporuje jak .NET Framework, tak .NET Core.

### Mohu upravit vložený objekt OLE v dokumentu aplikace Word?
Ne, objekt OLE nemůžete upravovat přímo v aplikaci Word. Musíte jej otevřít v jeho nativní aplikaci.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
