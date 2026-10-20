---
category: general
date: 2026-09-18
description: Δημιουργήστε ένα κενό έγγραφο και εισάγετε σχήματα στο Word με το Aspose.Words
  – μάθετε πώς να προσθέσετε ένα σχήμα τριγώνου και άλλα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε κενό έγγραφο στο Word χρησιμοποιώντας το Aspose.Words
  και μάθετε πώς να εισάγετε ένα σχήμα τριγώνου, να ομαδοποιήσετε σχήματα και άλλα
  γραφικά. Ακολουθήστε αυτόν τον πλήρη οδηγό.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Δημιουργήστε κενό έγγραφο και προσθέστε σχήματα στο Word – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Πώς να δημιουργήσετε ένα κενό έγγραφο και να προσθέσετε σχήματα στο Word
url: /el/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο και να προσθέσετε σχήματα στο Word

Αν χρειάζεστε να **create blank document** και στη συνέχεια να το εμπλουτίσετε με γραφικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα περάσουμε από τη δημιουργία ενός αρχείου Word από το μηδέν και **add shapes to Word**, συμπεριλαμβανομένου του **how to insert triangle** σχήματος, χρησιμοποιώντας το Aspose.Words for Java.

Θα ολοκληρώσετε τον οδηγό με ένα έτοιμο *.docx* αρχείο που περιέχει ένα ομαδοποιημένο σχήμα που κρατάει ένα τρίγωνο. Τα βήματα καλύπτουν τα πάντα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού **create word document**. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από το Aspose.Words.

## Προαπαιτούμενα

* Java 17 ή νεότερη έκδοση εγκατεστημένη  
* Maven ή Gradle για διαχείριση εξαρτήσεων  
* Άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για αυτή τη demo)  

Αν προτιμάτε διαφορετικό σύστημα κατασκευής, προσαρμόστε τη σύνταξη των εξαρτήσεων αναλόγως. Ο κώδικας λειτουργεί σε οποιαδήποτε πλατφόρμα που υποστηρίζει Java.

## Δημιουργία κενού εγγράφου με Aspose.Words

Η πρώτη ενέργεια είναι να **create blank document** στη μνήμη. Το Aspose.Words παρέχει μια κλάση `Document` που αντιπροσωπεύει ένα αρχείο Word χωρίς κανένα περιεχόμενο.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Ο κατασκευαστής `new Document()` δημιουργεί μια κενή δομή *.docx*, την οποία μπορείτε αργότερα να γεμίσετε με παραγράφους, πίνακες ή γραφικά. Επειδή το έγγραφο είναι κενό, έχετε πλήρη έλεγχο σε κάθε στοιχείο που προσθέτετε.

## Προσθήκη σχημάτων στο Word – εισαγωγή ομαδοποιημένου σχήματος

Ένα ομαδοποιημένο σχήμα σας επιτρέπει να αντιμετωπίζετε πολλά γραφικά ως μία ενιαία μονάδα. Αυτό είναι χρήσιμο όταν θέλετε να μετακινήσετε ή να αλλάξετε το μέγεθος πολλών σχημάτων μαζί.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` είναι το κύριο API για την προσθήκη περιεχομένου. Η κλήση `insertGroupShape` δημιουργεί ένα κοντέινερ μεγέθους 300 × 300 points (περίπου 4 × 4 ίντσες). Μετά από αυτήν την κλήση ο κέρσορας τοποθετείται *μέσα* στην ομάδα, έτοιμος για επιπλέον σχήματα.

### Γιατί να χρησιμοποιήσετε ομαδοποιημένο σχήμα;

Η ομαδοποίηση διατηρεί τα σχετιζόμενα γραφικά ευθυγραμμισμένα και καθιστά πιο εύκολο την εφαρμογή ομοιόμορφης μορφοποίησης. Αν αργότερα αποφασίσετε να μετακινήσετε το τρίγωνο, ολόκληρη η ομάδα μετακινείται μαζί, διατηρώντας τη διάταξη.

## Πώς να εισαγάγετε σχήμα τριγώνου μέσα στην ομάδα

Τώρα αντιμετωπίζουμε το **how to insert triangle** σχήμα. Το τρίγωνο είναι μία από τις ενσωματωμένες τιμές `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Η κλήση `moveTo` εξασφαλίζει ότι το σημείο εισαγωγής του builder είναι η πρώτη παράγραφος της ομάδας. Η `insertShape` προσθέτει στη συνέχεια ένα τρίγωνο μεγέθους 60 × 60 points. Επειδή ο κέρσορας είναι μέσα στην ομάδα, το τρίγωνο γίνεται παιδί του ομαδοποιημένου σχήματος.

**Add triangle shape** συμβουλές:

