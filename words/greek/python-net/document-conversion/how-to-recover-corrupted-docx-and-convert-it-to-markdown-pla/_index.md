---
category: general
date: 2026-10-13
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx, να μετατρέψετε docx
  σε markdown, να μετατρέψετε docx σε απλό κείμενο και να αποθηκεύσετε το έγγραφο
  ως markdown χρησιμοποιώντας το Aspose.Words για Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to recover corrupted word file
- convert docx to plain text
- how to save document as markdown
language: el
lastmod: 2026-10-13
og_description: Ανακτήστε κατεστραμμένα αρχεία docx και μετατρέψτε docx σε markdown,
  απλό κείμενο και PDF με το Aspose.Words για Python. Ακολουθήστε αυτό το πλήρες σεμινάριο.
og_image_alt: Diagram showing recover corrupted docx workflow from loading to saving
  in multiple formats
og_title: Ανάκτηση κατεστραμμένου docx και μετατροπή σε markdown, απλό κείμενο, PDF
  – οδηγός βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to recover corrupted docx files, convert docx to markdown,
    convert docx to plain text, and save document as markdown using Aspose.Words for
    Python.
  headline: How to recover corrupted docx and convert it to markdown, plain text,
    and PDF with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: Πώς να ανακτήσετε κατεστραμμένα αρχεία docx και να τα μετατρέψετε σε markdown,
  απλό κείμενο και PDF με το Aspose.Words
url: /el/python/document-conversion/how-to-recover-corrupted-docx-and-convert-it-to-markdown-pla/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ανακτήσετε κατεστραμμένα docx και να τα μετατρέψετε σε markdown, απλό κείμενο και PDF με το Aspose.Words

Αν χρειάζεστε **ανάκτηση κατεστραμμένων docx** αρχείων, αυτός ο οδηγός σας δείχνει έναν αξιόπιστο, προγραμματιστικό τρόπο για να το κάνετε. Χρησιμοποιώντας το Aspose.Words για Python μπορείτε να φορτώσετε ένα κατεστραμμένο έγγραφο Word, να εξάγετε το περιεχόμενό του και στη συνέχεια **να μετατρέψετε docx σε markdown**, **να μετατρέψετε docx σε απλό κείμενο**, ή ακόμη και να αποθηκεύσετε το αποτέλεσμα ως PDF.

Η ανάκτηση ενός κατεστραμμένου αρχείου συχνά φαίνεται αδιέξοδο, αλλά η λειτουργία ανάκτησης του Aspose.Words κάνει τη διαδικασία ντετερμινιστική. Αφού φορτωθεί το έγγραφο, μπορείτε να το εξάγετε σε οποιαδήποτε μορφή υποστηρίζεται από τη βιβλιοθήκη, συμπεριλαμβανομένου του Markdown με εξισώσεις LaTeX, αρχείων plain‑text, και PDF όπου τα αιωρούμενα σχήματα γίνονται ετικέτες inline.

Σε αυτό το tutorial θα:

* Φορτώσετε ένα πιθανώς κατεστραμμένο `.docx` με λειτουργία ανάκτησης.
* Εξάγετε το έγγραφο σε Markdown διατηρώντας το Office Math ως LaTeX.
* Αποθηκεύσετε το ίδιο περιεχόμενο ως απλό κείμενο με εξισώσεις μορφοποιημένες σε LaTeX.
* Δημιουργήσετε ένα PDF που επισημαίνει τα αιωρούμενα σχήματα ως στοιχεία inline.
* Ρυθμίσετε το εφέ σκιάς του πρώτου σχήματος και αποθηκεύσετε το τροποποιημένο αρχείο.

**Προαπαιτούμενα:**

* Python 3.8+ εγκατεστημένο.
* `aspose-words` package (`pip install aspose-words`).
* Ένα αρχείο `.docx` που μπορεί να είναι κατεστραμμένο (π.χ., `corrupted.docx`).

