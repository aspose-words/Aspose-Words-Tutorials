---
category: general
date: 2026-06-24
description: Δημιουργήστε σχήμα ορθογωνίου στην Python με το Aspose.Words, μάθετε
  πώς να προσθέσετε σκιά στο σχήμα, ορίστε τη γωνία της σκιάς και αποθηκεύστε το έγγραφο
  ως PDF σε λίγα λεπτά.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου στην Python, προσθέστε σκιά στο σχήμα,
  ορίστε τη γωνία της σκιάς και αποθηκεύστε το έγγραφο ως PDF με το Aspose.Words.
  Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα.
og_title: Δημιουργία Σχήματος Ορθογωνίου σε Python – Πλήρες Μάθημα Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Δημιουργία σχήματος ορθογωνίου σε Python – Πλήρης οδηγός Aspose.Words
url: /el/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Σχήματος Ορθογωνίου σε Python – Πλήρης Οδηγός Aspose.Words

Σας έχει ποτέ περάσει στο μυαλό πώς να **create rectangle shape** σε ένα έγγραφο Word χρησιμοποιώντας Python; Ίσως χρειάζεστε ένα έντονο πλαίσιο επισήμανσης, μια οπτική ένδειξη για ένα διάγραμμα, ή απλώς ένα κομψό ορθογώνιο για μια αναφορά. Ό,τι και αν είναι, βρίσκεστε στο σωστό σημείο. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — από την εισαγωγή του ορθογωνίου, στην προσθήκη μιας διακριτικής σκιάς, στη ρύθμιση της γωνίας της σκιάς, και τέλος στο **save document as PDF** ώστε να μπορείτε να το μοιραστείτε με όποιον.

Θα χρησιμοποιήσουμε το **Aspose.Words for Python via .NET**, μια ισχυρή βιβλιοθήκη που σας επιτρέπει να διαχειρίζεστε αρχεία Word χωρίς ποτέ να ανοίγετε το Word. Στο τέλος αυτού του οδηγού θα μπορείτε να απαντήσετε με σιγουριά στην ερώτηση *«πώς να προσθέσω σκιά σε σχήμα»* και θα έχετε ένα έτοιμο script που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο.

---

## What You’ll Need

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

- **Python 3.8+** εγκατεστημένο στο σύστημά σας.  
- **Aspose.Words for Python via .NET** (πακέτο `aspose-words`). Εγκαταστήστε το με:

  ```bash
  pip install aspose-words
  ```

- Έναν φάκελο με δικαιώματα εγγραφής όπου θα αποθηκευτεί το παραγόμενο PDF.  
- (Προαιρετικά) Ένα IDE ή κειμενογράφο — το VS Code λειτουργεί εξαιρετικά.

Αυτό είναι όλο. Χωρίς επιπλέον DLLs, χωρίς εγκατάσταση Office, μόνο ένα pip package.

---

## Step 1: Set Up the Document and Builder

Το πρώτο πράγμα που πρέπει να κάνετε είναι **create rectangle shape**‑friendly objects: ένα `Document` και ένα `DocumentBuilder`. Σκεφτείτε τον builder ως το στυλό σας· σχεδιάζει τα πάντα για εσάς.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Why this matters:** Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει μεθόδους όπως `insert_shape` που κάνουν το σχεδιασμό σχημάτων παιχνιδάκι.

---

## Step 2: Insert the Rectangle Shape

Τώρα που έχουμε έναν builder, μπορούμε τελικά να **create rectangle shape**. Η μέθοδος `insert_shape` χρειάζεται τρία ορίσματα: τον τύπο του σχήματος, το πλάτος και το ύψος. Θα χρησιμοποιήσουμε πλάτος 200 pt και ύψος 100 pt για ωραία αναλογία.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Σε αυτό το σημείο έχετε δημιουργήσει επιτυχώς **create rectangle shape** στο έγγραφό σας. Αν ανοίξετε το παραγόμενο DOCX (θα το κάνουμε αργότερα), θα δείτε ένα απλό ορθογώνιο που βρίσκεται εκεί που ήταν ο κέρσορας.

---

## Step 3: Access the Shadow Formatting Object

Για να **add shadow to shape**, πρώτα πρέπει να πάρουμε τη ρύθμιση σκιάς του σχήματος. Κάθε σχήμα στο Aspose.Words έχει μια ιδιότητα `shadow_format` που εκθέτει όλες τις ρυθμίσεις που αφορούν τη σκιά.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Η αναφορά `shadow` μας επιτρέπει να εναλλάξουμε την ορατότητα, το blur, την απόσταση, την γωνία, το χρώμα και τη διαφάνεια — όλα σε λίγες γραμμές κώδικα.

---

## Step 4: Enable the Shadow and Configure Its Appearance

Εδώ συμβαίνει η μαγεία. Θα **add shadow to shape**, θα το κάνουμε ελαφρώς θολό, θα το μετατοπίσουμε λίγο, θα ορίσουμε την κατεύθυνση (το τμήμα **set shadow angle**) και θα του δώσουμε μια ημιδιαφανή μαύρη απόχρωση.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Pro tip:** Αν χρειάζεστε πιο δραματικό αποτέλεσμα, αυξήστε το `blur_radius` ή μειώστε το `transparency`. Αντίθετα, μια αιχμηρή, πλήρως αδιαφανής σκιά μπορεί να επιτευχθεί με `blur_radius = 0` και `transparency = 0`.

