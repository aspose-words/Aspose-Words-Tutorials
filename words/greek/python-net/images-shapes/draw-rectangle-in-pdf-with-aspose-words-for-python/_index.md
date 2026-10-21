---
category: general
date: 2026-08-07
description: Σχεδιάστε ένα ορθογώνιο σε PDF χρησιμοποιώντας το Aspose.Words για Python
  και μάθετε πώς να προσθέσετε σκιά σε σχήμα, να ρυθμίσετε τη σκιά του σχήματος και
  να αποθηκεύσετε το έγγραφο ως PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: el
lastmod: 2026-08-07
og_description: Σχεδιάστε ορθογώνιο σε PDF με το Aspose.Words για Python. Αυτό το
  σεμινάριο δείχνει πώς να προσθέσετε σκιά σε σχήμα, να διαμορφώσετε τη σκιά του σχήματος
  και να αποθηκεύσετε το έγγραφο ως PDF για επαγγελματική δημιουργία εγγράφων.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Σχεδίαση ορθογωνίου σε PDF με το Aspose.Words για Python – οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Σχεδίαση ορθογωνίου σε PDF με Aspose.Words για Python
url: /el/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Σχεδίαση ορθογωνίου σε PDF με το Aspose.Words για Python

Αν χρειάζεστε να **draw rectangle in PDF** ενώ εργάζεστε με Python, αυτός ο οδηγός σας παρέχει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε ακριβώς πώς να **add shadow to shape**, να ρυθμίσετε αυτήν τη σκιά, και τελικά να **save document as PDF** για διανομή ή αρχειοθέτηση.

Η δημιουργία ενός σκιασμένου ορθογωνίου είναι μια κοινή απαίτηση για αναφορές, τιμολόγια ή οπτικές σημειώσεις. Στο τέλος αυτού του οδηγού θα έχετε ένα μόνο script που παράγει ένα PDF που περιέχει ένα ορθογώνιο με ρεαλιστική σκιά, και θα κατανοήσετε πώς να ρυθμίσετε το μέγεθος, το χρώμα και την απόσταση για να ταιριάζει σε οποιοδήποτε σχέδιο.

## Προαπαιτούμενα

* Python 3.8+ εγκατεστημένο.
* Το πακέτο Aspose.Words for Python via .NET (`aspose-words`) – εγκαταστήστε το με:

```bash
pip install aspose-words
```

* Δικαίωμα εγγραφής στον φάκελο όπου σκοπεύετε να αποθηκεύσετε το PDF.

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· το Aspose.Words διαχειρίζεται τη δημιουργία σχήματος, τη ρύθμιση σκιάς και την εξαγωγή PDF εσωτερικά.

## Βήμα 1: Δημιουργία νέου κεντρικού εγγράφου (draw rectangle in PDF – initialize)

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο PDF και παρέχει ένα κοντέινερ για ενότητες, παραγράφους και σχήματα.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Γιατί είναι σημαντικό:** Το Aspose.Words αντιμετωπίζει τη δημιουργία PDF ως μετατροπή από μοντέλο εγγράφου Word, έτσι ξεκινάμε με ένα `Document` παρόλο που το τελικό αποτέλεσμα είναι PDF.

## Βήμα 2: Εισαγωγή σχήματος ορθογωνίου στο σώμα του εγγράφου

Ένα ορθογώνιο είναι ένας συγκεκριμένος `ShapeType`. Το προσθέτουμε στο σώμα της πρώτης ενότητας, το οποίο αυτόματα δημιουργεί μια νέα σελίδα όταν αποθηκευτεί ως PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Εξήγηση:** Οι ιδιότητες `width` και `height` ελέγχουν το οπτικό μέγεθος του σχήματος στο PDF. Η προσθήκη κειμένου κάνει το ορθογώνιο πιο εύκολο να επαληθευτεί κατά τη δοκιμή.

## Βήμα 3: Προσθήκη σκιάς στο σχήμα – ενεργοποίηση και προσαρμογή

