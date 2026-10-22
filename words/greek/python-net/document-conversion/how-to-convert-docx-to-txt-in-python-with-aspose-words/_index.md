---
category: general
date: 2026-09-27
description: Μετατρέψτε docx σε txt σε Python χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να φορτώνετε ένα έγγραφο Word, να ορίζετε κωδικοποίηση UTF‑8 και να εξάγετε
  το έγγραφο Word σε txt με λίγες γραμμές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to txt
- convert word to plain text
- save word as plain text
- export word document txt
- load word document python
language: el
lastmod: 2026-09-27
og_description: Μετατρέψτε docx σε txt σε Python με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να φορτώσετε ένα έγγραφο Word, να ρυθμίσετε την κωδικοποίηση και να
  αποθηκεύσετε το Word ως απλό κείμενο.
og_image_alt: Screenshot of Python code that converts a DOCX file to a TXT file
og_title: Μετατροπή docx σε txt με Python – οδηγός βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Convert docx to txt in Python using Aspose.Words. Learn to load a Word
    document, set UTF‑8 encoding, and export Word document txt in a few lines.
  headline: How to convert docx to txt in Python with Aspose.Words
  type: TechArticle
tags:
- Python
- Aspose.Words
- Document conversion
title: Πώς να μετατρέψετε docx σε txt στην Python με το Aspose.Words
url: /el/python/document-conversion/how-to-convert-docx-to-txt-in-python-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μετατρέψετε docx σε txt σε Python με Aspose.Words

Αν χρειάζεστε **γρήγορη μετατροπή docx σε txt**, αυτός ο οδηγός σας παρουσιάζει μια πλήρη λύση σε Python. Θα μάθετε πώς να **φορτώνετε word document python**, να ρυθμίσετε κωδικοποίηση UTF‑8 και να **εξάγετε word document txt** με λίγες μόνο γραμμές κώδικα.

Το tutorial καλύπτει όλα όσα χρειάζεστε για να εκτελέσετε τη μετατροπή σε οποιαδήποτε πλατφόρμα που υποστηρίζει Python 3. Στο τέλος του άρθρου θα μπορείτε να **αποθηκεύσετε word ως plain text** αξιόπιστα, ακόμη και όταν το πηγαίο έγγραφο περιέχει ειδικούς χαρακτήρες ή σύμβολα μη‑ASCII.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Python 3.8 ή νεότερη έκδοση εγκατεστημένη.
* Ένα ενεργό license του Aspose.Words for Python (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).
* Το πακέτο `aspose-words` εγκατεστημένο μέσω `pip install aspose-words`.
* Ένα αρχείο DOCX που θέλετε να μετατρέψετε (το παράδειγμα χρησιμοποιεί το `input.docx`).

> **Pro tip:** Κρατήστε το αρχείο license (`Aspose.Words.lic`) στον ίδιο φάκελο με το script σας ή ορίστε ρητά τη διαδρομή του `Aspose.Words.License` για να αποφύγετε υδατογραφήματα λειτουργίας σε δοκιμαστική λειτουργία.

## Εγκατάσταση Aspose.Words

Εκτελέστε την παρακάτω εντολή στο τερματικό ή στο command prompt σας:

```bash
pip install aspose-words
```

Το πακέτο περιλαμβάνει το namespace `aw` που χρησιμοποιείται σε όλα τα παραδείγματα κώδικα.

## Βήμα 1 – Φόρτωση του εγγράφου Word (convert docx to txt)

Η πρώτη ενέργεια είναι η ανάγνωση του αρχείου DOCX σε ένα αντικείμενο `aw.Document`. Αυτό το βήμα αντιστοιχεί στην απαίτηση **load word document python**.

