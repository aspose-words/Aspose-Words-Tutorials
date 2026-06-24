---
category: general
date: 2026-06-21
description: Skapa en rektangulär form i Python med Aspose.Words. Lär dig hur du lägger
  till skugga på formen, ställer in fyllningsfärg för formen och sparar dokumentet
  som PDF på några minuter.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: sv
og_description: Skapa rektangelform i Python med Aspose.Words. Denna guide visar hur
  du lägger till skugga på formen, ställer in fyllningsfärg för formen och sparar
  dokumentet som PDF.
og_title: Skapa rektangelform i Python – Aspose.Words‑handledning
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Skapa rektangelform i Python – Aspose.Words-handledning
url: /sv/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa rektangulär form i Python – Aspose.Words‑handledning

Har du någonsin undrat **hur man skapar en rektangulär form** i ett Word‑dokument medan du kodar i Python? Du är inte ensam. Många utvecklare stöter på problem när de behöver ett snabbt visuellt element—som en färgad ruta med en subtil skugga—och sedan exporterar hela saken som en PDF.  

I den här guiden går vi igenom ett komplett, körbart exempel som **skapar rektangulär form**, **sätter fyllningsfärg för formen**, **lägger till skugga på formen** och slutligen **sparar dokumentet som PDF**. Inga vaga referenser, bara konkret kod som du kan kopiera‑klistra in och köra idag.

## Vad du behöver

Innan vi dyker ner, se till att du har följande på din maskin:

- Python 3.8 eller nyare (syntaxen vi använder fungerar på alla moderna versioner).
- En aktiv Aspose.Words för Python‑licens eller en gratis provperiod (biblioteket är ren‑Python, ingen COM‑interop behövs).
- En textredigerare eller IDE du är bekväm med—VS Code fungerar utmärkt, men vilken som helst duger.

Det är allt. Inga tunga ramverk, inga extra OS‑nivå‑beroenden. Låt oss komma igång.

## Steg 1: Installera Aspose.Words för Python

Först och främst. Om du inte redan har gjort det, hämta paketet från PyPI:

```bash
pip install aspose-words
```

Varför detta steg är viktigt: Aspose.Words tillhandahåller klasserna `Document` och `DocumentBuilder` som vi kommer att förlita oss på. Utan biblioteket finns ingen av de senare anropen—som `insert_shape`—så skriptet skulle krascha innan det ens ritar en linje.

> **Pro tip:** Håll din virtuella miljö prydlig. Kör `python -m venv .venv && source .venv/bin/activate` innan du installerar, så att biblioteket hålls isolerat från systempaket.

## Steg 2: Skapa ett nytt dokument och en DocumentBuilder

Nu **skapar vi rektangulär form** – men först behöver vi en tom duk.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

`Document`‑objektet representerar hela filen, medan `DocumentBuilder` är en praktisk hjälpreda som vet var markören är och kan infoga element på den platsen. Tänk på buildern som en penna som skriver på sidan.

## Steg 3: Infoga rektangulär form

Här sker den primära handlingen. Vi **skapar rektangulär form** med en fast bredd och höjd, och placerar den sedan på sidan.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Varför en rektangel? Det är den enklaste formen som ändå låter oss visa fyllningsfärger och skuggor. Om du senare behöver en cirkel eller en stjärna, byt bara `ShapeType.RECTANGLE` mot ett annat enum‑värde.

## Steg 4: Sätt fyllningsfärg för formen

En enkel vit ruta är inte särskilt spännande, så låt oss **sätta fyllningsfärg för formen** till något milt—ljusblått fungerar bra för rapporter.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Du kan använda någon av de fördefinierade `aw.Color`‑medlemmarna (`red`, `green`, `dark_gray` osv.) eller skicka ett RGB‑tupel (`aw.Color.from_argb(255, 30, 144, 255)`). Fyllningsfärgen är vad användaren ser innan någon skugga eller kant appliceras.

## Steg 5: Lägg till skugga på formen

Nu till den visuella poleringen: **lägg till skugga på formen**. Skuggor ger djup och får rektangeln att sticka ut på sidan.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Hur lägger man till skugga**? Koden ovan gör exakt det, men låt oss gå igenom varför varje egenskap är viktig:

- `visible` – slår på/av effekten.
- `color` – definierar nyansen; en mörkgrå efterliknar naturligt ljus.
- `blur` – högre värden ger en mjukare kant.
- `offset_x` / `offset_y` – flyttar skuggan bort från formen; justera dessa för att simulera olika ljusvinklar.
- `transparency` – 0 är solid, 1 är osynlig; 0.2 ger ett subtilt intryck.
- `type` – `OUTER` kastar skuggan utanför formen, medan `INNER` skulle lägga den inuti.

