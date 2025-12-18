---
category: general
date: 2025-12-18
description: Αποθηκεύστε το Word ως PDF γρήγορα χρησιμοποιώντας το Aspose.Words για
  Python. Μάθετε πώς να μετατρέπετε το Word σε PDF, να εξάγετε αιωρούμενα σχήματα
  και να διαχειρίζεστε τη μετατροπή docx σε ένα ενιαίο σενάριο.
draft: false
keywords:
- save word as pdf
- convert word to pdf
- how to convert docx
- how to export shapes
- python word to pdf conversion
language: el
og_description: Αποθηκεύστε το Word ως PDF άμεσα. Αυτό το σεμινάριο δείχνει πώς να
  μετατρέψετε DOCX, να εξάγετε σχήματα και να εκτελέσετε μετατροπή Word σε PDF με
  Python χρησιμοποιώντας το Aspose.Words.
og_title: Αποθήκευση Word ως PDF – Πλήρες Μάθημα Python
tags:
- Aspose.Words
- PDF conversion
- Python
title: Αποθήκευση Word ως PDF με Python – Πλήρης Οδηγός για Εξαγωγή Σχημάτων και Μετατροπή
  DOCX
url: /greek/python/document-operations/save-word-as-pdf-with-python-full-guide-to-export-shapes-and/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Word ως PDF – Πλήρης Εγχειρίδιο Python

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε Word ως PDF** χωρίς να ανοίξετε το Microsoft Word; Ίσως αυτοματοποιείτε μια αλυσίδα αναφορών ή χρειάζεστε να επεξεργαστείτε μαζικά δεκάδες συμβόλαια. Τα καλά νέα είναι ότι δεν χρειάζεται να κοιτάζετε το UI—το Aspose.Words for Python μπορεί να κάνει τη βαριά δουλειά με λίγες γραμμές κώδικα.

Σε αυτόν τον οδηγό θα δείτε ακριβώς πώς να **μετατρέψετε Word σε PDF**, να εξάγετε πλωτά σχήματα ως ετικέτες inline και να αντιμετωπίσετε το συνηθισμένο πρόβλημα «πώς να εξάγετε σχήματα». Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση script που μετατρέπει οποιοδήποτε `.docx` σε καθαρό PDF, ακόμη και όταν το αρχείο προέλευσης περιέχει εικόνες, πλαίσια κειμένου ή WordArt.

---

![Διάγραμμα που απεικονίζει τη ροή εργασίας αποθήκευσης word ως pdf – φόρτωση docx, ρύθμιση επιλογών PDF, εξαγωγή σε PDF](image.png)

## Τι Θα Χρειαστεί

- **Python 3.8+** – οποιαδήποτε πρόσφατη έκδοση λειτουργεί· δοκιμάσαμε στην 3.11.  
- **Aspose.Words for Python via .NET** – εγκαταστήστε με `pip install aspose-words`.  
- Ένα δείγμα αρχείου **input.docx** που περιέχει τουλάχιστον ένα πλωτό σχήμα (π.χ. εικόνα ή πλαίσιο κειμένου).  
- Βασική εξοικείωση με scripts Python (δεν απαιτείται προχωρημένη γνώση).

Αυτό είναι όλο. Χωρίς εγκατάσταση Office, χωρίς COM interop, μόνο καθαρός κώδικας.

## Βήμα 1: Φόρτωση του Πηγαίου Εγγράφου Word

Πρώτα, πρέπει να φέρουμε το `.docx` στη μνήμη. Το Aspose.Words αντιμετωπίζει το έγγραφο ως γράφημα αντικειμένων, ώστε να μπορείτε να το επεξεργαστείτε πριν το αποθηκεύσετε.

