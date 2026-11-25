---
category: general
date: 2026-11-25
description: Μάθετε πώς να αποθηκεύσετε το docx ως pdf χρησιμοποιώντας το Aspose.Words,
  να μετατρέψετε το docx σε pdf και να εξάγετε τα αιωρούμενα σχήματα ως ενσωματωμένες
  ετικέτες σε ένα μόνο βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as pdf
- convert docx to pdf
- how to export shapes
- convert word to pdf
- aspose docx to pdf
language: el
lastmod: 2026-11-25
og_description: Αποθηκεύστε το docx ως pdf με το Aspose.Words, μετατρέψτε το docx
  σε pdf και μάθετε πώς να εξάγετε τα σχήματα ως ενσωματωμένες ετικέτες για τέλεια
  έξοδο PDF.
og_image_alt: Screenshot showing a DOCX file being saved as PDF with shapes preserved
og_title: Αποθήκευση docx ως pdf με το Aspose.Words – εξαγωγή σχημάτων σωστά
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  headline: How to save docx as pdf with Aspose.Words while exporting shapes
  type: TechArticle
- description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  name: How to save docx as pdf with Aspose.Words while exporting shapes
  steps:
  - name: Converting multiple DOCX files in a batch
    text: 'When you need to **convert docx to pdf** for many files, wrap the three
      steps in a loop:'
  - name: Dealing with very large documents
    text: For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF`
      (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance.
      These options do not affect shape export but improve compatibility with archival
      systems.
  - name: When shapes should remain floating
    text: If a specific document requires floating shapes to stay floating (e.g.,
      a design‑heavy brochure), set the flag to `False`. The PDF will then render
      shapes as separate drawing objects, which may be preferable for precise graphic
      positioning.
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- Word automation
title: Πώς να αποθηκεύσετε το docx ως pdf με το Aspose.Words κατά την εξαγωγή σχημάτων
url: /el/python/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-while-exporting-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε docx ως pdf με Aspose.Words ενώ εξάγετε σχήματα

Αν χρειάζεστε να **save docx as pdf** και να διατηρήσετε κάθε αιωρούμενο σχήμα ακριβώς εκεί που ανήκει, αυτός ο οδηγός σας δείχνει τη πλήρη διαδικασία. Στο τέλος του tutorial θα μπορείτε να μετατρέψετε ένα έγγραφο Word σε αρχείο PDF, να εξάγετε τα σχήματα σωστά και να καταλάβετε γιατί κάθε ρύθμιση έχει σημασία.

Η μετατροπή αρχείων Word σε PDF είναι μια κοινή απαίτηση για δημιουργία τιμολογίων, δημοσίευση αναφορών και αρχειοθέτηση εγγράφων. Αυτό το tutorial καλύπτει τη ροή εργασίας **convert docx to pdf**, εξηγεί **how to export shapes** ώστε να εμφανίζονται ενσωματωμένα, και επιδεικνύει τη λειτουργία **convert word to pdf** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από το πακέτο Aspose.Words for Python via .NET.

## Προαπαιτούμενα

* Python 3.9+ εγκατεστημένο στο μηχάνημα ανάπτυξής σας.  
* Το πακέτο `aspose-words` (εγκαταστάσιμο μέσω `pip install aspose-words`).  
* Ένα αρχείο DOCX που περιέχει αιωρούμενα σχήματα (π.χ., πλαίσια κειμένου, εικόνες ή SmartArt).  
* Δικαίωμα εγγραφής στον φάκελο εξόδου.

Όλες αυτές οι προαπαιτήσεις είναι ελεύθερης μορφής· το tutorial λειτουργεί σε Windows, macOS και Linux.

## Βήμα 1: Φόρτωση του πηγαίου εγγράφου

Η πρώτη ενέργεια είναι η φόρτωση του αρχείου DOCX σε ένα αντικείμενο `aw.Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το έγγραφο Word στη μνήμη, παρέχοντάς σας πρόσβαση στις ενότητες, τις παραγράφους και τα αντικείμενα σχεδίασης.

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

**Γιατί αυτό το βήμα είναι σημαντικό:**  
Η φόρτωση του αρχείου δημιουργεί ένα δομημένο μοντέλο αντικειμένων που μπορεί να χειριστεί το Aspose.Words. Χωρίς αυτό το μοντέλο η επακόλουθη μετατροπή σε PDF δεν θα είχε πηγή για ανάγνωση.

