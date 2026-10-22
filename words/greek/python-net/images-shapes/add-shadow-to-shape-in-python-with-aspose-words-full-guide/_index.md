---
category: general
date: 2026-06-30
description: Προσθέστε σκιά σε σχήμα χρησιμοποιώντας το Aspose.Words για Python. Μάθετε
  πώς να ορίσετε την απόσταση της σκιάς, να προσαρμόσετε το θόλωμα και να αποθηκεύσετε
  γρήγορα ένα PDF με σκιά στο σχήμα.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: el
og_description: Προσθέστε σκιά σε σχήμα σε έγγραφο Word με το Aspose.Words για Python.
  Αυτό το σεμινάριο δείχνει πώς να ορίσετε την απόσταση της σκιάς, τη θόλωση και το
  χρώμα, και στη συνέχεια να αποθηκεύσετε ως PDF.
og_title: Προσθήκη σκιάς σε σχήμα με Python – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Προσθήκη Σκιάς σε Σχήμα σε Python με το Aspose.Words – Πλήρης Οδηγός
url: /el/python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Σκιάς σε Σχήμα σε Python με Aspose.Words – Πλήρης Οδηγός

Η προσθήκη σκιάς σε σχήμα σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words για Python είναι πιο εύκολη απ' ό,τι νομίζετε. Αν ποτέ αναρωτηθήκατε **πώς να ορίσετε την απόσταση σκιάς** ή **πώς να προσθέσετε σκιά σε σχήμα** για ένα επαγγελματικό αποτέλεσμα, αυτός ο οδηγός σας καλύπτει.

Στα επόμενα λίγα λεπτά θα περάσουμε από όλα όσα χρειάζεστε: από τη δημιουργία ενός νέου εγγράφου, την εισαγωγή ενός ορθογωνίου, την προσαρμογή των ιδιοτήτων της σκιάς, μέχρι την τελική αποθήκευση ενός PDF που παρουσιάζει το εφέ. Στο τέλος θα μπορείτε να προσθέσετε σκιά σε οποιοδήποτε σχήμα—ορθογώνιο, έλλειψη ή προσαρμοσμένο σχέδιο—χωρίς να ψάχνετε στα έγγραφα του API.

> **Απαιτούμενα** – Θα πρέπει να έχετε εγκατεστημένο το Python 3.7+, άδεια Aspose.Words for Python (ή δωρεάν αξιολόγηση) και βασική εξοικείωση με το scripting σε Python. Δεν απαιτούνται άλλες εξωτερικές βιβλιοθήκες.

---

## Προσθήκη Σκιάς σε Σχήμα – Βήμα-Βήμα Επισκόπηση

Below is a quick roadmap of what we’ll accomplish:

1. **Δημιουργήστε ένα νέο έγγραφο** και ένα `DocumentBuilder` για να το επεξεργαστείτε.  
2. **Εισάγετε ένα σχήμα ορθογωνίου** με το μέγεθος που χρειάζεστε.  
3. **Ενεργοποιήστε και προσαρμόστε τη σκιά** – εδώ λάμπει η κύρια λέξη-κλειδί.  
4. **Αποθηκεύστε το έγγραφο** ως PDF που διατηρεί τη σκιά του σχήματος.

Each step is broken out into its own section, so you can copy‑paste the code snippets directly into your IDE.

---

## Βήμα 1: Αρχικοποίηση του Εγγράφου και του Builder

Πρώτα απ' όλα—χωρίς ένα `Document` δεν έχετε τίποτα πάνω στο οποίο να εργαστείτε. Το `DocumentBuilder` είναι το πινέλο σας.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Γιατί είναι σημαντικό*: Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ το `DocumentBuilder` απλοποιεί την εισαγωγή κειμένου, πινάκων και σχημάτων. Σκεφτείτε το builder ως έναν κέρσορα που μπορείτε να μετακινήσετε στη σελίδα.

---

## Βήμα 2: Εισαγωγή Σχήματος Ορθογωνίου

Τώρα θα προσθέσουμε ένα ορθογώνιο—τον καμβά μας για το εφέ της σκιάς. Μπορείτε να αντικαταστήσετε το `RECTANGLE` με `ELLIPSE`, `STAR` ή οποιοδήποτε άλλο `ShapeType` αν χρειάζεστε διαφορετική γεωμετρία.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Συμβουλή*: Οι διαστάσεις είναι σε points (1 pt ≈ 1/72 inch). Προσαρμόστε τις ώστε να ταιριάζουν στο layout σας· η σκιά θα κλιμακωθεί αυτόματα.

---

## Πώς να Ορίσετε την Απόσταση Σκιάς