```python
import aspose.words as aw

# Step 1 – Load the source Word document
# Replace "YOUR_DIRECTORY/input.docx" with the actual path to your file.
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Γιατί είναι σημαντικό:* Η φόρτωση του εγγράφου σας δίνει πρόσβαση σε κάθε κόμβο—παραγράφους, πίνακες και, το πιο σημαντικό για εμάς, **πλωτά σχήματα**. Αν παραλείψετε αυτό το βήμα, δεν θα έχετε ποτέ την ευκαιρία να ρυθμίσετε πώς αυτά τα σχήματα θα αποδοθούν στο PDF.

## Βήμα 2: Διαμόρφωση Επιλογών Αποθήκευσης PDF – Εξαγωγή Πλωτών Σχημάτων ως Ετικέτες Inline

Από προεπιλογή, το Aspose.Words προσπαθεί να διατηρήσει την ακριβή διάταξη των πλωτών αντικειμένων, κάτι που μερικές φορές μπορεί να προκαλέσει μετατοπίσεις στη διάταξη του PDF. Ορίζοντας `export_floating_shapes_as_inline_tag` εξαναγκάζει αυτά τα αντικείμενα να αντιμετωπίζονται ως στοιχεία inline, προσφέροντας πιο προβλέψιμο αποτέλεσμα.

```python
# Step 2 – Configure PDF save options
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
```

*Γιατί είναι σημαντικό:* Αν ρωτάτε **πώς να εξάγετε σχήματα** από ένα αρχείο Word, αυτή η σημαία είναι η απάντηση. Λέει στη μηχανή να τυλίξει κάθε πλωτό σχήμα σε μια κρυφή ετικέτα `<span>`, η οποία ο PDF renderer αντιμετωπίζει όπως το κανονικό ροή κειμένου. Το αποτέλεσμα; Καμία «ορφανή» εικόνα που να αιωρείται εκτός σελίδας.

### Πότε Μπορεί να Θέλετε να Διατηρήσετε την Προεπιλογή;

- Αν το έγγραφό σας εξαρτάται από ακριβή τοποθέτηση (π.χ. διάταξη φυλλαδίου), αφήστε τη σημαία `False`.  
- Για τις περισσότερες επιχειρηματικές αναφορές, τιμολόγια ή συμβόλαια, ορίζοντας την σε `True` εξαλείφει τις εκπλήξεις.

## Βήμα 3: Αποθήκευση του Εγγράφου ως PDF

Τώρα που οι επιλογές έχουν οριστεί, μπορούμε τελικά να **αποθηκεύσουμε Word ως PDF**. Η μέθοδος `save` παίρνει τη διαδρομή εξόδου και το αντικείμενο επιλογών που μόλις διαμορφώσαμε.

```python
# Step 3 – Save the document as a PDF using the configured options
# Replace "YOUR_DIRECTORY/output.pdf" with your desired output location.
document.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

Όταν το script ολοκληρωθεί, ελέγξτε το `output.pdf`. Θα πρέπει να δείτε το αρχικό κείμενο, τους πίνακες και τυχόν πλωτά σχήματα να αποδίδονται inline—ακριβώς όπως θα περιμένατε από μια καθαρή μετατροπή.

## Πλήρες, Έτοιμο‑για‑Εκτέλεση Script

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα αρχείο με όνομα `convert_docx_to_pdf.py`:

```python
import aspose.words as aw

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Convert a DOCX file to PDF while exporting floating shapes as inline tags.
    
    Parameters
    ----------
    input_path : str
        Full path to the source .docx file.
    output_path : str
        Desired path for the generated PDF.
    """
    # Load the Word document
    document = aw.Document(input_path)

    # Set PDF options – export floating shapes as inline tags
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True

    # Save as PDF
    document.save(output_path, pdf_options)

if __name__ == "__main__":
    # Example usage – adjust paths as needed
    convert_docx_to_pdf(
        input_path="YOUR_DIRECTORY/input.docx",
        output_path="YOUR_DIRECTORY/output.pdf"
    )
```

### Αναμενόμενο Αποτέλεσμα

Η εκτέλεση του script πρέπει να παραγάγει ένα PDF που:

1. Διατηρεί όλο το κείμενο, τις επικεφαλίδες και τους πίνακες.  
2. Εμφανίζει εικόνες ή πλαίσια κειμένου **inline** με τις γύρω παραγράφους.  
3. Ταιριάζει στενά με την αρχική διάταξη, χωρίς ανεπιθύμητα πλωτά αντικείμενα.

