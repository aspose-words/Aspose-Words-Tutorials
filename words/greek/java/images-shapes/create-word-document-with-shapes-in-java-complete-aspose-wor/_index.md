---
category: general
date: 2026-07-29
description: Δημιουργήστε έγγραφο Word σε Java χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να εισάγετε σχήμα ορθογωνίου, να ομαδοποιείτε σχήματα στο Word και να αποθηκεύετε
  το έγγραφο ως docx γρήγορα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: el
lastmod: 2026-07-29
og_description: Δημιουργήστε έγγραφο Word σε Java με το Aspose.Words. Εισάγετε σχήμα
  ορθογωνίου, ομαδοποιήστε σχήματα στο Word και αποθηκεύστε το έγγραφο ως docx σε
  λίγα λεπτά.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Δημιουργία εγγράφου Word με σχήματα – Java Aspose.Words Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Δημιουργία εγγράφου Word με σχήματα σε Java – Πλήρης οδηγός Aspose.Words
url: /el/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Σχήματα σε Java – Πλήρης Οδηγός Aspose.Words

Έχετε αναρωτηθεί ποτέ πώς να **create word document** προγραμματιστικά και να το διακοσμήσετε με προσαρμοσμένα γραφικά; Δεν είστε μόνοι. Είτε χρειάζεται να δημιουργήσετε μια αναφορά με επισημασμένα τμήματα είτε να σχεδιάσετε ένα φυλλάδιο εν κινήσει, η εξοικείωση με τη διαχείριση σχημάτων στο Word μπορεί να σας εξοικονομήσει ώρες χειροκίνητης εργασίας.

Σε αυτό το tutorial θα περάσουμε από τα ακριβή βήματα για **create word document** χρησιμοποιώντας Aspose.Words for Java, **insert rectangle shape**, **group shapes in Word**, και τέλος **save document as docx**. Στο τέλος θα έχετε ένα πλήρως εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο.

## Τι Θα Αποκομίσετε

- Ένα νέο αρχείο Word που δημιουργείται εξ ολοκλήρου από κώδικα Java.  
- Δύο διαφορετικά σχήματα (ένα ορθογώνιο και μια έλλειψη) προστιθέμενα στη σελίδα.  
- Τα σχήματα ομαδοποιημένα με το API **group shapes in word**, ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο.  
- Το αρχείο αποθηκευμένο στο δίσκο ως τυπικό `.docx` που ανοίγει στο Microsoft Word χωρίς προβλήματα.  

Χωρίς εξωτερικά εργαλεία, χωρίς περίπλοκες τροποποιήσεις XML—μόνο καθαρός, τυποποιημένος Java κώδικας και Aspose.Words.

---

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

1. **Java Development Kit (JDK) 8 ή νεότερο** – ο κώδικας στοχεύει σε Java 8+.  
2. **Aspose.Words for Java** JAR (μπορείτε να κατεβάσετε την πιο πρόσφατη έκδοση από το Maven Central repository).  
3. Ένα απλό IDE (IntelliJ IDEA, Eclipse ή ακόμη και έναν απλό επεξεργαστή κειμένου).  

Αν έχετε όλα αυτά, τέλεια—ας ξεκινήσουμε.

---

## Υλοποίηση Βήμα‑Βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε μικρά βήματα. Κάθε βήμα περιλαμβάνει ένα απόσπασμα κώδικα, μια σύντομη εξήγηση και μια συμβουλή που ίσως δεν βρείτε στα επίσημα docs.

### ## Δημιουργία Εγγράφου Word με Σχήματα Χρησιμοποιώντας Aspose.Words

Το πρώτο που χρειάζεστε είναι ένα κενό αρχείο Word για να δουλέψετε. Το Aspose.Words το κάνει με μία γραμμή κώδικα.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:**  
`Document` είναι το δοχείο για τα πάντα—κείμενο, πίνακες, εικόνες και σχήματα. `DocumentBuilder` είναι ο φιλικός βοηθός που σας επιτρέπει να προσθέτετε περιεχόμενο χωρίς να ασχολείστε με αντικείμενα χαμηλού επιπέδου. Σκεφτείτε το ως ένα στυλό που γράφει απευθείας στη σελίδα.

> **Pro tip:** Αν σκοπεύετε να ξεκινήσετε από ένα πρότυπο (π.χ., εταιρική κεφαλίδα), αντικαταστήστε το `new Document()` με `new Document("template.docx")`.

### ## Εισαγωγή Σχήματος Ορθογωνίου και Άλλων Σχημάτων

Τώρα θα προσθέσουμε ένα μπλε ορθογώνιο και μια πράσινη έλλειψη. Το ορθογώνιο δείχνει τη λέξη-κλειδί **insert rectangle shape**, ενώ η έλλειψη δείχνει ότι μπορείτε να συνδυάσετε ελεύθερα τύπους σχημάτων.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Τι συμβαίνει στο παρασκήνιο;**  
Κάθε κλήση στο `insertShape` δημιουργεί ένα αντικείμενο `Shape` και το προσθέτει αυτόματα στην τρέχουσα παράγραφο. Οι μέθοδοι `setLeft`/`setTop` τοποθετούν το σχήμα σε σχέση με τα περιθώρια της σελίδας, μετρημένα σε points (1 pt = 1/72 in). Με την τροποποίηση αυτών των αριθμών μπορείτε να τοποθετήσετε τα σχήματα όπου θέλετε.