---

## Πώς να ανακτήσετε κατεστραμμένα docx με το Aspose.Words

Το Aspose.Words παρέχει μια κλάση `LoadOptions` που σας επιτρέπει να καθορίσετε μια στρατηγική ανάκτησης. Ορίζοντας το `recovery_mode` σε `RECOVER` λέτε στη βιβλιοθήκη να προσπαθήσει να διορθώσει δομικά προβλήματα και να συνεχίσει τη φόρτωση.

```python
import aspose.words as aw

# Load the document in recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # RECOVER, SKIP, FAIL
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Γιατί λειτουργεί:** Όταν το αρχείο Word περιέχει κατεστραμμένα τμήματα (απόντες κόμβους XML, περικομμένα ρεύματα), η λειτουργία ανάκτησης αναλύει ό,τι μπορεί και απορρίπτει ακατάλληλα τμήματα, αποτρέποντας μια εξαίρεση που διαφορετικά θα σταματούσε το πρόγραμμα.

> **Συμβουλή:** Αν χρειάζεστε μόνο να παραλείψετε κατεστραμμένα τμήματα χωρίς να προσπαθήσετε επιδιόρθωση, χρησιμοποιήστε το `RecoveryMode.SKIP`. Για αυστηρή επικύρωση, το `RecoveryMode.FAIL` ρίχνει σφάλμα σε οποιοδήποτε πρόβλημα.

---

## Μετατροπή docx σε markdown

Μόλις φορτωθεί το έγγραφο, μπορείτε να το αποθηκεύσετε ως Markdown. Η κλάση `MarkdownSaveOptions` σας επιτρέπει να ελέγξετε πώς εξάγονται οι εξισώσεις Office Math. Ορίζοντας το `office_math_export_mode` σε `LATEX` διασφαλίζει ότι οι εξισώσεις εμφανίζονται ως κώδικας LaTeX, που είναι η πιο φορητή αναπαράσταση για επιστημονικά έγγραφα.

```python
# Save as Markdown with LaTeX equations
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
```

**Αποτέλεσμα:** Το `output.md` περιέχει το κειμενικό περιεχόμενο του αρχικού αρχείου Word, με επικεφαλίδες, λίστες και πίνακες αποτυπωμένα σε σύνταξη Markdown. Οποιεσδήποτε ενσωματωμένες εξισώσεις εμφανίζονται ως μπλοκ LaTeX `$…$`.

> **Συχνή ερώτηση:** *Λειτουργεί αυτό και με αρχεία DOC;*  
> Ναι. Οι ίδιες `MarkdownSaveOptions` μπορούν να χρησιμοποιηθούν με εισόδους `.doc` ή `.docx` επειδή η μετατροπή γίνεται αφού το έγγραφο έχει φορτωθεί πλήρως.

---

## Μετατροπή docx σε απλό κείμενο

Η εξαγωγή σε plain‑text είναι χρήσιμη για ευρετηρίαση αναζήτησης ή γρήγορες προεπισκοπήσεις. Η κλάση `TxtSaveOptions` αντικατοπτρίζει τις επιλογές Markdown για το Office Math, επιτρέποντάς σας να διατηρήσετε τις εξισώσεις σε μορφή LaTeX ακόμη και σε αρχείο `.txt`.

```python
# Save as plain text with LaTeX equations
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)
```

**Αποτέλεσμα:** Το `output.txt` περιέχει το ακατέργαστο κείμενο του εγγράφου, με διατηρημένα τα line‑breaks, και τις εξισώσεις ως αλφαριθμητικά LaTeX (π.χ., `\frac{a}{b}`).

---

## Αποθήκευση εγγράφου ως PDF με σχήματα inline

Κατά τη μετατροπή σε PDF, μπορεί να χρειαστείτε τα αιωρούμενα σχήματα (πλαίσια κειμένου, εικόνες) να συμπεριφέρονται ως στοιχεία inline για καλύτερη προσβασιμότητα ή επεξεργασία σε επόμενα στάδια. Η κλάση `PdfSaveOptions` προσφέρει μια σημαία `export_floating_shapes_as_inline_tag` που επιβάλλει αυτή τη συμπεριφορά.

```python
# Export to PDF, tagging floating shapes as inline
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)
```

**Αποτέλεσμα:** Το `output.pdf` αντικατοπτρίζει τη διάταξη του αρχικού αρχείου Word, αλλά οποιοδήποτε αιωρούμενο σχήμα σημειώνεται ως ετικέτα inline στη δομή του PDF, κάτι που πολλοί αναλυτές PDF το θεωρούν ως μέρος της ροής κειμένου.

---

## Ρύθμιση εφέ σκιάς σχήματος (προαιρετικό)

Αν χρειάζεστε να τροποποιήσετε οπτικές πτυχές ενός σχήματος—π.χ., για να βελτιώσετε μια παρουσίαση—μπορείτε να έχετε άμεση πρόσβαση στον κόμβο του σχήματος και να αλλάξετε τις ιδιότητες σκιάς του.

```python
# Locate the first shape in the document
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()

