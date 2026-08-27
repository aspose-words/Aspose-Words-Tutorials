---
category: general
date: 2026-01-11
description: Lär dig hur du fångar varningar om teckensnittssubstitution med Aspose.Words
  för Java. Denna steg‑för‑steg‑handledning täcker också LoadOptions och varningsåteruppringningar.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words font substitution
- Java warning callback
- LoadOptions usage
- document loading warnings
language: sv
og_description: Fånga varningar om teckensnittssubstitution med Aspose.Words för Java.
  Följ den här guiden för att konfigurera LoadOptions och en varningsåteruppringning
  för pålitlig dokumentladdning.
og_title: Fånga varningar om teckensnittssubstitution i Java – Fullständig handledning
tags:
- Aspose.Words
- Java
- Document Processing
title: Fånga varningar om teckensnittsbyte i Java med Aspose.Words – Komplett guide
url: /sv/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fånga varningar för teckensnittssubstitution – Fullständig Java‑handledning

Har du någonsin behövt **fånga varningar för teckensnittssubstitution** när du öppnar ett Word‑dokument med saknade teckensnitt? Det är ett vanligt huvudvärk, särskilt när du genererar PDF‑filer eller skriver ut på en server som inte har alla teckensnitt installerade. Den goda nyheten? Aspose.Words for Java gör det enkelt—bara konfigurera ett `LoadOptions`‑objekt och anslut en varnings‑callback. I den här guiden kommer du att se exakt hur du gör det, varför det är viktigt och vad du kan förvänta dig när varningen avfyras.

Vi kommer också att beröra relaterade ämnen som **Aspose.Words font substitution**, att använda en **Java warning callback**, och bästa praxis för **LoadOptions usage**. I slutet har du ett färdigt kodexempel som loggar varje saknat‑teckensnitt‑händelse, så att din efterföljande bearbetning aldrig överraskar dig.

## Förutsättningar

- Java 17 (eller någon nyare JDK) installerad och konfigurerad.
- Aspose.Words for Java 23.10 (eller nyare) på din classpath.
- Ett Word‑dokument som refererar till ett teckensnitt du inte har lokalt (t.ex. `DocWithMissingFont.docx`).
- Grundläggande kunskap om Java try/catch‑block—inget avancerat.

Om någon av dessa känns obekant, pausa ett ögonblick och installera biblioteket från Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Nu när grunderna är lagda, låt oss gå in i koden.

## Steg 1: Ställ in en varnings‑callback för att **fånga varningar för teckensnittssubstitution**

Det första du behöver är en callback som Aspose.Words kommer att anropa när den stöter på ett saknat teckensnitt. Det är här vi **fångar varningar för teckensnittssubstitution**. Callbacken implementerar `IWarningCallback`‑gränssnittet och kontrollerar `WarningType`.

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    // Custom callback that prints details of each font substitution warning
    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            // Only act on font‑substitution warnings
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Code continues in the next steps...
    }
}
```

**Varför detta är viktigt:** Utan en callback byter Aspose.Words tyst ut det saknade teckensnittet mot ett standardteckensnitt, och du får aldrig veta att den visuella utmatningen har förändrats. Genom att fånga varningen kan du logga, varna eller till och med avbryta inläsningen om det saknade teckensnittet är kritiskt.

## Steg 2: Konfigurera **LoadOptions** och registrera callbacken

Nu skapar vi en `LoadOptions`‑instans och fäster vår `FontWarningCallback`. Detta steg är avgörande för **LoadOptions usage** och säkerställer att varje dokumentladdning går igenom samma varningsfilter.

```java
public static void main(String[] args) throws Exception {
    // Step 2: Prepare LoadOptions and hook the warning callback
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new FontWarningCallback());

    // Continue to load the document in the next step...
}
```

**Tips:** Du kan återanvända samma `LoadOptions`‑objekt för flera dokument, vilket sparar några rader kod och garanterar konsekvent hantering av **document loading warnings** i hela din applikation.

## Steg 3: Ladda dokumentet och observera resultatet

Med callbacken ansluten, ladda helt enkelt din Word‑fil. Om dokumentet refererar till ett teckensnitt som inte är installerat, kommer callbacken att avfyras och skriva ut detaljer till konsolen.

```java
    // Step 3: Load the document using the configured LoadOptions
    Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

    // Step 4: Confirm that the load completed
    System.out.println("Document loaded; check console for any font‑substitution warnings.");
}
```

### Förväntad konsolutmatning

Om vi antar att `DocWithMissingFont.docx` refererar till det saknade teckensnittet *“Comic Sans MS”*, kommer du att se något liknande:

```
Font substitution warning:
  Original font: Comic Sans MS
  Substituted by: Arial
