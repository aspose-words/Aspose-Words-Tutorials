---
category: general
date: 2026-11-25
description: Ανακτήστε κατεστραμμένα αρχεία docx και μετατρέψτε τα σε markdown χρησιμοποιώντας
  το Aspose.Words για Python. Ακολουθήστε έναν οδηγό βήμα‑βήμα που δείχνει επίσης
  πώς να αποθηκεύσετε το PDF ενσωματωμένα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to recover word
- how to convert word pdf
- how to save pdf inline
language: el
lastmod: 2026-11-25
og_description: Ανακτήστε κατεστραμμένα αρχεία docx και μετατρέψτε τα σε markdown
  με το Aspose.Words για Python. Το σεμινάριο καλύπτει επίσης την ενσωματωμένη αποθήκευση
  PDF και το στυλ σχήματος.
og_image_alt: Diagram showing the recover corrupted docx workflow and conversion steps
og_title: Ανάκτηση κατεστραμμένου docx και μετατροπή σε markdown – πλήρης οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Recover corrupted docx files and convert them to markdown using Aspose.Words
    for Python. Follow a step‑by‑step guide that also shows how to save PDF inline.
  headline: How to recover corrupted docx and convert to markdown
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: Πώς να ανακτήσετε κατεστραμμένα αρχεία docx και να τα μετατρέψετε σε markdown
url: /el/python/document-conversion/how-to-recover-corrupted-docx-and-convert-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να επαναφέρετε κατεστραμμένα αρχεία docx και να τα μετατρέψετε σε markdown

Αν χρειάζεστε **επαναφορά κατεστραμμένων αρχείων docx**, αυτός ο οδηγός σας δείχνει έναν αξιόπιστο τρόπο με το Aspose.Words for Python. Επιπλέον, θα μάθετε πώς να **μετατρέψετε docx σε markdown**, να δημιουργήσετε PDF με ενσωματωμένα σχήματα και να βελτιώσετε την εμφάνιση του πρώτου σχήματος.

Η επαναφορά ενός κατεστραμμένου εγγράφου Word μπορεί να φαίνεται αδιέξοδο, αλλά το Aspose.Words παρέχει ενσωματωμένη λειτουργία ανάκτησης που προσπαθεί να ξαναχτίσει τη δομή του εγγράφου. Μόλις το αρχείο γίνει αναγνώσιμο, μπορείτε να εξάγετε το περιεχόμενό του σε πολλές μορφές, συμπεριλαμβανομένων των Markdown και PDF.

Σε αυτό το tutorial θα:

* Φορτώσετε ένα πιθανώς κατεστραμμένο `.docx` σε λειτουργία ανάκτησης.  
* Εξάγετε εξισώσεις Office Math ως LaTeX μέσα σε αρχείο Markdown (`convert docx to markdown`).  
* Αποθηκεύσετε PDF όπου τα αιωρούμενα σχήματα επισημαίνονται ως ενσωματωμένα στοιχεία (`how to save pdf inline`).  
* Ρυθμίσετε τη σκιά του πρώτου σχήματος για βελτιωμένη οπτική ποιότητα.  
* Αποθηκεύσετε το τροποποιημένο έγγραφο ξανά σε Word (`how to recover word`).

Το παράδειγμα χρησιμοποιεί Python 3 και Aspose.Words 23.10, αλλά οι έννοιες ισχύουν για οποιαδήποτε πρόσφατη έκδοση της βιβλιοθήκης.

## Προαπαιτούμενα

| Απαίτηση | Αιτία |
|----------|-------|
| Python 3.8+ | Απαιτείται από το Aspose.Words for Python |
| `aspose-words` package (`pip install aspose-words`) | Παρέχει το API που χρησιμοποιείται στον κώδικα |
| Ένα αρχείο `.docx` που δεν ανοίγει στο Microsoft Word (προαιρετικό) | Επιδεικνύει τη ροή εργασίας ανάκτησης |
| Βασική εξοικείωση με scripting σε Python | Σας βοηθά να προσαρμόσετε το παράδειγμα στο πρόγραμμά σας |

> **Pro tip:** Εκτελέστε `pip show aspose-words` για να επαληθεύσετε την εγκατεστημένη έκδοση πριν ξεκινήσετε.