> **Συχνή ερώτηση:** *Μπορώ να προσθέσω μια εικόνα αντί για ένα γερό χρώμα;*  
> Σίγουρα—απλώς αντικαταστήστε το χρώμα γεμίσματος με μια εικόνα χρησιμοποιώντας `shape.getFill().setImage("path/to/image.png")`.

### ## Ομαδοποίηση Σχημάτων σε Word για Εύκολη Διαχείριση

Η ύπαρξη δύο ξεχωριστών αντικειμένων είναι εντάξει, αλλά συχνά θέλετε να τα μετακινήσετε μαζί. Εδώ έρχεται στο προσκήνιο η **group shapes in word**.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Γιατί ομαδοποίηση;**  
Όταν τα σχήματα ομαδοποιούνται, οποιαδήποτε μετασχηματισμός—μετακίνηση, περιστροφή, αλλαγή μεγέθους—εφαρμόζεται σε ολόκληρη τη συλλογή. Αυτό αντικατοπτρίζει τη συμπεριφορά που παίρνετε όταν επιλέγετε πολλαπλά σχήματα στο UI του Word και πατάτε *Group*. Επίσης απλοποιεί τον κώδικα, επειδή χρειάζεται να ρυθμίσετε μόνο ένα αντικείμενο αντί για πολλά.

> **Edge case:** Αν χρειαστεί αργότερα να αποομαδοποιήσετε, καλέστε `group.getParentNode().removeChild(group)` και επανεισάγετε τα παιδιά ξεχωριστά.

### ## Αποθήκευση Εγγράφου ως DOCX και Επαλήθευση Αποτελέσματος

Τέλος, αποθηκεύουμε το αρχείο. Αυτό το βήμα ικανοποιεί την απαίτηση **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Τι να περιμένετε:**  
Ανοίξτε το παραγόμενο `GroupShapeExample.docx` στο Microsoft Word. Θα δείτε ένα μπλε ορθογώνιο και μια πράσινη έλλειψη, ομαδοποιημένα. Σύρετε την ομάδα—και τα δύο σχήματα θα μετακινηθούν μαζί, όπως θα περιμένατε από το UI.

> **Tip:** Χρησιμοποιήστε `SaveFormat.PDF` αν χρειάζεστε έκδοση PDF· ο ίδιος κώδικας λειτουργεί χωρίς αλλαγές.

### ## Πλήρες Παράδειγμα Εργασίας και Συνηθισμένα Πιθανά Σφάλματα

Παρακάτω είναι η πλήρης, έτοιμη‑για‑εκτέλεση κλάση Java. Αντιγράψτε‑και‑επικολλήστε την στο πρόγραμμά σας, προσαρμόστε το φάκελο εξόδου, και πατήστε *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **`NullPointerException` στο `builder`** | Λάθος στην δημιουργία του `DocumentBuilder` μετά τη δημιουργία του `Document`. | Βεβαιωθείτε ότι εκτελείται `new DocumentBuilder(doc)` πριν από οποιαδήποτε εισαγωγή σχήματος. |
| **Τα σχήματα εμφανίζονται εκτός σελίδας** | Χρήση τιμών pixel αντί για points, ή μη λήψη υπόψη των περιθωρίων. | Θυμηθείτε ότι το Aspose.Words χρησιμοποιεί points· 72 pt = 1 in. Ρυθμίστε τα `setLeft`/`setTop` αναλόγως. |
| **Η ομάδα εξαφανίζεται μετά την αποθήκευση** | Προσθήκη σχημάτων στην ομάδα *μετά* την αποθήκευση του εγγράφου. | Πάντα ομαδοποιείτε πριν καλέσετε `doc.save()`. |
| **Το αρχείο δεν βρέθηκε κατά την αποθήκευση** | Ο φάκελος εξόδου δεν υπάρχει. | Δημιουργήστε το φάκελο προγραμματιστικά (`new File("output").mkdirs();`) ή χρησιμοποιήστε υπάρχουσα διαδρομή. |

---

## Συμπέρασμα

Μόλις **create word document** από το μηδέν, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, και τέλος **save document as docx**—όλα με λίγες γραμμές Java. Η δύναμη του Aspose.Words έγκειται στο σαφές μοντέλο αντικειμένων· μπορείτε να αντιμετωπίσετε ένα αρχείο Word σαν καμβά, να το ζωγραφίσετε με σχήματα, και να το εξάγετε όπου χρειάζεται.

Νιώθετε περιπετειώδεις; Δοκιμάστε να αντικαταστήσετε το ορθογώνιο με ένα αστέρι, προσθέστε κείμενο μέσα στα σχήματα με `Shape.getTextBox()`, ή πειραματιστείτε με περιστροφή (`shape.setRotationAngle(45)`). Το API είναι πλούσιο, και οι δυνατότητες σχεδόν απεριόριστες.

Έχετε ερωτήσεις για πιο προχωρημένα σενάρια—όπως σύνδεση σχημάτων με σελιδοδείκτες ή εξαγωγή σε PDF με ενσωματωμένες γραμματοσειρές; Αφήστε ένα σχόλιο παρακάτω, και θα εμβαθύνουμε μαζί. Καλό κώδικα!

## Τι Θα Μάθετε Στη Σειρά;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}