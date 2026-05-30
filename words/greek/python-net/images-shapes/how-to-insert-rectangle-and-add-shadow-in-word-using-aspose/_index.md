---
category: general
date: 2026-05-30
description: Πώς να εισάγετε ένα ορθογώνιο και να προσθέσετε σκιά στο Word χρησιμοποιώντας
  το Aspose – ένας βήμα‑προς‑βήμα οδηγός Python για τη δημιουργία εγγράφου Word με
  εφέ σκιάς σχήματος.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: el
og_description: Πώς να εισάγετε ένα ορθογώνιο σχήμα και να προσθέσετε σκιά στο Word
  χρησιμοποιώντας το Aspose – μάθετε πώς να δημιουργήσετε ένα έγγραφο Word με εφέ
  σκιά σχήματος σε Python.
og_title: Πώς να εισάγετε ένα ορθογώνιο και να προσθέσετε σκιά στο Word χρησιμοποιώντας
  το Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Πώς να εισάγετε ορθογώνιο και να προσθέσετε σκιά στο Word χρησιμοποιώντας το
  Aspose
url: /el/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισάγετε ορθογώνιο και να προσθέσετε σκιά στο Word χρησιμοποιώντας το Aspose

Έχετε αναρωτηθεί ποτέ **πώς να εισάγετε ορθογώνιο** σε ένα αρχείο Word χωρίς να ανοίξετε το UI; Δεν είστε μόνοι. Πολλοί προγραμματιστές χρειάζονται να δημιουργούν αναφορές, τιμολόγια ή πιστοποιητικά επί τόπου, και η σχεδίαση ενός απλού ορθογωνίου με ωραία σκιά μπορεί να κάνει το αποτέλεσμα πιο επαγγελματικό. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από τη δημιουργία ενός εγγράφου Word, την προσθήκη ενός σχήματος ορθογωνίου, και την εφαρμογή μιας ρεαλιστικής σκιάς χρησιμοποιώντας το Aspose.Words for Python.

Θα καλύψουμε τα πάντα, από τη ρύθμιση του πακέτου Aspose μέχρι τη ρύθμιση της απόστασης, της θολότητας και της αδιαφάνειας της σκιάς. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε pipeline αυτοματοποίησης. Χωρίς μαγεία, μόνο καθαρός κώδικας και μερικές πρακτικές συμβουλές.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- Εγκατεστημένο Python 3.8+ (ο κώδικας λειτουργεί σε 3.9, 3.10 και νεότερες εκδόσεις)
- Ένα ενεργό license του Aspose.Words for Python ή ένα δωρεάν κλειδί αξιολόγησης
- Το πακέτο `aspose-words` εγκατεστημένο μέσω `pip install aspose-words`
- Έναν φάκελο με δικαιώματα εγγραφής όπου θα αποθηκευτεί το **create word document aspose** που θα δημιουργηθεί

Αυτό είναι όλο—χωρίς επιπλέον DLLs, χωρίς COM interop, μόνο καθαρό Python.

## Βήμα 1: Αρχικοποίηση του Εγγράφου (Πώς να δημιουργήσετε έγγραφο Word με Aspose)

Πρώτα απ' όλα: χρειάζεστε ένα νέο αντικείμενο `Document`. Σκεφτείτε το ως ένα κενό καμβά. Ο παρακάτω κώδικας δημιουργεί το έγγραφο και έναν `DocumentBuilder` που θα μας επιτρέψει να εισάγουμε σχήματα.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Γιατί είναι σημαντικό:* Ο `DocumentBuilder` σας παρέχει ένα υψηλού επιπέδου API για την προσθήκη παραγράφων, πινάκων και—ναι—σχημάτων χωρίς να ασχολείστε με δέντρα κόμβων χαμηλού επιπέδου. Αν παραλείψετε τον builder και χειριστείτε απευθείας τους κόμβους, θα καταλήξετε με πολύπλοκο κώδικα που είναι πιο δύσκολο στη συντήρηση.

## Βήμα 2: Εισαγωγή του Ορθογωνίου (πώς να εισάγετε ορθογώνιο)

Τώρα πράγματι **πώς να εισάγετε ορθογώνιο**. Το Aspose.Words αντιμετωπίζει ένα ορθογώνιο ως γενικό τύπο σχήματος. Καθορίζετε το πλάτος και το ύψος σε points (1 point ≈ 1/72 inch). Αλλάξτε ελεύθερα τους αριθμούς ώστε να ταιριάζουν στο layout σας.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tip:** Αν χρειάζεται το ορθογώνιο να τοποθετηθεί σε συγκεκριμένη θέση στη σελίδα, ορίστε `shape.left` και `shape.top` μετά την εισαγωγή. Αυτό σας δίνει έλεγχο pixel‑perfect.

## Βήμα 3: Πρόσβαση στο ShadowFormat του Σχήματος (προσθήκη σκιάς στο σχήμα)

Η οπτική εμφάνιση ενός σχήματος βρίσκεται στο `ShadowFormat`. Ανακτώντας το, αποκτούμε πρόσβαση σε κάθε ιδιότητα που ορίζει την εμφάνιση της σκιάς.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

Σε αυτό το σημείο η σκιά είναι αόρατη—σκεφτείτε το ως κρυφό στρώμα που περιμένει τις οδηγίες σας.