## Βήμα 2: Διαμόρφωση επιλογών αποθήκευσης PDF και ενεργοποίηση ενσωματωμένης εξαγωγής για αιωρούμενα σχήματα

Το Aspose.Words παρέχει μια κλάση `PdfSaveOptions` που σας επιτρέπει να ρυθμίσετε λεπτομερώς το PDF εξόδου. Η ιδιότητα `export_floating_shapes_as_inline_tag` ελέγχει αν τα αιωρούμενα σχήματα θα αποδοθούν ως ενσωματωμένες ετικέτες `<w:wrap>` (που ο renderer PDF θεωρεί ως μέρος της ροής κειμένου) ή ως ξεχωριστά αντικείμενα σχεδίασης.

```python
# Step 2: Create PDF save options and enable inline export for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
```

**Γιατί αυτή η ρύθμιση είναι σημαντική:**  
Όταν **how to export shapes** σωστά, αποφεύγετε το κοινό πρόβλημα όπου ένα σχήμα εξαφανίζεται ή μετακινείται σε απροσδόκητη θέση στο PDF. Ορίζοντας τη σημαία σε `True` λέει στον renderer να αντιμετωπίζει κάθε αιωρούμενο σχήμα σαν να ήταν ενσωματωμένο, διατηρώντας την πιστότητα της διάταξης. Αυτή είναι η προτεινόμενη προσέγγιση για τα περισσότερα επιχειρηματικά έγγραφα.

## Βήμα 3: Αποθήκευση του εγγράφου ως PDF χρησιμοποιώντας τις διαμορφωμένες επιλογές

Με το έγγραφο φορτωμένο και τις επιλογές αποθήκευσης προετοιμασμένες, μπορείτε τώρα να γράψετε το αρχείο PDF στον δίσκο.

```python
# Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**Γιατί αυτό το τελικό βήμα ολοκληρώνει τη ροή εργασίας:**  
Η κλήση του `doc.save` με το αντικείμενο `PdfSaveOptions` ενεργοποιεί την αλυσίδα μετατροπής. Το Aspose.Words διαβάζει τη δομή του DOCX, εφαρμόζει τον κανόνα ενσωματωμένων σχημάτων και γράφει ένα PDF που αντικατοπτρίζει την αρχική διάταξη. Μετά από αυτή την κλήση, το `output.pdf` περιέχει το ίδιο κείμενο, εικόνες και σχήματα με το αρχικό DOCX.

## Αναμενόμενο αποτέλεσμα

* Το `output.pdf` εμφανίζεται στον προορισμένο φάκελο.  
* Όλες οι παράγραφοι, πίνακες και αιωρούμενα σχήματα (πλαίσια κειμένου, εικόνες, SmartArt) τοποθετούνται ακριβώς όπως ήταν στο `input.docx`.  
* Το μέγεθος του αρχείου είναι συγκρίσιμο με ένα τυπικό PDF που δημιουργείται από έγγραφο Word χωρίς τροποποιήσεις εξαγωγής σχημάτων.

Αν ανοίξετε το PDF στο Adobe Acrobat ή σε οποιονδήποτε σύγχρονο προβολέα, δεν θα πρέπει να δείτε ελλιπείς γραφικές παραστάσεις ή μετατοπισμένα στοιχεία.

## Συνηθισμένες παραλλαγές και ακραίες περιπτώσεις

### Μετατροπή πολλαπλών αρχείων DOCX σε παρτίδα

Όταν χρειάζεται να **convert docx to pdf** για πολλά αρχεία, τυλίξτε τα τρία βήματα σε έναν βρόχο:

```python
import pathlib

source_dir = pathlib.Path("YOUR_DIRECTORY")
for docx_path in source_dir.glob("*.docx"):
    doc = aw.Document(str(docx_path))
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True
    pdf_path = docx_path.with_suffix(".pdf")
    doc.save(str(pdf_path), pdf_opts)
