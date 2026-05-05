---
category: general
date: 2026-05-04
description: Μάθετε πώς να ενσωματώνετε εικόνες σε Markdown όταν μετατρέπετε DOCX
  σε markdown, χρησιμοποιώντας Python και Aspose.Words. Δείτε επίσης πώς να ανακτήσετε
  κατεστραμμένα αρχεία docx.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- recover corrupted docx
language: el
og_description: Μάθετε πώς να ενσωματώνετε εικόνες σε Markdown κατά τη μετατροπή DOCX,
  με ένα βήμα‑βήμα παράδειγμα Python και συμβουλές για την ανάκτηση κατεστραμμένων
  αρχείων docx.
og_title: πώς να ενσωματώσετε εικόνες σε Markdown από DOCX – Πλήρης Οδηγός
tags:
- Aspose.Words
- Python
- Markdown
- DOCX conversion
title: Πώς να ενσωματώσετε εικόνες σε Markdown από DOCX – Πλήρης Οδηγός
url: /el/python/document-conversion/how-to-embed-images-in-markdown-from-docx-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να ενσωματώσετε εικόνες σε Markdown από DOCX – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **how to embed images** σε Markdown κατά τη μετατροπή ενός αρχείου DOCX; Αυτός ο οδηγός σας δείχνει ακριβώς **how to embed images** χρησιμοποιώντας Python και Aspose.Words, και το κάνει με τρόπο που λειτουργεί ακόμη και όταν το πηγαίο έγγραφο είναι μερικώς κατεστραμμένο. Θα καλύψουμε επίσης **convert docx to markdown**, θα εξηγήσουμε **how to convert docx**, θα δείξουμε **embed images as base64**, και θα σας δείξουμε πώς να **recover corrupted docx** αρχεία χωρίς κανένα πρόβλημα.

Στις επόμενες λίγες λεπτά θα αποχωρήσετε με ένα εκτελέσιμο script, μια σαφή κατανόηση του γιατί κάθε γραμμή είναι σημαντική, και μια σειρά από πρακτικές συμβουλές που μπορείτε να αντιγράψετε‑επικολλήσετε στα δικά σας έργα. Χωρίς κρυφές εξαρτήσεις, χωρίς ασαφείς συντομεύσεις “δείτε την τεκμηρίωση”—απλώς μια σταθερή, ολοκληρωμένη λύση.

---

## Τι Θα Δημιουργήσετε

* Ένα script Python που φορτώνει ένα DOCX (ακόμη και ένα κατεστραμμένο) με Aspose.Words.
* Μια προσαρμοσμένη callback που μετατρέπει κάθε ενσωματωμένη εικόνα σε **Base64** data‑URI, απαντώντας ουσιαστικά στην ερώτηση **how to embed images** απευθείας μέσα στο αρχείο Markdown.
* Ένα αρχείο Markdown όπου οι εξισώσεις εμφανίζονται ως LaTeX, τα αιωρούμενα σχήματα γίνονται ετικέτες inline, και όλες οι εικόνες είναι ασφαλώς ενσωματωμένες.
* Μια σύντομη λίστα ελέγχου για την αντιμετώπιση κοινών προβλημάτων όταν **convert docx to markdown**.

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Python 3.8+ | Απαιτείται για το πακέτο `aspose.words`. |
| `aspose-words` pip package | Παρέχει το namespace `aw` που χρησιμοποιείται σε όλο τον κώδικα. |
| A DOCX file (any size) | Η πηγή που θα μετατρέψετε. |
| Optional: a corrupted DOCX | Για να δοκιμάσετε τη διαδρομή **recover corrupted docx**. |

Εγκαταστήστε τη βιβλιοθήκη με:

```bash
pip install aspose-words
```

---

## Ρύθμιση του περιβάλλοντος

Πριν εμβαθύνουμε στην πραγματική μετατροπή, βεβαιωθείτε ότι το περιβάλλον σας μπορεί να εντοπίσει το assembly του Aspose.Words. Αν χρησιμοποιείτε εικονικό περιβάλλον, ενεργοποιήστε το πρώτα:

```bash
# Activate your venv (Linux/macOS)
source venv/bin/activate

# Or on Windows
venv\Scripts\activate
```

Τώρα εισάγετε τις μονάδες που θα χρειαστούμε. Παρατηρήστε την εισαγωγή `base64` – αυτή είναι η καρδιά του **embed images as base64**.

```python
# Step 1: Import Aspose.Words and base64 for encoding image data
import aspose.words as aw
import base64
```

> **Pro tip:** Αν λάβετε ένα `ModuleNotFoundError`, ελέγξτε ξανά ότι εγκαταστήσατε το `aspose-words` μέσα στο ίδιο εικονικό περιβάλλον από το οποίο εκτελείτε το script.

---

## Γραφή της callback ενσωμάτωσης εικόνων

Το Aspose.Words σας επιτρέπει να συνδέσετε στη διαδικασία αποθήκευσης μέσω μιας *resource‑saving callback*. Εδώ απαντάμε στο **how to embed images** μετατρέποντας το δυαδικό payload σε μια συμβολοσειρά data‑URI.

```python
# Step 2: Define a callback that converts embedded images to Base64 data URIs
def embed_images(resource):
    # We only care about images; other resources (like CSS) are ignored.
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build a data URI: data:<mime_type>;base64,<encoded_bytes>
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        # Return a tuple (name, bytes) – the name is used as the image reference.
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to skip this resource.
    return None
```