# Adjust shadow parameters
shape.shadow.blur = 5.0          # Blur radius
shape.shadow.offset_x = 2.0     # Horizontal offset
shape.shadow.offset_y = 2.0     # Vertical offset

# Save the modified document
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Γιατί να ρυθμίσετε τις σκιές:** Η αλλαγή της θολότητας και της μετατόπισης μπορεί να κάνει ένα σχήμα να φαίνεται ανυψωμένο από τη σελίδα, βελτιώνοντας την αναγνωσιμότητα σε έντυπα ή οθονικές εκδόσεις.

---

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες script που ενσωματώνει κάθε βήμα που περιγράφηκε παραπάνω. Αποθηκεύστε το ως `process_docx.py` και εκτελέστε το από τη γραμμή εντολών.

```python
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Load the potentially corrupted document using recovery mode.
# ------------------------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# ------------------------------------------------------------------
# 2. Export to Markdown (with LaTeX equations).
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_options)

# ------------------------------------------------------------------
# 3. Export to plain text (also with LaTeX equations).
# ------------------------------------------------------------------
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)

# ------------------------------------------------------------------
# 4. Export to PDF, tagging floating shapes as inline.
# ------------------------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)

# ------------------------------------------------------------------
# 5. Optional: modify the first shape's shadow and save a new DOCX.
# ------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shape.shadow.blur = 5.0
shape.shadow.offset_x = 2.0
shape.shadow.offset_y = 2.0
doc.save("YOUR_DIRECTORY/shadowed.docx")
```

**Αναμενόμενα αρχεία εξόδου**

| File                | Description                                            |
|---------------------|--------------------------------------------------------|
| `output.md`         | Έκδοση Markdown με εξισώσεις LaTeX.                |
| `output.txt`        | Έκδοση απλού κειμένου, εξισώσεις σε σύνταξη LaTeX.        |
| `output.pdf`        | PDF όπου τα αιωρούμενα σχήματα σημειώνονται ως ετικέτες inline.  |
| `shadowed.docx`     | Αρχικό έγγραφο με την σκιά του πρώτου σχήματος τροποποιημένη.|

Εκτελέστε το script και βεβαιωθείτε ότι κάθε αρχείο εμφανίζεται στο `YOUR_DIRECTORY`. Ανοίξτε το αρχείο Markdown σε έναν προβολέα που υποστηρίζει LaTeX (π.χ., VS Code με επέκταση προεπισκόπησης Markdown) για να δείτε τις εξισώσεις να αποδίδονται σωστά.

---

## Συχνές ερωτήσεις

