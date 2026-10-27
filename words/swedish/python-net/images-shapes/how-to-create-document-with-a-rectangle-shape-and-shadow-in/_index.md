---
category: general
date: 2026-10-04
description: Hur man skapar ett dokument i Python och lägger till skugga på en form
  med Aspose.Words. Lär dig att ställa in skuggfärg, infoga en rektangelform och anpassa
  yttre skugga.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: sv
lastmod: 2026-10-04
og_description: Hur man skapar ett dokument i Python och lägger till skugga på en
  form. Denna guide visar hur du ställer in skuggfärgen, infogar en rektangelform
  och applicerar en yttre skugga med Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Hur man skapar ett dokument med en rektangelform och skugga i Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Hur man skapar ett dokument med en rektangelform och skugga i Python
url: /sv/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man skapar ett dokument med en rektangelform och skugga i Python

Om du behöver **hur man skapar ett dokument** som innehåller en stylad rektangel, ger den här guiden en komplett lösning. Du kommer att se hur du **lägger till skugga på form**, sätter skuggans färg och styr dess förskjutning och oskärpa – allt med Aspose.Words for Python. I slutet av handledningen kan du generera en `.docx`‑fil som ser polerad ut och är klar för distribution.

Stegen nedan täcker allt från att installera biblioteket till att anpassa skuggans utseende. Ingen extern dokumentation krävs; koden är redo att kopieras, köras och anpassas till dina egna projekt. Du kommer också att lära dig hur du **infoga rektangelform**, väljer en **outer shadow style**, och hanterar vanliga fallgropar som osynliga skuggor eller felaktiga omslagsinställningar.

## Förutsättningar

* Python 3.8 eller nyare installerat.
* En aktiv Aspose.Words for Python-licens (eller en gratis utvärderingsnyckel).
* Grundläggande kunskap om Python‑skriptning.
* Tillgång till en filsystemplats där det genererade dokumentet kommer att sparas.

Du kan installera SDK:n med pip:

```bash
pip install aspose-words
```

## Steg 1: Importera biblioteket och skapa ett nytt tomt dokument

Att skapa ett nytt dokument är den första åtgärden i alla Word‑automatiseringsscenarier. `aw.Document()`‑konstruktorn ger dig en tom fil som du kan fylla med text, bilder eller former.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

`DocumentBuilder`‑objektet förenklar införandet av innehåll. Det håller reda på den aktuella markörpositionen, så att du kan lägga till element sekventiellt utan att manuellt hantera sektioner.

## Steg 2: Infoga en rektangelform med önskad storlek

En rektangelform fungerar som en behållare för visuella element. Du kan definiera dess bredd och höjd i punkter (1 pt ≈ 1/72 tum).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

I detta skede har formen ingen visuell stil, så den visas som en enkel kontur. Nästa steg kommer att ge den djup och färg.

## Steg 3: Ställ in formen så att den flyter inline med omgivande text

När en form är **inline** beter den sig som ett tecken i ett stycke. Detta säkerställer att rektangeln förblir där du förväntar dig den i dokumentlayouten.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Om du föredrar att formen flyter över texten kan du använda `WrapType.SQUARE` eller `WrapType.TOP_BOTTOM`, men för de flesta rapporter ger en inline‑form en förutsägbar layout.

## Steg 4: Gör skuggan synlig och välj dess färg

En skugga som inte är synlig ger ingen visuell nytta. `visible`‑flaggan aktiverar effekten, och `color`‑egenskapen bestämmer dess nyans. Att använda svart ger ett klassiskt, subtilt djup.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Du kan ersätta `aw.drawing.Color.black` med någon annan färg, såsom `aw.drawing.Color.gray` eller ett anpassat RGB‑värde (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Steg 5: Definiera skuggans förskjutning och oskärpa för att ge den djup

Förskjutningen styr hur långt skuggan förflyttas från formen, medan oskärpradien mjukar upp kanterna. Små värden skapar en skarp skugga; större värden ger ett mjukare utseende.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimentera med dessa siffror för att matcha dina designriktlinjer. För en kraftig drop‑shadow kan du öka både förskjutning och oskärpa.

## Steg 6: Välj en yttre skuggstil

Aspose.Words erbjuder flera skuggstilar, såsom `INNER`, `OUTER` och `PERSPECTIVE`. **outer**‑stilen placerar skuggan utanför formens kant, vilket är idealiskt för ett rent, professionellt utseende.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Om du behöver en mer dramatisk effekt, prova `ShadowStyle.PERSPECTIVE` — den lägger till en tredimensionell lutning.

## Steg 7: Spara dokumentet med den formade skuggan

Spara avslutar filen och skriver all formatering till disk. Välj en katalog som du har skrivrättigheter till, och ge filen ett beskrivande namn.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

När skriptet körs genereras en Word‑fil som innehåller en rektangel med en synlig, färgad skugga. Öppna filen i Microsoft Word eller LibreOffice för att verifiera resultatet.

## Fullt körbart exempel

Nedan är det kompletta skriptet som inkluderar alla steg som diskuterats. Kopiera koden till en fil med namnet `create_shadowed_shape.py` och kör den med `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Förväntat resultat**

När du öppnar `ShapeWithShadow.docx` kommer du att se en enda rektangel centrerad på sidan. Rektangeln följs av en subtil svart skugga som är förskjuten till nedre‑höger, lätt oskärpad för att skapa djup. Skuggan följer den yttre stilen, så den intersectar inte rektangelns inre.

## Vanliga frågor och specialfall

### Varför visas skuggan ibland som osynlig?

Skuggan renderas endast om `shadow.visible` är satt till `True` **och** formens `wrap_type` tillåter att den visas. En inline‑form fungerar pålitligt; flytande former kan kräva ytterligare layoutjusteringar.

### Hur kan jag ändra skuggans färg för att matcha en varumärkespalett?

Ersätt `aw.drawing.Color.black` med ett anpassat RGB‑värde:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Vad händer om jag vill att formen ska visas bakom texten?

Ställ in omslagstypen till `WrapType.BEHIND` och justera `z_order_position` om nödvändigt. Tänk på att vissa visare kan rendera former bakom text på olika sätt.

### Kan jag tillämpa samma skugginställningar på flera former?

Ja. Skapa en hjälpfunktion som konfigurerar skuggan och anropa den för varje form du infogar. Detta främjar kodåteranvändning och säkerställer enhetlig stil.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Slutsats

Du vet nu **hur man skapar dokument** som innehåller en rektangelform med en anpassad skugga med hjälp av Aspose.Words for Python. Handledningen täckte införandet av en rektangel, att göra formen inline, aktivera skuggan, sätta dess färg, förskjutning, oskärpa och stil, och slutligen spara filen.

Härifrån kan du utforska relaterade ämnen såsom **add shadow to shape** för andra formtyper, **set shadow color** dynamiskt baserat på data, eller **how to add shadow** till bilder och textrutor. Experimentera med olika dimensioner, färger och skuggstilar för att matcha dina varumärkesriktlinjer eller designsystem.

Redo att automatisera fler Word‑dokument? Prova att lägga till tabeller, rubriker eller dynamiskt innehåll nästa gång — varje steg bygger på samma principer som demonstrerats här. Lycka till med kodandet!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa rektangelform, lägg till skugga & spara PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Skapa tomt Word‑dokument med skuggad rektangelform – steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Hur man hanterar dokumentvariabler med Aspose.Words i Python&#58; En komplett guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}