**Why this works:** Η ιδιότητα `resource.bytes` περιέχει τα ακατέργαστα bytes της εικόνας. Η `base64.b64encode` μετατρέπει αυτά τα bytes σε μια συμβολοσειρά ASCII, και προσθέτουμε τον τύπο MIME ώστε τα προγράμματα περιήγησης να ξέρουν πώς να εμφανίσουν την εικόνα. Το αποτέλεσμα είναι ένα αυτόνομο αρχείο Markdown χωρίς εξωτερικά αρχεία εικόνας – ακριβώς αυτό που υπόσχεται το **embed images as base64**.

---

## Φόρτωση του DOCX σε λειτουργία ανάκτησης

Ένα κοινό πρόβλημα είναι η αντιμετώπιση μερικώς κατεστραμμένων αρχείων Word. Το Aspose.Words προσφέρει μια *recovery mode* που προσπαθεί να διασώσει ό,τι μπορεί. Αυτό ικανοποιεί την απαίτηση **recover corrupted docx**.

```python
# Step 3: Load the source DOCX document with recovery mode enabled
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER  # Attempts to fix broken parts
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_options)
```

Αν το αρχείο είναι άψογο, η λειτουργία ανάκτησης δεν έχει σχεδόν κανένα κόστος. Αν είναι κατεστραμμένο, το Aspose θα παραλείψει τα μη αναγνώσιμα τμήματα ενώ θα σας παρέχει ένα χρήσιμο αντικείμενο εγγράφου.

---

## Διαμόρφωση επιλογών εξαγωγής Markdown

Τώρα λέμε στο Aspose ακριβώς πώς θέλουμε να φαίνεται η έξοδος Markdown. Δύο ρυθμίσεις είναι κρίσιμες για ένα καθαρό αποτέλεσμα:

* `office_math_export_mode = LATEX` – μετατρέπει τις εξισώσεις Word σε LaTeX, το οποίο καταλαβαίνουν οι περισσότεροι renderers Markdown.
* `export_floating_shapes_as_inline_tag = True` – αναγκάζει τις αιωρούμενες εικόνες να συμπεριφέρονται ως εικόνες inline, κάνοντας το τελικό αρχείο να μοιάζει περισσότερο με απόδοση τύπου PDF.

```python
# Step 4: Configure Markdown export options
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
markdown_options.resource_saving_callback = embed_images      # Hook we defined earlier
markdown_options.export_floating_shapes_as_inline_tag = True
```

---

## Αποθήκευση του αρχείου Markdown

Με όλα συνδεδεμένα, το τελικό βήμα είναι μια εντολή μίας γραμμής που γράφει το Markdown στο δίσκο. Η callback που παρέχουμε θα κληθεί για κάθε εικόνα, μετατρέποντας το **how to embed images** σε μια αδιάσπαστη μέρος της διαδικασίας αποθήκευσης.

```python
# Step 5: Save the document as a Markdown file with the configured options
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
print("✅ Conversion complete! Find your Markdown at YOUR_DIRECTORY/output.md")
```

Όταν ανοίξετε το `output.md` θα δείτε κάτι όπως:

```markdown
![image1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Αυτή η γραμμή είναι το αποτέλεσμα του **embed images as base64** – η εικόνα βρίσκεται εξ ολοκλήρου μέσα στο αρχείο Markdown, ώστε να μπορείτε να διανείμετε ένα μόνο αρχείο `.md` οπουδήποτε χωρίς να ανησυχείτε για ελλιπή πόρους.

---

## Επαλήθευση της εξόδου και αντιμετώπιση προβλημάτων

### Γρήγορος έλεγχος λογικής

1. Ανοίξτε το `output.md` σε έναν προβολέα Markdown (VS Code, Typora, προεπισκόπηση GitHub, κ.λπ.).
2. Επιβεβαιώστε ότι όλες οι εικόνες εμφανίζονται σωστά.
3. Αναζητήστε μπλοκ LaTeX για εξισώσεις, π.χ.:

   ```latex
   $$\int_{0}^{\infty} e^{-x^2} dx = \frac{\sqrt{\pi}}{2}$$
   ```

Αν λείπουν εικόνες, ελέγξτε ξανά:

* Το πηγαίο DOCX περιέχει πράγματι εικόνες.
* Το `resource.mime_type` ανιχνεύεται (σπάνια μπορεί να είναι `image/svg+xml`; το Aspose το διαχειρίζεται ακόμα).

### Συνηθισμένες περιπτώσεις άκρων

| Situation | What to do |
|-----------|------------|
| **Corrupted DOCX εξακολουθεί να προκαλεί σφάλματα** | Ορίστε `load_options.password` αν το αρχείο είναι προστατευμένο με κωδικό, ή δοκιμάστε να ανοίξετε το αρχείο στο Word και να το αποθηκεύσετε ξανά. |
| **Πολύ μεγάλες εικόνες προκαλούν τεράστια αρχεία Markdown** | Αλλάξτε το μέγεθος των εικόνων πριν τη μετατροπή ή τροποποιήστε την callback για να μειώσετε την ανάλυση χρησιμοποιώντας Pillow (`PIL.Image`). |
| **You need external image files instead of** |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}