* Το μέγεθος μετράται σε points· 72 points ισοδυναμούν με μία ίντσα. Προσαρμόστε τις διαστάσεις ώστε να ταιριάζουν στη διάταξή σας.  
* Αν χρειάζεστε διαφορετικό προσανατολισμό, χρησιμοποιήστε `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` για να ευθυγραμμίσετε το σχήμα μέσα στην ομάδα.  
* Το τρίγωνο κληρονομεί τα στυλ γεμίσματος και γραμμής της ομάδας εκτός εάν τα παρακάμψετε με `shape.getFillColor()` ή `shape.getStrokeColor()`.

## Αποθήκευση του εγγράφου – create word document

Αφού δημιουργήσετε τα γραφικά, αποθηκεύετε το αρχείο. Αυτό το βήμα ολοκληρώνει τη λειτουργία **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` γράφει την αναπαράσταση στη μνήμη στο δίσκο ως ένα τυπικό έγγραφο Word. Μπορείτε να ανοίξετε το `ExtendedGroup.docx` στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή OOXML. Το αρχείο θα εμφανίσει ένα ομαδοποιημένο σχήμα που περιέχει ένα τρίγωνο, ακριβώς όπως δημιουργήθηκε από τον κώδικα.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `ExtendedGroup.docx`, θα δείτε ένα μοναδικό ομαδοποιημένο σχήμα που καταλαμβάνει το κέντρο της σελίδας. Μέσα σε αυτήν την ομάδα, εμφανίζεται ένα μικρό τρίγωνο στην προεπιλεγμένη θέση. Το τρίγωνο μπορεί να επιλεγεί και να μετακινηθεί ως μέρος της ομάδας, επιβεβαιώνοντας ότι το **add shapes to word** λειτούργησε όπως αναμενόταν.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να προσθέσω περισσότερα από ένα σχήματα μέσα στην ομάδα;* | Ναι. Μετά την εισαγωγή του τριγώνου, κρατήστε τον κέρσορα μέσα στην ομάδα και καλέστε ξανά το `builder.insertShape` με διαφορετικό `ShapeType`. |
| *Τι γίνεται αν χρειάζομαι το τρίγωνο να είναι κόκκινο;* | Ανακτήστε το `Shape` που επιστρέφεται από το `insertShape` και καλέστε `shape.getFillColor().setColor(Color.RED)`. |
| *Λειτουργεί αυτό με παλαιότερα αρχεία .doc;* | Το Aspose.Words αποθηκεύει στη μορφή που καθορίζετε. Χρησιμοποιήστε `doc.save("file.doc", SaveFormat.DOC)` για να δημιουργήσετε ένα παλαιό έγγραφο Word. |
| *Πώς μπορώ να αλλάξω το περίγραμμα της ομάδας;* | Χρησιμοποιήστε `group.getStrokeColor().setColor(Color.BLUE)` και `group.setLineWeight(2.0)` για να προσαρμόσετε το περίγραμμα. |
| *Υπάρχει τρόπος να περιστρέψετε το τρίγωνο;* | Καλέστε `shape.getRotation()` για να ορίσετε γωνία σε μοίρες. |

## Συμβουλές επαγγελματιών

* **Reuse the builder** – η δημιουργία νέου `DocumentBuilder` για κάθε σχήμα προσθέτει επιβάρυνση. Διατηρήστε έναν μόνο builder ανά έγγραφο.  
* **Unit conversion** – εάν εργάζεστε με χιλιοστά, μετατρέψτε τα σε points (`points = mm * 2.83465`).  
* **Performance** – για μεγάλα έγγραφα, καλέστε το `doc.updatePageLayout()` μόνο μία φορά μετά την προσθήκη όλων των σχημάτων.  

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create blank document**, **add shapes to Word**, και συγκεκριμένα **how to insert triangle** σχήμα χρησιμοποιώντας το Aspose.Words for Java. Το πλήρες παράδειγμα δείχνει τη πλήρη ροή εργασίας από ένα κενό αρχείο μέχρι ένα αποθηκευμένο **create word document** που περιέχει ένα ομαδοποιημένο τρίγωνο.

Από εδώ μπορείτε να εξερευνήσετε πρόσθετες τιμές `ShapeType`, να εφαρμόσετε προσαρμοσμένο στυλ, ή να συνδυάσετε πολλαπλές ομάδες για να δημιουργήσετε σύνθετα διαγράμματα. Πειραματιστείτε με διαφορετικά μεγέθη, χρώματα και θέσεις για να κυριαρχήσετε στην αυτοματοποίηση του Word με Java.

--- 

*Έτοιμοι να αυτοματοποιήσετε την επόμενη αναφορά σας; Κλωνοποιήστε το παράδειγμα, προσαρμόστε τις διαστάσεις και ενσωματώστε τον κώδικα στην δική σας εφαρμογή σήμερα.*

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία ομαδοποιημένου σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία κενού εγγράφου Word με σχήμα ορθογωνίου με σκιά – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}