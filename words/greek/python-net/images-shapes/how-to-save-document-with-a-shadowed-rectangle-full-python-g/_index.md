---
category: general
date: 2026-06-17
description: Μάθετε πώς να αποθηκεύσετε ένα έγγραφο ενώ προσθέτετε μια προσαρμοσμένη
  σκιά σε σχήμα ορθογωνίου στην Python χρησιμοποιώντας το Aspose.Words. Περιλαμβάνει
  πώς να προσθέσετε σκιά, να δημιουργήσετε ορθογώνιο, να εφαρμόσετε σκιά και να ορίσετε
  τη διαφάνεια.
draft: false
keywords:
- how to save document
- how to add shadow
- how to create rectangle
- how to apply shadow
- how to set opacity
language: el
og_description: Οδηγός βήμα‑προς‑βήμα για το πώς να αποθηκεύσετε ένα έγγραφο, να προσθέσετε
  σκιά, να δημιουργήσετε ορθογώνιο, να εφαρμόσετε σκιά και να ορίσετε τη διαφάνεια
  χρησιμοποιώντας το Aspose.Words για Python.
og_title: Πώς να αποθηκεύσετε ένα έγγραφο με σκιώδες ορθογώνιο – Πλήρες μάθημα Python
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to save document while adding a custom shadow to a rectangle
    shape in Python using Aspose.Words. Includes how to add shadow, create rectangle,
    apply shadow, and set opacity.
  headline: How to Save Document with a Shadowed Rectangle – Full Python Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Automation
title: Πώς να αποθηκεύσετε ένα έγγραφο με σκιώδες ορθογώνιο – Πλήρης οδηγός Python
url: /el/python/images-shapes/how-to-save-document-with-a-shadowed-rectangle-full-python-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε ένα έγγραφο με ένα σκιώδες ορθογώνιο – Πλήρης οδηγός Python

Έχετε αναρωτηθεί ποτέ **πώς να αποθηκεύσετε ένα έγγραφο** που περιέχει ένα όμορφα σκιώδες ορθογώνιο; Ίσως να δημιουργείτε έναν γεννήτορα αναφορών και χρειάζεστε αυτό το επιπλέον οπτικό αποτέλεσμα—δεν είστε μόνοι. Σε αυτό το σεμινάριο θα περάσουμε από **πώς να προσθέσετε σκιά** σε ένα σχήμα, **πώς να δημιουργήσετε ορθογώνιο**, **πώς να εφαρμόσετε σκιά**, και τελικά **πώς να ορίσετε τη διαφάνεια** πριν πραγματικά **αποθηκεύσουμε το έγγραφο**.

Θα χρησιμοποιήσουμε το Aspose.Words for Python via .NET, μια ισχυρή βιβλιοθήκη που σας επιτρέπει να χειρίζεστε αρχεία Word χωρίς εγκατεστημένο Office. Στο τέλος αυτού του οδηγού θα έχετε ένα έτοιμο‑για‑εκτέλεση script που παράγει ένα *.docx* με ένα ορθογώνιο που φαίνεται να έχει σηκωθεί από τη σελίδα. Χωρίς περιττές πληροφορίες, μόνο μια πρακτική, ολοκληρωμένη λύση.

## Τι θα μάθετε

- Ο ακριβής κώδικας που χρειάζεται για να **δημιουργήσετε ένα ορθογώνιο** σχήμα προγραμματιστικά.  
- Πώς να ενεργοποιήσετε ένα **προσαρμοσμένο εφέ σκιάς** και να ρυθμίσετε το θολό, την απόσταση, την κατεύθυνση, το χρώμα και τη **διαφάνεια**.  
- Η ακριβής κλήση που **αποθηκεύει το έγγραφο** στο δίσκο, συμπεριλαμβανομένων των παραμέτρων διαδρομής φακέλου.  
- Συμβουλές για την προσαρμογή των παραμέτρων της σκιάς για διαφορετικά οπτικά στυλ.  

**Προαπαιτούμενα:** Python 3.8+, Aspose.Words for Python via .NET (εγκατάσταση με `pip install aspose-words`), και ένας φάκελος με δικαιώματα εγγραφής στον υπολογιστή σας. Αυτό είναι όλο—χωρίς επιπλέον εξαρτήσεις.

![Screenshot showing how to save document with a shadowed rectangle](shadowed_rectangle.png "how to save document with a shadowed rectangle")

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή του Aspose.Words

Πριν εμβαθύνουμε στα σχήματα, ας βεβαιωθούμε ότι η βιβλιοθήκη είναι διαθέσιμη.

```python
# Install Aspose.Words if you haven’t already:
# pip install aspose-words

import aspose.words as aw
```

> **Συμβουλή:** Χρησιμοποιήστε ένα εικονικό περιβάλλον ώστε η παγκόσμια εγκατάσταση του Python να παραμένει καθαρή. Επίσης, διευκολύνει τον καθορισμό της έκδοσης του Aspose.Words που δοκιμάσατε.