---

## Step 5: Save the Document as a PDF

Έχουμε **create rectangle shape**, έχουμε **add shadow to shape**, και τώρα θα **save document as PDF** ώστε το αποτέλεσμα να φαίνεται ίδιο σε οποιαδήποτε συσκευή. Το Aspose.Words το κάνει με μία μόνο γραμμή κώδικα.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Η εκτέλεση του script θα δημιουργήσει το `shadowed_rectangle.pdf` στον φάκελο `output`. Ανοίξτε το με οποιονδήποτε PDF viewer και θα δείτε ένα καθαρό ορθογώνιο με μια ήπια, 45‑μοίρες σκιά — ακριβώς όπως τη ρυθμίσαμε.

---

## Full Working Example

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση script που συνδυάζει όλα τα παραπάνω βήματα. Αντιγράψτε‑και‑επικολλήστε το σε ένα αρχείο με όνομα `create_rectangle_with_shadow.py` και τρέξτε `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Αναμενόμενο αποτέλεσμα:** Ένα αρχείο PDF που εμφανίζει ένα μόνο ορθογώνιο με ήπια, διαγώνια σκιά. Χωρίς επιπλέον σελίδες, χωρίς κρυφά artefacts — μόνο το σχήμα που δημιουργήσαμε.

---

## Common Questions & Edge Cases

### What if I need a different shape?

Το Aspose.Words υποστηρίζει πολλές τιμές `ShapeType` (έλλειψη, αστέρι, callout κ.λπ.). Απλώς αντικαταστήστε το `aw.drawing.ShapeType.RECTANGLE` με το επιθυμητό enum, π.χ. `aw.drawing.ShapeType.ELLIPSE`.

### Can I add multiple shadows?

Το API εκθέτει μόνο ένα `ShadowFormat` ανά σχήμα, αλλά μπορείτε να προσομοιώσετε πολλαπλές σκιές διπλασιάζοντας το σχήμα, μετατοπίζοντας κάθε αντίγραφο και ρυθμίζοντας τη διαφάνεια.

### How do I change the shadow color to match my brand?

Απλώς ορίστε `shadow.color` σε οποιοδήποτε `aw.drawing.Color`. Για ένα εταιρικό μπλε, χρησιμοποιήστε `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### What about saving as DOCX instead of PDF?

Αντικαταστήστε το `document.save(pdf_path)` με `document.save("output/shadowed_rectangle.docx")`. Η απόδοση της σκιάς διατηρείται και στα δύο φορμά.

### Does the shadow work on older PDF viewers?

Το Aspose.Words αποδίδει τη σκιά ως διανυσματικό εφέ, το οποίο υποστηρίζεται ευρέως. Ωστόσο, πολύ παλιοί viewers μπορεί να «flatten» το εφέ· η δοκιμή σε συσκευές του κοινού σας είναι πάντα καλή πρακτική.

---

## Tips for Polishing Your PDF

- **Add a border:** `rectangle.line_format.width = 1.5` και ορίστε χρώμα για καθαρό περίγραμμα.  
- **Center the rectangle:** Χρησιμοποιήστε `builder.move_to_document_start()` πριν την εισαγωγή, μετά `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Εισάγετε ένα `TextFragment` μετά το ορθογώνιο για ετικέτα, π.χ. `"Important Section"`.

Αυτές οι μικρές βελτιώσεις μπορούν να μετατρέψουν ένα απλό ορθογώνιο σε ένα επαγγελματικό call‑out box που φαίνεται εξαιρετικό σε αναφορές, προτάσεις ή e‑books.

---

## Conclusion

Τώρα έχετε μια ολοκληρωμένη, end‑to‑end συνταγή για **create rectangle shape** σε Python, **add shadow to shape**, **set shadow angle**, και **save document as PDF** χρησιμοποιώντας το Aspose.Words. Τα βήματα είναι απλά, ο κώδικας πλήρως αυτόνομος, και έχετε δει γιατί κάθε γραμμή είναι σημαντική — από την αρχικοποίηση του εγγράφου μέχρι το τελικό polish του PDF.

Στη συνέχεια, μπορείτε να εξερευνήσετε **how to add shape shadow** σε πιο σύνθετα σχέδια, να πειραματιστείτε με gradient fills, ή να δημιουργήσετε πίνακες μέσα στα σχήματά σας. Η βιβλιοθήκη υποστηρίζει επίσης τη σύνδεση σχημάτων με bookmarks, κάτι χρήσιμο για διαδραστικά PDFs.

Δοκιμάσατε κάτι διαφορετικό; Μοιραστείτε το στα σχόλια ή ρωτήστε ό,τι απορίες έχετε. Καλό coding και καλή διασκέδαση προσθέτοντας βάθος στα έγγραφά σας! 

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## What Should You Learn Next?

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}