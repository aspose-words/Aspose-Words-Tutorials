---
date: 2026-02-16
description: Μάθετε πώς να δημιουργείτε πλαίσιο κειμένου, να προσθέτετε λέξη ως υδατογράφημα,
  να ομαδοποιείτε πολλαπλά σχήματα, να ορίζετε την αναλογία διαστάσεων του σχήματος
  και να τοποθετείτε το σχήμα σε κελί πίνακα χρησιμοποιώντας το Aspose.Words for Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Πώς να δημιουργήσετε πλαίσιο κειμένου και να χρησιμοποιήσετε σχήματα εγγράφου
  στο Aspose.Words για Java
url: /el/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

 unchanged.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση Σχημάτων Εγγράφου στο Aspose.Words for Java

## Εισαγωγή στη Χρήση Σχημάτων Εγγράφου στο Aspose.Words for Java

Σε αυτόν τον ολοκληρωμένο οδηγό, **θα μάθετε πώς να δημιουργείτε αντικείμενα text box** και άλλα ισχυρά σχήματα με το Aspose.Words for Java. Τα σχήματα σας επιτρέπουν να εμπλουτίζετε τα έγγραφα Word με επεξηγήσεις, κουμπιά, υδατογραφήματα, SmartArt και άλλα—κάνοντας τα οπτικά ελκυστικά και διαδραστικά. Θα περάσουμε από παραδείγματα πραγματικού κόσμου, από την εισαγωγή ενός απλού text box μέχρι την ομαδοποίηση πολλαπλών σχημάτων, τον καθορισμό αναλογιών και την τοποθέτηση σχημάτων μέσα σε κελιά πίνακα.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο κύριος τρόπος για να προσθέσετε ένα text box;** Χρησιμοποιήστε `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Μπορώ να ομαδοποιήσω σχήματα μαζί;** Ναι – δημιουργήστε ένα `GroupShape` και προσθέστε τα παιδικά σχήματα.
- **Πώς κλειδώνω ή ξεκλειδώνω την αναλογία διαστάσεων ενός σχήματος;** Καλέστε `shape.setAspectRatioLocked(true/false)`.
- **Μπορεί να προστεθεί υδατογράφημα με σχήμα;** Απόλυτα – εισάγετε ένα `Shape` με `TEXT_PLAIN_TEXT` και ορίστε το γέμισμα/περίγραμμα.
- **Λειτουργούν τα διαγράμματα SmartArt με το Aspose.Words;** Ναι – ανιχνεύστε με `shape.hasSmartArt()` και ενημερώστε μέσω `shape.updateSmartArtDrawing()`.

## Τι είναι ένα text box και γιατί να δημιουργήσετε σχήματα text box;

Ένα text box είναι ένα δοχείο που μπορεί να περιέχει μορφοποιημένο κείμενο, εικόνες ή άλλα σχήματα. Η χρήση του **create text box** στην αυτοματοποίηση σας επιτρέπει να τοποθετείτε αιωρούμενο περιεχόμενο οπουδήποτε στη σελίδα, ιδανικό για σημειώσεις, επεξηγήσεις ή διακοσμητικά στοιχεία χωρίς να αλλάζει η κύρια ροή του εγγράφου.

## Πώς να προσθέσετε σχήμα

Πριν βυθιστούμε στον κώδικα, βεβαιωθείτε ότι το Aspose.Words for Java είναι αναφορά στο έργο σας. Εάν δεν το έχετε προσθέσει ακόμη, κατεβάστε τη βιβλιοθήκη από την επίσημη ιστοσελίδα:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Προσθήκη Σχημάτων σε Έγγραφα

## Πώς να ομαδοποιήσετε πολλαπλά σχήματα

Ένα `GroupShape` σας επιτρέπει να αντιμετωπίζετε πολλά μεμονωμένα σχήματα ως μία ενιαία μονάδα—χρήσιμο για τη μετακίνηση ή περιστροφή τους μαζί.

### Εισαγωγή GroupShape

Παρακάτω υπάρχει ένα πλήρες παράδειγμα που δημιουργεί μια ομάδα, προσθέτει δύο διαφορετικά σχήματα και εισάγει την ομάδα στο έγγραφο.

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

## Πώς να δημιουργήσετε ένα text box (create text box)

### Εισαγωγή Σχήματος Text Box

Η μέθοδος `insertShape` καθιστά απλό το να προσθέσετε ένα text box. Το παρακάτω παράδειγμα δείχνει δύο τρόπους τοποθέτησης και περιστροφής ενός text box.

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

## Πώς να ορίσετε την αναλογία διαστάσεων του σχήματος

### Διαχείριση Αναλογίας Διαστάσεων

Μερικές φορές χρειάζεται ένα σχήμα να τεντωθεί χωρίς να διατηρεί τις αρχικές του αναλογίες. Το παρακάτω απόσπασμα δείχνει το ξεκλείδωμα της αναλογίας διαστάσεων ενός σχήματος εικόνας.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Πώς να τοποθετήσετε σχήμα σε κελί πίνακα

### Τοποθέτηση Σχήματος μέσα σε Κελί Πίνακα

Παρακάτω υπάρχει ένα βήμα‑βήμα παράδειγμα που δημιουργεί έναν πίνακα, στη συνέχεια εισάγει ένα σχήμα υδατογραφήματος που τοποθετείται σχετικά με τη σελίδα αλλά μπορεί επίσης να τοποθετηθεί μέσα σε κελί.

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

## Εργασία με Σχήματα SmartArt

### Ανίχνευση Σχημάτων SmartArt

Μπορείτε προγραμματιστικά να βρείτε αντικείμενα SmartArt σε ένα έγγραφο χρησιμοποιώντας τη μέθοδο `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Ενημέρωση Σχεδίων SmartArt

