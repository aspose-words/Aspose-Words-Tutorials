---
category: general
date: 2026-10-04
description: Ενεργοποιήστε τη λειτουργία ανάκτησης στο Aspose.Words για να ανακτήσετε
  με ασφάλεια ένα κατεστραμμένο έγγραφο Word. Ακολουθήστε τον βήμα‑προς‑βήμα οδηγό
  με πλήρη κώδικα Python και εξηγήσεις.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- enable recovery mode
- recover corrupted word document
- Aspose.Words load options
- document recovery Python
- handling damaged .docx files
language: el
lastmod: 2026-10-04
og_description: Ενεργοποιήστε τη λειτουργία ανάκτησης για να επαναφέρετε ένα κατεστραμμένο
  έγγραφο Word χρησιμοποιώντας το Aspose.Words. Αυτό το σεμινάριο δείχνει τον ακριβή
  κώδικα Python, γιατί λειτουργεί και πώς να αντιμετωπίσετε τις ειδικές περιπτώσεις.
og_image_alt: Screenshot of Python code loading a corrupted Word document with recovery
  mode enabled
og_title: Ενεργοποιήστε τη λειτουργία ανάκτησης για να επανακτήσετε ένα κατεστραμμένο
  έγγραφο Word – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  headline: Enable recovery mode to recover a corrupted Word document
  type: TechArticle
- description: Enable recovery mode in Aspose.Words to recover a corrupted Word document
    safely. Follow the step‑by‑step guide with full Python code and explanations.
  name: Enable recovery mode to recover a corrupted Word document
  steps:
  - name: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
    text: Create `LoadOptions` and set `recovery_mode` to `RECOVER`.
  - name: Load the `.docx` using those options.
    text: Load the `.docx` using those options.
  - name: Verify the mode and optionally save a repaired copy.
    text: Verify the mode and optionally save a repaired copy.
  type: HowTo
tags:
- Aspose.Words
- Python
- Document processing
- Error handling
title: Ενεργοποίηση λειτουργίας ανάκτησης για την αποκατάσταση ενός κατεστραμμένου
  εγγράφου Word
url: /el/python/document-options-and-settings/enable-recovery-mode-to-recover-a-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ενεργοποίηση λειτουργίας ανάκτησης για αποκατάσταση κατεστραμμένου εγγράφου Word

Αν χρειάζεται να **ενεργοποιήσετε τη λειτουργία ανάκτησης** κατά τη φόρτωση ενός αρχείου Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Python. Ενεργοποιώντας τη λειτουργία ανάκτησης μπορείτε να **ανακτήσετε ένα κατεστραμμένο έγγραφο Word** που διαφορετικά θα προκαλούσε εξαίρεση.

Στις επόμενες ενότητες θα μάθετε:

* Ποιες κλάσεις και ιδιότητες ελέγχουν τη συμπεριφορά της ανάκτησης.  
* Πώς να φορτώσετε ένα πιθανώς κατεστραμμένο αρχείο `.docx` χωρίς να καταρρεύσει η εφαρμογή σας.  
* Συμβουλές για την αντιμετώπιση κοινών προβλημάτων φόρτωσης και την προσαρμογή της στρατηγικής ανάκτησης.

> **Προαπαιτούμενο** – Έχετε εγκατεστημένο το Aspose.Words for Python (`pip install aspose-words`) και βασική κατανόηση του Python file I/O.

## Τι κάνει η λειτουργία ανάκτησης και γιατί πρέπει να την ενεργοποιήσετε

Το Aspose.Words αναλύει τη εσωτερική δομή ενός αρχείου Word πριν το εκθέσει ως αντικείμενο `Document`. Όταν το αρχείο είναι κατεστραμμένο — λείπουν τμήματα, σπασμένο XML ή μη έγκυρες σχέσεις — ο parser μπορεί είτε:

| Λειτουργία | Συμπεριφορά |
|------------|--------------|
| `STRICT` | Εγείρει εξαίρεση στην πρώτη ένδειξη σφάλματος. |
| `IGNORE_ERRORS` | Παραλείπει μη αναγνώσιμα τμήματα, αλλά μπορεί να χάσει περιεχόμενο σιωπηρά. |
| `RECOVER` (η επιλογή **ενεργοποίησης λειτουργίας ανάκτησης**) | Προσπαθεί να ξαναχτίσει το έγγραφο, διατηρώντας όσο το δυνατόν περισσότερο περιεχόμενο και εκθέτει τη λειτουργία μέσω `load_options.recovery_mode`. |

