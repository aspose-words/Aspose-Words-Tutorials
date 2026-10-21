---
category: general
date: 2026-10-16
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx, να ενεργοποιήσετε
  τη λειτουργία ανάκτησης και να ελέγξετε τον αριθμό των σελίδων σε ένα ενιαίο script
  Python χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- enable recovery mode
- check page count
- recover word document
- how to open corrupted docx
language: el
lastmod: 2026-10-16
og_description: Ανακτήστε κατεστραμμένα αρχεία docx χρησιμοποιώντας το Aspose.Words
  για Python. Αυτός ο οδηγός δείχνει πώς να ενεργοποιήσετε τη λειτουργία ανάκτησης,
  να ανοίξετε το κατεστραμμένο αρχείο και να ελέγξετε τον αριθμό σελίδων.
og_image_alt: Screenshot of Python code that recovers a corrupted docx document using
  Aspose.Words
og_title: Ανάκτηση κατεστραμμένου docx με το Aspose.Words – ενεργοποίηση λειτουργίας
  ανάκτησης και επαλήθευση αριθμού σελίδων
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to recover corrupted docx, enable recovery mode, and check
    page count in a single Python script using Aspose.Words.
  headline: How to recover corrupted docx files with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document recovery
- DOCX
title: Πώς να ανακτήσετε κατεστραμμένα αρχεία docx με το Aspose.Words για Python
url: /el/python/document-operations/how-to-recover-corrupted-docx-files-with-aspose-words-for-py/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ανακτήσετε κατεστραμμένα αρχεία docx με το Aspose.Words for Python

Αν χρειάζεστε **ανάκτηση κατεστραμμένων docx** αρχείων, το Aspose.Words for Python το κάνει απλό. Αυτό το tutorial δείχνει πώς να **ενεργοποιήσετε τη λειτουργία ανάκτησης**, να φορτώσετε το κατεστραμμένο έγγραφο και να **ελέγξετε τον αριθμό σελίδων** για να επιβεβαιώσετε ότι η λειτουργία **ανάκτησης εγγράφου Word** ολοκληρώθηκε με επιτυχία.

Τα κατεστραμμένα αρχεία DOCX εμφανίζονται συχνά μετά από διακοπή αποθήκευσης, εσφαλμένη μετατροπή ή σφάλματα δίσκου. Αντί να ζητάτε από τους χρήστες να στείλουν ξανά το αρχείο, μπορείτε αυτόματα να προσπαθήσετε ανάκτηση από την πλευρά του διακομιστή. Παρακάτω θα μάθετε τη πλήρη ροή εργασίας, από την εγκατάσταση του SDK μέχρι την επαλήθευση ότι το έγγραφο άνοιξε σωστά.

## Προαπαιτήσεις

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Έχει εγκατασταθεί Python 3.8 ή νεότερη έκδοση.  
* Έγκυρη άδεια Aspose.Words for Python (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).  
* Το πακέτο `aspose-words` εγκατεστημένο μέσω `pip`:

```bash
pip install aspose-words
```

* Ένα κατεστραμμένο αρχείο DOCX διαθέσιμο στο δίσκο (π.χ., `corrupted.docx`).  
  Αν δεν έχετε κάποιο, μπορείτε να προσομοιώσετε την καταστροφή ανοίγοντας ένα DOCX σε επεξεργαστή κειμένου και διαγράφοντας μερικά byte.

## Βήμα 1: Ενεργοποίηση λειτουργίας ανάκτησης για την ανάκτηση κατεστραμμένων docx

Η λειτουργία ανάκτησης λέει στο Aspose.Words να αγνοήσει δομικά προβλήματα και να προσπαθήσει να ξαναχτίσει το δέντρο του εγγράφου. Χωρίς αυτήν, η φόρτωση ενός κατεστραμμένου αρχείου θα προκαλούσε εξαίρεση.

```python
import aspose.words as aw

# Create LoadOptions and turn on recovery mode
load_options = aw.LoadOptions()
load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
```

**Γιατί είναι σημαντικό:**  
`LoadOptions.RecoveryMode.RECOVER` δίνει στον parser την οδηγία να θεωρήσει το αρχείο ως μερικώς έγκυρο, παραλείποντας τα μη αναγνώσιμα τμήματα και διασώζοντας το υπόλοιπο. Αυτό είναι το βασικό βήμα που σας επιτρέπει να **ανακτήσετε κατεστραμμένα docx** αυτόματα.

## Βήμα 2: Φόρτωση του εγγράφου με τις επιλογές που έχουν ενεργοποιήσει την ανάκτηση

