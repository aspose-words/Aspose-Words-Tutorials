---
category: general
date: 2026-08-11
description: Πώς να μορφοποιήσετε ένα γράφημα σε έγγραφο Word χρησιμοποιώντας Python
  – φορτώστε το έγγραφο Word με Python και εφαρμόστε γρήγορα προεπιλεγμένο στυλ γραφήματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: el
lastmod: 2026-08-11
og_description: Πώς να μορφοποιήσετε ένα γράφημα σε ένα έγγραφο Word χρησιμοποιώντας
  Python. Μάθετε πώς να φορτώνετε ένα έγγραφο Word με Python, να εφαρμόζετε ένα προκαθορισμένο
  στυλ γραφήματος και να αποθηκεύετε το ενημερωμένο αρχείο.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: Πώς να μορφοποιήσετε ένα γράφημα στο Word με Python – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: Πώς να μορφοποιήσετε ένα γράφημα σε έγγραφο Word με Python
url: /el/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μορφοποιήσετε γράφημα σε έγγραφο Word χρησιμοποιώντας Python

Αν χρειάζεστε **πώς να μορφοποιήσετε γράφημα** σε αρχείο Word, αυτό το tutorial σας δείχνει τα ακριβή βήματα. Μέχρι το τέλος των πρώτων δύο προτάσεων θα ξέρετε πώς να φορτώσετε ένα έγγραφο Word με Python, να ανακτήσετε ένα γράφημα και να εφαρμόσετε ένα προ‑ορισμένο στυλ γραφήματος. Η λύση αυτή λειτουργεί με τη βιβλιοθήκη Aspose.Words for Python και δεν απαιτεί χειροκίνητη επεξεργασία του εγγράφου.

Θα μάθετε πώς να **load word document python**, να επιλέξετε το πρώτο σχήμα γραφήματος, να ορίσετε ένα ενσωματωμένο στυλ και να αποθηκεύσετε το τροποποιημένο αρχείο. Ο οδηγός καλύπτει επίσης κοινά προβλήματα, όπως η διαχείριση εγγράφων χωρίς γραφήματα και η επιλογή της σωστής απαρίθμησης στυλ. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από το πακέτο Aspose.Words.

## Πώς να μορφοποιήσετε γράφημα σε έγγραφο Word χρησιμοποιώντας Python

Η εφαρμογή ενός στυλ σε ένα γράφημα είναι μια λειτουργία μίας γραμμής μόλις έχετε ένα αντικείμενο `Chart`. Η βιβλιοθήκη εκθέτει την απαρίθμηση `ChartStyle`, η οποία περιλαμβάνει δεκάδες προ‑ορισμένες εμφανίσεις (Style 1 … Style 50). Σε αυτήν την ενότητα ορίζουμε **Style 5**, αλλά μπορείτε να αντικαταστήσετε την τιμή της enum με οποιοδήποτε στυλ ταιριάζει στις οδηγίες σχεδίασής σας.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**Γιατί λειτουργεί αυτό:**  
* `aw.Document` αναλύει το αρχείο .docx και δημιουργεί ένα μοντέλο αντικειμένων.  
* `get_child(..., aw.NodeType.SHAPE, ...)` εντοπίζει το πρώτο σχήμα, το οποίο είναι το κοντέινερ του γραφήματος.  
* `as_chart()` μετατρέπει το σχήμα σε αντικείμενο `Chart`, αποκαλύπτοντας την ιδιότητα `style`.  
* Η ανάθεση του `ChartStyle.STYLE_5` λέει στο Aspose.Words να αντικαταστήσει το οπτικό θέμα του γραφήματος με τον προ‑ορισμένο ορισμό.

Το αρχείο εξόδου `output.docx` περιέχει τα ίδια δεδομένα με το αρχικό, αλλά με το γράφημα να αποδίδεται χρησιμοποιώντας το επιλεγμένο στυλ.

## Φόρτωση εγγράφου Word σε Python

Πριν μπορέσετε να μορφοποιήσετε ένα γράφημα, πρέπει να **load word document python** σωστά. Ο κατασκευαστής `aw.Document` δέχεται μια διαδρομή προς ένα αρχείο .docx, .doc ή .rtf. Βεβαιωθείτε ότι η διαδρομή του αρχείου είναι απόλυτη ή ότι ο τρέχων φάκελος δείχνει στη θέση του αρχείου εισόδου σας.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**Συμβουλές για τη φόρτωση εγγράφων:**  
* Χρησιμοποιήστε ακατέργαστες συμβολοσειρές (`r"..."`) στα Windows για να αποφύγετε την διαφυγή των ανάστροφων κάθετων.  
* Επαληθεύστε ότι το αρχείο υπάρχει με `os.path.isfile(doc_path)` για να αποτρέψετε σφάλματα χρόνου εκτέλεσης.  
* Εάν το έγγραφο περιέχει προστατευμένες ενότητες, δώστε τον κωδικό πρόσβασης μέσω `aw.LoadOptions`.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## Εφαρμογή προ‑ορισμένου στυλ γραφήματος

Το βήμα **apply predefined chart style** είναι εκεί όπου συμβαίνει η οπτική μετασχηματισμός. Η Aspose.Words ορίζει την enum `ChartStyle` με τιμές από `STYLE_1` έως `STYLE_50`. Κάθε στυλ αντιστοιχεί σε ένα σύνολο χρωμάτων, σημείων και μορφών γραμμών που μιμούνται τα ενσωματωμένα θέματα γραφημάτων του Microsoft Office.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**Πότε να χρησιμοποιήσετε προ‑ορισμένο στυλ:**  