Τώρα ενεργοποιούμε το εφέ σκιάς και ρυθμίζουμε λεπτομερώς την εμφάνισή της. Εδώ είναι που η λέξη-κλειδί **add shadow to shape** έρχεται σε δράση.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Γιατί να ρυθμίσετε τη σκιά του σχήματος;** Η ρύθμιση των `blur`, `distance` και `angle` σας επιτρέπει να προσομοιώσετε ρεαλιστικό φωτισμό, κάτι που βελτιώνει την αναγνωσιμότητα και την οπτική ιεραρχία στα παραγόμενα PDF.

## Βήμα 4: Αποθήκευση εγγράφου ως PDF – τελικό αποτέλεσμα

Με το ορθογώνιο και τη σκιά του ορισμένα, το τελευταίο βήμα είναι η εξαγωγή του εγγράφου Word σε PDF. Αυτό ικανοποιεί την απαίτηση **save document as pdf**.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Όταν ανοίξετε το `shadow_rectangle.pdf`, θα δείτε μια μοναδική σελίδα που περιέχει ένα γκρι‑περιγράμματα ορθογώνιο με τίτλο “Shadow demo” και μια καθαρή, διαγώνια σκιά.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο PDF με όνομα `shadow_rectangle.pdf`.
* Μία σελίδα με ένα ορθογώνιο 200 pt × 100 pt.
* Μια ορατή σκιά με μετατόπιση 5 pt σε γωνία 45°, θολή κατά 8 pt.

## Βήμα 5: Εξερεύνηση παραλλαγών και ακραίων περιπτώσεων (προαιρετικό)

Παρακάτω είναι κοινές προσαρμογές που μπορεί να χρειαστείτε σε πραγματικά έργα:

| Παραλλαγή | Κώδικας | Πότε να χρησιμοποιηθεί |
|-----------|--------------|-------------|
| **Διαφορετικός τύπος σχήματος** (π.χ., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | Για στρογγυλεμένα γραφικά ή εμβλήματα |
| **Προσαρμοσμένο χρώμα σκιάς** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Όταν απαιτείται γκρι ή σκιά συγκεκριμένης μάρκας |
| **Πολλαπλά σχήματα** | Repeat the shape‑creation block and adjust `left`/`top` properties | Για τη δημιουργία σύνθετων διαγραμμάτων |
| **Χωρίς κείμενο μέσα στο σχήμα** | Omit `rectangle.text = "..."` | Όταν το σχήμα είναι μόνο διακοσμητικό |
| **Έξοδος υψηλότερης DPI** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | Για PDF έτοιμα για εκτύπωση |

**Pro tip:** Πάντα ορίστε `shadow.visible = True` πριν ρυθμίσετε άλλες ιδιότητες· διαφορετικά οι αλλαγές αγνοούνται σιωπηρά.

## Πλήρες script – αντιγράψτε, επικολλήστε και εκτελέστε

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Εκτελέστε το script από το τερματικό ή το IDE σας. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή φακέλου, όπως `"/tmp"` ή `"C:\\Users\\Me\\Documents"`.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **draw rectangle in PDF** χρησιμοποιώντας το Aspose.Words for Python, **add shadow to shape**, **configure shape shadow**, και **save document as PDF**. Το πλήρες παράδειγμα δείχνει κάθε βήμα από τη δημιουργία του εγγράφου μέχρι την τελική εξαγωγή, και οι προαιρετικές παραλλαγές δείχνουν πώς να προσαρμόσετε τον κώδικα για πιο σύνθετα σενάρια.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη άλλων τύπων σχήματος (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Εφαρμογή διαβαθμισμένων γεμισμάτων ή περιγραμμάτων για βελτίωση της οπτικής ελκυστικότητας.
* Χρήση του `PdfSaveOptions` για ενσωμάτωση γραμματοσειρών ή έλεγχο συμπίεσης εικόνων.

Μη διστάσετε να πειραματιστείτε με τις παραμέτρους ώστε να ταιριάζουν με την επωνυμία ή τις οδηγίες σχεδίασής σας. Καλή δημιουργία PDF!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}