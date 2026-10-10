---
category: general
date: 2026-10-07
description: Μάθετε πώς να αποθηκεύετε ένα έγγραφο ως PDF προσθέτοντας ένα σχήμα ορθογωνίου
  και προσαρμοσμένη σκιά χρησιμοποιώντας το Aspose.Words για Python. Περιλαμβάνεται
  κώδικας βήμα‑προς‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: el
lastmod: 2026-10-07
og_description: Αποθηκεύστε το έγγραφο ως PDF με προσαρμοσμένο σχήμα ορθογωνίου χρησιμοποιώντας
  το Aspose.Words για Python. Ακολουθήστε το πλήρες παράδειγμα για να σχεδιάσετε,
  να μορφοποιήσετε και να εξάγετε το Word σε PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Αποθήκευση εγγράφου ως PDF με σχήμα ορθογωνίου – πλήρης οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Πώς να αποθηκεύσετε ένα έγγραφο ως PDF με προσαρμοσμένο σχήμα ορθογωνίου στην
  Python
url: /el/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε το έγγραφο ως PDF με προσαρμοσμένο σχήμα ορθογωνίου σε Python

Αν χρειάζεστε **αποθήκευση εγγράφου ως PDF** ενώ προσθέτετε προσαρμοσμένα γραφικά, αυτός ο οδηγός σας δείχνει πώς. Θα περάσουμε από τη δημιουργία ενός κεντρικού αρχείου Word, **σχεδίαση σχήματος ορθογωνίου**, ορισμό του μεγέθους του, εφαρμογή ορατής σκιάς και τέλος **εξαγωγή Word σε PDF** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Python.

Θα ολοκληρώσετε με ένα PDF που περιέχει ένα τέλεια τοποθετημένο ορθογώνιο, έτοιμο για αναφορές, τιμολόγια ή οποιοδήποτε σενάριο αυτοματοποίησης εγγράφων. Δεν απαιτούνται εξωτερικά εργαλεία — μόνο Python και το πακέτο Aspose.Words.

## Τι θα χρειαστείτε

| Απαίτηση | Γιατί είναι σημαντικό |
|----------|------------------------|
| Python 3.8+ | Το Aspose.Words for Python API στοχεύει σε σύγχρονους διερμηνείς. |
| Πακέτο `aspose-words` (`pip install aspose-words`) | Παρέχει το χώρο ονομάτων `aw` που χρησιμοποιείται στα παραδείγματα κώδικα. |
| Βασική εξοικείωση με Python και αντικειμενοστραφή προγραμματισμό | Το tutorial χειρίζεται αντικείμενα όπως `Document` και `Shape`. |
| Δικαίωμα εγγραφής σε φάκελο όπου θα αποθηκευτεί το PDF | Το βήμα **αποθήκευσης εγγράφου ως pdf** γράφει ένα αρχείο στο δίσκο. |

> **Pro tip:** Χρησιμοποιήστε ένα εικονικό περιβάλλον (`python -m venv venv`) για να διατηρήσετε τις εξαρτήσεις απομονωμένες.

## Πώς να αποθηκεύσετε το έγγραφο ως PDF με σχήμα ορθογωνίου

Παρακάτω υπάρχει ένα πλήρες, εκτελέσιμο παράδειγμα. Κάθε βήμα εξηγείται ώστε να καταλάβετε **γιατί** κάνουμε την ενέργεια, όχι μόνο **τι** κάνει ο κώδικας.

### Βήμα 1: Αρχικοποίηση νέου κεντρικού εγγράφου

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Η δημιουργία ενός φρέσκου αντικειμένου `Document` σας δίνει μια καθαρή συλλογή σελίδων. Μπορείτε επίσης να φορτώσετε ένα υπάρχον *.docx* αν θέλετε αργότερα **να εξάγετε Word σε PDF**, αλλά η εκκίνηση από το μηδέν κρατά το παράδειγμα εστιασμένο.

### Βήμα 2: Προσθήκη σχήματος ορθογωνίου στο έγγραφο

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Το βήμα `add rectangle shape` χρησιμοποιεί `ShapeType.RECTANGLE`. Προσθέτοντας το σχήμα σε μια παράγραφο, το Aspose.Words ξέρει πού να το αποδώσει στο τελικό PDF.

### Βήμα 3: Ορισμός διαστάσεων ορθογωνίου

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Ο καθορισμός ρητών **διαστάσεων ορθογωνίου** εξασφαλίζει ότι το σχήμα φαίνεται συνεπές σε όλες τις πλατφόρμες. Μπορείτε επίσης να χρησιμοποιήσετε βοηθητικές μεθόδους `convert_to_inches` αν προτιμάτε μονάδες ίντσας.

