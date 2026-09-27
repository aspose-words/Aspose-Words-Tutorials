---
category: general
date: 2026-09-27
description: Δημιουργήστε ένα κενό έγγραφο Word σε Java και ομαδοποιήστε σχήματα χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να ορίζετε το μέγεθος του σχήματος, το χρώμα γεμίσματος
  του σχήματος και να προσθέτετε παιδί στην ομάδα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: el
lastmod: 2026-09-27
og_description: Δημιουργήστε κενό έγγραφο Word σε Java με το Aspose.Words. Αυτό το
  σεμινάριο δείχνει πώς να ομαδοποιήσετε σχήματα στο Word, να ορίσετε το μέγεθος του
  σχήματος, να ορίσετε το χρώμα γεμίσματος του σχήματος και να προσθέσετε παιδί στην
  ομάδα.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Δημιουργήστε ένα κενό έγγραφο Word και ομαδοποιήστε σχήματα σε Java – οδηγός
  βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να δημιουργήσετε κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε Java
url: /el/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε Java

Αν χρειάζεστε να **δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Java. Θα μάθετε επίσης να **ομαδοποιείτε σχήματα στο Word**, να ορίζετε το μέγεθος κάθε σχήματος, να εφαρμόζετε χρώμα γεμίσματος και να **προσθέτετε παιδί στην ομάδα** ώστε τα αντικείμενα να συμπεριφέρονται ως μία ενιαία μονάδα.

Η εργασία με αρχεία Word από κώδικα σας εξοικονομεί το χρόνο που απαιτείται για χειροκίνητη μορφοποίηση και σας επιτρέπει να δημιουργείτε αυτόματα εκθέσεις, συμβάσεις ή διαφημιστικά φυλλάδια. Στο τέλος αυτού του tutorial θα έχετε ένα εκτελέσιμο πρόγραμμα Java που παράγει ένα αρχείο `.docx` που περιέχει ένα μπλε ορθογώνιο και μια εικόνα, και τα δύο ομαδοποιημένα μαζί.

## Προαπαιτούμενα

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο.
- Maven ή Gradle για διαχείριση εξαρτήσεων.
- Άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για δοκιμές).
- Ένα δείγμα αρχείου εικόνας (π.χ., `sample.jpg`) τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε από τον κώδικα.

> **Συμβουλή επαγγελματία:** Διατηρήστε τα αρχεία εικόνας σε φάκελο `resources` και φορτώστε τα με `ClassLoader.getResourceAsStream` για να αποφύγετε τις σκληρά κωδικοποιημένες απόλυτες διαδρομές.

## Βήμα 1: Δημιουργία κενού εγγράφου Word και προσθήκη GroupShape

Το πρώτο βήμα είναι η δημιουργία ενός νέου αντικειμένου `Document`, το οποίο αντιπροσωπεύει ένα κενό αρχείο Word, και στη συνέχεια η εισαγωγή ενός `GroupShape`. Η ομάδα θα λειτουργήσει ως κοντέινερ για τυχόν σχήματα που θα προσθέσετε αργότερα.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Γιατί είναι σημαντικό:* Ένα `GroupShape` σας επιτρέπει να μετακινείτε, να περιστρέφετε ή να μορφοποιείτε πολλαπλά σχήματα μαζί, κάτι που είναι απαραίτητο για σύνθετες διατάξεις όπως διαγράμματα ή υδατογραφήματα.

## Βήμα 2: Εισαγωγή ορθογωνίου και **ορισμός μεγέθους σχήματος**

Στη συνέχεια, δημιουργήστε ένα ορθογώνιο, ορίστε τις διαστάσεις του και προσθέστε το στην ομάδα. Αυτό δείχνει τη λειτουργία **ορισμού μεγέθους σχήματος**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Εξήγηση:* `setWidth` και `setHeight` ελέγχουν το ακριβές μέγεθος του σχήματος σε points (1 point = 1/72 ίντσα). Προσαρμόστε αυτές τις τιμές ώστε να ταιριάζουν στις απαιτήσεις της διάταξής σας.

## Βήμα 3: **Ορισμός χρώματος γεμίσματος σχήματος** για το ορθογώνιο

