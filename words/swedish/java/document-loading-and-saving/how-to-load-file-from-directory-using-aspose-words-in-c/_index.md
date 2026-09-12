---
category: general
date: 2026-09-11
description: Ladda fil från katalog med Aspose.Words med standardläsalternativ och
  lär dig hur du ställer in dokumentkodning eller anpassar läsalternativ i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: sv
lastmod: 2026-09-11
og_description: Läs in fil från katalog med Aspose.Words med standardalternativ för
  inläsning, ange dokumentkodning och anpassa inläsningsalternativ för vilket Word‑dokument
  som helst.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Ladda fil från katalog med Aspose.Words – komplett C#‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Hur man laddar en fil från en katalog med Aspose.Words i C#
url: /sv/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Så laddar du en fil från katalog med Aspose.Words i C#

Om du behöver **ladda en fil från katalog** i ett Word‑bearbetningsflöde, gör Aspose.Words det enkelt. Denna guide visar hur du använder **standard‑laddningsalternativ**, **ange dokumentkodning**, och **ange laddningsalternativ** för att passa ditt specifika scenario.

Dokumentladdning ställer ofta till problem för utvecklare när källfilen ligger i en anpassad mapp eller använder en icke‑UTF‑8‑kodning. I slutet av den här handledningen kommer du att kunna ladda vilken `.docx`‑fil som helst från vilken katalog som helst, kontrollera dess kodning och justera laddningsbeteendet utan att skriva extra infrastruktur‑kod.

## Vad du kommer att uppnå

- Ladda ett Word‑dokument från en godtycklig katalog med en enda kodrad.  
- Förstå vad **standard‑laddningsalternativen** erbjuder och när du behöver ändra dem.  
- Använd **ange dokumentkodning** för att korrekt tolka äldre teckenuppsättningar som Big5.  
- Anpassa **ange laddningsalternativ** för att finjustera minnesanvändning, lösenordshantering och mer.  

### Förutsättningar

- .NET 6.0 eller senare (exemplet riktar sig mot .NET 6, men någon recent .NET‑version fungerar).  
- Aspose.Words för .NET 23.9 eller nyare – lägg till NuGet‑paketet `Aspose.Words`.  
- Grundläggande kunskap om C# samt Visual Studio eller din föredragna IDE.

---

## Så laddar du en fil från katalog med Aspose.Words

Kärnan i operationen är en enda `Document`‑konstruktor som accepterar en filsökväg och ett valfritt `LoadOptions`‑objekt. När du utelämnar `LoadOptions` använder Aspose.Words automatiskt **standard‑laddningsalternativen**, vilka är tillräckliga för de flesta moderna dokument.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Varför detta fungerar:**  
- `Document`‑konstruktorn läser filen som finns på `filePath`.  
- Att skicka `new LoadOptions()` talar om för Aspose.Words att använda **standard‑laddningsalternativen**, som automatiskt upptäcker filformatet, väljer en lämplig kodning och tillämpar standard‑säkerhetskontroller.  

När programmet körs skrivs sidantalet ut, vilket bekräftar att **ladda fil från katalog**‑operationen lyckades.

---

## Använda standard‑laddningsalternativ

Även om du kan hoppa över `LoadOptions`‑argumentet helt, klargör ett explicit skapande av ett `LoadOptions`‑objekt avsikten och förbereder dig för senare anpassningar.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Viktiga punkter om standard‑laddningsalternativen**

| Funktion | Standardbeteende |
|----------|-------------------|
| **Formatdetektion** | Upptäcker automatiskt DOC, DOCX, ODT, RTF, HTML och många andra format. |
| **Kodning** | Upptäcker UTF‑8, UTF‑16 och vanliga äldre kodningar; faller tillbaka till UTF‑8. |
| **Lösenordshantering** | Kastar `IncorrectPasswordException` om filen är lösenordsskyddad. |
| **Minnesanvändning** | Laddar hela dokumentet i minnet, vilket är optimalt för filer under 100 MB. |

Om ditt dokument är kodat i en äldre teckenuppsättning (t.ex. Big5) och auto‑detektionen misslyckas, måste du manuellt **ange dokumentkodning**.

---

## Ange dokumentkodning

När en fil innehåller teckensnitt eller text kodad med en äldre kodsida kan du tala om för Aspose.Words vilken kodning som ska användas via egenskapen `LoadOptions.Encoding`. Detta är det vanliga sättet att **ange dokumentkodning** för filer som standarddetektorn inte kan lösa.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Varför du behöver detta:**  
- Utan att explicit ange `Encoding` kan Aspose.Words tolka bytena som UTF‑8, vilket resulterar i felaktiga tecken.  
- Genom att ange rätt kodsida läser biblioteket texten exakt som författaren avsåg.

**Tips:** Använd `Encoding.GetEncoding("big5")` eller den numeriska kodsidan (`950`) för traditionell kinesisk (Big5) dokument.

---

## Anpassa laddningsalternativ (ange laddningsalternativ)

Utöver kodning exponerar `LoadOptions` många egenskaper som låter dig **ange laddningsalternativ** för avancerade scenarier:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Förklaring av de valda egenskaperna**

| Egenskap | Syfte |
|----------|-------|
| `LoadFormat` | Tvingar ett specifikt format, kringgår auto‑detektering. Användbart när filändelser är missvisande. |
| `LoadOptionsMemoryUsage` | Väljer en minnesbesparande strategi (`LowMemory`) för enorma dokument. |
| `Password` | Anger ett lösenord för krypterade filer, vilket undviker ett undantag. |
| `ValidateDocumentStructure` | När `true` validerar laddaren den interna XML‑strukturen och kastar ett fel om den är korrupt. |

Du kan kombinera någon av dessa med **ange dokumentkodning** för att hantera de mest krävande importpipelines.

---

## Fullständigt körbart exempel

Nedan är ett fristående program som demonstrerar alla koncept i ett flöde:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Förväntad konsolutdata**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Att köra programmet visar hur man **laddar en fil från katalog**, **anger dokumentkodning** och **anger laddningsalternativ** i ett enda tydligt arbetsflöde.

---

## Vanliga fallgropar och hur du undviker dem

| Symptom | Trolig orsak | Åtgärd |
|---------|---------------|--------|
| Felaktiga kinesiska tecken | Kodning är inte angiven eller fel kodsida | **Ange dokumentkodning** till `Encoding.GetEncoding(950)` för Big5. |
| `IncorrectPasswordException` även om filen inte är lösenordsskyddad | Laddaren felaktigt identifierade en binär fil som krypterad | Ange explicit `LoadFormat` till rätt typ (t.ex. `LoadFormat.Docx`). |
| Out |  |  |

## Vad bör du lära dig härnäst?

Följande handledningar täcker närliggande ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Master Markdown Load Options with Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}