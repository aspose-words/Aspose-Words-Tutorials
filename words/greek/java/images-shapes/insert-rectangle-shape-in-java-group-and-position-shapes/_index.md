---
category: general
date: 2026-07-26
description: Εισαγωγή σχήματος ορθογωνίου σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να ορίσετε το μέγεθος του σχήματος, τη θέση του σχήματος και πώς να ομαδοποιήσετε
  σχήματα σε αρχείο DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: el
lastmod: 2026-07-26
og_description: Εισάγετε σχήμα ορθογωνίου στην Java για να δημιουργήσετε πλούσια γραφικά
  DOCX. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να ορίσετε το μέγεθος του σχήματος,
  τη θέση του σχήματος και να ομαδοποιήσετε τα σχήματα χωρίς κόπο.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Εισαγωγή Σχήματος Ορθογωνίου στη Java – Αριστεία στην Ομαδοποίηση & Τοποθέτηση
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Εισαγωγή σχήματος ορθογωνίου στη Java – Ομαδοποίηση και τοποθέτηση σχημάτων
url: /el/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Σχήματος Ορθογωνίου σε Java – Ομαδοποίηση και Τοποθέτηση Σχημάτων

Έχετε ποτέ χρειαστεί να **εισάγετε σχήμα ορθογωνίου** σε ένα έγγραφο Word ενώ γράφετε κώδικα Java; Δεν είστε μόνοι—προγραμματιστές που δημιουργούν αναφορές, τιμολόγια ή προσαρμοσμένα πρότυπα συναντούν αυτό το πρόβλημα συνεχώς. Τα καλά νέα είναι ότι με μερικές γραμμές κώδικα Aspose.Words for Java μπορείτε να **εισάγετε σχήμα ορθογωνίου**, **ορίσετε το μέγεθος του σχήματος**, **τοποθετήσετε το σχήμα**, και ακόμη **πώς να ομαδοποιήσετε σχήματα** ώστε να μετακινούνται ως μία μονάδα.

Σε αυτόν τον οδηγό θα περάσουμε από τη δημιουργία ενός κεντρικού εγγράφου μέχρι την αποθήκευση ενός `.docx` που περιέχει δύο ορθογώνια ομαδοποιημένα μαζί. Στο τέλος θα ξέρετε **πώς να προσθέσετε ορθογώνιο** αντικείμενο, να ελέγξετε τις διαστάσεις του, να το τοποθετήσετε ακριβώς όπου θέλετε και να το ενσωματώσετε σε μια επαναχρησιμοποιήσιμη ομάδα. Δεν απαιτούνται εξωτερικές βιβλιοθήκες πέρα από το Aspose.Words, και ο κώδικας λειτουργεί με Java 8‑plus.

## Προαπαιτούμενα