## Βήμα 2: Πώς να δημιουργήσετε σχήμα ορθογωνίου

Η δημιουργία ενός ορθογωνίου είναι η βάση—χωρίς σχήμα δεν υπάρχει τίποτα για να σκιάσει. Η κλάση `DocumentBuilder` μας παρέχει έναν άμεσο τρόπο να εισάγουμε σχήματα απευθείας στο έγγραφο.

```python
# Step 2: Create a new blank document and a builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert a rectangle of 200x100 points (about 2.78 x 1.39 inches)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

**Γιατί είναι σημαντικό:** Η μέθοδος `insert_shape` επιστρέφει ένα αντικείμενο `Shape` που μπορούμε να τροποποιήσουμε αργότερα. Οι διαστάσεις εκφράζονται σε σημεία (1 pt = 1/72 in), κάτι που σας δίνει ακριβή έλεγχο στο τελικό μέγεθος.

### Προσαρμογή του Ορθογωνίου (Προαιρετικό)

Ίσως θέλετε να αλλάξετε το γέμισμα ή το περίγραμμα:

```python
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0  # points
rectangle.line_format.color = aw.drawing.Color.dark_blue
```

Αυτές οι γραμμές είναι προαιρετικές αλλά δείχνουν πώς μπορείτε να μορφοποιήσετε το ορθογώνιο πριν προσθέσετε σκιά.

## Βήμα 3: Πώς να προσθέσετε σκιά – Ενεργοποίηση του εφέ

Τώρα το διασκεδαστικό μέρος: η προσθήκη σκιάς. Το Aspose.Words εκθέτει μια ιδιότητα `shadow_effect` που περιέχει όλες τις ρυθμίσεις σκιάς.

```python
# Step 3: Enable and configure a custom shadow for the rectangle
shadow = rectangle.shadow_effect
shadow.enabled = True               # Turn the shadow on
shadow.blur_radius = 5.0            # Softness of the shadow edge (points)
shadow.distance = 3.0               # How far the shadow is offset (points)
shadow.direction = 45               # Angle in degrees (0 = left, 90 = down)
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6                # 60% opaque – this is where we **how to set opacity**
```

**Γιατί ορίζουμε κάθε ιδιότητα:**

- **`blur_radius`** μαλακώνει την άκρη, κάνοντας τη σκιά να φαίνεται πιο φυσική.  
- **`distance`** μετακινεί τη σκιά μακριά από το σχήμα· μια μεγαλύτερη τιμή δημιουργεί το εφέ «πλωματικό».  
- **`direction`** καθορίζει από πού προέρχεται η πηγή φωτός—45° δίνει μια διαγώνια πτώση.  
- **`color`** και **`opacity`** ελέγχουν το οπτικό βάρος· ένα ημιδιαφανές μαύρο λειτουργεί καλά στα περισσότερα έγγραφα.  

### Ακραίες περιπτώσεις & Παραλλαγές

- **Πολύ μεγάλο θολό:** Αν ορίσετε `blur_radius` πάνω από 20, η σκιά μπορεί να γίνει αδιάκριτη από το σχήμα—χρησιμοποιήστε το με μέτρο.  
- **Πλήρης διαφάνεια:** Ορίζοντας `opacity = 1.0` δημιουργεί μια στερεή μαύρη σκιά· καλό για δραματικούς τίτλους.  
- **Χωρίς θολό:** `blur_radius = 0` δημιουργεί μια καθαρή, σκληρή άκρη σκιάς, που θυμίζει διανυσματικά γραφικά.  

## Βήμα 4: Πώς να εφαρμόσετε τις ρυθμίσεις σκιάς και να αποθηκεύσετε το έγγραφο

Με το ορθογώνιο και τη σκιά του διαμορφωμένα, το τελευταίο βήμα είναι η αποθήκευση του αρχείου. Εδώ τελικά απαντάμε στο **πώς να αποθηκεύσετε ένα έγγραφο**.

```python
# Step 4: Save the document with the shadowed rectangle
output_path = "output/shadowed_rectangle.docx"
document.save(output_path)

print(f"Document saved successfully at: {output_path}")
```

**Σημαντικές σημειώσεις για την αποθήκευση:**

- Ο φάκελος (`output/` στο παράδειγμα) πρέπει να υπάρχει· διαφορετικά το `document.save` πετάει `FileNotFoundError`. Χρησιμοποιήστε `os.makedirs('output', exist_ok=True)` εκ των προτέρων αν χρειάζεται να τον δημιουργήσετε προγραμματιστικά.  
- Το Aspose.Words καθορίζει αυτόματα τη μορφή αρχείου από την επέκταση, έτσι το `.docx` σας δίνει ένα σύγχρονο έγγραφο Word. Μπορείτε επίσης να αποθηκεύσετε ως `.pdf` αλλάζοντας την επέκταση.  

## Πλήρες Script – Όλα τα Βήματα σε Ένα Σημείο

Συνδυάζοντας όλα, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση script:

```python
import os
import aspose.words as aw

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# 1️⃣ Create a blank document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle (200x100 points)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional styling (feel free to comment out)
rectangle.fill_color = aw.drawing.Color.light_blue
rectangle.line_format.width = 2.0
rectangle.line_format.color = aw.drawing.Color.dark_blue

