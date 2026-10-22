---
category: general
date: 2026-08-17
description: Πώς να αποθηκεύσετε PNG χρησιμοποιώντας το Aspose.Words για Python. Μάθετε
  πώς να προσθέσετε σκιά σε σχήμα, να αποθηκεύσετε το έγγραφο ως PDF και να εξάγετε
  το Word σε PNG σε έναν ενιαίο οδηγό.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: el
lastmod: 2026-08-17
og_description: Πώς να αποθηκεύσετε PNG με το Aspose.Words. Αυτό το σεμινάριο δείχνει
  πώς να προσθέσετε σκιά σε ένα σχήμα, να αποθηκεύσετε το έγγραφο ως PDF και να εξάγετε
  το Word σε PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Πώς να αποθηκεύσετε PNG και να προσθέσετε σκιά σε σχήμα με το Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Πώς να αποθηκεύσετε PNG και να προσθέσετε σκιά σε σχήμα με το Aspose.Words
url: /el/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε PNG και να προσθέσετε σκιά σε σχήμα με Aspose.Words

Αν χρειάζεστε **πώς να αποθηκεύσετε PNG** από ένα αρχείο Word, αυτός ο οδηγός σας παρέχει μια πλήρη, εκτελέσιμη λύση. Θα δείτε επίσης πώς να **προσθέσετε σκιά σε σχήμα**, **αποθηκεύσετε το έγγραφο ως PDF**, και **εξάγετε Word σε PNG** χωρίς να αφήσετε το περιβάλλον Aspose.Words.

Το σεμινάριο καλύπτει όλα όσα απαιτούνται για να μετατρέψετε ένα κενό έγγραφο Word σε PDF και εικόνα PNG, εφαρμόζοντας ένα απλό εφέ σκιάς σε σχήμα ορθογωνίου. Δεν απαιτούνται εξωτερικά εργαλεία και ο κώδικας λειτουργεί με Aspose.Words for Python via .NET 7 ή νεότερο.

## Τι θα επιτύχετε

* Δημιουργήστε ένα νέο έγγραφο Word προγραμματιστικά.  
* Εισάγετε ένα σχήμα ορθογωνίου και διαμορφώστε ένα εφέ σκιάς.  
* Αποθηκεύστε το ίδιο έγγραφο ως αρχείο PDF.  
* Εξάγετε το έγγραφο ως εικόνα PNG.  

Αυτά τα βήματα απαντούν στο συνηθισμένο ερώτημα **πώς να αποθηκεύσετε PNG** ενώ επίσης διαχειρίζονται **προσθήκη σκιάς σε σχήμα** και **αποθήκευση εγγράφου ως PDF** σε μια ενιαία ροή εργασίας.

## Προαπαιτούμενα

* Python 3.9 ή νεότερο.  
* Aspose.Words for Python via .NET εγκατεστημένο (`pip install aspose-words`).  
* Δικαιώματα εγγραφής στον φάκελο εξόδου που καθορίζετε.  

Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, εκτελέστε:

```bash
pip install aspose-words
```

## Πώς να αποθηκεύσετε PNG με Aspose.Words

Το πρώτο σημαντικό βήμα είναι η δημιουργία ενός εγγράφου και ενός `DocumentBuilder`. Ο builder σας παρέχει μια ευέλικτη API για την εισαγωγή περιεχομένου όπως σχήματα, πίνακες ή κείμενο.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη. `aw.DocumentBuilder` δείχνει στην τρέχουσα θέση εισαγωγής, η οποία αρχικά είναι η αρχή της πρώτης (και μοναδικής) ενότητας.

## Προσθήκη σκιάς σε σχήμα πριν την εξαγωγή

Ένα σχήμα μπορεί να είναι οποιοδήποτε αντικείμενο σχεδίασης—ορθογώνιο, έλλειψη ή προσαρμοσμένο πολύγωνο. Εδώ δημιουργούμε ένα ορθογώνιο 100 × 100 σημείων και εφαρμόζουμε μια ήπια σκιά.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Γιατί να διαμορφώσετε τη σκιά πριν την αποθήκευση; Το Aspose.Words αποδίδει τη σκιά κατά τις φάσεις εξαγωγής PDF και PNG, έτσι το οπτικό εφέ διατηρείται και στις δύο μορφές εξόδου.

### Συμβουλή επαγγελματία
Αν χρειάζεστε πιο έντονη σκιά, μειώστε το `blur`. Για πιο έντονη μετατόπιση, αυξήστε το `distance`. Η κλάση `Shadow` εκθέτει επίσης τα `angle` και `transparency` για ακριβή έλεγχο.

## Αποθήκευση εγγράφου ως PDF

Η αποθήκευση ενός εγγράφου Word ως PDF είναι μια εντολή μίας γραμμής μόλις το περιεχόμενο είναι έτοιμο. Η σταθερά `SaveFormat.PDF` ενημερώνει το Aspose.Words να εκτελέσει τη μετατροπή.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Το παραγόμενο PDF περιέχει το ορθογώνιο με την ακριβή σκιά που ορίσατε. Το Aspose.Words διαχειρίζεται γραφικά vector, έτσι το μέγεθος του PDF παραμένει μέτριο.