- Java 8 ή νεότερη εγκατεστημένη (χρησιμοποιώ JDK 17, αλλά ό,τι υποστηρίζει Maven είναι εντάξει)
- Aspose.Words for Java 23.9 ή νεότερη – προσθέστε την εξάρτηση στο `pom.xml` ή κατεβάστε το JAR
- Βασική κατανόηση της σύνταξης Java (αν μπορείτε να γράψετε μια μέθοδο `main`, είστε έτοιμοι)
- Ένα IDE ή κειμενογράφο της επιλογής σας (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** Αν χρησιμοποιείτε Maven, η εξάρτηση έχει την εξής μορφή:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Τώρα που έχουμε θέσει τα θεμέλια, ας βουτήξουμε στον κώδικα.

## Εισαγωγή Σχήματος Ορθογωνίου και Ορισμός Μεγέθους

Το πρώτο βήμα είναι να δημιουργήσετε ένα νέο `Document` και ένα `DocumentBuilder`. Ο builder είναι το «στυλό» που σχεδιάζει σχήματα στη σελίδα. Παρακάτω **εισάγουμε σχήμα ορθογωνίου** και αμέσως **ορίζουμε το μέγεθος του σχήματος** σε 100 × 80 σημεία.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Παρατηρήστε πώς οι κλήσεις `setWidth`/`setHeight` **ορίζουν το μέγεθος του σχήματος** σε σημεία (1 pt ≈ 1/72 ίντσες). Μπορείτε επίσης να χρησιμοποιήσετε `setSize` αν προτιμάτε μία μέθοδο, αλλά οι ξεκάθαρες κλήσεις κάνουν την πρόθεση προφανή.

## Τοποθέτηση Σχήματος στη Σελίδα

Αφού δημιουργήσουμε το πρώτο ορθογώνιο, πρέπει να **τοποθετήσουμε το σχήμα** του δεύτερου ώστε να μην επικαλύπτεται με το πρώτο. Η τοποθέτηση λειτουργεί με τον ίδιο τρόπο: ορίζετε τις ιδιότητες `Left` και `Top` σε σχέση με το αρχικό σημείο της ομάδας.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Αν αναρωτιέστε γιατί χρησιμοποιούμε `setLeft` αντί για `setX`, είναι επειδή το Aspose.Words ακολουθεί το κλασικό σύστημα συντεταγμένων Windows GDI—`Left` είναι η οριζόντια μετατόπιση, `Top` η κάθετη. Η αλλαγή αυτών των τιμών σας επιτρέπει να ρυθμίσετε ακριβώς τη διάταξη χωρίς να παίζετε με πίνακες ή παραγράφους.

## Πώς να Ομαδοποιήσετε Σχήματα

Μπορεί να αναρωτηθείτε, “Γιατί να δημιουργήσω μια ομάδα;” Η ομαδοποίηση είναι χρήσιμη όταν θέλετε τα σχήματα να μετακινούνται μαζί, να περιστρέφονται ως ενιαία μονάδα ή να μοιράζονται κοινό στυλ. Στο παραπάνω απόσπασμα κώδικα έχουμε ήδη δημιουργήσει ένα `GroupShape` μέσω `builder.insertGroupShape`. Αυτό το αντικείμενο λειτουργεί ως κοντέινερ—σκεφτείτε το ως φάκελο που κρατά άλλα σχήματα.

> **Γιατί είναι σημαντικό:** Αν αργότερα αποφασίσετε να προσθέσετε λεζάντα ή να περιστρέψετε ολόκληρο το διάγραμμα, χρειάζεται να τροποποιήσετε μόνο την ομάδα, όχι κάθε ορθογώνιο ξεχωριστά.

## Πώς να Προσθέσετε Ορθογώνιο σε Μια Ομάδα

Η ενέργεια **πώς να προσθέσετε ορθογώνιο** στην ομάδα είναι απλώς η κλήση `group.appendChild(rectangle)`. Στο παρασκήνιο το Aspose.Words ενημερώνει τη συλλογή της ομάδας και επαναϋπολογίζει αυτόματα το περιβάλλον πλαίσιο ώστε η ομάδα να ταιριάζει ακόμη με το δηλωμένο πλάτος και ύψος.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Μπορείτε να πειραματιστείτε με άλλα `ShapeType`—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` κ.λπ.—και το ίδιο μοτίβο `appendChild` λειτουργεί.

## Αποθήκευση του Εγγράφου

Τέλος, αποθηκεύουμε το έγγραφο στο δίσκο. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική· απλώς βεβαιωθείτε ότι ο φάκελος υπάρχει.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Όταν ανοίξετε το `GroupShape.docx` στο Microsoft Word, θα δείτε δύο ορθογώνια δίπλα-δίπλα, και τα δύο κλειδωμένα μέσα σε ένα ανοιχτό γκρι πλαίσιο. Επιλέγοντας το γκρι πλαίσιο θα επισημαίνονται και τα δύο ορθογώνια ταυτόχρονα—απόδειξη ότι **πώς να ομαδοποιήσετε σχήματα** λειτουργεί πραγματικά.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Παράδειγμα εισαγωγής σχήματος ορθογωνίου που δείχνει δύο ορθογώνια ομαδοποιημένα σε αρχείο DOCX που δημιουργήθηκε με Java"}

*Κείμενο alt εικόνας (SEO):* **παράδειγμα εισαγωγής σχήματος ορθογωνίου που δείχνει δύο ορθογώνια ομαδοποιημένα σε αρχείο DOCX που δημιουργήθηκε με Java**.

## Αναμενόμενο Αποτέλεσμα

- Ένα αρχείο `GroupShape.docx` τοποθετημένο στον φάκελο `output`.
- Μέσα στο έγγραφο: μια ομάδα 400 × 200 pt που περιέχει δύο ορθογώνια (100 × 80 pt και 120 × 60 pt) τοποθετημένα στα (20, 30) και (150, 50) αντίστοιχα.
- Η ομάδα έχει λεπτό μαύρο περίγραμμα και γκρι γέμισμα, καθιστώντας την ομαδοποίηση οπτικά εμφανή.

Ανοίξτε το αρχείο και δοκιμάστε να σύρετε το γκρι πλαίσιο—και τα δύο ορθογώνια πρέπει να μετακινούνται μαζί. Αν δεν συμβαίνει, ελέγξτε ξανά ότι κάλεσατε `group.appendChild` για κάθε σχήμα.

## Συνηθισμένα Προβλήματα & Ακραίες Περιπτώσεις

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Τα ορθογώνια εμφανίζονται εκτός σελίδας** | Οι τιμές `Left`/`Top` υπερβαίνουν τις διαστάσεις της ομάδας | Αυξήστε το μέγεθος της ομάδας (`insertGroupShape(width, height)`) ή μειώστε τις μετατοπίσεις |
| **Η ομάδα εξαφανίζεται μετά την αποθήκευση** | Τα `Width`/`Height` της ομάδας είναι 0 | Παρέχετε μη‑μηδενικές διαστάσεις κατά την κλήση `insertGroupShape` |
| **Τα χρώματα του σχήματος είναι λανθασμένα** | Η προεπιλεγμένη γέμιση είναι διαφανής· το Word μπορεί να το εμφανίσει ως λευκό | Ορίστε ρητά `setFillColor` ή χρησιμοποιήστε `ShapeStyle` |
| **Εξαίρεση `ArgumentOutOfRangeException`** | Χρήση αρνητικών συντεταγμένων | Διατηρήστε τα `Left` και `Top` μη‑αρνητικά |

Η αντιμετώπιση αυτών των ζητημάτων νωρίς σας σώζει από τους «γιατί εξαφανίζεται το σχήμα μου;» πονοκεφάλους που αντιμετωπίζουν πολλοί αρχάριοι.

## Περίληψη & Επόμενα Βήματα

Καλύψαμε ολόκληρο τον κύκλο ζωής του **εισαγωγής σχήματος ορθογωνίου** σε Java: δημιουργία εγγράφου, **ορισμός μεγέθους σχήματος**, **τοποθέτηση σχήματος**, **πώς να ομαδοποιήσετε σχήματα**, και **πώς να προσθέσετε ορθογώνιο** στην ομάδα. Το πλήρες, εκτελέσιμο παράδειγμα βρίσκεται στο παραπάνω μπλοκ κώδικα και μπορείτε να το επικολλήσετε απευθείας σε ένα έργο Maven για να δείτε το αποτέλεσμα.

Τι ακολουθεί; Σκεφτείτε να πειραματιστείτε με:

- Προσθήκη κειμένου μέσα σε κάθε ορθογώνιο μέσω

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}