Η **απόσταση** της σκιάς καθορίζει πόσο μακριά εμφανίζεται από το σχήμα. Μεγαλύτερη απόσταση μιμείται μια πηγή φωτός πιο μακριά, ενώ μικρότερη τιμή δίνει μια ήπια ανύψωση.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Σημείωση**: Η απόσταση λειτουργεί μαζί με το `angle`. Η αλλαγή της γωνίας περιστρέφει τη σκιά γύρω από το σχήμα, ενώ η `distance` την ωθεί προς τα έξω.

---

## Πώς να Προσθέσετε Σκιά σε Σχήμα – Προσαρμογή Θολώματος, Χρώματος και Γωνίας

Η προσθήκη σκιάς δεν είναι μόνο το άναψή της· συχνά θέλετε να ρυθμίσετε το θόλωμα, το χρώμα και την κατεύθυνση για ένα ρεαλιστικό αποτέλεσμα.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Γιατί αυτές οι ρυθμίσεις?*  
- **Ακτίνα θολώματος** μαλακώνει την άκρη, αποτρέποντας μια σκληρή σιλουέτα.  
- **Γωνία** προσομοιώνει την πηγή φωτός· 45° είναι μια κοινή προεπιλογή που φαίνεται ισορροπημένη.  
- **Χρώμα** μπορεί να είναι οποιοδήποτε αντικείμενο `Color`; δοκιμάστε `Color.gray` για πιο ήπιο αποτέλεσμα.

---

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF

Μόλις το σχήμα και η σκιά του είναι έτοιμα, η αποθήκευση του αποτελέσματος είναι παιχνιδάκι. Το Aspose.Words διαχειρίζεται αυτόματα τη μετατροπή σε PDF, διατηρώντας την οπτική πιστότητα.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Αναμενόμενο αποτέλεσμα*: Ανοίξτε το παραγόμενο `ShadowShape.pdf`. Θα δείτε μια σελίδα με ένα ορθογώνιο 200 × 100 pt, η σκιά του εκτοξευμένη 4 pt μακριά με γωνία 45°, θολωμένη κατά 5 pt. Η σκιά θα εμφανίζεται ως ένας ήπιος γκρι‑μαύρος άνεμος που αγκαλιάζει το σχήμα.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζομαι διαφορετικό σχήμα;

Αντικαταστήστε το `aw.drawing.ShapeType.RECTANGLE` με οποιαδήποτε άλλη τιμή enum, π.χ., `aw.drawing.ShapeType.ELLIPSE`. Οι ίδιες ιδιότητες σκιάς ισχύουν—δεν χρειάζεται επιπλέον κώδικας.

### Μπορώ να εφαρμόσω σκιά σε πολλά σχήματα ταυτόχρονα;

Ναι. Κάντε βρόχο πάνω στα σχήματα που δημιουργείτε και ρυθμίστε κάθε `shadow_format` ξεχωριστά. Εδώ είναι ένα σύντομο απόσπασμα:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### Πώς αλλάζω τη διαφάνεια της σκιάς;

Χρησιμοποιήστε την ιδιότητα `shadow.transparency` (0 = αδιαφανής, 1 = πλήρως διαφανής):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες script—αντιγράψτε το, προσαρμόστε το φάκελο εξόδου και τρέξτε το. Δεν λείπουν κομμάτια.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Τρέξτε το script, μετά ανοίξτε το παραγόμενο PDF. Θα πρέπει να δείτε το ορθογώνιο με μια καθαρή, εκτοξευμένη σκιά—ακριβώς αυτό που υπόσχεται η **add shadow to shape**.

---

## Συμπέρασμα

Μόλις δείξαμε πώς να **add shadow to shape** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for Python, καλύπτοντας τα βασικά βήματα για **set shadow distance**, προσαρμογή θολώματος, γωνίας και χρώματος, και τελικά εξαγωγή PDF που διατηρεί το εφέ. Αυτή η τεχνική λειτουργεί για οποιονδήποτε τύπο σχήματος, και μπορείτε να την επεκτείνετε με βρόχους, ρυθμίσεις διαφάνειας ή ακόμη και σκιά διαβάθμισης.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να συνδυάσετε πολλαπλές σκιές, να στρώσετε σχήματα ή να δημιουργήσετε μια αναφορά όπου κάθε διάγραμμα παίρνει τη δική του στιλιζαρισμένη σκιά. Η πειραματική προσέγγιση θα ενισχύσει τις έννοιες και θα αποκαλύψει νέες δυνατότητες για αυτοματοποίηση εγγράφων.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, μη διστάσετε να τον μοιραστείτε, να δώσετε αστέρι στο αποθετήριο Aspose.Words, ή να αφήσετε ένα σχόλιο με τις δικές σας συμβουλές για ρύθμιση σκιών. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}