Το `RECOVER` είναι η προτεινόμενη επιλογή όταν πρέπει να **ανακτήσετε κατεστραμμένα έγγραφα Word** για επεξεργασία downstream, όπως εξαγωγή κειμένου ή μετατροπή σε PDF.

## Βήμα 1: Δημιουργία LoadOptions και ενεργοποίηση λειτουργίας ανάκτησης

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `LoadOptions` και ορισμός της ιδιότητας `recovery_mode` σε `RecoveryMode.RECOVER`. Αυτό ενημερώνει τη βιβλιοθήκη να ακολουθήσει τη διαδρομή ανάκτησης κατά την ανάλυση.

```python
import aspose.words as aw

# Step 1: Create load options and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER  # alternatives: .IGNORE_ERRORS, .STRICT
```

**Γιατί είναι σημαντικό:**  
Αν παραλείψετε αυτό το βήμα και το έγγραφο είναι κατεστραμμένο, ο κατασκευαστής `aw.Document(...)` θα εγείρει `InvalidOperationException`. Η ενεργοποίηση της λειτουργίας ανάκτησης αποτρέπει την κατάρρευση και σας παρέχει ένα μερικώς επισκευασμένο αντικείμενο `Document` με το οποίο μπορείτε ακόμη να εργαστείτε.

## Βήμα 2: Φόρτωση του πιθανώς κατεστραμμένου εγγράφου χρησιμοποιώντας τις καθορισμένες επιλογές

Περάστε το στιγμιότυπο `load_options` στον κατασκευαστή `Document`. Ο φορτωτής θα εφαρμόσει αυτόματα τον αλγόριθμο ανάκτησης.

```python
# Step 2: Load the potentially corrupted document using the specified options
doc_path = "YOUR_DIRECTORY/Corrupted.docx"
doc = aw.Document(doc_path, load_options)
```

**Συμβουλή:** Αντικαταστήστε το `YOUR_DIRECTORY` με την απόλυτη ή σχετική διαδρομή που μπορεί να προσπελάσει το runtime σας. Εάν το αρχείο δεν υπάρχει, το Aspose.Words θα εγείρει `FileNotFoundError` πριν φτάσει στη λογική ανάκτησης.

## Βήμα 3: Επαλήθευση ότι η λειτουργία ανάκτησης εφαρμόστηκε

Μπορείτε να επιβεβαιώσετε τη λειτουργία ελέγχοντας το `load_options.recovery_mode`. Αυτό είναι χρήσιμο για καταγραφή ή για συνθήκες επεξεργασίας αργότερα στην αλυσίδα.

```python
# Step 3: Confirm that the document was loaded with the chosen recovery mode
print("Document loaded with recovery mode:", load_options.recovery_mode)
```

**Αναμενόμενη έξοδος**

```
Document loaded with recovery mode: RecoveryMode.RECOVER
```

Αν η έξοδος εμφανίζει `RECOVER`, έχετε ενεργοποιήσει επιτυχώς τη **λειτουργία ανάκτησης** και το έγγραφο είναι έτοιμο για περαιτέρω επεξεργασία (π.χ. εξαγωγή κειμένου, μετατροπή σε PDF ή αποθήκευση μιας επισκευασμένης αντιγραφής).

## Βήμα 4 (προαιρετικό): Αποθήκευση μιας επισκευασμένης αντιγραφής για μελλοντική χρήση

Μετά τη φόρτωση, ίσως θέλετε να αποθηκεύσετε το ανακτηθέν έγγραφο ώστε να μην χρειάζεται να επαναλάβετε το βήμα ανάκτησης.

```python
# Optional: Save the repaired document
repaired_path = "YOUR_DIRECTORY/Corrupted_Repaired.docx"
doc.save(repaired_path)
print(f"Repaired document saved to {repaired_path}")
```

