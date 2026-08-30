---
category: general
date: 2026-06-30
description: Πώς να μετονομάζετε τις εικόνες κατά τη μετατροπή DOCX σε markdown. Μάθετε
  πώς να αλλάζετε τα ονόματα των εικόνων και να αποθηκεύετε το Word ως markdown με
  προσαρμοσμένα ονόματα αρχείων εικόνας.
draft: false
keywords:
- how to rename images
- convert docx to markdown
- change image names
- save word as markdown
- custom image filenames
language: el
og_description: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή DOCX σε markdown.
  Αυτός ο οδηγός σας δείχνει πώς να αλλάξετε τα ονόματα των εικόνων, να αποθηκεύσετε
  το Word ως markdown και να χρησιμοποιήσετε προσαρμοσμένα ονόματα αρχείων εικόνας.
og_title: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή DOCX σε Markdown
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  headline: How to Rename Images When Converting DOCX to Markdown
  type: TechArticle
- description: How to rename images while converting DOCX to markdown. Learn to change
    image names and save Word as markdown with custom image filenames.
  name: How to Rename Images When Converting DOCX to Markdown
  steps:
  - name: Why Use a GUID?
    text: '* **Uniqueness** – A GUID (`uuid4`) guarantees that two images will never
      clash, even across multiple runs. * **Traceability** – If you need to debug
      later, the GUID can be logged alongside the original Word paragraph number.
      * **Portability** – No reliance on the original Word naming scheme, which '
  - name: Expected Output (excerpt)
    text: '```markdown # Sample Document'
  - name: What if the document contains non‑image resources?
    text: Our callback already checks the file extension and returns `True` for anything
      that isn’t an image. This means CSS files, fonts, or embedded OLE objects keep
      their original names, which is usually what you want when you **save word as
      markdown**.
  - name: Can I use a custom naming scheme instead of GUIDs?
    text: 'Absolutely. Replace the `uuid.uuid4()` call with any function that returns
      a string. For example, you could prepend the original paragraph index:'
  - name: How does this affect performance on large documents?
    text: The callback runs once per resource, so the overhead is minimal—mostly the
      time to generate a GUID. Even a 200‑page report with dozens of images finishes
      in under a second on a modern laptop.
  - name: What if I need the image filenames to be deterministic (e.g., for CI builds)?
    text: 'Swap `uuid.uuid4()` for a hash of the original image bytes:'
  type: HowTo
tags:
- Aspose.Words
- Python
- Markdown
- Image Processing
title: Πώς να μετονομάσετε τις εικόνες κατά τη μετατροπή DOCX σε Markdown
url: /el/python/document-conversion/how-to-rename-images-when-converting-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Μετονομάσετε τις Εικόνες Κατά τη Μετατροπή DOCX σε Markdown

Έχετε αναρωτηθεί ποτέ **πώς να μετονομάζετε τις εικόνες** αυτόματα όταν μετατρέπετε ένα αρχείο DOCX σε Markdown; Δεν είστε οι μόνοι. Σε πολλές γραμμές τεκμηρίωσης τα προεπιλεγμένα ονόματα εικόνων (όπως `image1.png`) γίνονται εφιάλτης για παρακολούθηση, ειδικά όταν το ίδιο markdown ελέγχεται σε έκδοση από ομάδες.  

Τα καλά νέα είναι ότι το Aspose.Words for Python το κάνει παιχνιδάκι να **αλλάξετε τα ονόματα των εικόνων** εν κινήσει, και μπορείτε να διατηρήσετε το Markdown σας καθαρό ενώ διατηρείτε έναν τακτοποιημένο φάκελο με προσαρμοσμένα ονόματα πόρων.  

Σε αυτό το tutorial θα μάθετε πώς να:

* Φορτώσετε ένα έγγραφο Word (`.docx`) σε Python.  
* Συνδέσετε μια callback στη διαδικασία αποθήκευσης Markdown που δίνει σε κάθε εικόνα ένα όνομα αρχείου βασισμένο σε GUID.  
* Αποθηκεύσετε το έγγραφο ως Markdown ώστε το παραγόμενο αρχείο να αναφέρεται στις νεομετονομασμένες εικόνες.  

Αν είστε άνετοι με τις βασικές γνώσεις Python και έχετε εγκατεστημένο το Aspose.Words, θα είστε έτοιμοι σε λιγότερο από πέντε λεπτά. Χωρίς εξωτερικά scripts, χωρίς χειροκίνητη μετονομασία — μόνο ένα ενιαίο, αυτόνομο πρόγραμμα που κάνει όλη τη βαριά δουλειά για εσάς.

---

## Προαπαιτήσεις — Τι Χρειάζεστε Πριν Ξεκινήσετε

