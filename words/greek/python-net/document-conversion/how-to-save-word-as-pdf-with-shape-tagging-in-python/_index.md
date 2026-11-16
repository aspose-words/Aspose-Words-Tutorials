---
category: general
date: 2026-11-15
description: Αποθηκεύστε το Word ως PDF σε Python με τη χρήση του Aspose.Words, μάθετε
  πώς να εξάγετε σχήματα και να χαρακτηρίσετε τα αιωρούμενα σχήματα ως ενσωματωμένα
  για ακριβή μετατροπή docx σε PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: el
lastmod: 2026-11-15
og_description: Αποθήκευση του Word ως PDF σε Python με τη χρήση του Aspose.Words.
  Αυτός ο οδηγός δείχνει πώς να εξάγετε σχήματα, να επισημάνετε τα αιωρούμενα σχήματα
  ως ενσωματωμένα και να μετατρέψετε αξιόπιστα το docx σε PDF.
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: Αποθήκευση Word ως PDF με ετικετοποίηση σχημάτων σε Python – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: Πώς να αποθηκεύσετε το Word ως PDF με ετικετοποίηση σχήματος σε Python
url: /el/python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε το Word ως PDF με ετικετοποίηση σχήματος σε Python

Αν χρειάζεστε να **αποθηκεύσετε το Word ως PDF** και να διατηρήσετε κάθε σχέδιο ακριβώς εκεί που ανήκει, αυτός ο οδηγός σας δείχνει έναν αξιόπιστο τρόπο για να το κάνετε με το Aspose.Words for Python. Θα μάθετε επίσης **πώς να εξάγετε σχήματα** και **πώς να ετικετοποιήσετε σχήματα** ώστε τα αιωρούμενα αντικείμενα να γίνουν ενσωματωμένα στοιχεία κατά τη μετατροπή.

Σε αυτό το tutorial καλύπτουμε:

* Μετατροπή αρχείου DOCX σε PDF (`convert docx to pdf`)  
* Εξαγωγή αιωρούμενων σχημάτων ως ενσωματωμένες ετικέτες (`how to export shapes`)  
* Ετικετοποίηση σχημάτων κατά τη λειτουργία αποθήκευσης PDF (`how to tag shapes`)  

Δεν απαιτούνται εξωτερικά εργαλεία—μόνο μερικές γραμμές κώδικα Python.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Εγκατεστημένο Python 3.8+  
* Ένα ενεργό άδεια Aspose.Words for Python (ή δωρεάν δοκιμή)  
* Το πακέτο `aspose-words` εγκατεστημένο (`pip install aspose-words`)  
* Ένα αρχείο DOCX (`input.docx`) που περιέχει αιωρούμενα σχήματα (εικόνες, πλαίσια κειμένου κ.λπ.)

## Βήμα 1: Εγκατάσταση και εισαγωγή του Aspose.Words

Πρώτα, προσθέστε τη βιβλιοθήκη στο περιβάλλον σας και εισάγετέ την στο script σας.

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*Γιατί;* Το module `aspose.words` παρέχει την κλάση `Document` και το `PdfSaveOptions` που χρειαζόμαστε για να ελέγξουμε τη διαχείριση σχημάτων.

## Βήμα 2: Φόρτωση του εγγράφου Word

Χρησιμοποιήστε τον κατασκευαστή `Document` για να διαβάσετε το αρχείο προέλευσης.

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

Αν το αρχείο δεν υπάρχει, το Aspose.Words εγείρει ένα `FileNotFoundError`. Τυλίξτε την κλήση σε ένα μπλοκ `try/except` για κώδικα παραγωγής.

## Βήμα 3: Διαμόρφωση επιλογών αποθήκευσης PDF – εξαγωγή και ετικετοποίηση σχημάτων

Το κλειδί για μια καθαρή μετατροπή είναι το αντικείμενο `PdfSaveOptions`. Ορίζοντας το `export_floating_shapes_as_inline_tag` σε `True` λέει στη μηχανή να αντιμετωπίζει τα αιωρούμενα σχέδια ως ενσωματωμένα στοιχεία, κάτι που εξαλείφει τις μετατοπίσεις διάταξης στο παραγόμενο PDF.

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*Γιατί;* Όταν το `export_floating_shapes_as_inline_tag` είναι `False` (η προεπιλογή), τα αιωρούμενα σχήματα διατηρούν τα αρχικά μεταδεδομένα θέσης, κάτι που μπορεί να τα κάνει να εμφανίζονται λανθασμένα στο PDF. Η ενεργοποίηση της ενσωματωμένης ετικέτας αναγκάζει το Aspose.Words να ενσωματώσει μια μικρή ετικέτα XML που ο PDF renderer ερμηνεύει ως ενσωματωμένο αντικείμενο, διατηρώντας την οπτική πιστότητα.

