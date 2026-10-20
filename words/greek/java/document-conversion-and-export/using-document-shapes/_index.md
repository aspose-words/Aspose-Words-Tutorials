---
date: 2025-12-14
description: Μάθετε πώς να **εισάγετε σχήμα εικόνας** με το Aspose.Words for Java.
  Αυτός ο οδηγός σας δείχνει πώς να προσθέτετε σχήματα, να δημιουργείτε σχήματα πλαισίου
  κειμένου, να τοποθετείτε σχήματα σε πίνακες, να ορίζετε την αναλογία διαστάσεων
  του σχήματος και να προσθέτετε σχήματα επεξήγησης.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Χρήση Σχημάτων Εγγράφου στο Aspose.Words για Java
url: /el/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να **εισάγετε σχήμα εικόνας** με Aspose.Words for Java

Σε αυτό το ολοκληρωμένο tutorial θα ανακαλύψετε πώς να **εισάγετε σχήμα εικόνας** αντικείμενα σε έγγραφα Word χρησιμοποιώντας το Aspose.Words for Java. Είτε δημιουργείτε αναφορές, υλικό μάρκετινγκ ή διαδραστικές φόρμες, τα σχήματα σας επιτρέπουν να προσθέτετε σημειώσεις, κουμπιά, πλαίσια κειμένου, υδατογραφήματα και ακόμη SmartArt. Θα περάσουμε βήμα προς βήμα, θα εξηγήσουμε γιατί θα χρησιμοποιούσατε ένα συγκεκριμένο σχήμα και θα παρέχουμε έτοιμα παραδείγματα κώδικα.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο κύριος τρόπος για να προσθέσετε ένα σχήμα;** Χρησιμοποιήστε `DocumentBuilder.insertShape` ή δημιουργήστε ένα αντικείμενο `Shape` και προσθέστε το στο δέντρο του εγγράφου.  
- **Μπορώ να εισάγω μια εικόνα ως σχήμα;** Ναι – καλέστε `builder.insertImage` και στη συνέχεια αντιμετωπίστε το επιστρεφόμενο `Shape` όπως οποιοδήποτε άλλο.  
- **Πώς διατηρώ την αναλογία διαστάσεων ενός σχήματος;** Ορίστε `shape.setAspectRatioLocked(true)` ή `false` ανάλογα με τις ανάγκες σας.  
- **Μπορεί να ομαδοποιηθούν σχήματα;** Απόλυτα – τυλίξτε τα σε ένα `GroupShape` και εισάγετε την ομάδα ως έναν ενιαίο κόμβο.  
- **Λειτουργούν τα διαγράμματα SmartArt με το Aspose.Words;** Ναι, μπορείτε να εντοπίσετε και να ενημερώσετε τα σχήματα SmartArt προγραμματιστικά.

## Τι είναι το **εισάγετε σχήμα εικόνας**;
Ένα *σχήμα εικόνας* είναι ένα οπτικό στοιχείο που περιέχει ραστερ ή διανυσματικά γραφικά μέσα σε ένα έγγραφο Word. Στο Aspose.Words, μια εικόνα αντιπροσωπεύεται από ένα αντικείμενο `Shape`, παρέχοντάς σας πλήρη έλεγχο στο μέγεθος, τη θέση, την περιστροφή και την περιτύλιξη.

## Γιατί να χρησιμοποιείτε σχήματα στα έγγραφά σας;
- **Οπτική επίδραση:** Τα σχήματα τραβούν την προσοχή σε βασικές πληροφορίες.  
- **Διαδραστικότητα:** Τα κουμπιά και οι σημειώσεις μπορούν να συνδεθούν με URLs ή σελιδοδείκτες.  
- **Ευελιξία διάταξης:** Τοποθετήστε γραφικά ακριβώς με απόλυτες ή σχετικές συντεταγμένες.  
- **Αυτοματοποίηση:** Δημιουργήστε σύνθετες διατάξεις χωρίς χειροκίνητη επεξεργασία.

## Προαπαιτούμενα
- Java Development Kit (JDK 8 ή νεότερο)  
- Βιβλιοθήκη Aspose.Words for Java (κατεβάστε από την επίσημη ιστοσελίδα)  
- Βασικές γνώσεις Java και αντικειμενοστραφούς προγραμματισμού  

Μπορείτε να κατεβάσετε τη βιβλιοθήκη εδώ: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Πώς να **προσθέσετε σχήμα** – Εισαγωγή GroupShape
Ένα `GroupShape` σας επιτρέπει να αντιμετωπίζετε πολλά σχήματα ως μία ενιαία μονάδα. Αυτό είναι χρήσιμο για τη μετακίνηση ή τη μορφοποίηση πολλαπλών στοιχείων μαζί.

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