Μπορείτε να το επαληθεύσετε ανοίγοντας το PDF σε οποιονδήποτε προβολέα—Adobe Reader, Chrome ή ακόμη και σε εφαρμογή κινητού.

## Συχνές Παραλλαγές & Ακραίες Περιπτώσεις

### Μετατροπή Πολλών Αρχείων σε Φάκελο

Αν χρειάζεται να **μετατρέψετε word σε pdf** για ολόκληρο κατάλογο, τυλίξτε τη λειτουργία σε βρόχο:

```python
import os, glob

source_folder = "YOUR_DIRECTORY/docs"
target_folder = "YOUR_DIRECTORY/pdfs"
os.makedirs(target_folder, exist_ok=True)

for docx_path in glob.glob(os.path.join(source_folder, "*.docx")):
    pdf_name = os.path.splitext(os.path.basename(docx_path))[0] + ".pdf"
    pdf_path = os.path.join(target_folder, pdf_name)
    convert_docx_to_pdf(docx_path, pdf_path)
```

### Διαχείριση Εγγράφων με Κωδικό Πρόσβασης

Το Aspose.Words μπορεί να ανοίξει κρυπτογραφημένα αρχεία παρέχοντας κωδικό πρόσβασης:

```python
load_options = aw.loading.LoadOptions()
load_options.password = "mySecret"
protected_doc = aw.Document("protected.docx", load_options)
protected_doc.save("protected.pdf", pdf_options)
```

### Χρήση Διαφορετικού PDF Renderer

Μερικές φορές μπορεί να θέλετε υψηλότερη πιστότητα (π.χ. διατήρηση ακριβών μορφών γραμματοσειράς). Αλλάξτε τον renderer:

```python
pdf_options.pdf_rendering_options = aw.saving.PdfRenderingOptions()
pdf_options.pdf_rendering_options.use_emf_embedded_fonts = True
```

## Επαγγελματικές Συμβουλές & Πιθανά Προβλήματα

- **Pro tip:** Δοκιμάστε πάντα με ένα έγγραφο που περιέχει τουλάχιστον ένα πλωτό σχήμα. Είναι ο πιο γρήγορος τρόπος να επιβεβαιώσετε ότι η σημαία `export_floating_shapes_as_inline_tag` λειτουργεί σωστά.  
- **Watch out for:** Πολύ μεγάλες εικόνες μπορούν να αυξήσουν το μέγεθος του PDF. Σκεφτείτε να μειώσετε την ανάλυση τους πριν τη μετατροπή χρησιμοποιώντας `ImageSaveOptions`.  
- **Version check:** Το API που εμφανίζεται λειτουργεί με Aspose.Words 23.9 και νεότερες εκδόσεις. Αν χρησιμοποιείτε παλαιότερη έκδοση, το όνομα της ιδιότητας μπορεί να είναι `ExportFloatingShapesAsInlineTag` (κεφαλαίο “E”).

## Συμπέρασμα

Τώρα έχετε μια σταθερή, ολοκληρωμένη λύση για **αποθήκευση Word ως PDF** χρησιμοποιώντας Python. Φορτώνοντας το έγγραφο, ρυθμίζοντας τις επιλογές αποθήκευσης PDF και καλώντας τη `save`, έχετε κατακτήσει τον πυρήνα της **python word to pdf conversion** ενώ έχετε μάθει και **πώς να εξάγετε σχήματα** σωστά.

Από εδώ μπορείτε:

- Να επεξεργαστείτε μαζικά χιλιάδες αρχεία,  
- Να ενσωματώσετε το script σε μια web υπηρεσία,  
- Να το επεκτείνετε για διαχείριση εγγράφων DOCX με κωδικό πρόσβασης, ή  
- Να μεταβείτε σε άλλη μορφή εξόδου όπως XPS ή HTML.

Δοκιμάστε το, προσαρμόστε τις επιλογές και αφήστε τον αυτοματισμό να αφαιρέσει το βαριά δουλειά από τη ροή εργασίας των εγγράφων σας. Καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}