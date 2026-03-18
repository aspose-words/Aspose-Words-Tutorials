---
category: general
date: 2026-03-17
description: Lär dig Aspose-handledningen om varningsåteruppringning för att upptäcka
  saknade teckensnitt och spåra dem i Java-dokument, med ett komplett, körbart exempel.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: sv
og_description: Behärska Aspose‑varningscallback‑handledningen för att upptäcka saknade
  teckensnitt och spåra saknade teckensnitt i ditt Java‑ordbehandlingsflöde.
og_title: aspose varningsåteruppringning handledning – Upptäck saknade teckensnitt
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: aspose varningsåteranrop handledning – Upptäck och spåra saknade teckensnitt
url: /sv/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

ensnitt". So heading: "# aspose warning callback tutorial – Upptäck och spåra saknade teckensnitt".

Proceed similarly for other headings.

Translate paragraphs.

Make sure to keep code block placeholders unchanged.

Also translate table content.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Upptäck och spåra saknade teckensnitt

Har du någonsin funderat på hur du **upptäcker saknade teckensnitt** när du konverterar eller redigerar Word‑filer med Aspose.Words? Du är inte ensam. I många verkliga projekt kan ett felaktigt teckensnitt orsaka layout‑problem, och du behöver ett pålitligt sätt att **spåra saknade teckensnitt** innan de ger dig huvudvärk senare.  

Den goda nyheten? **aspose warning callback tutorial** ger dig en ren, programmerbar krok som skriver ut exakt de teckensnitt‑substitutionsvarningar som uppstår. I den här guiden går vi igenom hur du ställer in återuppringningen, laddar ett dokument och ser varningarna i aktion – allt i Java.

När du är klar med artikeln kan du automatiskt identifiera saknade teckensnitt, logga dem och besluta om du ska bädda in ett ersättnings‑teckensnitt eller justera dina källfiler. Inga externa verktyg behövs.

## Förutsättningar

- **Java 8+** (koden kompileras med vilken recent JDK som helst)
- **Aspose.Words for Java** version 23.10 eller nyare – ladda ner från Aspose‑portalen eller lägg till Maven‑beroendet.
- Ett exempel‑DOCX som medvetet refererar till ett teckensnitt du inte har installerat (t.ex. “Comic Sans MS” på en Linux‑maskin).

Det är allt – inga extra bibliotek, inga komplicerade byggsteg.

## Steg 1: Registrera en varningsåteruppringning – Kärnan i aspose warning callback tutorial

Det första som tutorialen visar är hur du fäster en varningslyssnare. Aspose.Words höjer ett `WarningInfo`‑objekt för varje problem den stöter på, och flaggan `WarningSource.FONT_SUBSTITUTION` talar om exakt när ett teckensnitt byts ut.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Varför detta är viktigt:** Utan återuppringningen ersätter Aspose tyst saknade teckensnitt, och du får aldrig veta vilka tecken som kan se felaktiga ut. Genom att logga varningen kan du **upptäcka saknade teckensnitt** tidigt och besluta om du ska bädda in det korrekta.

> **Proffstips:** Om du behöver samla varningar för senare rapportering, lagra dem i en `List<WarningInfo>` istället för att skriva ut dem direkt.

## Steg 2: Ladda dokumentet – Där saknade teckensnitt kan gömma sig

Nu laddar vi DOCX‑filen som kan referera till teckensnitt som inte finns på maskinen. Själva laddningen triggar varningsåteruppringningen om några teckensnitt saknas.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Vad händer i bakgrunden?** Aspose analyserar dokumentets stildefinitioner, skannar varje text‑run och kontrollerar systemets teckensnittsförråd. När den inte kan hitta en exakt matchning faller den tillbaka på ett substitut och avfyrar varningen som vi just kopplat.

## Steg 3: Spara dokumentet – Spola ut varningarna

Till sist sparar vi dokumentet. Spara‑operationen utvärderar teckensnitten igen, så eventuella varningar som inte avfyrades under laddning visas nu.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

När du kör programmet får du konsolutdata liknande:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Denna utdata bevisar att **aspose warning callback tutorial** fungerar, och du har framgångsrikt **upptäckt saknade teckensnitt** samt **spårat saknade teckensnitt** via loggen.

## Så här upptäcker du saknade teckensnitt i ett Word‑dokument – Utöver grunderna

Återuppringningsmetoden är utmärkt för engångskörningar, men ibland behöver du ett återanvändbart verktyg. Här är ett snabbt omslag du kan slänga in i vilket projekt som helst:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Anropa det så här:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Nu har du en återanvändbar **detect missing fonts**‑metod som returnerar en lista du kan mata in i en CI‑pipeline eller ett UI.

## Spåra saknade teckensnitt med Aspose.Words – Rapportering för team

I ett större team kan det vara bra att producera en CSV‑rapport över alla saknade teckensnitt i många dokument. Kombinera det föregående verktyget med enkel fil‑iteration:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

När du kör detta skript får du en **track missing fonts**‑CSV som varje utvecklare kan kika på innan de checkar in ett dokument i produktion.

## Vanliga fallgropar & hur du undviker dem

| Fallgrop | Varför det händer | Lösning |
|----------|-------------------|---------|
| **Återuppringning avfyras inte** | Du glömde att sätta återuppringningen **före** dokumentet laddas. | Placera `Document.setWarningCallback` högst upp i `main`. |
| **Endast den första varningen visas** | Aspose cachar varningar per `Document`‑instans. | Använd ett nytt `Document`‑objekt för varje fil, eller återställ återuppringningen mellan körningar. |
| **Fel teckensnittsnamn i loggen** | Beskrivningen innehåller extra text (“Font … not found”). | Rensa med regex som visas i CSV‑exemplet. |
| **Prestandapåverkan vid stora batcher** | Återuppringningen körs för varje text‑run, vilket kan bli dyrt. | Begränsa kontrollen till ett förhandssteg; hoppa över sparning om du bara behöver upptäckt. |

## Förväntade resultat & verifiering

1. **Konsolutdata** – Du bör se minst en rad med “Font substitution warning” för varje saknat teckensnitt.  
2. **CSV‑rapport** – När bulk‑skriptet är klart, öppna `missing-fonts-report.csv` och verifiera att varje rad listar dokumentnamnet och det exakta saknade teckensnittet.  
3. **Sparat dokument** – Utdata‑DOCX kommer att renderas med fallback‑teckensnitt, men den visuella layouten kan skilja sig från originalet.

Om något av dessa steg inte beter sig som beskrivet, dubbelkolla att Aspose.Words‑JAR‑filen finns på din classpath och att `input.docx` verkligen refererar till ett teckensnitt som saknas i ditt OS.

## Slutsats

Du har precis slutfört en **aspose warning callback tutorial** som visar hur du **upptäcker saknade teckensnitt** och **spårar saknade teckensnitt** i Java‑applikationer. Genom att registrera en varningslyssnare, ladda dokumentet och eventuellt exportera resultaten får du full insyn i teckensnitt‑relaterade problem innan de dyker upp i produktion.

Nästa steg kan vara att utforska:

- Bädda in det saknade teckensnittet direkt med `LoadOptions.setFontSubstitution`.
- Använda `FontSettings`‑klassen för att mappa saknade teckensnitt till specifika substitut.
- Integrera CSV‑rapporten i en CI/CD‑pipeline för att misslyckas byggen när odokumenterade teckensnitt dyker upp.

Prova, justera återuppringningarna så de passar ditt loggnings‑ramverk, och se hur ditt dokument‑flöde blir mycket mer robust. Lycka till med kodandet!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}