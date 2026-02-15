---
category: general
date: 2026-02-15
description: Skapa en rektangelform i ett Word‑dokument med Java. Lär dig hur du lägger
  till skugga på formen, sparar Word‑dokumentet och lägger till en rektangel med Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: sv
og_description: Skapa en rektangelform i en Word‑fil med Java. Den här guiden visar
  hur du lägger till skugga på formen, sparar Word‑dokumentet och lägger till rektangelformen
  steg för steg.
og_title: Skapa rektangel form – Java Aspose.Words-handledning
tags:
- Aspose.Words
- Java
- Document Automation
title: Skapa rektangel i Word med Java – Fullständig guide
url: /sv/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangelform i Word med Java – Fullständig guide

Har du någonsin behövt **create rectangle shape** i en Word‑fil men varit osäker på var du ska börja? Du är inte ensam—många utvecklare stöter på samma problem när de automatiserar rapporter eller fakturor. Den goda nyheten? Med Aspose.Words för Java kan du skapa en rektangel, ge den ett snyggt skugga och spara Word‑dokumentet på några få rader.

I den här handledningen går vi igenom allt du behöver: från att initiera ett tomt dokument, till att konfigurera en skugga, och slutligen spara filen. I slutet kommer du att veta **how to shadow shape**‑objekt, hur du **add shape shadow**, och hur du **add rectangle shape** i vilket Word‑dokument du än genererar. Ingen extern dokumentation behövs—bara ren, körbar kod.

## Förutsättningar

- Java 8 eller nyare (API:et fungerar även med Java 11+).  
- Aspose.Words for Java‑biblioteket (version 23.9 eller senare).  
- En IDE som IntelliJ IDEA eller Eclipse—vilken som helst fungerar.  
- Grundläggande kunskap om Java‑syntax.

> **Pro tip:** Om du använder Maven, lägg till Aspose.Words‑beroendet i din `pom.xml` och låt IDE:n hantera resten.

---

## Steg 1: Initiera ett nytt dokument – How to **create rectangle shape**  

Först och främst: du behöver en ren canvas. I Aspose.Words är den canvasen ett `Document`‑objekt.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

`Document`‑klassen representerar hela .docx‑filen. Tänk på den som den anteckningsbok där du senare kommer att **add rectangle shape** och dess skugga.

## Steg 2: Bygg rektangeln – **Add rectangle shape**  

Nu konstruerar vi faktiskt rektangeln. Vi kommer att sätta dess storlek, layout och fyllningsfärg.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Varför `INLINE`‑wrap? För att vi vill att formen ska bete sig som ett stycke—perfekt för enkla rapporter. Du kan ändra det till `TOPBOTTOM` om du senare behöver att texten flyter runt formen.

## Steg 3: Applicera en skugga – **How to shadow shape**  

En platt rektangel ser lite tråkig ut. Att lägga till en skugga ger den djup och får dokumentet att kännas mer polerat. Här svarar vi på “**how to shadow shape**” i praktiken.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Varje egenskap gör något specifikt:

- `setVisible(true)` slår på skuggan.  
- `setColor` väljer en mörkgrå för en subtil effekt.  
- `setBlurRadius` styr hur mjuka kanterna blir.  
- `setOffsetX/Y` flyttar skuggan åt höger och ner, vilket efterliknar en ljuskälla.  
- `setTransparency` gör den lätt genomskinlig, så att formen förblir i fokus.

> **Note:** Om du någonsin behöver en färgad skugga, skicka bara en annan `java.awt.Color` till `setColor`.

## Steg 4: Infoga formen i dokumentet  

När rektangeln och dess skugga är klara, placerar vi den i dokumentets första sektion.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Att lägga till i kroppen placerar formen där ett nytt stycke skulle hamna. Om du vill ha rektangeln på en specifik plats kan du använda `insertBefore` eller manipulera `Paragraph`‑samlingen.

## Steg 5: **Save Word document** – Spara ditt arbete  

Det sista steget är att skriva filen till disk. Detta är ögonblicket då du faktiskt **save Word document**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Byt ut `YOUR_DIRECTORY` mot en absolut eller relativ sökväg på din maskin. Efter att programmet har körts, öppna `ShadowShape.docx` i Microsoft Word—du bör se en ljusgrå rektangel med en mjuk mörk skugga.

![Diagram som visar en rektangelform med skugga skapad med Aspose.Words](https://example.com/rectangle-shadow.png "skapa rektangelform med skugga")

---

## Vanliga frågor & edge‑cases  

### Vad händer om jag behöver flera rektanglar?  

Upprepa helt enkelt **Step 2** och **Step 3** i en loop, justera `setWidth`, `setHeight` eller `setFillColor` för varje iteration. Kom ihåg att ge varje form ett unikt variabelnamn eller lagra dem i en lista.

### Kan jag exportera till PDF istället för DOCX?  

Absolut. Efter att formen har lagts till, anropa `document.save("output.pdf")`. Aspose.Words hanterar konverteringen och bevarar skuggan.

### Vad händer med äldre Word‑versioner?  

Använd overload‑metoden `document.save("file.doc", SaveFormat.DOC)`. API:et nedgraderar automatiskt funktioner, men observera att vissa skuggstilar kan se något annorlunda ut i äldre format.

### Hur ändrar jag skuggans riktning?  

Manipulera `setOffsetX` och `setOffsetY`. Positiv X flyttar skuggan åt höger, negativ åt vänster. Positiv Y flyttar ner, negativ upp. Lek med dessa siffror för att simulera en ljuskälla från vilken vinkel som helst.

## Tips för att arbeta med former  

- **Group shapes**: Om du behöver en etikett bredvid rektangeln, skapa en `GroupShape` och lägg till både rektangeln och en `TextBox`.  
- **Z‑order matters**: Använd `shape.moveToFront()` eller `shape.moveToBack()` för att styra vilken form som visas överst.  
- **Performance**: Att lägga till hundratals former kan vara långsamt. Batcha dem i en enda sektion och anropa sedan `document.updatePageLayout()` en gång i slutet.

## Sammanfattning  

Vi har gått igenom hur man **create rectangle shape** i ett Word‑dokument med Java, hur man **add shape shadow**, och hur man **save Word document** med resultatet. Den kompletta, körbara koden finns i kodsnuttarna ovan, och du förstår nu “varför” bakom varje egenskap—så att du kan justera färger, suddighet och offset för att passa vilken design som helst.

Redo för nästa utmaning? Prova att kombinera rektangeln med ett diagram, eller exportera filen som PDF och se hur skuggan renderas. Du kan också utforska **add rectangle shape** i tabeller för snygga rapportlayouter.

Lycka till med kodningen, och må dina dokument alltid vara lika skarpa som din kod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}