## Βήμα 4: Διαμόρφωση της Σκιάς (πώς να προσθέσετε σκιά σχήματος, εφαρμόστε εφέ σκιάς στο Word)

Εδώ συμβαίνει η μαγεία. Θα ενεργοποιήσουμε τη σκιά και θα ρυθμίσουμε την εμφάνισή της. Οι τιμές παρακάτω παράγουν μια ήπια, διαγώνια σκιά που λειτουργεί καλά για τα περισσότερα έγγραφα, αλλά μπορείτε να πειραματιστείτε.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Τι κάνει κάθε ιδιότητα

| Ιδιότητα | Επίδραση | Τυπικό εύρος |
|----------|----------|--------------|
| `visible` | Ενεργοποίηση/απενεργοποίηση της σκιάς | `True` / `False` |
| `distance` | Απόσταση της σκιάς από το σχήμα | 2 – 10 pts |
| `blur` | Απαλότητα των άκρων της σκιάς | 4 – 12 pts |
| `color` | Χρώμα σκιάς· το σκούρο γκρι είναι ασφαλές προεπιλογή | Οποιοδήποτε `aw.Color` |
| `opacity` | Διαφάνεια· 0 = αόρατη, 1 = αδιαφανής | 0.3 – 0.8 για ήπιο αποτέλεσμα |
| `angle` | Κατεύθυνση του φωτός | 0 – 360° |

**Γιατί να ρυθμίσετε αυτά;** Μια καλά ρυθμισμένη σκιά μπορεί να κάνει ένα επίπεδο ορθογώνιο να φαίνεται ανυψωμένο από τη σελίδα, προσθέτοντας βάθος χωρίς εικόνες. Αν ορίσετε `opacity` πολύ υψηλό, η σκιά φαίνεται σκληρή· πολύ χαμηλό και εξαφανίζεται.

## Βήμα 5: Αποθήκευση του Εγγράφου (δημιουργία εγγράφου Word με Aspose)

Τέλος, γράψτε το αρχείο στο δίσκο. Μπορείτε να χρησιμοποιήσετε οποιαδήποτε επέκταση υποστηρίζεται από το Aspose.Words (`.docx`, `.pdf`, `.html`). Για αυτό το tutorial θα παραμείνουμε στο `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word και θα δείτε ένα καθαρό ορθογώνιο με ήπια σκιά—ακριβώς αυτό που θα περιμένατε από ένα επαγγελματικά σχεδιασμένο πρότυπο.

![how to insert rectangle shape with shadow using Aspose.Words](/images/rectangle-shadow.png){alt="πώς να εισάγετε σχήμα ορθογωνίου με σκιά χρησιμοποιώντας το Aspose.Words"}

*Το screenshot (παραπάνω) δείχνει το ορθογώνιο με την εφαρμοσμένη σκιά. Παρατηρήστε τη ήπια θολότητα και τη γωνία 45°, που δίνει φυσική εμφάνιση.*

## Συνηθισμένες Παραλλαγές και Edge Cases

### Προσθήκη Πολλαπλών Σχημάτων

Αν χρειάζεστε περισσότερα από ένα ορθογώνια, απλώς επαναλάβετε την κλήση `insert_shape`. Θυμηθείτε να μετακινήσετε τον κέρσορα του builder (`builder.move_to(shape)`) ή να προσαρμόσετε `shape.left`/`shape.top` ώστε να αποφύγετε την επικάλυψη.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Αλλαγή Τύπου Σχήματος

Αν και αυτός ο οδηγός εστιάζει στα ορθογώνια, το ίδιο μοτίβο λειτουργεί για ωοειδή, αστέρια ή προσαρμοσμένα ελεύθερα σχήματα. Αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.OVAL`, `ShapeType.CLOUD` κ.λπ., και οι ρυθμίσεις σκιάς παραμένουν ίδιες.

### Αποθήκευση σε Άλλες Μορφές

Το Aspose.Words μπορεί να εξάγει σε PDF, PNG ή ακόμη και XPS με μία μόνο γραμμή:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Η απόδοση της σκιάς διατηρείται σε όλες τις μορφές, έτσι το PDF σας θα φαίνεται ακριβώς όπως το αρχείο Word.

### Διαχείριση Μεγάλων Εγγράφων

Όταν δημιουργείτε τεράστιες αναφορές, σκεφτείτε να καλέσετε `doc.update_page_layout()` μετά την εισαγωγή όλων των σχημάτων. Αυτό αναγκάζει μια διέλευση διάταξης και μπορεί να βελτιώσει την απόδοση όταν μετατρέπετε αργότερα σε PDF.

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα Συνδυασμένα)

Παρακάτω είναι το πλήρες script που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα αρχείο με όνομα `rectangle_shadow.py`. Εκτελέστε το με `python rectangle_shadow.py` και ελέγξτε το φάκελο `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Η εκτέλεση αυτού του script παράγει ακριβώς το ίδιο έγγραφο που συζητήσαμε νωρίτερα. Μη διστάσετε να τροποποιήσετε τις τιμές· ο κώδικας είναι σκόπιμα απλός ώστε να πειραματιστείτε χωρίς φόβο.

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό σε Linux;**

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}