Document loaded; check console for any font‑substitution warnings.
```

Om dokumentet **inte innehåller några saknade teckensnitt**, kommer konsolen bara att visa den sista raden, vilket bekräftar att din callback inte genererade några falska positiva.

## Steg 4: Hantera kantfall och vanliga fallgropar

### Flera saknade teckensnitt

Om ett dokument använder flera otillgängliga teckensnitt, körs callbacken en gång per teckensnitt. Du får en serie meddelanden, var och en med sin egen `source` och `description`. Ingen extra kod krävs—se bara till att ditt loggningssystem kan hantera snabba på varandra följande anrop.

### Undertrycka varningar

I sällsynta fall kan du vilja ignorera vissa substitutioner (t.ex. du vet att en viss reserv är acceptabel). Utöka callback‑logiken:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION &&
    !info.getSource().equalsIgnoreCase("SomeFontYouAccept")) {
    // Log or act on the warning
}
```

### Trådsäkerhet

Aspose.Words `LoadOptions` är inte trådsäker som standard. Om du laddar dokument parallellt, skapa en separat `LoadOptions`‑instans per tråd, eller synkronisera callbacken för att undvika race‑condition.

## Steg 5: Verifiera det ersatta teckensnittet i det resulterande dokumentet

Efter inläsning kan du vilja bekräfta att substitutionen faktiskt har skett. API:et låter dig iterera över alla runs och inspektera det faktiska teckensnittsnamnet:

```java
for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
    System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
}
```

Detta kodexempel skriver ut varje text‑run med sitt slutgiltiga teckensnitt. Det är en praktisk kontroll när du bygger automatiserade PDF‑konverteringspipelines.

## Fullständigt fungerande exempel

När vi sätter ihop allt, här är det kompletta, färdiga programmet:

```java
import com.aspose.words.*;

public class FontSubstitutionInfo {

    private static class FontWarningCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("Font substitution warning:");
                System.out.println("  Original font: " + info.getSource());
                System.out.println("  Substituted by: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) throws Exception {
        // Prepare LoadOptions and register the warning callback
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new FontWarningCallback());

        // Load the document (replace with your actual path)
        Document doc = new Document("YOUR_DIRECTORY/DocWithMissingFont.docx", loadOptions);

        // Optional: verify effective fonts in the document
        for (Run run : (Iterable<Run>) doc.getFirstSection().getBody().getChildNodes(NodeType.RUN, true)) {
            System.out.println("Run text: \"" + run.getText() + "\" uses font: " + run.getFont().getName());
        }

        System.out.println("Document loaded; check console for any font‑substitution warnings.");
    }
}
```

Spara detta som `FontSubstitutionInfo.java`, kompilera med `javac` och kör `java FontSubstitutionInfo`. Du bör se varningsmeddelandena (om några) följt av listan över runs och deras slutgiltiga teckensnitt.

## Visuell hjälp

![Skärmbild av konsolutmatning som visar varningar för teckensnittssubstitution](/images/font-substitution-warning.png "exempel på fånga varningar för teckensnittssubstitution")

*Alt‑text:* **capture font substitution warnings** – konsolutmatning efter att ha laddat ett dokument med saknade teckensnitt.

## Slutsats

Du vet nu hur du **fångar varningar för teckensnittssubstitution** med Aspose.Words for Java. Genom att konfigurera ett `LoadOptions`‑objekt och tillhandahålla en anpassad `IWarningCallback` får du full insyn i alla saknade‑teckensnitt‑händelser som annars tyst kan påverka dokumentets utseende. Denna teknik kopplar direkt in i **Aspose.Words font substitution**‑hantering, säkerställer pålitliga **document loading warnings**, och ger dig flexibiliteten att logga, varna eller avbryta baserat på dina affärsregler.

### Vad blir nästa steg?

- Utforska **Java warning callback**‑mönster för andra varningstyper (t.ex. `DEPRECATED_FEATURE`).
- Kombinera detta tillvägagångssätt med **PDF conversion** för att garantera att ersatta teckensnitt inte förstör layouten.
- Fördjupa dig i **LoadOptions usage**—experimentera med `Password`, `Encoding` och `ResourceLoadingCallback` för mer avancerade scenarier.

Känn dig fri att justera callbacken, dirigera varningar till ett loggningsramverk, eller till och med kasta ett anpassat undantag om ett kritiskt teckensnitt saknas. Himlen är gränsen, och nu har du en solid grund att bygga vidare på.

Lycka till med kodandet, och må dina dokument alltid renderas precis som du förväntar dig!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}