## Βήμα 4: Αποθήκευση του εγγράφου ως PDF

Τώρα γράψτε το αρχείο PDF χρησιμοποιώντας τις διαμορφωμένες επιλογές.

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

Μετά την εκτέλεση, το `output.pdf` περιέχει την αρχική διάταξη του Word με όλα τα αιωρούμενα σχήματα σωστά αποδομένα ως ενσωματωμένα στοιχεία.

## Βήμα 5: Επαλήθευση της μετατροπής (προαιρετικό)

Μπορείτε προγραμματιστικά να επαληθεύσετε ότι το PDF δημιουργήθηκε και περιέχει τουλάχιστον μία σελίδα:

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*Συμβουλή:* Χρησιμοποιήστε έναν προβολέα PDF για να ελέγξετε διπλά ότι οι εικόνες, τα πλαίσια κειμένου και οι επεξηγήσεις εμφανίζονται ακριβώς εκεί που ήταν στο αρχείο DOCX.

## Συχνές παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Τι να αλλάξετε |
|-----------|----------------|
| **Θέλετε να διατηρήσετε τα αιωρούμενα σχήματα ως αιωρούμενα** | Ορίστε `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **Μετατροπή πολλών αρχείων σε παρτίδα** | Επανάληψη πάνω σε λίστα διαδρομών αρχείων και επαναχρησιμοποίηση μιας μόνο στιγμής `PdfSaveOptions`. |
| **Θέλετε να ενσωματώσετε κωδικό πρόσβασης** | Χρησιμοποιήστε `pdf_opts.encrypt_options.password = "your‑password"` πριν καλέσετε `save`. |
| **Μεγάλα έγγραφα προκαλούν πίεση μνήμης** | Ενεργοποιήστε `pdf_opts.memory_optimization = True` για μείωση της χρήσης RAM. |

## Pro tip: διαχείριση ελλιπών γραμματοσειρών

Αν το αρχικό DOCX χρησιμοποιεί γραμματοσειρές που δεν είναι εγκατεστημένες στον διακομιστή, η απόδοση PDF μπορεί να επιστρέψει σε προεπιλεγμένη γραμματοσειρά. Καταχωρίστε τις ελλιπείς γραμματοσειρές με `FontSettings`:

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

Αυτό εξασφαλίζει ότι το PDF φαίνεται ταυτόσημο με το αρχικό αρχείο Word.

## Πλήρες εκτελέσιμο παράδειγμα

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

Η εκτέλεση του script παράγει το `output.pdf` με όλα τα αιωρούμενα σχήματα σωστά ετικετοποιημένα, παρέχοντάς σας ένα καθαρό αποτέλεσμα **save word as pdf**.

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποθηκεύσετε το Word ως PDF** σε Python ενώ ελέγχετε τη διαχείριση σχημάτων. Διαμορφώνοντας το `PdfSaveOptions.export_floating_shapes_as_inline_tag`, μπορείτε αξιόπιστα να **μετατρέψετε docx σε pdf**, να **εξάγετε σχήματα** ως ενσωματωμένες ετικέτες, και να απαντήσετε στο **πώς να ετικετοποιήσετε σχήματα** κατά τη μετατροπή.  

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη υδατογραφιών (`pdf_opts.add_watermark`) – μια φυσική επέκταση της προσαρμογής PDF.  
* Μετατροπή άλλων μορφών (HTML, EPUB) χρησιμοποιώντας το ίδιο μοτίβο `save`.  
* Αυτοματοποίηση παρτίδας μετατροπών για μεγάλα αποθετήρια εγγράφων.

Δοκιμάστε το script, πειραματιστείτε με τις προαιρετικές ρυθμίσεις, και ενσωματώστε το στη γραμμή επεξεργασίας εγγράφων σας σήμερα. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Αποθήκευση Word ως PDF – Μετατροπή Σχημάτων σε Inline με Aspose.Words](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [Πώς να αποθηκεύσετε το Word ως PDF με Aspose.Words for Python](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [Πώς να μετατρέψετε DOCX σε PDF σε Python χρησιμοποιώντας Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}