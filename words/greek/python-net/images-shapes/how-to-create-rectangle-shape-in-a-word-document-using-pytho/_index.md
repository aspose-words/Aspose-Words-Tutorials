---
category: general
date: 2026-09-30
description: Μάθετε πώς να δημιουργήσετε σχήμα ορθογωνίου, να εφαρμόσετε σκιά στο
  σχήμα και να αποθηκεύσετε το Word με το σχήμα χρησιμοποιώντας το Aspose.Words για
  Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: el
lastmod: 2026-09-30
og_description: Δημιουργήστε γρήγορα σχήμα ορθογωνίου σε έγγραφο Word. Αυτό το σεμινάριο
  δείχνει πώς να προσθέσετε σχήμα, να εφαρμόσετε σκιά στο σχήμα, να ορίσετε τη θόλωση
  της σκιάς και να αποθηκεύσετε το Word με το σχήμα.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Δημιουργία σχήματος ορθογωνίου στο Word με Python – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Πώς να δημιουργήσετε σχήμα ορθογωνίου σε έγγραφο Word χρησιμοποιώντας Python
url: /el/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε σχήμα ορθογωνίου σε έγγραφο Word χρησιμοποιώντας Python

Αν χρειάζεται να **δημιουργήσετε σχήμα ορθογωνίου** σε αρχείο Word, αυτός ο οδηγός σας παρουσιάζει μια πλήρη, εκτελέσιμη λύση. Θα δείτε πώς να προσθέσετε το σχήμα, να εφαρμόσετε εφέ σκιάς, να ρυθμίσετε το θόλωση και, τέλος, **να αποθηκεύσετε το Word με το σχήμα** ώστε το αποτέλεσμα να μπορεί να ανοιχθεί στο Microsoft Word ή σε οποιονδήποτε συμβατό προβολέα.

Το παράδειγμα χρησιμοποιεί **Aspose.Words for Python via .NET**, μια βιβλιοθήκη που σας επιτρέπει να διαχειρίζεστε έγγραφα Word χωρίς εγκατεστημένο Microsoft Office. Δεν απαιτείται προηγούμενη εμπειρία με το API—απλώς βασικές γνώσεις Python.

## Τι θα πετύχετε

- Εισαγωγή ενός ορθογωνίου στην πρώτη ενότητα ενός νέου εγγράφου.  
- Διαμόρφωση μιας ήπιας σκιάς ορίζοντας το θόλωμά της, την απόσταση και το χρώμα.  
- Αποθήκευση του εγγράφου στο δίσκο και επαλήθευση του οπτικού αποτελέσματος.

## Προαπαιτούμενα

- Python 3.8 ή νεότερη.  
- Πακέτο `aspose-words` εγκατεστημένο (`pip install aspose-words`).  
- Δικαίωμα εγγραφής στον φάκελο εξόδου.

## Δημιουργία σχήματος ορθογωνίου και διαμόρφωση εμφάνισής του

Το πρώτο βήμα είναι η δημιουργία ενός κενών εγγράφου και η προσθήκη σε αυτό ενός σχήματος ορθογωνίου. Το σχήμα θα λειτουργήσει ως καμβάς για το εφέ σκιάς.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Γιατί είναι σημαντικό:**  
Η δημιουργία του ορθογωνίου σας παρέχει ένα συγκεκριμένο αντικείμενο (`shape`) που μπορείτε αργότερα να μορφοποιήσετε. Ορίζοντας ρητές διαστάσεις διασφαλίζετε ότι το σχήμα θα φαίνεται το ίδιο σε κάθε πλατφόρμα.

## Πώς να προσθέσετε σχήμα σε έγγραφο Word