```

### Διαχείριση πολύ μεγάλων εγγράφων

Για μεγάλα αρχεία Word, σκεφτείτε να ενεργοποιήσετε το `pdf_opts.save_format = aw.SaveFormat.PDF` (η προεπιλογή) και να προσαρμόσετε το `pdf_opts.compliance` εάν χρειάζεστε συμμόρφωση PDF/A. Αυτές οι επιλογές δεν επηρεάζουν την εξαγωγή σχημάτων αλλά βελτιώνουν τη συμβατότητα με συστήματα αρχειοθέτησης.

### Όταν τα σχήματα πρέπει να παραμείνουν αιωρούμενα

Αν ένα συγκεκριμένο έγγραφο απαιτεί τα αιωρούμενα σχήματα να παραμείνουν αιωρούμενα (π.χ., ένα έντονα σχεδιασμένο φυλλάδιο), ορίστε τη σημαία σε `False`. Το PDF τότε θα αποδώσει τα σχήματα ως ξεχωριστά αντικείμενα σχεδίασης, κάτι που μπορεί να είναι προτιμότερο για ακριβή τοποθέτηση γραφικών.

## Συμβουλές Pro

* **Pro tip:** Πάντα δοκιμάζετε το PDF στον προορισμένο προβολέα (π.χ., Chrome, Edge, Acrobat) επειδή ορισμένοι προβολείς ερμηνεύουν τις ενσωματωμένες ετικέτες ελαφρώς διαφορετικά.  
* **Watch out for:** Έγγραφα που χρησιμοποιούν παλαιά φορμά VML για σχέδια· το Aspose.Words μετατρέπει αυτόματα το VML σε σύγχρονα αντικείμενα σχεδίασης, αλλά πολύπλοκο VML μπορεί να χρειαστεί επιπλέον καθαρισμό.  
* **Performance tip:** Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `PdfSaveOptions` όταν επεξεργάζεστε πολλά αρχεία για να μειώσετε το κόστος κατανομής αντικειμένων.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες script που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα αρχείο με όνομα `docx_to_pdf.py`. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή στο μηχάνημά σας.

```python
import aspose.words as aw
import pathlib

def convert_docx_to_pdf(input_path: pathlib.Path, output_path: pathlib.Path):
    """
    Loads a DOCX file, configures PDF save options to export floating shapes as inline tags,
    and writes the result to a PDF file.
    """
    # Load the DOCX document
    doc = aw.Document(str(input_path))

    # Configure PDF options – export floating shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True

    # Save the PDF
    doc.save(str(output_path), pdf_opts)

if __name__ == "__main__":
    base_dir = pathlib.Path("YOUR_DIRECTORY")
    input_file = base_dir / "input.docx"
    output_file = base_dir / "output.pdf"

    convert_docx_to_pdf(input_file, output_file)
    print(f"Conversion complete: {output_file}")
```

Η εκτέλεση του `python docx_to_pdf.py` παράγει το `output.pdf` με όλα τα σχήματα διατηρημένα. Το script επιδεικνύει τη δυνατότητα **aspose docx to pdf** σε μια καθαρή, επαναχρησιμοποιήσιμη συνάρτηση.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **save docx as pdf** χρησιμοποιώντας το Aspose.Words, πώς να **convert docx to pdf** ελέγχοντας την εξαγωγή σχημάτων, και γιατί η σημαία `export_floating_shapes_as_inline_tag` είναι το κλειδί για αξιόπιστη διατήρηση της διάταξης. Αυτή η προσέγγιση λειτουργεί για το σενάριο **convert word to pdf**, υποστηρίζει επεξεργασία παρτίδας και σας δίνει την ευελιξία να προσαρμόζετε τη διαχείριση σχημάτων ανά έγγραφο.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **adding watermarks to PDFs**, **compressing PDF output**, ή **converting DOCX to other formats** όπως HTML ή EPUB. Κάθε μία από αυτές τις δυνατότητες βασίζεται στο ίδιο μοντέλο αντικειμένου `aw.Document` που χρησιμοποιήσατε εδώ, ώστε να μπορείτε να επεκτείνετε την αυτοματοποιημένη διαδικασία σας με σιγουριά.

Καλή προγραμματιστική δουλειά και απολαύστε τα αδιάλειπτα αποτελέσματα PDF!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Επόμενη

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να αποθηκεύσετε docx ως pdf με Aspose.Words σε Python](/words/english/python-net/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-in-python/)
- [Αποθήκευση Word ως PDF σε C# – Πλήρης Οδηγός για τη Μετατροπή DOCX σε PDF με Εξαγωγή Σχημάτων](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Αποθήκευση docx ως pdf & ανίχνευση ελλιπών γραμματοσειρών χρησιμοποιώντας Aspose.Words](/words/english/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}