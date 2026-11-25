---
category: general
date: 2026-11-25
description: Lägg till skugga på en form i ett Word‑dokument med Python. Lär dig hur
  du infogar en rektangulär form i Word och applicerar en transparent skugga med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: sv
lastmod: 2026-11-25
og_description: Lägg till skugga på en form i ett Word‑dokument med Python. Den här
  handledningen visar hur du infogar en rektangelform i Word och ställer in en 30 %
  transparent skugga med Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Lägg till skugga på en form i ett Word‑dokument med Python – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Hur man lägger till skugga på en form i ett Word‑dokument med Python
url: /sv/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man lägger till skugga på en form i ett Word-dokument med Python

Om du behöver **lägga till skugga på en form** i ett Word-dokument, visar den här guiden en komplett, körbar lösning. Du kommer att se hur du skapar en Word‑fil, infogar en rektangel‑form och applicerar en 30 % transparent skugga — allt med Aspose.Words for Python‑biblioteket.

Att arbeta med Word-dokument programatiskt sparar dig från manuell formatering och låter dig generera rapporter, kontrakt eller marknadsföringsflygblad i stor skala. I slutet av den här handledningen kommer du att kunna svara på “**how to create Word document python**” med ett färdigt kodexempel.

## Förutsättningar

* Python 3.8 eller nyare installerat.
* En aktiv Aspose.Words for Python‑licens (gratis provversion fungerar för utvärdering).
* `aspose-words`‑paketet installerat via `pip install aspose-words`.
* En mapp där utdatafilen kan skrivas (ersätt `YOUR_DIRECTORY` i koden).

Inga ytterligare beroenden krävs.

## Steg 1: Skapa ett nytt Word‑dokument

Det första steget är att instansiera ett `Document`‑objekt. Detta objekt representerar hela .docx‑filen i minnet.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` fungerar som en virtuell markör. När du anropar dess metoder infogar biblioteket motsvarande element på den aktuella markörpositionen.

## Steg 2: Infoga rektangel‑form i Word

Därefter **infogar du rektangel‑form i Word** med builderns `insert_shape`‑metod. Metoden kräver formtypen och dess storlek i punkter (1 punkt = 1/72 tum).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Du kan ändra dimensionerna för att matcha din design. Rektangeln blir en del av dokumentets ritlager, vilket innebär att du senare kan modifiera dess fyllning, kontur eller skugga.

## Steg 3: Åtkomst till formens skuggformat

Varje ritobjekt exponerar en `shadow_format`‑egenskap som styr skuggans utseende. Hämta den så att du kan justera transparens, förskjutning, oskärpa och färg.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Vid detta tillfälle har formen standardskuggan (ingen skugga). `ShadowFormat`‑objektet innehåller alla parametrar du behöver för att skapa en realistisk effekt.

## Steg 4: Gör skuggan 30 % transparent

Transparens uttrycks som ett värde mellan `0` (helt ogenomskinlig) och `1` (helt genomskinlig). Att sätta det till `0.3` ger en 30 % transparent skugga, vilket ofta är tillräckligt för att lägga till djup utan att överväldiga texten.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Dessa extra egenskaper är inte obligatoriska, men de visar hur du kan finjustera effekten. `visible`‑flaggan är avgörande; om du glömmer den kommer skuggan inte att visas även om andra inställningar är konfigurerade.

## Steg 5: Spara dokumentet för att se resultatet

Slutligen skriver du dokumentet till disk. När du öppnar den resulterande `.docx`‑filen i Microsoft Word eller någon kompatibel visare visas rektangeln med den applicerade transparenta skuggan.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

När du öppnar `output.docx` kommer du att se en enkel rektangel med en subtil grå skugga förskjuten mot nedre‑höger. Skuggans 30 % transparens får formen att framstå som om den lyfts från sidan.

![Exempel på att lägga till skugga på en form](placeholder-image.png){: .align-center alt="Exempel på att lägga till skugga på en form i ett Word-dokument skapat med Python"}

## Fullständigt, körbart skript

Genom att sätta ihop alla delar får du ett självständigt skript som du kan kopiera, klistra in och köra omedelbart.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Förväntat resultat:** När du öppnar den genererade `output.docx` visas en enda sida med en rektangel som kastar en lätt, halvgenomskinlig skugga. Ingen ytterligare formatering krävs.

## Vanliga variationer och kantfall

| Situation | Hur du anpassar koden |
|-----------|-----------------------|
| **Olika formtyp** (t.ex. ellips) | Ändra `aw.drawing.ShapeType.RECTANGLE` till `aw.drawing.ShapeType.ELLIPSE`. |
| **Anpassad skuggfärg** | Sätt `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` för en rödaktig skugga. |
| **Flera former** | Anropa `builder.insert_shape` upprepade gånger; varje anrop returnerar ett separat `Shape`‑objekt som du kan formatera oberoende. |
| **Spara som PDF** | Byt ut `doc.save(output_path)` mot `doc.save(output_path.replace('.docx', '.pdf'))` och använd `.pdf`‑ändelsen. |
| **Kör utan licens** | Gratisprovversionen lägger till ett vattenmärke på första sidan. Skaffa en licens för att ta bort det i produktionsmiljö. |

## Tips och bästa praxis

* **Återanvänd buildern**: Behåll en enda `DocumentBuilder`‑instans för hela dokumentet för att undvika onödig objekt‑skapande.
* **Frigör resurser**: I långvariga tjänster, anropa `doc.dispose()` efter sparning för att frigöra inbyggt minne.
* **Validera utdata**: Använd `doc.validate(aw.ValidationType.FULL_VALIDATION)` före sparning om du behöver säkerställa efterlevnad av Open XML‑standarden.
* **Versionskompatibilitet**: Koden fungerar med Aspose.Words for Python ≥ 22.9. Säkerställ att ditt paket är uppdaterat med `pip install --upgrade aspose-words`.

## Slutsats

Du vet nu hur du **lägger till skugga på en form** i ett Word‑dokument med Python. Genom att följa de fem stegen — skapa ett dokument, **infoga rektangel‑form i Word**, konfigurera skuggan och spara — kan du automatisera skapandet av professionella dokument för rapporter, fakturor eller marknadsföringsmaterial.  

Härifrån kan du utforska andra formateringsalternativ som gradientfyllningar, textomslag eller konvertering av dokumentet till PDF. Varje av dessa ämnen bygger på samma `DocumentBuilder`‑ och formateringskoncept som introducerades i den här handledningen.

Lycka till med kodandet, och njut av den visuella djupet som en enkel skugga kan ge dina automatiserade Word‑dokument!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig behärska ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Hur man skapar rektangel‑form i ett Word‑dokument med Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Lägg till skugga på form i Python – Komplett Aspose.Words‑handledning](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Skapa tomt Word‑dokument och lägg till skugga på form – Fullständig Python‑guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}