## Επαναφορά κατεστραμμένου docx και προετοιμασία για μετατροπή

Το πρώτο βήμα είναι να ανοίξετε το έγγραφο σε **λειτουργία ανάκτησης**. Το Aspose.Words διαβάζει όσο το δυνατόν περισσότερο από το αρχείο, ξαναχτίζοντας τα ελλιπή τμήματα ώστε η υπόλοιπη αλυσίδα εργασιών να μπορεί να προχωρήσει.

```python
import aspose.words as aw

# Load a potentially corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/sample_corrupted.docx", load_options)
```

**Γιατί είναι σημαντικό:**  
Όταν η `recovery_mode` ορίζεται σε `RECOVER`, η βιβλιοθήκη αγνοεί μη‑κριτικές σφάλματα (π.χ. σπασμένες σχέσεις, ελλιπή τμήματα) και δημιουργεί μια καλύτερη δυνατή αναπαράσταση του αρχικού εγγράφου. Χωρίς αυτή τη σημαία, ο κατασκευαστής `Document` θα ρίξει εξαίρεση, διακόπτοντας τη διαδικασία μετατροπής.

Αν το έγγραφο φορτωθεί επιτυχώς, μπορείτε να το χειριστείτε όπως οποιοδήποτε άλλο αντικείμενο `Document`—να εξετάσετε παραγράφους, εικόνες ή σχήματα, και να προχωρήσετε στο επόμενο βήμα.

## Μετατροπή docx σε markdown

Το Aspose.Words μπορεί να αποδώσει ένα αρχείο Word ως Markdown, διατηρώντας τις περισσότερες μορφοποιήσεις και προαιρετικά εξάγοντας εξισώσεις Office Math ως LaTeX. Αυτό ικανοποιεί την απαίτηση **convert docx to markdown**.

```python
# Export Office Math equations as LaTeX within a Markdown file
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/sample.md", markdown_options)
```

**Τι λαμβάνετε:**  
Το `sample.md` περιέχει το κειμενικό περιεχόμενο του αρχικού εγγράφου. Οποιαδήποτε ενσωματωμένη εξίσωση εμφανίζεται ως μπλοκ LaTeX, τα οποία οι επεξεργαστές Markdown όπως *pandoc* ή *GitHub* μπορούν να αποδώσουν σωστά.

> **Common question:** *Θα συμπεριληφθούν οι εικόνες;*  
> Ναι. Οι εικόνες αποθηκεύονται ως ξεχωριστά αρχεία στον ίδιο φάκελο και αναφέρονται με σχετικές διαδρομές στην έξοδο Markdown.

## Πώς να μετατρέψετε word σε pdf και να αποθηκεύσετε PDF inline

Στη συνέχεια, δημιουργήστε μια έκδοση PDF του ανακτηθέντος εγγράφου. Η κλάση `PdfSaveOptions` σας επιτρέπει να ελέγξετε πώς θα αντιμετωπίζονται τα αιωρούμενα σχήματα. Ορίζοντας `export_floating_shapes_as_inline_tag` σε `True` επισημαίνει αυτά τα σχήματα ως ενσωματωμένα στοιχεία στη δομή του PDF (`how to save pdf inline`).

```python
# Save the same document as PDF, tagging floating shapes as inline elements
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/sample.pdf", pdf_options)
```

**Γιατί μπορεί να το χρειαστείτε:**  
Ορισμένα downstream εργαλεία PDF (π.χ. εργαλεία OCR) βασίζονται στην ετικέτα inline για να εντοπίσουν ακριβώς τα όρια των σχημάτων. Η σήμανση των σχημάτων ως inline βελτιώνει την προσβασιμότητα και διευκολύνει την εξαγωγή τους αργότερα.

## Βελτιώστε την οπτική εμφάνιση του πρώτου σχήματος

Αν το ανακτηθέν έγγραφο περιέχει αιωρούμενα σχήματα (π.χ. εικόνες, σχέδια), μπορείτε να ρυθμίσετε τις οπτικές τους ιδιότητες πριν την τελική αποθήκευση. Το παρακάτω παράδειγμα τροποποιεί τη σκιά του πρώτου σχήματος.

