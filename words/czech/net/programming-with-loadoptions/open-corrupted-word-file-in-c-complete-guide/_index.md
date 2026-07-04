---
category: general
date: 2026-06-08
description: Otevřete poškozený soubor Word v C# pomocí Aspose.Words. Naučte se nastavit
  režim obnovy a efektivně obnovit poškozený dokument.
draft: false
keywords:
- open corrupted word file
- set recovery mode
- recover corrupted document
- Aspose.Words recovery
- handling damaged docx
language: cs
og_description: Otevřete poškozený soubor Word v C# pomocí Aspose.Words. Tento návod
  ukazuje, jak nastavit režim obnovy a bezpečně obnovit poškozený dokument.
og_title: Otevřít poškozený soubor Word v C# – průvodce krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  headline: Open Corrupted Word File in C# – Complete Guide
  type: TechArticle
- description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  name: Open Corrupted Word File in C# – Complete Guide
  steps:
  - name: '**Create `LoadOptions`** – decide how strict the loader should be.'
    text: '**Create `LoadOptions`** – decide how strict the loader should be.'
  - name: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
    text: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
  - name: '**Load the document** – give the path and the options you just built.'
    text: '**Load the document** – give the path and the options you just built.'
  - name: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
    text: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
  type: HowTo
tags:
- C#
- Aspose.Words
- Document Recovery
title: Otevření poškozeného souboru Word v C# – Kompletní průvodce
url: /cs/net/programming-with-loadoptions/open-corrupted-word-file-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Otevření poškozeného souboru Word v C# – Kompletní průvodce

Už jste někdy potřebovali **otevřít poškozený soubor Word** v .NET projektu a přemýšleli, zda je soubor neodstranitelně poškozen? Nejste první—poškození dokumentů se objevuje častěji, než si myslíte, zejména když soubory putují po nespolehlivých sítích nebo jsou upravovány staršími verzemi Office.  

Dobrá zpráva? S Aspose.Words můžete **set recovery mode** a přesně určit, jak se knihovna má chovat, a můžete dokonce **recover corrupted document** obsah bez psaní vlastního parseru. V tomto tutoriálu projdeme každý krok, od konfigurace možností až po ověření, že soubor byl otevřen správně.

> **Co si odnesete**  
> • Fungující úryvek C# kódu, který otevře libovolný .docx, i poškozený.  
> • Porozumění třem hodnotám `RecoveryMode` a kdy kterou použít.  
> • Tipy pro zpracování výjimek, testování výsledku a volitelné uložení čisté kopie.

## Jak otevřít poškozený soubor Word pomocí Aspose.Words

Níže je obrázek vysoké úrovně celého toku.  
![Diagram znázorňující proces otevírání poškozeného souboru Word](/images/open-corrupted-word-file-flow.png){: .center alt="diagram toku otevírání poškozeného souboru Word"}

1. **Create `LoadOptions`** – rozhodněte, jak přísný má načítání být.  
2. **Pick a `RecoveryMode`** – *Passthrough* pro surové načtení, *Recover* pro automatickou opravu nebo *Throw* pro zachycení problémů co nejdříve.  
3. **Load the document** – zadejte cestu a možnosti, které jste právě vytvořili.  
4. **Validate** – zkontrolujte, že strom dokumentu není prázdný, případně uložte opravenou kopii.

Pojďme se podívat na jednotlivé části.

## Porozumění režimům obnovy

Aspose.Words definuje tři odlišné chování:

| Režim | Co dělá | Kdy jej použít |
|------|--------------|----------------|
| `RecoveryMode.Recover` | Pokouší se opravit strukturální problémy, chybějící části nebo špatně formovaný XML. Toto je **výchozí** nastavení a funguje pro většinu menších poškození. | Chcete opravu na nejlepší úsilí bez ruční intervence. |
| `RecoveryMode.Passthrough` | Načte soubor **přesně** tak, jak existuje, i když obsahuje poškozené části. Neaplikují se žádné automatické opravy. | Potřebujete prozkoumat surový obsah, nebo plánujete později aplikovat vlastní logiku obnovy. |
| `RecoveryMode.Throw` | Okamžitě vyhodí výjimku, pokud je detekován jakýkoli problém. | Dáváte přednost přístupu „fail‑fast“ a chcete poškozené soubory okamžitě odmítnout. |

Výběr správného režimu je podstatou **set recovery mode** správně. Většina vývojářů začíná s `Recover`, ale pokud ladíte odolný soubor, `Passthrough` vám může poskytnout přehled o tom, co se pokazilo.

## Krok za krokem: nastavení režimu obnovy