```python
import aspose.words as aw

# Load the source DOCX file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη που το Aspose.Words μπορεί να επεξεργαστεί, ανεξάρτητα από την αρχική μορφή αρχείου.

## Βήμα 2 – Ρύθμιση επιλογών αποθήκευσης TXT (convert word to plain text)

Το Aspose.Words παρέχει το `TxtSaveOptions` για να ελέγξετε πώς δημιουργείται η έξοδος plain‑text. Ορίζοντας την ιδιότητα `encoding` σε `"utf-8"` διασφαλίζετε ότι όλοι οι χαρακτήρες Unicode διατηρούνται.

```python
# Create TXT save options and set UTF‑8 encoding
txt_options = aw.saving.TxtSaveOptions()
txt_options.encoding = "utf-8"
```

*Γιατί είναι σημαντικό*: Χωρίς ρητή κωδικοποίηση, η προεπιλεγμένη κωδικοσελίδα του συστήματος μπορεί να αντικαταστήσει χαρακτήρες μη‑ASCII με ερωτηματικά. Η UTF‑8 είναι η πιο ασφαλής επιλογή για πολυγλωσσικά έγγραφα.

## Βήμα 3 – Αποθήκευση του εγγράφου ως plain text (save word as plain text)

Τώρα γράψτε το έγγραφο σε ένα αρχείο `.txt` χρησιμοποιώντας τις παραπάνω επιλογές.

```python
# Export the document to a plain‑text file
output_path = "YOUR_DIRECTORY/out.txt"
doc.save(output_path, txt_options)
print(f"Document exported successfully to {output_path}")
```

Το παραγόμενο αρχείο `out.txt` περιέχει μόνο το κειμενικό περιεχόμενο του `input.docx`, με αλλαγές γραμμής που ταιριάζουν στη δομή παραγράφων του αρχικού εγγράφου.

### Αναμενόμενη έξοδος

Αν το `input.docx` περιέχει την πρόταση:

> **“Hello, world! Привет мир!”**

το παραγόμενο `out.txt` θα εμφανίσει:

```
Hello, world! Привет мир!
```

Όλοι οι χαρακτήρες παραμένουν αμετάβλητοι επειδή εφαρμόστηκε κωδικοποίηση UTF‑8.

## Διαχείριση κοινών περιπτώσεων

| Κατάσταση | Προτεινόμενη προσέγγιση |
|-----------|------------------------|
| **Το έγγραφο περιέχει πίνακες** | Το Aspose.Words μετατρέπει τα κελιά των πινάκων σε plain text χωρισμένα με tabs. Αν χρειάζεστε προσαρμοσμένο διαχωριστικό, ορίστε το `txt_options.table_cell_separator` ανάλογα. |
| **Μεγάλα αρχεία (≥ 100 MB)** | Χρησιμοποιήστε streaming του εγγράφου για να αποφύγετε υψηλή κατανάλωση μνήμης: χρησιμοποιήστε `doc.save(output_stream, txt_options)` όπου το `output_stream` είναι αντικείμενο αρχείου ανοιγμένο σε binary mode. |
| **Απουσία γραμματοσειρών** | Εγκαταστήστε τις απαιτούμενες γραμματοσειρές στο σύστημα ή ενσωματώστε τις στο DOCX πριν τη μετατροπή. Η έλλειψη γραμματοσειρών επηρεάζει μόνο την οπτική απόδοση, όχι την εξαγωγή plain‑text. |
| **DOCX με κωδικό πρόσβασης** | Παρέχετε τον κωδικό κατά τη φόρτωση: `doc = aw.Document("secure.docx", aw.LoadOptions(password="MySecret"))`. |

## Πλήρες script – έτοιμο για εκτέλεση

Αποθηκεύστε τον παρακάτω κώδικα ως `convert_docx_to_txt.py` και τρέξτε τον με `python convert_docx_to_txt.py`.

```python
import aspose.words as aw
import os

def convert_docx_to_txt(input_path: str, output_path: str, encoding: str = "utf-8") -> None:
    """
    Converts a DOCX file to a TXT file using Aspose.Words.

    Args:
        input_path: Path to the source .docx file.
        output_path: Desired path for the resulting .txt file.
        encoding: Text encoding for the output file (default UTF‑8).
    """
    if not os.path.isfile(input_path):
        raise FileNotFoundError(f"Input file not found: {input_path}")

    # Load the Word document (load word document python)
    document = aw.Document(input_path)

    # Configure TXT save options (convert word to plain text)
    txt_options = aw.saving.TxtSaveOptions()
    txt_options.encoding = encoding

    # Save as plain‑text (save word as plain text)
    document.save(output_path, txt_options)
    print(f"Conversion complete: {output_path}")

if __name__ == "__main__":
    INPUT_FILE = "YOUR_DIRECTORY/input.docx"
    OUTPUT_FILE = "YOUR_DIRECTORY/out.txt"
    convert_docx_to_txt(INPUT_FILE, OUTPUT_FILE)
```

Η εκτέλεση του script εκτυπώνει μια γραμμή επιβεβαίωσης και δημιουργεί το `out.txt` στον καθορισμένο φάκελο.

## Επαλήθευση του αποτελέσματος

Μετά την εκτέλεση, ανοίξτε το `out.txt` σε οποιονδήποτε επεξεργαστή κειμένου (π.χ. VS Code, Notepad++) και βεβαιωθείτε ότι το περιεχόμενο ταιριάζει με το αρχικό κείμενο του DOCX. Αν δείτε παραμορφωμένους χαρακτήρες, ελέγξτε ξανά ότι το `txt_options.encoding` είναι ορισμένο σε `"utf-8"`.

## Επόμενα βήματα και συναφή θέματα

* **Convert docx to pdf** – χρησιμοποιήστε `aw.saving.PdfSaveOptions` για εξαγωγή PDF υψηλής πιστότητας.
* **Εξαγωγή εικόνων από έγγραφο Word** – εξερευνήστε το `aw.NodeType.SHAPE` και την κλάση `Shape`.
* **Batch conversion** – επαναλάβετε τη διαδικασία για όλα τα αρχεία DOCX σε έναν φάκελο, καλώντας τη συνάρτηση `convert_docx_to_txt` για κάθε αρχείο.
* **Προχωρημένη κωδικοποίηση** – πειραματιστείτε με το `txt_options.add_bidi_marks` όταν επεξεργάζεστε σενάρια δεξιά‑προς‑αριστερά.

Αποκτώντας εξοικείωση με τα παραπάνω βήματα, μπορείτε να **εξάγετε word document txt** σε οποιοδήποτε pipeline αυτοματοποίησης, είτε δημιουργείτε εργαλείο γραμμής εντολών, ενσωματώνετε σε web service, είτε επεξεργάζεστε έγγραφα στο cloud.

---


## Τι πρέπει να μάθετε στη συνέχεια;


Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να εξοικειωθείτε με επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Convert docx to txt – Complete Guide to Saving Word as Plain Text](/words/english/net/programming-with-txtsaveoptions/convert-docx-to-txt-complete-guide-to-saving-word-as-plain-t/)
- [Aspose.Words – Save docx as txt and Export Word Equations as LaTeX – Complete Guide](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [Word to PDF Tutorial: Convert DOCX to PDF with Aspose.Words](/words/english/net/basic-conversions/word-to-pdf-tutorial-convert-docx-to-pdf-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}