Τώρα που η λειτουργία ανάκτησης είναι ενεργή, φορτώστε το αρχείο. Αν το έγγραφο είναι σοβαρά κατεστραμμένο, το Aspose.Words θα επιστρέψει ακόμη ένα αντικείμενο `Document` που περιέχει όποιο περιεχόμενο μπορεί να διασωθεί.

```python
# Load the potentially corrupted DOCX using the recovery options
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Συμβουλή:** Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή. Η χρήση απόλυτης διαδρομής αποφεύγει ασαφείς σφάλματα σχετικών διαδρομών, ειδικά όταν το script εκτελείται ως υπηρεσία παρασκηνίου.

## Βήμα 3: Έλεγχος αριθμού σελίδων για επαλήθευση της λειτουργίας ανάκτησης εγγράφου Word

Ένας γρήγορος τρόπος να επιβεβαιώσετε ότι το αρχείο άνοιξε είναι να διαβάσετε το `page_count`. Αν ο αριθμός είναι μεγαλύτερος του μηδενός, η ανάκτηση πέτυχε επαρκώς ώστε να αποδοθεί τουλάχιστον μία σελίδα.

```python
# Verify that the document was loaded by printing its page count
print("Document loaded, pages:", doc.page_count)
```

Αν η έξοδος δείχνει `pages: 0`, το αρχείο μπορεί να είναι πέρα από την επισκευή, ή η καταστροφή να έχει αφαιρέσει όλο το εκτυπώσιμο περιεχόμενο. Σε αυτήν την περίπτωση, σκεφτείτε να ενημερώσετε τον χρήστη και να ζητήσετε νέο ανέβασμα.

## Πλήρες script – ανάκτηση κατεστραμμένου docx σε μία εκτέλεση

Συνδυάζοντας τα τρία βήματα παίρνετε ένα σύντομο, έτοιμο για παραγωγή απόσπασμα κώδικα:

```python
import aspose.words as aw

def recover_docx(file_path: str) -> int:
    """
    Attempts to recover a corrupted DOCX file and returns the page count.
    Returns -1 if the file cannot be opened at all.
    """
    # Step 1: Enable recovery mode
    load_options = aw.LoadOptions()
    load_options.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

    try:
        # Step 2: Load the document with recovery enabled
        doc = aw.Document(file_path, load_options)

        # Step 3: Check page count – this also confirms the file was recovered
        page_count = doc.page_count
        print(f"Recovered document page count: {page_count}")
        return page_count
    except Exception as e:
        # If loading fails even with recovery mode, report the error
        print(f"Failed to recover '{file_path}': {e}")
        return -1

if __name__ == "__main__":
    # Example usage – replace with your actual file location
    recover_docx("YOUR_DIRECTORY/corrupted.docx")
```

**Επεξήγηση της συνάρτησης:**

* **Παράμετροι** – `file_path` δείχνει στο DOCX που θέλετε να ανοίξετε.  
* **Τιμή επιστροφής** – Ο αριθμός σελίδων μετά την ανάκτηση, ή `-1` αν το αρχείο δεν μπορεί να ανοιχθεί.  
* **Διαχείριση σφαλμάτων** – Ακόμη και με τη λειτουργία ανάκτησης, κάποια αρχεία είναι ακατάσβεστα· το μπλοκ `except` εξασφαλίζει ότι το script αποτυγχάνει με χάρη.

## Πώς να ανοίξετε κατεστραμμένο docx σε web service (προαιρετικό)

Αν εκθέσετε αυτή τη λογική μέσω ενός endpoint Flask ή FastAPI, μπορείτε να επιτρέψετε στους πελάτες να ανεβάσουν ένα αρχείο και να λάβουν μια απάντηση JSON με τον αριθμό σελίδων.

```python
from fastapi import FastAPI, File, UploadFile
import shutil, os

app = FastAPI()

@app.post("/recover")
async def recover_endpoint(file: UploadFile = File(...)):
    temp_path = f"/tmp/{file.filename}"
    with open(temp_path, "wb") as buffer:
        shutil.copyfileobj(file.file, buffer)

    pages = recover_docx(temp_path)
    os.remove(temp_path)  # Clean up temporary file

    return {"filename": file.filename, "page_count": pages}
