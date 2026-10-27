---
category: general
date: 2026-10-16
description: Δημιουργήστε ένα κενό έγγραφο Word, εισάγετε σχήμα στο Word, προσθέστε
  εξωτερική σκιά και αποθηκεύστε το ως PDF χρησιμοποιώντας Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: el
lastmod: 2026-10-16
og_description: Δημιουργήστε ένα κενό έγγραφο Word με σχήμα εξωτερικής σκιάς χρησιμοποιώντας
  το Aspose.Words για Python. Αυτός ο οδηγός δείχνει πώς να εισάγετε το σχήμα, να
  εφαρμόσετε τη σκιά και να αποθηκεύσετε το αρχείο ως PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Δημιουργήστε κενό έγγραφο Word με σκιά σχήματος – Οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Δημιουργία κενού εγγράφου Word με σχήμα με σκιά σε Python
url: /el/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word με σχήμα σκιάς σε Python

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο Word** και να προσθέσετε ένα προσαρμοσμένο γραφικό, αυτός ο οδηγός σας καλύπτει. Θα σας καθοδηγήσουμε πώς να **εισάγετε σχήμα στο Word**, να εφαρμόσετε ένα **σχήμα εξωτερικής σκιάς**, και τελικά **να αποθηκεύσετε ως PDF χρησιμοποιώντας Python**.

Θα μάθετε πώς να ρυθμίσετε το Aspose.Words for Python, να δημιουργήσετε ένα ορθογώνιο, να μορφοποιήσετε τη σκιά του και να δημιουργήσετε ένα PDF που διατηρεί το οπτικό εφέ. Δεν απαιτείται προηγούμενη εμπειρία με το Aspose API, αλλά θα πρέπει να έχετε βασικές γνώσεις Python και μια λειτουργική εγκατάσταση του Python 3.10 ή νεότερης έκδοσης.

## Προαπαιτούμενα

* Python 3.10 ή νεότερη εγκατεστημένη.
* Ένα ενεργό άδεια Aspose.Words for Python (μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση).
* `pip` πρόσβαση για εγκατάσταση του πακέτου `aspose-words`.
* Δικαίωμα εγγραφής στον φάκελο όπου θα αποθηκευτεί το PDF.

Μπορείτε να εγκαταστήσετε τη βιβλιοθήκη με μια εντολή:

```bash
pip install aspose-words
```

## Δημιουργία κενής εγγράφου Word – ρύθμιση περιβάλλοντος

Το πρώτο βήμα είναι η δημιουργία ενός κενό αρχείου Word που θα λειτουργήσει ως καμβάς για το σχήμα.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` αντιπροσωπεύει ένα εντελώς κενό αρχείο Word. Χρησιμοποιώντας το `DocumentBuilder` αποκτάτε πρόσβαση σε μεθόδους όπως το `insert_shape`, την οποία θα χρησιμοποιήσουμε στο επόμενο βήμα.

## Εισαγωγή σχήματος στο Word και ορισμός διαστάσεων

Τώρα προσθέτουμε ένα ορθογώνιο που θα λάβει αργότερα εξωτερική σκιά. Το μέγεθος εκφράζεται σε points (1 pt ≈ 1/72 inch).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Η κλήση `insert_shape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να προσαρμόσετε περαιτέρω. Σε αυτό το σημείο το έγγραφο περιέχει ήδη ένα ορατό ορθογώνιο όταν ανοίγει στο Microsoft Word.

## Προσθήκη εξωτερικής σκιάς στο σχήμα – προσαρμογή του εφέ

Το Aspose.Words παρέχει μια κλάση `ShadowEffect` για τον ορισμό ιδιοτήτων σκιάς όπως το στυλ, η θολότητα, η απόσταση και το χρώμα.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Ορίζοντας το `style` σε `OUTER` εξασφαλίζει ότι η σκιά εμφανίζεται έξω από το περίγραμμα του ορθογωνίου, δίνοντας μια διακριτική 3‑Δ όψη. Μπορείτε να πειραματιστείτε με το `blur` και το `distance` για να πετύχετε πιο σφιχτή ή πιο διασκορπισμένη σκιά.

