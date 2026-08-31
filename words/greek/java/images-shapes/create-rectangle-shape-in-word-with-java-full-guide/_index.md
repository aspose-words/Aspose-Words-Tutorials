---
category: general
date: 2026-02-10
description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word χρησιμοποιώντας το
  Aspose.Words για Java. Μάθετε πώς να ορίσετε το χρώμα της σκιάς, πώς να προσθέσετε
  σκιά και πώς να δημιουργήσετε έγγραφο Word προγραμματιστικά.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words for Java. Ακολουθήστε αυτόν τον οδηγό βήμα-βήμα για να ορίσετε το
  χρώμα σκιάς, να προσθέσετε σκιά και να δημιουργήσετε έγγραφο Word.
og_title: Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός
tags:
- Aspose.Words
- Java
- Document Automation
title: Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης οδηγός
url: /el/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός

Έχετε ποτέ χρειαστεί να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word αλλά δεν ήξερατε από πού να ξεκινήσετε; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν προσπαθούν για πρώτη φορά να σχεδιάσουν γραφικά προγραμματιστικά στο Word. Τα καλά νέα; Με το Aspose.Words for Java μπορείτε να τοποθετήσετε ένα ορθογώνιο σε μια σελίδα, να του προσθέσετε μια ωραία σκιά και να αποθηκεύσετε το αρχείο σε δευτερόλεπτα. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα πώς **να προσθέσετε σκιά**, **να ορίσετε το χρώμα της σκιάς**, και **να δημιουργήσετε έγγραφο Word** από το μηδέν.  

Θα καλύψουμε όλα όσα χρειάζεστε: τις απαιτούμενες βιβλιοθήκες, κάθε γραμμή κώδικα, γιατί ορισμένες ρυθμίσεις έχουν σημασία, και μερικά κόλπα που ίσως δεν βρείτε στα επίσημα έγγραφα. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση παράδειγμα που δημιουργεί ένα σχήμα ορθογωνίου με μια απαλή γκρι σκιά, αποθηκευμένο ως *Shadow.docx*.

## Προαπαιτούμενα – Τι Χρειάζεστε Πριν Ξεκινήσετε

| Απαίτηση | Λόγος |
|-------------|--------|
| Java Development Kit (JDK) 8 or newer | Το Aspose.Words λειτουργεί σε οποιοδήποτε σύγχρονο JDK. |
| Maven or Gradle (optional) | Απλοποιεί την προσθήκη της εξάρτησης Aspose.Words. |
| Aspose.Words for Java license (or a free trial) | Η βιβλιοθήκη είναι εμπορική· μια δοκιμή λειτουργεί για δοκιμές. |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Σας βοηθά να εκτελέσετε και να εντοπίσετε σφάλματα του παραδείγματος γρήγορα. |

Αν έχετε ήδη ένα έργο Java, απλώς προσθέστε το Maven coordinate:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Δεν απαιτείται περίπλοκη ρύθμιση πέρα από αυτό—απλώς μια απλή μέθοδος `public static void main` αρκεί.