```

**Γιατί μπορεί να το χρειαστείτε:**  
Σε επιχειρηματικές γραμμές επεξεργασίας εγγράφων, η αυτόματη προσπάθεια ανάκτησης μειώνει τα εισερχόμενα tickets υποστήριξης και βελτιώνει την εμπειρία του χρήστη.

## Συνηθισμένα προβλήματα και αντιμετώπιση

| Σύμπτωμα | Πιθανή αιτία | Διόρθωση |
|---|---|---|
| `Exception: File not found` | Λάθος διαδρομή ή λείπει το αρχείο | Επαληθεύστε τη απόλυτη διαδρομή και βεβαιωθείτε ότι το αρχείο υπάρχει. |
| `pages: 0` even after recovery | Το αρχείο περιέχει μόνο μη‑οπτικά δεδομένα (π.χ., μόνο μεταδεδομένα) | Ελέγξτε αν το αρχικό έγγραφο είχε πράγματι σελίδες· διαφορετικά, ζητήστε νέο αρχείο. |
| `LicenseException` | Δεν υπάρχει έγκυρη άδεια Aspose.Words | Εφαρμόστε δοκιμαστική ή εμπορική άδεια χρησιμοποιώντας `aw.License().set_license("path/to/license.xml")`. |
| Slow loading on very large files | Η λειτουργία ανάκτησης επεξεργάζεται πολλά κατεστραμμένα τμήματα | Σκεφτείτε την ροή του αρχείου ή την αύξηση των ορίων μνήμης. |

**Pro tip:** Πάντα καταγράψτε το αρχικό μήνυμα εξαίρεσης όταν η ανάκτηση αποτυγχάνει. Το μήνυμα συχνά περιέχει τον ακριβή κόμβο XML που προκάλεσε το πρόβλημα, βοηθώντας σας να βελτιώσετε τη διαδικασία δημιουργίας εγγράφων.

## Αναμενόμενη έξοδος

Εκτελώντας το script σε ένα ανακτήσιμο `corrupted.docx` εκτυπώνει κάτι παρόμοιο με:

```
Recovered document page count: 5
```

Αν το αρχείο δεν μπορεί να διασωθεί, θα δείτε:

```
Failed to recover 'YOUR_DIRECTORY/corrupted.docx': The file is corrupted and cannot be opened.
```

Η εμφάνιση θετικού αριθμού σελίδων επιβεβαιώνει ότι έχετε **ανακτήσει κατεστραμμένα docx** και μπορείτε τώρα να συνεχίσετε την επεξεργασία του εγγράφου (π.χ., μετατροπή σε PDF, εξαγωγή κειμένου κ.λπ.).

## Επόμενα βήματα

Τώρα που ξέρετε **πώς να ανοίξετε κατεστραμμένα docx**, μπορείτε να επεκτείνετε τη ροή εργασίας:

* **Μετατροπή του ανακτημένου εγγράφου σε PDF** – καλέστε `doc.save("output.pdf")`.  
* **Εξαγωγή κειμένου για ευρετηρίαση** – επαναλάβετε πάνω από `doc.get_child_nodes(aw.NodeType.PARAGRAPH, True)`.  
* **Batch‑process ενός φακέλου με κατεστραμμένα αρχεία** – κάντε βρόχο στα αρχεία και αποθηκεύστε τα αποτελέσματα σε βάση δεδομένων.

Κάθε μία από αυτές τις επεκτάσεις χρησιμοποιεί το ίδιο αντικείμενο `Document` που αποκτήσατε μετά την **ενεργοποίηση της λειτουργίας ανάκτησης**, έτσι το βήμα ανάκτησης παραμένει η βάση κάθε αξιόπιστης γραμμής επεξεργασίας εγγράφων.

---

*Έχετε μάθει πώς να ανακτήσετε ένα κατεστραμμένο αρχείο DOCX, να ενεργοποιήσετε τη λειτουργία ανάκτησης και να επαληθεύσετε την επιτυχία ελέγχοντας τον αριθμό σελίδων. Εφαρμόστε αυτά τα πρότυπα για να διατηρήσετε τις υπηρεσίες επεξεργασίας εγγράφων ανθεκτικές και φιλικές προς τον χρήστη.*

## Τι Θα Μάθετε Στη Σειρά;

- [Ανάκτηση Κατεστραμμένου DOCX – Πλήρης Οδηγός για Ενεργοποίηση Λειτουργίας Ανάκτησης & Λήψη Αριθμού Σελίδων](/words/english/python-net/document-operations/recover-corrupted-docx-complete-guide-to-enable-recovery-mod/)
- [πώς να ανακτήσετε docx – ορίστε λειτουργία ανάκτησης & ανοίξτε κατεστραμμένα αρχεία Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Πώς να ανακτήσετε docx – Ενεργοποίηση Λειτουργίας Ανάκτησης & Ανάγνωση Προειδοποιήσεων](/words/english/java/document-loading-and-saving/how-to-recover-docx-enable-recovery-mode-read-warnings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}