Μόλις εντοπίσετε σχήματα SmartArt, μπορείτε να ανανεώσετε τα εσωτερικά δεδομένα σχεδίασής τους με `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Συμπέρασμα

Σε αυτόν τον οδηγό, καλύψαμε πώς να **δημιουργείτε αντικείμενα text box**, να ομαδοποιείτε πολλαπλά σχήματα, να ρυθμίζετε τις αναλογίες, να ενσωματώνετε σχήματα μέσα σε κελιά πίνακα, να προσθέτετε υδατογραφήματα και να εργάζεστε με διαγράμματα SmartArt χρησιμοποιώντας το Aspose.Words for Java. Αυτές οι τεχνικές σας δίνουν τη δυνατότητα να δημιουργείτε πλούσια μορφοποιημένα, διαδραστικά έγγραφα Word προγραμματιστικά.

## Συχνές Ερωτήσεις

### Τι είναι το Aspose.Words for Java;

Το Aspose.Words for Java είναι μια βιβλιοθήκη Java που επιτρέπει στους προγραμματιστές να δημιουργούν, τροποποιούν και μετατρέπουν έγγραφα Word προγραμματιστικά. Παρέχει μια ευρεία γκάμα λειτουργιών και εργαλείων για εργασία με έγγραφα σε διάφορες μορφές.

### Πώς μπορώ να κατεβάσω το Aspose.Words for Java;

Μπορείτε να κατεβάσετε το Aspose.Words for Java από την ιστοσελίδα της Aspose ακολουθώντας αυτόν τον σύνδεσμο: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Ποια είναι τα οφέλη της χρήσης σχημάτων εγγράφου;

Τα σχήματα εγγράφου προσθέτουν οπτικά στοιχεία και διαδραστικότητα στα έγγραφά σας, καθιστώντας τα πιο ελκυστικά και ενημερωτικά. Με τα σχήματα, μπορείτε να δημιουργήσετε επεξηγήσεις, κουμπιά, εικόνες, υδατογραφήματα και άλλα, βελτιώνοντας τη συνολική εμπειρία χρήστη.

### Μπορώ να προσαρμόσω την εμφάνιση των σχημάτων;

Ναι, μπορείτε να προσαρμόσετε την εμφάνιση των σχημάτων ρυθμίζοντας τις ιδιότητές τους όπως το μέγεθος, η θέση, η περιστροφή και το χρώμα γεμίσματος. Το Aspose.Words for Java παρέχει εκτενείς επιλογές για προσαρμογή σχημάτων.

### Είναι το Aspose.Words for Java συμβατό με SmartArt;

Ναι, το Aspose.Words for Java υποστηρίζει σχήματα SmartArt, επιτρέποντάς σας να εργάζεστε με σύνθετα διαγράμματα και γραφικά στα έγγραφά σας.

## Συχνές Ερωτήσεις

**Q: Μπορώ να συνδυάσω ένα text box με μια εικόνα μέσα στο ίδιο σχήμα;**  
A: Ναι. Εισάγετε μια εικόνα στο σχήμα text box χρησιμοποιώντας `builder.insertImage()` μετά τη δημιουργία του σχήματος, και στη συνέχεια προσαρμόστε τη διάταξή της όπως χρειάζεται.

**Q: Πώς μπορώ να εξασφαλίσω ότι ένα υδατογράφημα εμφανίζεται πίσω από όλο το περιεχόμενο του εγγράφου;**  
A: Ορίστε το `WrapType` του σχήματος σε `NONE` και ρυθμίστε το `RelativeHorizontalPosition` και το `RelativeVerticalPosition` σε `PAGE`. Αυτό τοποθετεί το υδατογράφημα πίσω από τη κύρια ροή.

**Q: Είναι δυνατόν να ανιματοποιηθεί ένα ομαδοποιημένο σχήμα στο Word;**  
A: Αν και το Aspose.Words μπορεί να δημιουργήσει και να ομαδοποιήσει σχήματα, οι δυνατότητες animation δεν υποστηρίζονται επειδή εξαρτώνται από τις δυνατότητες UI του Word.

**Q: Ποια έκδοση του Aspose.Words απαιτείται για υποστήριξη SmartArt;**  
A: Η ανίχνευση και η ενημέρωση SmartArt είναι διαθέσιμες από το Aspose.Words 20.9 για Java και μετά.

**Q: Διαχειρίζεται η βιβλιοθήκη μεγάλα έγγραφα με πολλά σχήματα αποδοτικά;**  
A: Ναι. Χρησιμοποιήστε `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` ή νεότερη έκδοση για βελτίωση της απόδοσης σε έγγραφα με πολλά σχήματα.

---

**Τελευταία Ενημέρωση:** 2026-02-16  
**Δοκιμή Με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}