![παράδειγμα δημιουργίας σχήματος ορθογωνίου](https://example.com/rectangle-shadow.png "δημιουργία σχήματος ορθογωνίου με σκιά στο Word")

*Κείμενο alt εικόνας: παράδειγμα δημιουργίας σχήματος ορθογωνίου που δείχνει ένα κυανό ορθογώνιο με γκρι σκιά.*

## Βήμα 1 – Δημιουργία Νέου Εγγράφου Word

Το πρώτο πράγμα που πρέπει να κάνουμε είναι να δημιουργήσουμε ένα κενό έγγραφο. Σκεφτείτε το ως το άνοιγμα ενός φρέσκου αρχείου Word στο οποίο θα σχεδιάσετε αργότερα.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Γιατί να ξεκινήσουμε με ένα κενό `Document`; Επειδή το Aspose.Words θεωρεί την κλάση `Document` ως καμβά για όλες τις επόμενες λειτουργίες—προσθήκη παραγράφων, πινάκων ή σχημάτων. Αν παραλείψετε αυτό το βήμα, θα λάβετε ένα `NullPointerException` τη στιγμή που θα προσπαθήσετε να εισάγετε κάτι.

## Βήμα 2 – Ρύθμιση του DocumentBuilder

Ένας `DocumentBuilder` είναι το φιλικό σας στυλό που γράφει στο `Document`. Είναι ο συνιστώμενος τρόπος προσθήκης περιεχομένου επειδή διαχειρίζεται αυτόματα τη θέση του κέρσορα.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Μπορεί να αναρωτηθείτε, «Γιατί να μην χειριστούμε το έγγραφο απευθείας;» Η απάντηση: ο builder αφαιρεί τις λεπτομέρειες χαμηλού επιπέδου όπως η διαχείριση ενοτήτων, κάνοντας τον κώδικα πιο καθαρό και λιγότερο επιρρεπή σε σφάλματα.

## Βήμα 3 – Εισαγωγή του Σχήματος Ορθογωνίου

Τώρα έρχεται το διασκεδαστικό μέρος—**πώς να δημιουργήσετε σχήμα**. Θα εισάγουμε ένα ορθογώνιο 100 × 50 points και θα του δώσουμε γέμισμα κυανό ώστε να το βλέπετε πραγματικά.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Μερικές σημειώσεις:

* `ShapeType.RECTANGLE` λέει στο Aspose ότι θέλουμε ένα ορθογώνιο· μπορείτε να το αντικαταστήσετε με `OVAL`, `LINE`, κ.λπ.
* Οι διαστάσεις εκφράζονται σε points (1 pt ≈ 1/72 in). Προσαρμόστε τις ώστε να ταιριάζουν στη διάταξή σας.
* Χωρίς χρώμα γεμίσματος το σχήμα θα ήταν αόρατο πάνω σε λευκή σελίδα—για αυτό το κυανό.

## Βήμα 4 – Προσθήκη Σκιάς και **Ορισμός Χρώματος Σκιάς**

Εδώ απαντάμε στο τμήμα του παζλ **πώς να προσθέσετε σκιά**. Το αντικείμενο `ShadowFormat` ελέγχει κάθε οπτικό στοιχείο της σκιάς, από το χρώμα μέχρι την ακτίνα θολώματος.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Γιατί αυτές οι συγκεκριμένες τιμές;

* **Visibility** – Χωρίς `setVisible(true)` οι υπόλοιπες ρυθμίσεις αγνοούνται.
* **Color** – Το γκρι είναι μια ουδέτερη επιλογή που λειτουργεί τόσο σε ανοιχτά όσο και σε σκούρα φόντα. Μπορείτε ελεύθερα να αντικαταστήσετε το `java.awt.Color.GRAY` με οποιοδήποτε `java.awt.Color` θέλετε.
* **Blur radius** – Μια τιμή `5.0` δίνει ένα απαλό φτερό· μεγαλύτεροι αριθμοί κάνουν τη σκιά πιο διαχυτική.
* **OffsetX/Y** – Οι μετατοπίσεις μετακινούν τη σκιά δεξιά και κάτω, μιμούμενες μια πηγή φωτός από πάνω‑αριστερά.
* **Transparency** – Μια ημιδιαφανής σκιά ενσωματώνεται καλύτερα στη σελίδα, ειδικά κατά την εκτύπωση.

Αν χρειάζεστε πιο έντονη εμφάνιση, μειώστε την ακτίνα θολώματος σε `0` και αυξήστε τη μετατόπιση. Η πειραματισμός ενθαρρύνεται—οι σκιές είναι πολύ οπτικές, και οι σωστές ρυθμίσεις εξαρτώνται από το σχεδιασμό του εγγράφου σας.

## Βήμα 5 – Αποθήκευση του Εγγράφου

Τέλος, αποθηκεύουμε όλα σε ένα αρχείο `.docx`. Μπορείτε να επιλέξετε οποιοδήποτε μονοπάτι θέλετε· απλώς βεβαιωθείτε ότι ο φάκελος υπάρχει.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Όταν ανοίξετε το *Shadow.docx* στο Microsoft Word, θα δείτε ένα κυανό ορθογώνιο με μια διακριτική γκρι σκιά που αιωρείται 4 pts δεξιά και κάτω. Αυτή είναι η πλήρης ροή εργασίας **create word document**.

### Αναμενόμενο Αποτέλεσμα

| Στοιχείο | Εμφάνιση |
|---------|------------|
| Ορθογώνιο | Γέμισμα κυανό, μέγεθος 100 × 50 pt |
| Σκιά | Γκρι, 30 % διαφανής, θόλωση 5 pt, μετατόπιση (4, 4) |
| Αρχείο | `Shadow.docx` αποθηκευμένο στο μονοπάτι που δώσατε |

Αν το σχήμα δεν εμφανίζεται, ελέγξτε ξανά ότι το χρώμα γεμίσματος δεν είναι το ίδιο με το φόντο της σελίδας και ότι η σκιά είναι ορισμένη ως ορατή.

## Συμβουλές & Συνηθισμένα Πιθανά Σφάλματα

* **Συμβουλή:** Χρησιμοποιήστε `rectangle.setStrokeColor(java.awt.Color.BLACK);` αν θέλετε ένα περίγραμμα γύρω από το σχήμα. Κάνει το ορθογώνιο να ξεχωρίζει περισσότερο σε μια εκτυπωμένη σελίδα.
* **Προσοχή:** Η αποθήκευση σε φάκελο μόνο για ανάγνωση θα προκαλέσει `IOException`. Επιλέξτε μια θέση με δικαιώματα εγγραφής ή προσαρμόστε τα δικαιώματα αρχείου.
* **Ακραία περίπτωση:** Αν χρειάζεστε διαφανές γέμισμα (χωρίς χρώμα), καλέστε `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Το σχήμα θα εξακολουθεί να ρίχνει σκιά, κάτι που μπορεί να είναι χρήσιμο για γραφικά τύπου υδατογραφήματος.
* **Σημείωση απόδοσης:** Η προσθήκη εκατοντάδων σχημάτων σε βρόχο μπορεί να αυξήσει τη χρήση μνήμης. Καλέστε `document.save` μόνο μία φορά μετά την προσθήκη όλων των σχημάτων.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι ολόκληρο το πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια κλάση Java με όνομα `ShadowDemo`. Συγκεντρώνεται και εκτελείται όπως είναι (εφόσον έχετε το JAR του Aspose.Words στο classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο *Shadow.docx*, και θα δείτε το ορθογώνιο με τη σκιά του ακριβώς όπως περιγράφεται.

## Τι Αν Χρειάζεστε Περισσότερα Σχήματα;

Μπορεί να αναρωτηθείτε, «Μπορώ να **δημιουργήσω σχήμα ορθογωνίου** πολλές φορές ή να χρησιμοποιήσω άλλα σχήματα;» Απόλυτα. Απλώς κάντε βρόχο πάνω στον κώδικα εισαγωγής και προσαρμόστε τις συντεταγμένες χρησιμοποιώντας `builder.moveTo` ή `builder.insertParagraph`. Οι ίδιες ρυθμίσεις σκιάς μπορούν να επαναχρησιμοποιηθούν εξάγοντας τις σε μια βοηθητική μέθοδο:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Καλέστε `applyStandardShadow(rectangle);` μετά από κάθε εισαγωγή σχήματος για να διατηρήσετε τον κώδικά σας DRY (Don’t Repeat Yourself).

## Επόμενα Βήματα – Πέρα από τα Βασικά

Τώρα που γνωρίζετε **πώς να προσθέσετε σκιά**, σκεφτείτε να εξερευνήσετε τα παρακάτω συναφή θέματα:

* **How to set shadow color** για κείμενα – δίνει στους τίτλους μια διακριτική άνοδο.
* **Create word document** με πίνακες και εικόνες – συνδυάστε σχήματα με άλλο περιεχόμενο.
* **How to create shape** animations using Word’s built‑in

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}