**Πώς να ανακτήσετε κατεστραμμένο αρχείο Word χωρίς το Aspose;**  
Μπορείτε να δοκιμάσετε τη ενσωματωμένη λειτουργία του Microsoft Word «Open and Repair», αλλά προσφέρει περιορισμένο έλεγχο και δεν παρέχει προγραμματιστική εξαγωγή. Το Aspose.Words παρέχει ντετερμινιστική ανάκτηση και σας επιτρέπει να αυτοματοποιήσετε τις μεταγενέστερες μετατροπές.

**Μπορώ να μετατρέψω ένα DOCX σε markdown χωρίς να χάσω τις εικόνες;**  
Κατά τη χρήση του `MarkdownSaveOptions`, οι εικόνες αποθηκεύονται ως ξεχωριστά αρχεία σε έναν υποφάκελο δίπλα στο αρχείο `.md`. Το Markdown αναφέρει τα αρχεία εικόνας χρησιμοποιώντας σχετικές διαδρομές, διατηρώντας τη οπτική διάταξη.

**Τι γίνεται αν το έγγραφο περιέχει πίνακα με συγχωνευμένα κελιά;**  
Το Aspose.Words διατηρεί τα συγχωνευμένα κελιά κατά τη μετατροπή τόσο σε Markdown όσο και σε plain text. Στο Markdown, τα συγχωνευμένα κελιά γίνονται κανονικά κελιά με κατάλληλους διαχωριστές pipe (`|`). Στο plain text, εμφανίζονται ως στήλες με κενά.

**Είναι η λειτουργία εξαγωγής LaTeX συμβατή με παλαιότερες εκδόσεις του Aspose.Words;**  
Η εξαγωγή LaTeX για το Office Math εισήχθη στην έκδοση 22.10. Εάν χρησιμοποιείτε παλαιότερη έκδοση, η ιδιότητα δεν θα είναι διαθέσιμη και οι εξισώσεις θα επιστρέψουν σε MathML.

---

## Επόμενα βήματα

Τώρα που ξέρετε πώς να **ανακτήσετε κατεστραμμένα docx**, **να μετατρέψετε docx σε markdown**, **να μετατρέψετε docx σε απλό κείμενο**, και **να αποθηκεύσετε το έγγραφο ως markdown**, μπορείτε να επεκτείνετε τη ροή εργασίας:

* **Επεξεργασία παρτίδας** – επανάληψη σε φάκελο κατεστραμμένων αρχείων και δημιουργία όλων των μορφών-στόχου σε μία εκτέλεση.
* **Ανάπτυξη στο cloud** – τυλίξτε το script σε Azure Function ή AWS Lambda για παροχή μετατροπής κατά απαίτηση ως υπηρεσία web.
* **Περαιτέρω υποστήριξη μορφών** – εξερευνήστε `HtmlSaveOptions`, `EpubSaveOptions` ή `MhtmlSaveOptions` για επιπλέον δυνατότητες εξαγωγής.

Δοκιμάστε τις επιλογές που παρέχει το Aspose.Words για να ρυθμίσετε λεπτομερώς τη διαχείριση εικόνων, την ενσωμάτωση γραμματοσειρών ή τις ρυθμίσεις ασφαλείας PDF. Το εκτενές API της βιβλιοθήκης καθιστά δυνατό το χτίσιμο μιας πλήρους γραμμής επεξεργασίας εγγράφων που ξεκινά με ανάκτηση και τελειώνει με έτοιμα προς δημοσίευση περιουσιακά στοιχεία.

---

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να εξάγετε LaTeX από το Word – Μετατροπή DOCX σε Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)
- [Αποθήκευση Word ως Markdown με Aspose.Words – Πλήρης οδηγός για μετατροπή DOCX και εξαγωγή εικόνων](/words/english/net/programming-with-markdownsaveoptions/save-word-as-markdown-complete-guide-to-convert-docx-and-ext/)
- [πώς να ανακτήσετε docx – ορισμός λειτουργίας ανάκτησης & άνοιγμα κατεστραμμένων αρχείων Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}