| Απαίτηση | Γιατί Είναι Σημαντική |
|-------------|----------------|
| **Python 3.7+** | Το παράδειγμα χρησιμοποιεί f‑strings και type hints που εισήχθησαν στην 3.6, αλλά η 3.7+ παρέχει τις ευκολίες του `os.path.splitext`. |
| **Aspose.Words for Python via .NET** (`pip install aspose-words`) | Αυτή η βιβλιοθήκη παρέχει την κλάση `aw.Document` και το `MarkdownSaveOptions` στο οποίο βασιζόμαστε. |
| **Δικαίωμα εγγραφής** στον φάκελο εξόδου | Η callback θα δημιουργήσει νέα αρχεία εικόνας, οπότε το script πρέπει να έχει άδεια εγγραφής. |
| **Ένα αρχείο DOCX** που θέλετε να μετατρέψετε | Οτιδήποτε, από μια απλή αναφορά έως ένα πολύπλοκο εγχειρίδιο, θα λειτουργήσει. |

> **Pro tip:** Αν χρησιμοποιείτε εικονικό περιβάλλον, ενεργοποιήστε το πριν εγκαταστήσετε το Aspose.Words. Απομονώνει τις εξαρτήσεις και αποτρέπει συγκρούσεις εκδόσεων.

---

## Βήμα 1: Φορτώστε το Έγγραφο Word  

Το πρώτο πράγμα που κάνετε όταν θέλετε να **μετατρέψετε docx σε markdown** είναι να ανοίξετε το αρχείο προέλευσης. Το Aspose.Words αφαιρεί την ανάγκη για χειρισμό χαμηλού επιπέδου OPC, οπότε μια μόνο γραμμή κάνει τη δουλειά.

```python
import aspose.words as aw

# Replace YOUR_DIRECTORY with the folder that holds your .docx file
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

*Γιατί είναι σημαντικό:* Χωρίς τη φόρτωση του εγγράφου δεν μπορείτε να εξετάσετε τους πόρους του, και ο εξαγωγέας Markdown δεν θα έχει τίποτα να γράψει. Το αντικείμενο `aw.Document` κρατά ολόκληρο το πακέτο Word στη μνήμη, καθιστώντας ασφαλή την επεξεργασία πριν την αποθήκευση.

---

## Βήμα 2: Γράψτε ένα Callback που **Μετονομάζει τους Πόρους Εικόνας**  

Το Aspose.Words σας επιτρέπει να συνδέσετε ένα `resource_saving_callback` στο `MarkdownSaveOptions`. Η callback λαμβάνει κάθε πόρο (εικόνες, CSS, κ.λπ.) ακριβώς πριν γραφτεί στο δίσκο. Με την τροποποίηση του `resource.file_name` μπορούμε να επιβάλλουμε **προσαρμοσμένα ονόματα εικόνων**.

```python
def rename_image_resource(resource):
    """
    Rename image resources with a unique GUID before saving.
    This is where we implement how to rename images.
    """
    import uuid, os

    # Guard: only process image resources, ignore CSS or other files
    if not resource.file_name.lower().endswith(('.png', '.jpg', '.jpeg', '.gif', '.bmp')):
        return True  # Let Aspose handle non‑image resources unchanged

    # Extract the original extension so we keep PNG as PNG, JPG as JPG, etc.
    _, ext = os.path.splitext(resource.file_name)

    # Generate a globally unique identifier and tack the original extension on
    new_name = f"{uuid.uuid4()}{ext}"
    resource.file_name = new_name

    # Returning True tells Aspose to proceed with the default saving logic
    return True
```

### Γιατί να Χρησιμοποιήσετε GUID;

* **Μοναδικότητα** – Ένα GUID (`uuid4`) εγγυάται ότι δύο εικόνες δεν θα συγκρούονται, ακόμη και σε πολλαπλές εκτελέσεις.  
* **Ιχνηλασιμότητα** – Αν χρειαστεί να εντοπίσετε σφάλματα αργότερα, το GUID μπορεί να καταγραφεί μαζί με τον αρχικό αριθμό παραγράφου του Word.  
* **Φορητότητα** – Δεν εξαρτάται από το αρχικό σχήμα ονοματοδοσίας του Word, που μπορεί να περιέχει κενά ή ειδικούς χαρακτήρες που σπάζουν τους συνδέσμους Markdown.

---

## Βήμα 3: Συνδέστε το Callback στις Επιλογές Αποθήκευσης Markdown  

Τώρα λέμε στο Aspose να χρησιμοποιεί τη λογική μετονομασίας μας όποτε γράφει μια εικόνα στον φάκελο εξόδου.

```python
md_options = aw.saving.MarkdownSaveOptions()
md_options.resource_saving_callback = rename_image_resource