```python
# Retrieve the first shape in the document
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Access and configure the shape's shadow format
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.color = aw.drawing.Color.black
shape_shadow.offset_x = 5          # Horizontal offset in points
shape_shadow.offset_y = 5          # Vertical offset in points
shape_shadow.blur = 8
shape_shadow.transparency = 0.2    # 20 % transparent
```

**Practical tip:**  
Αν το έγγραφο περιέχει πολλά σχήματα, κάντε βρόχο πάνω τους με `doc.get_child_nodes(aw.NodeType.SHAPE, True)` και εφαρμόστε το ίδιο στυλ υπό όρους.

## Αποθήκευση του τροποποιημένου εγγράφου (how to recover word)

Αφού προσαρμόσετε το σχήμα, αποθηκεύστε τις αλλαγές πίσω σε αρχείο Word. Αυτό δείχνει **how to recover word** έγγραφα μετά την επισκευή και την προγραμματιστική επεξεργασία τους.

```python
# Save the document with the modified shape
doc.save("YOUR_DIRECTORY/sample_modified.docx")
```

Τώρα έχετε τρία χρήσιμα τελικά προϊόντα:

| Αρχείο | Σκοπός |
|--------|--------|
| `sample.md` | Πηγαίος κώδικας Markdown με εξισώσεις LaTeX (`convert docx to markdown`). |
| `sample.pdf` | PDF με σχήματα επισημασμένα ως inline (`how to save pdf inline`). |
| `sample_modified.docx` | Ανακτημένο και βελτιωμένο έγγραφο Word (`how to recover word`). |

## Επαλήθευση των αποτελεσμάτων

Ανοίξτε κάθε αρχείο εξόδου για να βεβαιωθείτε ότι η λειτουργία ολοκληρώθηκε επιτυχώς:

* **Markdown:** Ανοίξτε το `sample.md` σε οποιονδήποτε επεξεργαστή κειμένου. Αναζητήστε μπλοκ LaTeX περικλεισμένα σε `$$ … $$`.
* **PDF:** Ανοίξτε το `sample.pdf` με το Adobe Reader. Χρησιμοποιήστε το πάνελ *Content* για να δείτε ότι τα αιωρούμενα σχήματα είναι σημειωμένα ως **Figure (Inline)**.
* **Word:** Ανοίξτε το `sample_modified.docx` στο Microsoft Word. Το πρώτο σχήμα θα πρέπει τώρα να εμφανίζει ήπια σκιά.

Αν κάποιο αρχείο δεν ανοίξει, εκτελέστε ξανά το script με `load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER_WITH_EXCEPTIONS` για λεπτομερή μηνύματα σφάλματος.

## Συνηθισμένες ακραίες περιπτώσεις και πώς να τις αντιμετωπίσετε

| Κατάσταση | Συνιστώμενη προσέγγιση |
|-----------|------------------------|
| Το αρχείο είναι **εντελώς μη αναγνώσιμο** (χωρίς XML τμήματα) | Χρησιμοποιήστε `RecoveryMode.RECOVER_WITH_EXCEPTIONS` για να καταγράψετε την ακριβή αποτυχία, έπειτα σκεφτείτε την αναδημιουργία του εγγράφου από την αρχή. |
| **Μεγάλα έγγραφα** (> 100 MB) προκαλούν πίεση μνήμης | Επεξεργαστείτε το έγγραφο σε ενότητες χρησιμοποιώντας `DocumentBuilder` ή κάντε streaming της εξόδου με `SaveOptions` που υποστηρίζουν σταδιακή αποθήκευση. |
| **Απουσία εικόνων** μετά τη μετατροπή | Βεβαιωθείτε ότι το αρχικό `.docx` περιέχει τα τμήματα εικόνας· διαφορετικά, αντικαταστήστε τις σπασμένες συνδέσεις με placeholders πριν την αποθήκευση. |
| **Η εξαγωγή εξισώσεων** εμφανίζει ακατέργαστο MathML αντί για LaTeX |  |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to recover corrupted docx files using Aspose.Words for Python](/words/english/python-net/document-operations/how-to-recover-corrupted-docx-files-using-aspose-words-for-p/)
- [How to convert DOCX to PDF in Python using Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)
- [How to save Word as PDF and convert DOCX to Markdown](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}