## Αποθήκευση ως PDF με Python – ολοκλήρωση του εγγράφου

Αφού μορφοποιήσετε το σχήμα, το έγγραφο μπορεί να αποθηκευτεί απευθείας ως PDF. Το Aspose.Words διαχειρίζεται τη μετατροπή εσωτερικά, διατηρώντας το εφέ της σκιάς.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Όταν ανοίξετε το `shape_with_shadow.pdf` σε οποιονδήποτε προβολέα PDF, θα δείτε το ορθογώνιο με την εξωτερική σκιά ακριβώς όπως εμφανιζόταν στο Word.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες script που συνδυάζει όλα τα βήματα. Αντιγράψτε το σε ένα αρχείο με όνομα `create_word_with_shadow.py` και εκτελέστε το.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Αναμενόμενο αποτέλεσμα**

Η εκτέλεση του script εκτυπώνει μια γραμμή επιβεβαίωσης, π.χ.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Ανοίγοντας το παραγόμενο PDF εμφανίζεται μια μονή σελίδα που περιέχει ένα ορθογώνιο 200 pt × 100 pt με μια ήπια μαύρη εξωτερική σκιά.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

* **Αλλαγή χρώματος σκιάς** – Αντικαταστήστε το `aw.Color.black` με οποιαδήποτε άλλη τιμή `aw.Color`, όπως `aw.Color.red` ή `aw.Color.from_argb(255, 0, 120, 215)`.
* **Χρήση διαφορετικού σχήματος** – Αλλάξτε το `aw.drawing.ShapeType.RECTANGLE` σε `OVAL`, `DIAMOND`, ή οποιαδήποτε υποστηριζόμενη τιμή enum.
* **Αποθήκευση ως DOCX αντί για PDF** – Καλέστε `doc.save("output/shape.docx")` για να διατηρήσετε τη μορφή Word.
* **Πολλαπλά σχήματα** – Δημιουργήστε επιπλέον σχήματα καλώντας ξανά το `builder.insert_shape`; κάθε σχήμα μπορεί να έχει το δικό του `ShadowEffect`.

**Συμβουλή:** Εάν χρειάζεται να τοποθετήσετε το σχήμα σε συγκεκριμένη θέση, ορίστε `rectangle.left` και `rectangle.top` μετά την εισαγωγή. Αυτό σας δίνει έλεγχο pixel‑perfect στην τοποθέτηση.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο Word**, **εισάγετε σχήμα στο Word**, **προσθέσετε εξωτερική σκιά στο σχήμα**, και **αποθηκεύσετε ως PDF χρησιμοποιώντας Python**. Το πλήρες παράδειγμα κώδικα δείχνει τη διαδικασία από την αρχή μέχρι το τέλος, και οι εξηγήσεις διευκρινίζουν γιατί κάθε κλήση API είναι απαραίτητη.

Από εδώ μπορείτε να εξερευνήσετε πιο προχωρημένες επιλογές μορφοποίησης, να προσθέσετε κείμενο μέσα στο σχήμα, ή να συνδυάσετε πολλαπλά σχήματα για τη δημιουργία σύνθετων διαγραμμάτων. Πειραματιστείτε με διαφορετικές παραμέτρους σκιάς για να ταιριάζουν με τη οπτική γλώσσα της μάρκας σας, και ενσωματώστε αυτήν την προσέγγιση σε μεγαλύτερους σωλήνες δημιουργίας εγγράφων.

Καλό κώδικα!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία σχήματος ορθογωνίου, προσθήκη σκιάς & αποθήκευση PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Δημιουργία PDF από Word – Πλήρης Οδηγός Python με Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Προσθήκη Σκιάς σε Σχήμα στο Word με Aspose.Words – Βήμα‑Βήμα](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}