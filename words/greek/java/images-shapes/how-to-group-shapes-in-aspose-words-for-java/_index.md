---
category: general
date: 2026-10-20
description: Πώς να ομαδοποιήσετε σχήματα στο Aspose.Words για Java – μάθετε πώς να
  εισάγετε σχήμα ορθογωνίου, να τα ομαδοποιήσετε και να αποθηκεύσετε το έγγραφο σε
  έναν ενιαίο οδηγό.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: el
lastmod: 2026-10-20
og_description: Πώς να ομαδοποιήσετε σχήματα στο Aspose.Words for Java. Αυτό το σεμινάριο
  δείχνει πώς να εισάγετε σχήμα ορθογωνίου, να τα ομαδοποιήσετε και να εξάγετε το
  αποτέλεσμα.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Πώς να ομαδοποιήσετε σχήματα στο Aspose.Words for Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Πώς να ομαδοποιήσετε σχήματα στο Aspose.Words για Java
url: /el/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Aspose.Words for Java

Αν χρειάζεστε **πώς να ομαδοποιήσετε σχήματα** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java, αυτός ο οδηγός σας δείχνει τη πλήρη ροή εργασίας. Θα μάθετε πώς να **εισάγετε σχήμα ορθογωνίου**, να προσθέσετε ένα δεύτερο ορθογώνιο, να ομαδοποιήσετε τα δύο σχήματα και, τέλος, να αποθηκεύσετε το αρχείο — όλα με σαφή, εκτελέσιμο κώδικα.

Η ομαδοποίηση σχημάτων είναι χρήσιμη όταν θέλετε να μετακινήσετε, περιστρέψετε ή μορφοποιήσετε πολλά σχέδια ως μία ενιαία μονάδα. Είτε δημιουργείτε ένα πρότυπο αναφοράς, ένα διάγραμμα ή ένα προσαρμοσμένο φυλλάδιο, η εξοικείωση με την ομαδοποίηση σχημάτων σας εξοικονομεί χρόνο και διατηρεί τη διάταξη συνεπή.

Σε αυτόν τον οδηγό θα:

* Δημιουργήσετε ένα νέο `Document` και ένα `DocumentBuilder`.
* **Πώς να εισάγετε σχήμα ορθογωνίου** με ακριβείς διαστάσεις.
* Ομαδοποιήσετε τα ορθογώνια σε ένα `GroupShape`.
* Αποθηκεύσετε το έγγραφο και επαληθεύσετε το αποτέλεσμα.

> **Προαπαιτούμενο** – Πρέπει να έχετε το Aspose.Words for Java (v23.12 ή νεότερο) προστιθέμενο στο έργο σας. Οι χρήστες Maven μπορούν να συμπεριλάβουν την εξάρτηση που φαίνεται παρακάτω.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Τι θα χρειαστείτε

| Στοιχείο | Αιτία |
|------|--------|
| Java 17+ | Σύγχρονα χαρακτηριστικά γλώσσας και καλύτερη απόδοση |
| Aspose.Words for Java | Παρέχει τα API `DocumentBuilder`, `Shape` και `GroupShape` |
| Ένα IDE (IntelliJ IDEA, Eclipse, VS Code, κ.λπ.) | Για τη μεταγλώττιση και εκτέλεση του παραδείγματος |
| Δικαίωμα εγγραφής σε φάκελο | Το έγγραφο θα αποθηκευτεί στο δίσκο |

---

## Πώς να εισάγετε σχήμα ορθογωνίου

Το πρώτο βήμα είναι η δημιουργία ενός `Document` και ενός `DocumentBuilder`. Ο builder παρέχει μεθόδους όπως η `insertShape` για την τοποθέτηση αντικειμένων σχεδίασης.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Γιατί είναι σημαντικό** – Η χρήση της `insertShape` είναι ο τυπικός τρόπος **πώς να εισάγετε σχήμα ορθογωνίου** αντικειμένων στο Aspose.Words. Προσθέτει αυτόματα το σχήμα στην τρέχουσα παράγραφο του εγγράφου, ώστε να μην χρειάζεται να διαχειριστείτε το χαμηλού επιπέδου OpenXML.

## Προσαρμογή θέσεων ορθογωνίου (προαιρετικό)

Αν το δεύτερο ορθογώνιο χρειάζεται προσαρμοσμένη θέση σε σχέση με το πρώτο, μπορείτε να τροποποιήσετε τις ιδιότητες `left` και `top`. Αυτό το βήμα είναι προαιρετικό αλλά συχνά απαιτείται για ακριβή διάταξη διαγράμματος.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Συμβουλή:** Όλες οι μετρήσεις είναι σε points (1 pt ≈ 1/72 in). Χρησιμοποιήστε `convertPointsToPixels` αν χρειάζεστε τιμές pixel για υπολογισμούς UI.

## Πώς να ομαδοποιήσετε σχήματα