### Βήμα 4: (Προαιρετικό) Εφαρμογή ορατής προσαρμοσμένης σκιάς

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Μια σκιά κάνει το ορθογώνιο πιο εμφανές στο PDF. Η σημαία `shadow.visible` είναι απαραίτητη· χωρίς αυτήν οι άλλες ιδιότητες δεν έχουν αποτέλεσμα.

### Βήμα 5: Αποθήκευση εγγράφου ως PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Καλώντας `document.save` με επέκταση **.pdf** εκτελεί αυτόματα **save document as pdf** χρησιμοποιώντας τον ενσωματωμένο PDF renderer του Aspose.Words. Δεν απαιτούνται επιπλέον βήματα μετατροπής, γι' αυτό αυτή η μέθοδος είναι η προτεινόμενη για **export Word to PDF**.

> **Γιατί λειτουργεί:** Το Aspose.Words γράφει τη διάταξη του εγγράφου, συμπεριλαμβανομένου του ορθογωνίου και της σκιάς του, απευθείας στο ρεύμα PDF. Η διαδικασία είναι χωρίς απώλειες και διατηρεί την ποιότητα των διανυσματικών στοιχείων.

## Πλήρης κώδικας (μονόσεντρο script)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Η εκτέλεση αυτού του script παράγει το `shadow_rectangle.pdf` που φαίνεται ως εξής:

![Διάγραμμα του παραγόμενου PDF που δείχνει το σχήμα ορθογωνίου μετά την αποθήκευση εγγράφου ως pdf](placeholder-image.png)

*Το PDF περιέχει μία σελίδα με ένα ορθογώνιο με μαύρη σκιά, κεντραρισμένο στο έγγραφο.*

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|----------|
| **Μπορώ να τοποθετήσω το ορθογώνιο σε συγκεκριμένη θέση;** | Ναι. Ορίστε `rectangle.left` και `rectangle.top` (σε points) πριν την αποθήκευση. |
| **Τι γίνεται αν χρειαστώ πολλαπλά σχήματα;** | Δημιουργήστε επιπλέον αντικείμενα `Shape`, ρυθμίστε το καθένα και προσθέστε τα στην ίδια ή σε διαφορετικές παραγράφους. |
| **Επηρεάζει η σκιά το μέγεθος του PDF;** | Μόνο ελαφρώς· η σκιά αποθηκεύεται ως διανυσματικό μεταδεδομένο, όχι ως raster εικόνα. |
| **Μπορώ να το χρησιμοποιήσω για μετατροπή υπαρχόντων *.docx* αρχείων;** | Απόλυτα. Αντικαταστήστε το `aw.Document()` με `aw.Document("input.docx")` και τα υπόλοιπα βήματα παραμένουν αμετάβλητα. |
| **Υπάρχει τρόπος να αλλάξω το χρώμα γεμίσματος του ορθογωνίου;** | Ορίστε `rectangle.fill_color = aw.drawing.Color.light_blue` (ή οποιοδήποτε `Color` προτιμάτε). |

## Επόμενα βήματα

Τώρα που ξέρετε πώς να **αποθηκεύσετε το έγγραφο ως PDF** με προσαρμοσμένο ορθογώνιο, μπορείτε να εξερευνήσετε:

* **Export Word to PDF** με κεφαλίδες, υποσέλιδα και αριθμούς σελίδων.  
* **Προσθήκη άλλων αντικειμένων σχεδίασης** (`Ellipse`, `Polygon`) χρησιμοποιώντας την ίδια κλάση `Shape`.  
* **Μαζική επεξεργασία** ενός φακέλου αρχείων Word, εφαρμόζοντας την ίδια επικάλυψη ορθογωνίου σε καθένα.

Αυτές οι επεκτάσεις ακολουθούν το ίδιο μοτίβο: δημιουργήστε ένα σχήμα, ρυθμίστε τις ιδιότητές του και **save document as pdf**.

---

**Σύνοψη:** Αυτό το tutorial σας έδειξε πώς να **αποθηκεύσετε το έγγραφο ως PDF** ενώ **προσθέτετε σχήμα ορθογωνίου**, **ορίζετε διαστάσεις ορθογωνίου** και εφαρμόζετε προσαρμοσμένη σκιά χρησιμοποιώντας το Aspose.Words for Python. Το πλήρες script είναι έτοιμο για αντιγραφή, εκτέλεση και προσαρμογή στις δικές σας ροές αυτοματοποίησης εγγράφων. Καλή προγραμματιστική δουλειά!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Add rectangle to PDF with Aspose.Words – Step‑by‑Step Guide](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Save Document as PDF with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}