* Χρειάζεστε μια συνεπή εμφάνιση σε πολλά έγγραφα.  
* Τα δεδομένα του γραφήματος αλλάζουν συχνά, αλλά το οπτικό θέμα πρέπει να παραμένει σταθερό.  
* Θέλετε να αποφύγετε τη χειροκίνητη μορφοποίηση στη διεπαφή του Word.

**Ακραία περίπτωση – έγγραφο χωρίς γραφήματα:**  
Αν το `doc.get_child(aw.NodeType.SHAPE, 0, True)` επιστρέψει `None`, το script θα προκαλέσει `AttributeError`. Προστατέψτε το ελέγχοντας τον τύπο του κόμβου πριν την μετατροπή.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## Αποθήκευση του μορφοποιημένου εγγράφου

Μετά τη μορφοποίηση, η αποθήκευση των αλλαγών είναι απλή. Η μέθοδος `doc.save` γράφει το ενημερωμένο μοντέλο αντικειμένων πίσω σε αρχείο .docx. Μπορείτε επίσης να εξάγετε σε άλλες μορφές όπως PDF, HTML ή PNG εάν η επόμενη χρήση απαιτεί διαφορετική αναπαράσταση.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**Επαλήθευση:** Ανοίξτε το `output.docx` στο Microsoft Word. Το γράφημα θα πρέπει να εμφανίζει το νέο θέμα, και οποιεσδήποτε σειρές δεδομένων να διατηρούν τις αρχικές τιμές τους. Εάν εξάγετε σε PDF, το οπτικό στυλ παραμένει αμετάβλητο.

## Συνηθισμένα προβλήματα και πρακτικές συμβουλές

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | Δεν βρέθηκε σχήμα γραφήματος στο δείκτη 0 | Χρησιμοποιήστε `doc.get_child(..., 0, True)` μέσα σε μπλοκ try/except ή επαναλάβετε όλα τα σχήματα με `doc.get_child_nodes(aw.NodeType.SHAPE, True)`. |
| Λάθος στυλ εφαρμόστηκε | Χρήση τιμής enum που δεν υπάρχει (π.χ., `STYLE_0`) | Επιλέξτε μια έγκυρη τιμή `ChartStyle` (1‑50). |
| Το αρχείο δεν αποθηκεύτηκε | Η διαδρομή εξόδου δείχνει σε φάκελο μόνο για ανάγνωση | Βεβαιωθείτε ότι η διαδικασία έχει δικαιώματα εγγραφής ή αλλάξτε το φάκελο. |
| Το γράφημα εξαφανίζεται μετά την αποθήκευση | Το σχήμα δεν ήταν γράφημα (π.χ., εικόνα) | Επαληθεύστε `shape.has_chart` πριν τη μετατροπή. |

**Pro tip:** Αποθηκεύστε σε cache το `ChartStyle` που χρησιμοποιείτε πιο συχνά σε μια σταθερά ώστε να μπορείτε να το επαναχρησιμοποιήσετε σε πολλά scripts χωρίς να πληκτρολογείτε την enum κάθε φορά.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## Πλήρες παράδειγμα από την αρχή μέχρι το τέλος

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο script που ενσωματώνει όλες τις βέλτιστες πρακτικές που συζητήθηκαν παραπάνω. Αντικαταστήστε το `YOUR_DIRECTORY` με τον πραγματικό φάκελο που περιέχει τα αρχεία Word σας.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**Αναμενόμενο αποτέλεσμα:**  
Όταν ανοίξετε το `output.docx`, το πρώτο γράφημα εμφανίζει το οπτικό θέμα που ορίζεται από το `STYLE_5`. Όλα τα σημεία δεδομένων, οι άξονες και οι υπομνήματα παραμένουν αμετάβλητα, αποδεικνύοντας ότι η μορφοποίηση είναι ανεξάρτητη από τα υποκείμενα δεδομένα.

## Συμπέρασμα

Τώρα ξέρετε **how to style chart** σε έγγραφο Word χρησιμοποιώντας Python. Το tutorial κάλυψε πώς να **load word document python**, να ανακτήσετε το σχήμα του γραφήματος, να **apply predefined chart style**, και να αποθηκεύσετε το ενημερωμένο αρχείο. Με αυτά τα δομικά στοιχεία μπορείτε να αυτοματοποιήσετε τη δημιουργία αναφορών, να επιβάλετε εταιρική ταυτότητα ή να επεξεργαστείτε μαζικά δεκάδες έγγραφα χωρίς χειροκίνητη προσπάθεια.

Στη συνέχεια, εξερευνήστε άλλες προσαρμογές γραφήματος όπως η αλλαγή χρωμάτων σειρών, η προσθήκη ετικετών δεδομένων ή η εξαγωγή του γραφήματος ως εικόνα. Ανατρέξτε στην τεκμηρίωση της Aspose.Words για θέματα όπως **apply chart style word**, **chart data manipulation**, και **document conversion** ώστε να επεκτείνετε τις δυνατότητες αυτοματοποίησής σας.

Μη διστάσετε να πειραματιστείτε με διαφορετικές τιμές `ChartStyle` και να ενσωματώσετε αυτό το script σε μεγαλύτερους pipelines που δημιουργούν αναφορές Word από βάσεις δεδομένων ή APIs. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή Στήλης Γραφήματος σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Εισαγωγή Απλού Στήλης Γραφήματος σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Εισαγωγή Γραφήματος Περιοχής σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}