# 3️⃣ Configure shadow effect
shadow = rectangle.shadow_effect
shadow.enabled = True
shadow.blur_radius = 5.0
shadow.distance = 3.0
shadow.direction = 45
shadow.color = aw.drawing.Color.black
shadow.opacity = 0.6  # How to set opacity

# 4️⃣ Save the document (how to save document)
output_file = "output/shadowed_rectangle.docx"
document.save(output_file)

print(f"Document saved successfully at: {output_file}")
```

Εκτελώντας αυτό το script παράγει το `output/shadowed_rectangle.docx`. Ανοίξτε το στο Microsoft Word και θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο με μια διακριτική, ημιδιαφανή μαύρη σκιά που κατευθύνεται κάτω‑δεξιά.

## Συχνές Ερωτήσεις & Παγίδες

- **«Μπορώ να χρησιμοποιήσω διαφορετικό τύπο σχήματος;»** Απόλυτα. Αντικαταστήστε το `aw.drawing.ShapeType.RECTANGLE` με `CIRCLE`, `ELLIPSE` ή οποιαδήποτε άλλη υποστηριζόμενη τιμή enum. Το API σκιάς λειτουργεί με τον ίδιο τρόπο.  
- **«Τι γίνεται αν χρειάζομαι διαφορετικό χρώμα σκιάς;»** Απλώς ορίστε `shadow.color` σε οποιοδήποτε `aw.drawing.Color` θέλετε, π.χ., `aw.drawing.Color.gray`.  
- **«Η τιμή της διαφάνειας είναι πάντα μεταξύ 0 και 1;»** Ναι. Τιμές εκτός αυτού του εύρους περιορίζονται, αλλά είναι καλύτερο να παραμένετε στο διάστημα 0‑1 για προβλέψιμα αποτελέσματα.  
- **«Πρέπει να καλέσω `document.update_page_layout()` πριν την αποθήκευση;»** Όχι. Το Aspose.Words διαχειρίζεται τη διάταξη αυτόματα κατά την αποθήκευση, αν και μπορείτε να το καλέσετε χειροκίνητα αν κάνετε βαριές τροποποιήσεις και χρειάζεστε ενδιάμεσες πληροφορίες διάταξης.  

## Επόμενα Βήματα – Πού να Πηγαίνετε Από Εδώ

Τώρα που ξέρετε **πώς να αποθηκεύσετε ένα έγγραφο** με σκιώδες ορθογώνιο, μπορείτε να εξερευνήσετε:

- **Πώς να προσθέσετε σκιά** σε άλλα στοιχεία όπως εικόνες ή πλαίσια κειμένου.  
- **Πώς να δημιουργήσετε ορθογώνιο** με διαβαθμισμένα γέμισμα για πιο πλούσια οπτικά στοιχεία.  
- **Πώς να εφαρμόσετε σκιά** δυναμικά βάσει εισόδου χρήστη (π.χ., επιτρέποντας σε ένα UI να ελέγχει το blur radius).  
- **Πώς να ορίσετε τη διαφάνεια** για πολλαπλά επικαλυπτόμενα σχήματα ώστε να πετύχετε εφέ βάθους.  

Κάθε ένα από αυτά τα θέματα βασίζεται στις ίδιες βασικές έννοιες που καλύψαμε, οπότε είστε καλά προετοιμασμένοι να επεκτείνετε τη λύση.

**Συμπέρασμα:** Μόλις κατακτήσατε τη πλήρη ροή εργασίας—από τη δημιουργία ενός ορθογωνίου, τη διαμόρφωση της σκιάς του, την προσαρμογή της διαφάνειας, μέχρι τελικά **πώς να αποθηκεύσετε ένα έγγραφο** με όλες αυτές τις ρυθμίσεις αμετάβλητες. Δοκιμάστε το, τροποποιήστε τις παραμέτρους και παρακολουθήστε τα αρχεία Word σας να αποκτούν επαγγελματική, τρισδιάστατη εμφάνιση.

Καλό κώδικα, και μη διστάσετε να αφήσετε ένα σχόλιο αν συναντήσετε κάποιο πρόβλημα!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Κενής Εγγράφου Word με Σκιώδες Ορθογώνιο Σχήμα – Οδηγός Βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Πώς να Αποθηκεύσετε Markdown από Word – Πλήρης Οδηγός Python](/words/english/python-net/document-conversion/how-to-save-markdown-from-word-complete-python-guide/)
- [Πώς να Προσθέσετε Σκιά σε C# – Πλήρης Οδηγός Προγραμματισμού](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}