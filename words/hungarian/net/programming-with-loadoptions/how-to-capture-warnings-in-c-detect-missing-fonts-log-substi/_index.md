---
category: general
date: 2026-04-04
description: Tanulja meg, hogyan rögzítse a figyelmeztetéseket, észlelje a hiányzó
  betűtípusokat, valamint hogyan naplózza a helyettesítési eseményeket az Aspose.Words
  LoadOptions használatával C#‑ban.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: hu
og_description: Hogyan rögzítsünk figyelmeztetéseket, észleljük a hiányzó betűtípusokat,
  valamint hogyan naplózzuk a helyettesítési eseményeket az Aspose.Words LoadOptions
  használatával C#-ban.
og_title: Hogyan rögzítsünk figyelmeztetéseket C#-ban – Hiányzó betűtípusok észlelése
  és helyettesítés naplózása
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Hogyan rögzítsünk figyelmeztetéseket C#-ban – Hiányzó betűtípusok észlelése
  és a helyettesítés naplózása
url: /hu/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan rögzítsünk figyelmeztetéseket C#‑ban – Hiányzó betűtípusok észlelése és helyettesítések naplózása

Gondolkodtál már azon, **hogyan rögzítsd a figyelmeztetéseket**, amelyek akkor jelennek meg, amikor hiányzó betűtípusokkal rendelkező Word‑dokumentumot töltesz be? Nem vagy egyedül. Sok valós projektben a betűtípusok elvesznek a migráció során, és a csendes helyettesítés tönkreteheti a megjelenést. A jó hír? Az Aspose.Words tiszta módot biztosít arra, hogy hallgass ezekre a figyelmeztetésekre, észleld a hiányzó betűtípusokat, és még minden helyettesítést naplózz, hogy később javíthasd a forrást.

Ebben az útmutatóban egy teljes, azonnal futtatható megoldáson keresztül mutatjuk be, **hogyan rögzítsd a figyelmeztetéseket**, **hiányzó betűtípusok észlelését**, és **hogyan naplózd a helyettesítési** eseményeket. A végére egy újrahasználható figyelmeztetési kezelővel, teljesen konfigurált `LoadOptions` objektummal és egy minta konzolkimenettel fogsz rendelkezni, amelyet ellenőrizhetsz.

> **Előfeltétel:** Szükséged van az Aspose.Words for .NET (v24.x vagy újabb) telepítésére a NuGet‑en keresztül, valamint egy alap C# fejlesztői környezetre (Visual Studio 2022 vagy VS Code megfelelő).

---

## Figyelmeztetések rögzítése dokumentumok betöltésekor

A megoldás központja egy olyan osztály, amely megvalósítja a `IWarningCallback` interfészt. Az Aspose.Words automatikusan meghívja ezt a visszahívást minden, a dokumentum betöltése során keletkező figyelmeztetéshez, beleértve a betűtípus‑helyettesítési figyelmeztetéseket.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Miért ez a lépés?**  
> A `WarningType.FontSubstitution` szűrésével elkerülhetjük a nem releváns figyelmeztetések (például elavult funkciók) által okozott zsúfoltságot. Így a napló pontosan arra a problémára fókuszál, amely érdekel – a hiányzó betűtípusokra.

---

## Hiányzó betűtípusok észlelése az Aspose.Words‑szal

Amikor egy dokumentum olyan betűtípust hivatkozik, amely nincs telepítve a gépen, az Aspose.Words a legközelebbi egyezést helyettesíti, és figyelmeztetést generál. A fenti kezelő minden előfordulást elkap, így **hiányzó betűtípusokat észlel**.

A működés megtekintéséhez konfigurálnunk kell a `LoadOptions`‑t, és csatolni a kezelőt:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tipp:** Ha a figyelmeztetéseket későbbi feldolgozásra szeretnéd gyűjteni (például fájlba írásra), cseréld le a `Console.WriteLine`‑t olyan kóddal, amely a üzenetet egy `List<string>`‑hez adja.

---

## Hogyan naplózzuk a helyettesítési eseményeket