Αν και ο παραπάνω κώδικας προσθέτει ήδη το ορθογώνιο, μπορεί να χρειαστεί να προσθέσετε επιπλέον σχήματα (π.χ. κύκλους, βέλη) αργότερα. Η ίδια λογική ισχύει: καλέστε `append_child` στο σώμα του εγγράφου και περάστε το επιθυμητό `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Συμβουλή:** Χρησιμοποιήστε την απαρίθμηση `ShapeType` για να εξερευνήσετε όλα τα υποστηριζόμενα σχήματα. Αυτό κρατά τον κώδικά σας ευανάγνωστο και αποφεύγει «μαγικούς» αριθμούς.

## Εφαρμογή σκιάς στο σχήμα και ορισμός θόλωσης σκιάς

Μια σκιά προσθέτει βάθος και οπτικό ενδιαφέρον. Η κλάση `ShadowEffect` σας επιτρέπει να ελέγξετε το θόλωμα, την απόσταση και το χρώμα. Παρακάτω εφαρμόζουμε μια ήπια μαύρη σκιά στο ορθογώνιο.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Γιατί να ορίσετε θόλωμα;**  
Το `blur` καθορίζει πόσο διασκορπισμένη φαίνεται η σκιά. Μια χαμηλή τιμή (π.χ. 1.0) δίνει έντονη άκρη, ενώ μια υψηλότερη τιμή (π.χ. 5.0) δημιουργεί απαλό ξεθώριασμα, που συχνά είναι πιο αισθητικά ευχάριστο.

**Ακραία περίπτωση:** Αν ορίσετε `blur` στο 0, η σκιά γίνεται στερεό σιλουέτα. Κάποιοι προβολείς μπορεί να την αποδώσουν με εφέ aliasing, γι’ αυτό επιλέξτε τιμή μεγαλύτερη του 0 για πιο ομαλή απόδοση.

## Αποθήκευση Word με σχήμα

Η αποθήκευση του εγγράφου ολοκληρώνει όλες τις αλλαγές. Η μέθοδος `save` γράφει ένα αρχείο `.docx` που μπορεί να ανοίξει οποιοσδήποτε σύγχρονος επεξεργαστής Word.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Όταν ανοίξετε το `output.docx`, θα δείτε ένα ορθογώνιο τοποθετημένο ένα ίντσα από την επάνω‑αριστερή γωνία, με μια ήπια μαύρη σκιά μετατοπισμένη δύο σημεία προς τα δεξιά και κάτω. Η θόλωση της σκιάς κάνει το σχήμα να φαίνεται ότι "προεξέχει" από τη σελίδα.

**Επαγγελματική συμβουλή:** Αν χρειάζεται να δημιουργήσετε πολλά έγγραφα σε βρόχο, επαναχρησιμοποιήστε το ίδιο αντικείμενο `Document` και καθαρίστε το σώμα του μεταξύ των επαναλήψεων για μείωση του φορτίου μνήμης.

## Συχνές παραλλαγές και αντιμετώπιση προβλημάτων

| Κατάσταση | Τι να αλλάξετε | Λόγος |
|-----------|----------------|--------|
| Διαφορετικό χρώμα σκιάς | `shadow.color = aw.Color.red` | Χρησιμοποιήστε χρώματα της μάρκας ή τονίστε σημαντικά σχήματα. |
| Μεγαλύτερη απόσταση σκιάς | Αυξήστε `shadow.offset_x`/`offset_y` | Τονίζει το βάθος για προσαρμογές UI. |
| Καμία σκιά | Παραλείψτε τη γραμμή `shape.shadow = shadow` | Χρήσιμο για μινιμαλιστικές αναφορές. |
| Εξαγωγή σε PDF αντί για DOCX | `doc.save("output.pdf")` | Το PDF είναι ιδανικό για διανομή μόνο για ανάγνωση. |

Αν το σχήμα δεν εμφανίζεται, ελέγξτε ότι το προσθέτετε στην σωστή ενότητα (`get_first_section()`) και ότι το έγγραφο αποθηκεύεται μετά τις τροποποιήσεις.

## Πλήρες, εκτελέσιμο παράδειγμα

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Η εκτέλεση του script παράγει το `output.docx` που περιέχει το ορθογώνιο με ήπια σκιά. Ανοίξτε το αρχείο στο Microsoft Word για να επιβεβαιώσετε ότι το οπτικό αποτέλεσμα ταιριάζει με την περιγραφή.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε σχήμα ορθογωνίου**, **πώς να προσθέσετε σχήμα** σε έγγραφο Word, **να εφαρμόσετε σκιά στο σχήμα**, **να ορίσετε θόλωμα σκιάς**, και τέλος **να αποθηκεύσετε το Word με σχήμα** χρησιμοποιώντας το Aspose.Words for Python. Το ίδιο μοτίβο μπορεί να επεκταθεί σε άλλους τύπους σχημάτων, χρώματα και εφέ, δίνοντάς σας πλήρη έλεγχο στα γραφικά του εγγράφου χωρίς εξάρτηση από αυτοματισμούς του Office.

**Επόμενα βήματα**

- Πειραματιστείτε με το `Shape.fill` για προσθήκη διαβαθμίσεων ή εικόνων φόντου.  
- Χρησιμοποιήστε αντικείμενα `Paragraph` για τοποθέτηση κειμένου μέσα στο ορθογώνιο.  
- Συνδυάστε πολλαπλά σχήματα για δημιουργία σύνθετων διαγραμμάτων, έπειτα εξαγάγετε σε PDF για διανομή.  

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα στις δικές σας ανάγκες αναφοράς ή προτύπων, και μοιραστείτε τα αποτελέσματά σας στα σχόλια!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}