## Εξαγωγή Word σε PNG

Η εξαγωγή σε PNG δημιουργεί μια raster εικόνα για κάθε σελίδα. Από προεπιλογή το Aspose.Words χρησιμοποιεί 96 DPI· μπορείτε να αυξήσετε αυτήν την τιμή για υψηλότερη ανάλυση παρέχοντας ένα αντικείμενο `PngSaveOptions`.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Όταν **εξάγετε Word σε PNG**, κάθε σελίδα αποθηκεύεται ως ξεχωριστό αρχείο PNG. Επειδή το παράδειγμα εγγράφου μας έχει μόνο μία σελίδα, εμφανίζεται μόνο ένα αρχείο PNG.

### Προαιρετικό: PNG υψηλότερης ανάλυσης

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Υψηλότερο DPI είναι χρήσιμο όταν το PNG θα χρησιμοποιηθεί στην εκτύπωση ή όταν χρειάζεστε μια καθαρή μικρογραφία.

## Πλήρες σενάριο – αντιγράψτε, επικολλήστε και εκτελέστε

Παρακάτω βρίσκεται το πλήρες, αυτόνομο σενάριο που υλοποιεί κάθε βήμα που περιγράφηκε παραπάνω. Αποθηκεύστε το ως `generate_assets.py` και εκτελέστε το από τη γραμμή εντολών.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Αναμενόμενη έξοδος

Η εκτέλεση του σεναρίου δημιουργεί τρία αρχεία:

* `output/output.pdf` – ένα PDF με ένα ορθογώνιο που ρίχνει μαύρη σκιά.  
* `output/output.png` – μια PNG απόδοση 96 DPI της ίδιας σελίδας.  
* `output/high_res_output.png` – μια PNG 300 DPI για υψηλότερη ποιότητα.  

Ανοίξτε οποιοδήποτε από τα αρχεία στον αγαπημένο σας προβολέα για να επαληθεύσετε ότι η σκιά εμφανίζεται ακριβώς όπως ορίστηκε.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

**Τι γίνεται αν ο φάκελος εξόδου δεν υπάρχει;**  
Το σενάριο καλεί `os.makedirs(output_dir, exist_ok=True)`, το οποίο δημιουργεί αυτόματα το φάκελο. Αυτό αποτρέπει ένα `FileNotFoundError` κατά τις λειτουργίες αποθήκευσης.

**Μπορώ να προσθέσω πολλαπλά σχήματα με διαφορετικές σκιές;**  
Ναι. Δημιουργήστε επιπλέον αντικείμενα `Shape`, διαμορφώστε κάθε ιδιότητα `shadow` ανεξάρτητα και εισάγετέ τα με `builder.insert_node(shape)` πριν την αποθήκευση.

**Θα διατηρηθεί η σκιά κατά τη μετατροπή σε άλλες μορφές raster (π.χ., JPEG);**  
Το Aspose.Words αποδίδει τη σκιά για όλες τις μορφές raster που υποστηρίζονται από το `SaveFormat`. Μπορείτε να αντικαταστήσετε το `aw.SaveFormat.PNG` με `aw.SaveFormat.JPEG` και η σκιά θα παραμείνει.

**Πώς διαφέρει αυτό από το “convert word to pdf”;**  
`convert word to pdf` είναι ουσιαστικά η ίδια λειτουργία που εκτελείται στο βήμα 4. Η ίδια κλήση `doc.save` με `SaveFormat.PDF` διαχειρίζεται τη μετατροπή εσωτερικά, διατηρώντας τη διάταξη, τις γραμματοσειρές και τα γραφικά όπως οι σκιές.

**Υπάρχει όριο στο μέγεθος του σχήματος;**  
Τα σχήματα μετρώνται σε points (1 pt ≈ 1/72 inch). Πολύ μεγάλες διαστάσεις μπορεί να αυξήσουν το μέγεθος του παραγόμενου αρχείου, αλλά το Aspose.Words δεν επιβάλλει σκληρό όριο. Προσαρμόστε τα επιχειρήματα `width` και `height` κατά τη δημιουργία του `aw.Shape` ώστε να ταιριάζουν στη διάταξή σας.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να αποθηκεύσετε PNG** από ένα έγγραφο Word ενώ επίσης έχετε μάθει να **προσθέτετε σκιά σε σχήμα**, **αποθηκεύετε το έγγραφο ως PDF**, και **εξάγετε Word σε PNG** χρησιμοποιώντας το Aspose.Words for Python. Το πλήρες σενάριο δείχνει ένα καθαρό, επαναλαμβανόμενο πρότυπο που μπορείτε να προσαρμόσετε για μεγαλύτερα έγγραφα, πολλαπλές σελίδες ή πιο σύνθετα γραφικά εφέ.

Τα επόμενα βήματα θα μπορούσαν να περιλαμβάνουν:

* Πειραματισμός με άλλες τιμές `ShapeType` (ellipse, cloud, κ.λπ.).  
* Using `

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετικότατα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}