Η αποθήκευση δημιουργεί ένα νέο `.docx` που το Aspose.Words θεωρεί έγκυρο, το οποίο μπορεί να ανοιχτεί στο Microsoft Word χωρίς προειδοποιήσεις.

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|----------|
| **Τι γίνεται αν το έγγραφο είναι εντελώς μη αναγνώσιμο;** | Ακόμη και σε λειτουργία `RECOVER`, ορισμένα αρχεία είναι πέρα από την επισκευή. Το αντικείμενο `Document` θα δημιουργηθεί, αλλά μπορεί να περιέχει μόνο μία κενή σελίδα. Ελέγξτε το `doc.get_page_count()` για να επαληθεύσετε το περιεχόμενο. |
| **Μπορώ να αλλάξω σε `IGNORE_ERRORS` μετά τη φόρτωση;** | Όχι. Η λειτουργία ανάκτησης πρέπει να οριστεί **πριν** εκτελεστεί ο κατασκευαστής `Document`. Δημιουργήστε ένα νέο στιγμιότυπο `LoadOptions` αν χρειάζεστε διαφορετική στρατηγική. |
| **Επηρεάζει η λειτουργία ανάκτησης την απόδοση;** | Ναι, προσθέτει μικρό επιπλέον φόρτο επειδή η βιβλιοθήκη προσπαθεί να ανασυνθέσει σπασμένα τμήματα. Η επίπτωση είναι αμελητέα για τα περισσότερα αρχεία (< 2 MB). |
| **Είναι αυτή η προσέγγιση ανεξάρτητη από τη γλώσσα;** | Η ίδια έννοια υπάρχει στα .NET, Java και Node.js APIs (`LoadOptions.RecoveryMode`). Η σύνταξη του κώδικα αλλάζει, αλλά η λογική είναι η ίδια. |

## Pro tip: Καταγραφή λεπτομερών πληροφοριών ανάκτησης

Το Aspose.Words παρέχει ένα `LoadOptions.recovery_callback` που λαμβάνει λεπτομερή μηνύματα για κάθε βήμα ανάκτησης. Η σύνδεσή του μπορεί να σας βοηθήσει να διαγνώσετε γιατί ένα συγκεκριμένο έγγραφο απέτυχε.

```python
def recovery_logger(message):
    print("[Recovery] ", message)

load_options.recovery_callback = recovery_logger
```

Τώρα κάθε εσωτερική διόρθωση (π.χ. “Removed duplicate relationship”) θα εκτυπώνεται στην κονσόλα.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια, εδώ είναι ένα αυτόνομο script που μπορείτε να αντιγράψετε‑επικολλήσετε και να τρέξετε αμέσως:

```python
import aspose.words as aw

def enable_recovery_and_load(doc_path: str, save_repaired: bool = False):
    # Create load options and enable recovery mode
    load_options = aw.loading.LoadOptions()
    load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER

    # Optional: attach a simple logger
    load_options.recovery_callback = lambda msg: print("[Recovery] ", msg)

    # Load the document with recovery enabled
    doc = aw.Document(doc_path, load_options)

    # Verify the mode
    print("Document loaded with recovery mode:", load_options.recovery_mode)

    # Show basic info
    print("Page count:", doc.page_count)
    print("Word count:", doc.get_text().split())

    # Optionally save a repaired copy
    if save_repaired:
        repaired_path = doc_path.replace(".docx", "_repaired.docx")
        doc.save(repaired_path)
        print(f"Repaired document saved to {repaired_path}")

    return doc

if __name__ == "__main__":
    corrupted_path = "YOUR_DIRECTORY/Corrupted.docx"
    enable_recovery_and_load(corrupted_path, save_repaired=True)
```

Η εκτέλεση του script εκτυπώνει τη λειτουργία ανάκτησης, τον αριθμό σελίδων και μια λίστα λέξεων που εξήχθησαν από το επισκευασμένο έγγραφο. Αν ορίσετε `save_repaired=True`, ένα νέο καθαρό αρχείο εμφανίζεται δίπλα στο αρχικό.

## Συμπέρασμα

Τώρα ξέρετε πώς να **ενεργοποιήσετε τη λειτουργία ανάκτησης** στο Aspose.Words for Python και να **ανακτήσετε αξιόπιστα κατεστραμμένα έγγραφα Word**. Τα βασικά βήματα είναι:

1. Δημιουργήστε `LoadOptions` και ορίστε `recovery_mode` σε `RECOVER`.  
2. Φορτώστε το `.docx` χρησιμοποιώντας αυτές τις επιλογές.  
3. Επαληθεύστε τη λειτουργία και, προαιρετικά, αποθηκεύστε μια επισκευασμένη αντιγραφή.

Από εδώ μπορείτε να εξερευνήσετε περαιτέρω θέματα όπως **εξαγωγή κειμένου από ένα ανακτηθέν έγγραφο**, **μετατροπή σε PDF**, ή **αυτοματοποίηση μαζικής ανάκτησης** για μεγάλες βιβλιοθήκες εγγράφων.

---

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Recover Corrupted DOCX – Complete Guide to Enable Recovery Mode & Get Page](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)
- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}