## Δημιουργία **σχήματος πλαισίου κειμένου**
Ένα πλαίσιο κειμένου είναι ένας δοχείο που μπορεί να περιέχει μορφοποιημένο κείμενο. Μπορείτε επίσης να το περιστρέψετε για μια δυναμική εμφάνιση.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Ορισμός **αναλογίας διαστάσεων σχήματος**
Μερικές φορές χρειάζεστε ένα σχήμα να τεντωθεί ελεύθερα, άλλες φορές θέλετε να διατηρήσετε τις αρχικές του αναλογίες. Ο έλεγχος της αναλογίας διαστάσεων είναι απλός.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Τοποθέτηση **σχήματος σε πίνακα**
Η ενσωμάτωση ενός σχήματος μέσα σε κελί πίνακα μπορεί να είναι χρήσιμη για διατάξεις αναφορών. Το παρακάτω παράδειγμα δημιουργεί έναν πίνακα και στη συνέχεια εισάγει ένα σχήμα τύπου υδατογραφήματος που καλύπτει ολόκληρη τη σελίδα.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Προσθήκη **σχήματος σημείωσης**
Ένα σχήμα σημείωσης είναι ιδανικό για την επισήμανση σημειώσεων ή προειδοποιήσεων. Ενώ ο παραπάνω κώδικας δείχνει ήδη ένα `ACCENT_BORDER_CALLOUT_1`, μπορείτε να αλλάξετε το `ShapeType` σε οποιαδήποτε παραλλαγή σημείωσης για να ταιριάζει στο σχέδιό σας.

## Εργασία με σχήματα SmartArt

### Ανίχνευση σχημάτων SmartArt
Τα διαγράμματα SmartArt μπορούν να εντοπιστούν προγραμματιστικά, επιτρέποντάς σας να τα επεξεργαστείτε ή να τα αντικαταστήσετε όπως απαιτείται.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Ενημέρωση σχεδίων SmartArt
Μόλις εντοπιστούν, μπορείτε να ανανεώσετε τα γραφικά SmartArt για να αντικατοπτρίζουν τυχόν αλλαγές δεδομένων.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Συνηθισμένα Προβλήματα & Συμβουλές
- **Το σχήμα δεν εμφανίζεται:** Βεβαιωθείτε ότι το σχήμα εισάγεται μετά τον στόχο κόμβο χρησιμοποιώντας `builder.insertNode`.  
- **Απροσδόκητη περιστροφή:** Θυμηθείτε ότι η περιστροφή εφαρμόζεται γύρω από το κέντρο του σχήματος· προσαρμόστε `setLeft`/`setTop` αν χρειάζεται.  
- **Κλειδωμένη αναλογία διαστάσεων:** Από προεπιλογή, πολλά σχήματα κλειδώνουν την αναλογία τους· καλέστε `setAspectRatioLocked(false)` για ελεύθερη τέντωμα.  
- **Αποτυχία ανίχνευσης SmartArt:** Επαληθεύστε ότι χρησιμοποιείτε έκδοση Aspose.Words που υποστηρίζει SmartArt (v24+).

## Συχνές Ερωτήσεις

**Q: Τι είναι το Aspose.Words for Java;**  
A: Το Aspose.Words for Java είναι μια βιβλιοθήκη Java που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να μετατρέπουν έγγραφα Word προγραμματιστικά. Παρέχει μια ευρεία γκάμα χαρακτηριστικών και εργαλείων για εργασία με έγγραφα σε διάφορες μορφές.

**Q: Πώς μπορώ να κατεβάσω το Aspose.Words for Java;**  
A: Μπορείτε να κατεβάσετε το Aspose.Words for Java από την ιστοσελίδα Aspose ακολουθώντας αυτόν τον σύνδεσμο: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: Ποια είναι τα οφέλη της χρήσης σχημάτων εγγράφου;**  
A: Τα σχήματα εγγράφου προσθέτουν οπτικά στοιχεία και διαδραστικότητα στα έγγραφά σας, καθιστώντας τα πιο ελκυστικά και ενημερωτικά. Με τα σχήματα, μπορείτε να δημιουργήσετε σημειώσεις, κουμπιά, εικόνες, υδατογραφήματα και πολλά άλλα, βελτιώνοντας τη συνολική εμπειρία του χρήστη.

**Q: Μπορώ να προσαρμόσω την εμφάνιση των σχημάτων;**  
A: Ναι, μπορείτε να προσαρμόσετε την εμφάνιση των σχημάτων ρυθμίζοντας τις ιδιότητές τους όπως το μέγεθος, η θέση, η περιστροφή και το χρώμα γεμίσματος. Το Aspose.Words for Java παρέχει εκτενείς επιλογές για προσαρμογή σχημάτων.

**Q: Είναι το Aspose.Words for Java συμβατό με SmartArt;**  
A: Ναι, το Aspose.Words for Java υποστηρίζει σχήματα SmartArt, επιτρέποντάς σας να εργάζεστε με σύνθετα διαγράμματα και γραφικά στα έγγραφά σας.

---

**Τελευταία ενημέρωση:** 2025-12-14  
**Δοκιμή με:** Aspose.Words for Java 24.12 (latest)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}