Níže je první blok kódu, který vložíte do nové konzolové aplikace nebo libovolného C# projektu, který již odkazuje na `Aspose.Words`.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and choose a recovery behavior
LoadOptions loadOptions = new LoadOptions
{
    // Choose the desired recovery behavior:
    //   RecoveryMode.Recover      – attempt to fix the file (default)
    //   RecoveryMode.Passthrough – load the file exactly as it is
    //   RecoveryMode.Throw       – throw an exception if the file is damaged
    RecoveryMode = RecoveryMode.Passthrough   // <-- we are explicitly setting it
};
```

**Proč je to důležité:** Tím, že explicitně přiřadíme `RecoveryMode.Passthrough`, říkáme Aspose.Words **set recovery mode** na ne‑výchozí hodnotu. Tím se eliminuje hádání a záměr je jasný pro budoucí údržbu.

> **Pro tip:** Pokud budete někdy potřebovat přepnout zpět na automatickou opravu, stačí změnit výčtový typ na `RecoveryMode.Recover` a spustit znovu – žádné další změny kódu nejsou potřeba.

## Bezpečné načtení dokumentu

Nyní, když jsou možnosti připravené, dalším krokem je skutečně **open corrupted word file**. Následující úryvek ukazuje proces načítání a obsahuje malou kontrolu sanity.

```csharp
// Step 2: Load the possibly‑corrupted document using the configured options
try
{
    // Replace the path with the location of your damaged DOCX
    Document doc = new Document(@"C:\Temp\Corrupted.docx", loadOptions);

    // Quick validation – make sure the document contains at least one section
    if (doc.Sections.Count == 0)
    {
        Console.WriteLine("The document appears empty after loading. It may be severely corrupted.");
    }
    else
    {
        Console.WriteLine($"Successfully opened the file. Sections found: {doc.Sections.Count}");
    }
}
catch (Exception ex)
{
    // If you used RecoveryMode.Throw, you'll land here for any problem.
    Console.WriteLine($"Failed to open the file: {ex.Message}");
}
```

**Vysvětlení:**  
* Blok `try/catch` nás chrání před režimem `Throw`, ale je také bezpečnostní sítí pro neočekávané I/O chyby.  
* Po načtení kontrolujeme `doc.Sections.Count`. Počet nula je silným indikátorem, že soubor neobnovil žádný smysluplný obsah – ideální pro potvrzení, zda **recover corrupted document** skutečně uspěl.

## Zpracování výjimek a ověřování obnovy

I při `Passthrough` může knihovna stále vyvolat výjimku, pokud je podkladový ZIP balíček nečitelné. Zde je návod, jak rozlišit mezi *recoverable* problémem a *fatal* problémem:

```csharp
catch (CorruptedFileException cfe)
{
    // This exception means the file's internal structure is broken.
    Console.WriteLine("CorruptedFileException caught – the file cannot be read at all.");
}
catch (Exception ex)
{
    // Any other exception (e.g., FileNotFound, UnauthorizedAccess)
    Console.WriteLine($"General error: {ex.GetType().Name} – {ex.Message}");
}
```

Pokud narazíte na `CorruptedFileException`, můžete chtít přejít na jinou strategii obnovy, například:

* Zkusit `RecoveryMode.Recover` místo `Passthrough`.  
* Použít externí nástroj na opravu ZIP před předáním souboru do Aspose.Words.  
* Vyzvat uživatele k nahrání čerstvé kopie.

## Bonus: Uložení opraveného dokumentu

Jakmile máte **recover corrupted document** obsah, často chcete uložit čistou verzi. Následující kód zapíše opravený soubor na nové místo:

```csharp
// Assuming 'doc' was loaded successfully
string outputPath = @"C:\Temp\Repaired.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Repaired document saved to: {outputPath}");
```

Ukládání také slouží jako implicitní ověřovací krok – pokud `doc.Save` vyhodí výjimku, něco stále není v pořádku s interním stromem uzlů.

## Tipy pro scénáře obnovy poškozených dokumentů

| Situace | Doporučená akce |
|-----------|--------------------|
| Malá chyba v XML (např. chybějící uzavírací značka) | Zachovejte `RecoveryMode.Recover`; Aspose.Words automaticky opraví. |
| Úplně poškozený ZIP archiv | Použijte externí opravu ZIP, pak načtěte s `Passthrough`. |
| Smíšený režim (některé části v pořádku, jiné poškozené) | Načtěte s `Passthrough`, prozkoumejte problematické uzly a poté je ručně odstraňte nebo nahraďte. |
| Časté poškození z konkrétního zdroje | Automatizujte předběžnou kontrolu, která spustí `RecoveryMode.Recover` a zaznamená jakékoli `CorruptedFileException`. |

Pamatujte, **set recovery mode** není kouzelná hůlka – pochopení povahy poškození vám pomůže vybrat správnou strategii.

## Kompletní funkční příklad

Sestavením všeho dohromady získáte samostatnou konzolovou aplikaci, kterou můžete vložit do `Program.cs` a spustit okamžitě (po přidání NuGet balíčku Aspose.Words).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace OpenCorruptedWordFileDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure load options – we explicitly set the recovery mode.
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Passthrough // change to Recover if you prefer auto‑fix
            };

            // 2️⃣ Attempt to load the possibly damaged DOCX.
            string sourcePath = @"C:\Temp\Corrupted.docx";
            Document doc = null;

            try
            {
                doc = new Document(sourcePath, loadOptions);
                Console.WriteLine($"File loaded. Sections: {doc.Sections.Count}");
            }
            catch (CorruptedFileException)
            {
                Console.WriteLine("The file is too damaged to be opened even in Passthrough mode.");
                return;
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
                return;
            }

            // 3️⃣ Simple verification – ensure we have at least one paragraph.
            if (doc.GetChildNodes(NodeType.Paragraph, true).Count == 0)
            {
                Console.WriteLine("No paragraphs were recovered – the document may be empty.");
            }
            else
            {
                Console.WriteLine("Paragraphs recovered – the document appears usable.");
            }

            // 4️⃣ Optionally save a clean copy.
            string cleanPath = @"C:\Temp\Repaired.docx";
            doc.Save(cleanPath, SaveFormat.Docx);
            Console.WriteLine($"Clean copy saved to: {cleanPath}");
        }
    }
}
```

**Očekávaný výstup (když lze soubor otevřít):**



## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich vlastních projektech.

- [jak obnovit docx – nastavit režim obnovy a otevřít poškozené soubory Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Obnovení poškozeného souboru Word – Kompletní průvodce otevřením poškozeného DOCX a získáním stránky](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)
- [Obnovení dokumentu Word pomocí Aspose.Words v C#](/words/english/net/programming-with-loadoptions/recover-word-document-with-aspose-words-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}