Τώρα που τα ορθογώνια υπάρχουν, μπορείτε να τα τοποθετήσετε μέσα σε ένα `GroupShape`. Η ομαδοποίηση κάνει τα δύο ορθογώνια να συμπεριφέρονται σαν ένα ενιαίο αντικείμενο — η μετακίνηση, η περιστροφή ή η μορφοποίηση της ομάδας θα επηρεάσει και τα δύο σχήματα.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Γιατί λειτουργεί η ομαδοποίηση** – Το `GroupShape` κληρονομεί από το `Shape`, οπότε μπορείτε να αντιμετωπίζετε την ομάδα ακριβώς όπως οποιοδήποτε άλλο αντικείμενο σχεδίασης. Όταν καλείτε `appendChild`, τα σχήματα αφαιρούνται από την αρχική τους θέση και γίνονται παιδιά της ομάδας.

## Αποθήκευση του εγγράφου που περιέχει τα ομαδοποιημένα σχήματα

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα περιέχει ένα μόνο `GroupShape` με δύο ορθογώνια μέσα.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `GroupShape.docx` στο Microsoft Word:

* Θα δείτε δύο ορθογώνια (μπλε και πράσινο) τοποθετημένα πλάι‑πλάι.
* Η επιλογή οποιουδήποτε ορθογωνίου επιλέγει ολόκληρη την ομάδα — η μετακίνηση σύρεται και τα δύο μαζί.
* Η ομάδα έχει ένα λεπτό κόκκινο περίγραμμα, επιβεβαιώνοντας ότι οι ιδιότητες του `GroupShape` έχουν εφαρμοστεί.

Αν κάνετε δεξί‑κλικ στην ομάδα και επιλέξετε **Group → Ungroup**, τα ορθογώνια επιστρέφουν σε ανεξάρτητα σχήματα, δείχνοντας ότι η λειτουργία ομαδοποίησης είναι αντιστρέψιμη.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Περισσότερα από δύο σχήματα** | Εισάγετε κάθε σχήμα, έπειτα προσθέστε όλα στο ίδιο `GroupShape`. |
| **Διαφορετικοί τύποι σχημάτων** (π.χ., έλλειψη, εικόνα) | Χρησιμοποιήστε `builder.insertShape(ShapeType.ELLIPSE, …)` ή `builder.insertImage(...)` πριν την προσθήκη. |
| **Κλιμάκωση της ομάδας** | Καλέστε `group.setWidth(newWidth)` ή `group.setHeight(newHeight)`· τα παιδιά κλιμακώνονται αναλογικά. |
| **Περιστροφή της ομάδας** | `group.setRotationAngle(45);` περιστρέφει ολόκληρη τη συλλογή γύρω από το κέντρο της. |
| **Διατήρηση αρχικών θέσεων** | Αποθηκεύστε τα `left`/`top` κάθε σχήματος πριν την ομαδοποίηση και επαναφέρετε μετά την αποομαδοποίηση αν χρειάζεται. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται η πλήρης κλάση Java που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας. Περιλαμβάνει όλες τις εισαγωγές, τη διαχείριση σφαλμάτων και σχόλια για σαφήνεια.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο `GroupShape.docx` και θα δείτε τα ομαδοποιημένα ορθογώνια ακριβώς όπως περιγράφηκε.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να ομαδοποιήσετε σχήματα** στο Aspose.Words for Java, από τη δημιουργία εγγράφου μέχρι την εισαγωγή σχημάτων ορθογωνίου, την προσαρμογή των θέσεών τους και, τέλος, την ομαδοποίησή τους με `GroupShape`. Αυτή η τεχνική σας επιτρέπει να αντιμετωπίζετε πολλά σχέδια ως μία ενιαία οντότητα, απλοποιώντας τις προσαρμογές διάταξης και τη οπτική συνέπεια.

**Επόμενα βήματα**

* Εξερευνήστε **πώς να εισάγετε σχήμα ορθογωνίου** με διαφορετικά μοτίβα γεμίσματος ή περιγράμματα.
* Συνδυάστε **εισάγετε σχήμα ορθογωνίου** με πλαίσια κειμένου για τη δημιουργία επισημασμένων διαγραμμάτων.
* Πειραματιστείτε με την περιστροφή ή την κλιμάκωση της ομάδας για την παραγωγή πιο σύνθετων γραφικών.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα για άλλους τύπους σχημάτων, μεγαλύτερες ομάδες ή σενάρια δυναμικής δημιουργίας εγγράφων. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές ενότητες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή σχήματος ορθογωνίου σε Java – Ομαδοποίηση και τοποθέτηση σχημάτων](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [πώς να εισάγετε σχήμα ομάδας σε Java – Πλήρης Οδηγός](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Πώς να ορίσετε σκιά σε σχήμα στο Aspose.Words – Πλήρης Οδηγός](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}