Το φόντο του ορθογωνίου ορίζεται σε μπλε χρησιμοποιώντας `setFillColor`. Μπορείτε να χρησιμοποιήσετε οποιαδήποτε σταθερά `java.awt.Color` ή να δημιουργήσετε ένα προσαρμοσμένο χρώμα RGB.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Γιατί είναι χρήσιμο:* Τα χρώματα γεμίσματος βοηθούν στην οπτική διαφοροποίηση των αντικειμένων, ειδικά όταν εξάγετε το έγγραφο σε PDF ή το εκτυπώνετε.

## Βήμα 4: Εισαγωγή εικόνας και **προσθήκη παιδιού στην ομάδα**

Τώρα προσθέστε μια εικόνα στην ίδια `GroupShape`. Η εικόνα εισάγεται μέσω `DocumentBuilder.insertImage`, στη συνέχεια προσαρμόζεται στην ομάδα ώστε να κινείται μαζί με το ορθογώνιο.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Ακραία περίπτωση:* Αν η διαδρομή της εικόνας είναι λανθασμένη, το Aspose.Words ρίχνει `FileNotFoundException`. Χρησιμοποιήστε σχετική διαδρομή ή φορτώστε την εικόνα από τους πόρους για να αποφύγετε αυτό το πρόβλημα.

## Βήμα 5: **Αποθήκευση του εγγράφου με τα ομαδοποιημένα σχήματα**

Τέλος, γράψτε το έγγραφο στο δίσκο. Το παραγόμενο αρχείο θα περιέχει το ορθογώνιο και την εικόνα ομαδοποιημένα μαζί.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο με όνομα `GroupShape.docx` εμφανίζεται στον καθορισμένο φάκελο.
- Ανοίγοντας το αρχείο στο Microsoft Word βλέπετε μια κενή σελίδα με ένα μπλε ορθογώνιο και την επιλεγμένη εικόνα, και τα δύο επιλεγμένα ως ένα ενιαίο αντικείμενο (μπορείτε να τα μετακινήσετε ή να αλλάξετε το μέγεθός τους μαζί).

![δημιουργία κενού εγγράφου word με ομαδοποιημένα σχήματα](/images/grouped-shapes.png "δημιουργία κενού εγγράφου word με ομαδοποιημένα σχήματα")

*Το παραπάνω στιγμιότυπο οθόνης δείχνει τα τελικά ομαδοποιημένα σχήματα μέσα στο νεοδημιουργημένο έγγραφο Word.*

## Συχνές παραλλαγές και πρόσθετες συμβουλές

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Πολλαπλές εικόνες** | Εισάγετε κάθε εικόνα με `builder.insertImage` και καλέστε `group.appendChild(picture)` για καθεμία. |
| **Διαφορετικοί τύποι σχημάτων** | Χρησιμοποιήστε `ShapeType.OVAL`, `ShapeType.LINE`, κλπ., όταν δημιουργείτε το αντικείμενο `Shape`. |
| **Αλλαγή θέσης ομάδας** | Μετά την προσθήκη όλων των παιδιών, ορίστε `group.setLeft(x)` και `group.setTop(y)` για να μετακινήσετε ολόκληρη την ομάδα. |
| **Εξαγωγή σε PDF** | Καλέστε `doc.save("output.pdf")` μετά την ομαδοποίηση· το PDF θα διατηρήσει την ομαδοποίηση. |
| **Επιβολή άδειας** | Αν εκτελείτε την έκδοση αξιολόγησης, θα εμφανιστεί υδατογράφημα. Εγκαταστήστε μια έγκυρη άδεια για να το αφαιρέσετε. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο Word**, να εισάγετε ένα **GroupShape**, να **ορίσετε το μέγεθος σχήματος**, να **ορίσετε χρώμα γεμίσματος σχήματος** και να **προσθέσετε παιδί στην ομάδα** χρησιμοποιώντας το Aspose.Words for Java. Αυτό το μοτίβο σας επιτρέπει να δημιουργείτε σύνθετες, προγραμματιστικές διατάξεις που μπορούν να επεξεργαστούν αργότερα στο Word ή να εξαχθούν σε άλλες μορφές.

Στη συνέχεια, εξερευνήστε πώς να **ομαδοποιείτε σχήματα στο Word** με πλαίσια κειμένου, να προσθέτετε υπερσυνδέσμους σε σχήματα ή να αυτοματοποιείτε τη δημιουργία πολυσελιδών εκθέσεων. Οι ίδιες αρχές ισχύουν—απλώς δημιουργήστε επιπλέον σχήματα, ρυθμίστε τις ιδιότητές τους και προσαρμόστε τα στην ίδια ομάδα.

Καλό κώδικα!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}