Om du någonsin behöver en dramatisk dropskugga, öka `blur` till 10‑15 och höj `offset_x`/`offset_y` till 6‑8.

## Steg 6: Spara dokumentet som PDF

Allt detta arbete är meningslöst om vi inte kan **spara dokumentet som PDF** och dela det. Aspose.Words gör detta till en endaste rad:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Varför PDF? PDF‑filer bevarar layout över plattformar, vilket gör dem idealiska för rapporter, fakturor eller annat utskrivbart material. `save`‑metoden upptäcker automatiskt filändelsen och väljer rätt format—se bara till att sökvägen slutar på `.pdf`.

### Förväntat resultat

Öppna den resulterande `ShapeWithShadow.pdf` och du bör se en ljusblå rektangel centrerad nära toppen av första sidan, med en mjuk mörkgrå skugga som är förskjuten lite åt höger och ner. Formens kanter är skarpa, skuggan är subtil, och filstorleken är vanligtvis under 100 KB.

## Bonus: Justera skuggor – Svar på “hur lägger man till skugga”

Du kanske undrar, *“Kan jag ändra skuggans riktning utan att flytta formen?”* Absolut. Skuggans position är oberoende av formens koordinater; justera bara `offset_x` och `offset_y`. Positiva värden flyttar skuggan åt höger/nedåt, negativa värden åt vänster/uppåt. För ett ljus från övre vänstra hörnet, använd `offset_x = -3` och `offset_y = -3`.

En annan vanlig fråga: *“Vad händer om jag behöver flera skuggor på samma form?”* Aspose.Words stödjer endast en skugga per form. Om du behöver lager‑effekter, skapa en duplicerad form, förskjut den lite och applicera en annan skugga på varje. Det är lite en hack, men det fungerar.

## Fullt skript – Klart att köra

Nedan är det kompletta, självständiga skriptet. Kopiera det till en fil med namnet `create_rectangle_with_shadow.py` och kör det med `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Obs:** Ersätt `YOUR_DIRECTORY` med en absolut eller relativ sökväg som finns på din maskin. Om mappen inte finns kommer Python att kasta ett `FileNotFoundError`.

## Vanliga fallgropar & hur du undviker dem

| Problem | Varför det händer | Lösning |
|---------|-------------------|---------|
| Skugga visas inte | `shadow.visible` lämnades på standardvärdet `False` | Se till att `shadow.visible = True` |
| Formen är osynlig | Fyllningsfärgen sattes till `aw.Color.transparent` eller `None` | Använd en solid färg som `aw.Color.light_blue` |
| PDF är tom | Glömde att anropa `doc.save` eller sparade med fel filändelse | Anropa `doc.save("output.pdf")` och verifiera sökvägen |
| Körtidsfel `ImportError` | Aspose.Words är inte installerat eller fel Python‑miljö | Kör `pip install aspose-words` i den aktiva venv |

## Nästa steg – Utforska fler former och formatering

Nu när du har bemästrat **skapa rektangulär form**, kan du:

- Byt ut `ShapeType.RECTANGLE` mot `ShapeType.ELLIPSE` eller `ShapeType.PENTAGON` för att experimentera med andra geometriska former.
- Lägg till text i formen med `builder.move_to(rectangle.absolute_position)` och sedan `builder.writeln("Hello World")`.
- Kombinera flera former till en grupp med `group = aw.drawing.GroupShape(doc)` för komplexa diagram.
- Exportera till andra format som DOCX (`doc.save("output.docx")`) eller HTML (`doc.save("output.html")`) för att se hur skuggan översätts.

Varje av dessa utökningar bygger på samma grundkoncept: **lägg till skugga på formen**, **sätt fyllningsfärg för formen**, och **spara dokumentet som PDF** (eller ett annat format).

---

### Bildförhandsgranskning *(valfritt)*

![Skapa rektangulär form med skugga i Python](https://example.com/rectangle-shadow.png "Skapa rektangulär form med skugga i Python")

*Skärmdumpen visar det slutgiltiga PDF‑utdata med en ljusblå rektangel och en subtil yttre skugga.*

---

## Slutsats

Vi har gått igenom varje steg som behövs för att **skapa rektangulär form** i Python, applicera en anpassad fyllning, **lägga till skugga på formen**, och slutligen **spara dokumentet som PDF**. Koden är fullt körbar, förklaringarna täcker *varför* bakom varje egenskap, och vi har berört vanliga edge‑cases och nästa‑

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementeringsmetoder i dina egna projekt.

- [Skapa Word‑dokument Java – Lägg till rektangulär form med skuggeffekt](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Skapa rektangulär form i Word med C# – Steg‑för‑steg‑guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Formskugga‑handledning – Lägg till en skugga på Word‑form i C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}