# Optional: control where images are placed relative to the markdown file
md_options.images_folder = "images"  # creates a sub‑folder called 'images'
```

*Εξήγηση:* Η κλάση `MarkdownSaveOptions` ελέγχει τα πάντα, από τις αλλαγές γραμμής μέχρι τη θέση του φακέλου εικόνων. Ορίζοντας το `resource_saving_callback`, παίρνετε ένα **hook** που ενεργοποιείται για κάθε ενσωματωμένο πόρο, δίνοντάς σας την ευκαιρία να **αλλάξετε τα ονόματα των εικόνων** πριν το αρχείο φθάσει στο δίσκο.

---

## Βήμα 4: Αποθηκεύστε το Έγγραφο ως Markdown – Το Τελικό Τμήμα  

Με την callback σε θέση, το τελικό βήμα είναι απλό.

```python
output_path = "YOUR_DIRECTORY/CustomResources.md"
doc.save(output_path, md_options)
print(f"Markdown saved to {output_path}")
```

Όταν το script ολοκληρωθεί, θα βρείτε:

* `CustomResources.md` – η αναπαράσταση Markdown του αρχείου Word σας.  
* Έναν φάκελο `images/` (ή ό,τι έχετε ορίσει) που περιέχει αρχεία όπως `d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png`.  

Το αρχείο Markdown θα αναφέρεται στα νέα ονόματα αρχείων βασισμένα σε GUID, ώστε οποιοσδήποτε downstream επεξεργαστής (GitHub, MkDocs, κ.λπ.) να εντοπίζει τις σωστές εικόνες χωρίς να χρειάζεται να τις μετονομάσετε χειροκίνητα.

### Αναμενόμενη Έξοδος (απόσπασμα)

```markdown
# Sample Document

Here is an image that was originally called `image1.png` in the DOCX:

![d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e](images/d3b07384-d113-4f3a-9c6b-9f1e2a6a9c3e.png)

And another one:

![a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6](images/a1b2c3d4-e5f6-7a8b-9c0d-e1f2a3b4c5d6.jpg)
```

Τα GUID θα διαφέρουν σε κάθε εκτέλεση, αλλά το μοτίβο παραμένει το ίδιο.

---

## Διαχείριση Ακραίων Περιπτώσεων και Συχνών Ερωτήσεων  

### Τι γίνεται αν το έγγραφο περιέχει μη‑εικονογραφικούς πόρους;  

Η callback μας ήδη ελέγχει την επέκταση του αρχείου και επιστρέφει `True` για οτιδήποτε δεν είναι εικόνα. Αυτό σημαίνει ότι τα αρχεία CSS, οι γραμματοσειρές ή τα ενσωματωμένα αντικείμενα OLE διατηρούν τα αρχικά τους ονόματα, κάτι που συνήθως θέλετε όταν **αποθηκεύετε word ως markdown**.

### Μπορώ να χρησιμοποιήσω προσαρμοσμένο σχήμα ονοματοδοσίας αντί για GUIDs;  

Απόλυτα. Αντικαταστήστε την κλήση `uuid.uuid4()` με οποιαδήποτε συνάρτηση επιστρέφει μια συμβολοσειρά. Για παράδειγμα, μπορείτε να προσθέσετε το αρχικό δείκτη παραγράφου:

```python
new_name = f"para{resource.resource_id}{ext}"
```

Απλώς βεβαιωθείτε ότι το παραγόμενο όνομα είναι μοναδικό σε όλο το έγγραφο.

### Πώς επηρεάζει αυτό την απόδοση σε μεγάλα έγγραφα;  

Η callback εκτελείται μία φορά ανά πόρο, οπότε το πρόσθετο κόστος είναι ελάχιστο — κυρίως ο χρόνος δημιουργίας ενός GUID. Ακόμη και μια αναφορά 200 σελίδων με δεκάδες εικόνες ολοκληρώνεται σε λιγότερο από ένα δευτερόλεπτο σε σύγχρονο laptop.

### Τι γίνεται αν χρειάζομαι τα ονόματα εικόνων να είναι ντετερμινιστικά (π.χ., για CI builds);  

Αντικαταστήστε το `uuid.uuid4()` με ένα hash των αρχικών bytes της εικόνας:

```python
import hashlib
hash = hashlib.sha256(resource.raw_bytes).hexdigest()[:12]
new_name = f"{hash}{ext}"
```

Αυτό παράγει το ίδιο όνομα αρχείου κάθε φορά που τρέχετε το script στην ίδια πηγή εικόνας.

---

## Πλήρες Λειτουργικό Σενάριο – Αντιγράψτε, Επικολλήστε, Εκτελέστε  



## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [save docx as markdown – Full C# Guide with Image Extraction](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-full-c-guide-with-image-extraction/)
- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}