A naplózás olyan egyszerű, mint a figyelmeztetési kimenet átirányítása egy tartós tárolóba. Az alábbi gyors példa minden helyettesítési figyelmeztetést egy `font-warnings.log` nevű szövegfájlba ír.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Miért fájlba naplózzuk?**  
> A tartós naplók lehetővé teszik a betűtípus‑problémák auditálását több futtatás során, automatizált riasztások létrehozását, vagy az adatok beillesztését egy build‑pipeline ellenőrzésbe.

---

## Teljes működő példa

Mindent összevonva, itt egy önálló konzolalkalmazás, amelyet egyszerűen másolhatsz, beilleszthetsz és futtathatsz. Bemutatja, **hogyan rögzítsd a figyelmeztetéseket**, **hiányzó betűtípusok észlelését**, és **hogyan naplózd a helyettesítéseket** egy lépésben.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Várt konzolkimenet

Ha az `input.docx` olyan betűtípust hivatkozik, amely nincs telepítve, a következőhöz hasonló üzenetet látsz majd:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Ha a `FileLoggingWarningHandler`‑re váltasz, ugyanezek a sorok a `font-warnings.log`‑ban fognak megjelenni időbélyeggel együtt.

![how to capture warnings console output](image-placeholder.png)

---

## Gyakori kérdések és széljegyek

### Mi van, ha *minden* figyelmeztetést szeretnék rögzíteni, nem csak a betűtípus helyettesítést?

Egyszerűen távolítsd el a `if (info.Type == WarningType.FontSubstitution)` ellenőrzést. A visszahívás minden figyelmeztetést megkap (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, stb.). Ezután a `info.Type` alapján különböző eseteket kezelhetsz.

### Működik ez PDF‑ekkel vagy csak Word‑dokumentumokkal?

A `LoadOptions` és az `IWarningCallback` az Aspose.Words részei, így csak a Word‑kompatibilis formátumokra (`.docx`, `.doc`, `.rtf`, `.html`) vonatkoznak. PDF‑ekhez az Aspose.PDF saját figyelmeztetési mechanizmusait kell használni.

### Hogyan lehet elnyomni a figyelmeztetéseket a naplózás helyett?

Állítsd be a `LoadOptions.WarningCallback = null` értéket, vagy valósítsd meg a visszahívást, de hagyd a metódus törzsét üresen. A könyvtár továbbra is csendben végzi a helyettesítést.

### Mi a helyzet a szálbiztonsággal?

A visszahívási példány ugyanazon a szálon fut, amely a dokumentumot betölti, így extra szinkronizációra általában nincs szükség, hacsak nem osztod meg a kezelőt párhuzamos betöltések között. Ilyen esetben a megosztott erőforrásokat (például a naplófájlt) zárj le, vagy használj párhuzamos gyűjteményeket.

---

## Összegzés

Áttekintettük, **hogyan rögzítsük a figyelmeztetéseket** az Aspose.Words‑ból, megmutattuk, **hogyan észleljük a hiányzó betűtípusokat**, és elmagyaráztuk, **hogyan naplózzuk a helyettesítéseket** későbbi elemzés céljából. Egy egyszerű `IWarningCallback` implementáció `LoadOptions`‑ba illesztésével teljes átláthatóságot kapsz a betűtípus‑problémákra anélkül, hogy a kódbázisod zsúfolttá válna.

Mi legyen a következő lépés? Próbáld meg kibővíteni a naplózót, hogy e‑mailt küldjön, integrálja az Azure Monitor‑ba, vagy automatikusan telepítse a hiányzó betűtípusokat egy build‑szerveren. Érdemes tovább kutatni a többi figyelmeztetéstípust is – a `WarningType.DegradedDocument` például figyelmeztethet arra, hogy egyes funkciók nem maradtak meg a konverzió során.

További kérdéseid vannak a betűtípus‑kezeléssel vagy az Aspose.Words‑szal kapcsolatban? Hagyj egy megjegyzést, vagy nyiss új témát az Aspose fórumain. Boldog kódolást, és legyenek a dokumentumaid mindig a megfelelő betűtípussal renderelve!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}