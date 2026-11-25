---
category: general
date: 2026-11-25
description: Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας Java και πώς να
  ορίσετε τις διαστάσεις των σχημάτων σε ένα αρχείο DOCX με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: el
lastmod: 2026-11-25
og_description: Πώς να ομαδοποιήσετε σχήματα στο Word με το Aspose.Words Java API
  και να ρυθμίσετε γρήγορα το μέγεθος του σχήματος. Ακολουθήστε τη πλήρη βήμα‑βήμα
  λύση.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Πώς να ομαδοποιήσετε σχήματα στο Word και να ορίσετε τις διαστάσεις τους
  – Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Πώς να ομαδοποιήσετε σχήματα στο Word και να ορίσετε τις διαστάσεις τους προγραμματιστικά
url: /el/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word και να ορίσετε τις διαστάσεις τους προγραμματιστικά

Αν χρειάζεστε **πώς να ομαδοποιήσετε σχήματα στο Word** και να ελέγξετε το ακριβές τους μέγεθος, αυτός ο οδηγός σας δείχνει μια πλήρη, εκτελέσιμη λύση. Χρησιμοποιώντας το Aspose.Words for Java μπορείτε να δημιουργήσετε ένα ορθογώνιο, μια έλλειψη, να τα προσθέσετε σε ένα `GroupShape` και στη συνέχεια **πώς να ορίσετε διαστάσεις σχήματος** όπως το πλάτος και το ύψος σε ένα ενιαίο αρχείο DOCX.

Θα μάθετε πώς να:

* Δημιουργήσετε ένα νέο έγγραφο Word από το μηδέν.  
* Εισάγετε ένα `GroupShape` (νέο API στην έκδοση 24.9).  
* Προσθέσετε ένα ορθογώνιο και μια έλλειψη στην ομάδα.  
* **Ορίσετε το μέγεθος του σχήματος Word** με ακρίβεια χρησιμοποιώντας `setWidth` και `setHeight`.  
* Αποθηκεύσετε το έγγραφο στο δίσκο.

Δεν απαιτείται εξωτερικό εργαλείο—μόνο Java 17+, Maven και η βιβλιοθήκη Aspose.Words for Java.

## Προαπαιτούμενα

* Java Development Kit 17 ή νεότερο.  
* Maven (ή Gradle) για διαχείριση εξαρτήσεων.  
* Aspose.Words for Java 24.9 ή νεότερο (το API `GroupShape` εισήχθη στην 24.9).  
* Βασική εξοικείωση με τη σύνταξη της Java και τις αντικειμενο‑προσανατολισμένες έννοιες.

Αν δεν έχετε προσθέσει ακόμη το Aspose.Words στο έργο σας, συμπεριλάβετε την παρακάτω εξάρτηση Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Βήμα 1: Δημιουργία νέου εγγράφου και DocumentBuilder

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ η `DocumentBuilder` παρέχει έναν βολικό τρόπο για την προσθήκη περιεχομένου.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί αυτό το βήμα;*  
Η δημιουργία ενός φρέσκου `Document` σας δίνει έναν καθαρό καμβά. Η `DocumentBuilder` είναι ο υψηλού επιπέδου βοηθός που σας επιτρέπει να εισάγετε παραγράφους, πίνακες και, σε αυτήν την περίπτωση, σχήματα.

## Βήμα 2: Εισαγωγή GroupShape (νέο API στην έκδοση 24.9)

Ένα `GroupShape` λειτουργεί ως κοντέινερ· οποιοδήποτε σχήμα προσθέτετε γίνεται μέρος της ίδιας οπτικής ομάδας.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Γιατί να χρησιμοποιήσετε το `GroupShape`;*  
Η ομαδοποίηση σχημάτων απλοποιεί τη μετακίνηση, την περιστροφή ή την εφαρμογή μορφοποίησης σε πολλά αντικείμενα ταυτόχρονα. Το API προστέθηκε στην 24.9, οπότε παλαιότερες εκδόσεις δεν θα μπορούν να μεταγλωττίσουν αυτή τη γραμμή.

## Βήμα 3: Δημιουργία ορθογωνίου, ορισμός μεγέθους και προσθήκη στην ομάδα

Εδώ δείχνουμε **πώς να ορίσετε διαστάσεις σχήματος** για ένα ορθογώνιο.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Γιατί να ορίσετε ρητά το πλάτος και το ύψος;*  
Το Word αποθηκεύει το μέγεθος του σχήματος σε points. Καλώντας `setWidth` και `setHeight` ελέγχετε το ακριβές οπτικό αποτύπωμα, κάτι που είναι απαραίτητο όταν χρειάζεστε ακριβή διάταξη ή όταν εξάγετε σε PDF.

## Βήμα 4: Δημιουργία έλλειψης, ορισμός μεγέθους και προσθήκη στην ίδια ομάδα

Η ίδια τεχνική **set shape size word** λειτουργεί για οποιοδήποτε τύπο σχήματος.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Γιατί να προσθέσετε την έλλειψη στην ίδια `GroupShape`;*  
Και τα δύο σχήματα θα μετακινούνται μαζί ως μία μονάδα. Αυτό είναι χρήσιμο για τη δημιουργία εικονιδίων, λογοτύπων ή σύνθετων διαγραμμάτων που πρέπει να παραμένουν ευθυγραμμισμένα.

## Βήμα 5: Αποθήκευση του εγγράφου με τα ομαδοποιημένα σχήματα

Τέλος, αποθηκεύστε το αρχείο DOCX στο δίσκο.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Η εκτέλεση αυτού του προγράμματος παράγει ένα αρχείο με όνομα **GroupShape.docx** που περιέχει ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί. Όταν ανοίξετε το αρχείο στο Microsoft Word, θα δείτε τα δύο σχήματα να συμπεριφέρονται ως ένα ενιαίο αντικείμενο—μπορείτε να τα σύρετε, να αλλάξετε το μέγεθός τους ή να τα περιστρέψετε μαζί.

### Αναμενόμενο αποτέλεσμα

* Ένα έγγραφο Word (`GroupShape.docx`) με μία σελίδα.  
* Ένα `GroupShape` που περιέχει ένα ορθογώνιο 100 × 50 pt και μια έλλειψη 80 × 80 pt.  
* Η επιλογή οποιουδήποτε σχήματος επιλέγει ολόκληρη την ομάδα.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

### Πώς να αλλάξετε τη θέση των ομαδοποιημένων σχημάτων;

Μετά τη δημιουργία του `GroupShape`, μπορείτε να ορίσετε τις ιδιότητες `left` και `top`:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Αυτές οι συντεταγμένες μετρώνται επίσης σε points.

### Τι γίνεται αν χρειαστεί να προσθέσω περισσότερα από δύο σχήματα;

Το `GroupShape` λειτουργεί όπως οποιοδήποτε άλλο κόμβο κοντέινερ. Καλέστε `groupShape.appendChild(yourShape)` για κάθε επιπλέον σχήμα. Το API δεν περιορίζει τον αριθμό των παιδιών.

### Μπορώ να εφαρμόσω στυλ (χρώμα γεμίσματος, πάχος γραμμής) σε μεμονωμένα σχήματα;

Ναι. Κάθε αντικείμενο `Shape` εκθέτει ιδιότητες μορφοποίησης:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Λειτουργεί ο κώδικας με παλαιότερες εκδόσεις του Aspose.Words;

Η μέθοδος `insertGroupShape` εισήχθη στην έκδοση 24.9. Αν χρησιμοποιείτε παλαιότερη έκδοση, θα πρέπει να δημιουργήσετε ένα `GroupShape` χειροκίνητα μέσω του δέντρου κόμβων, κάτι που είναι πιο πολύπλοκο. Η αναβάθμιση είναι η προτεινόμενη λύση.

## Pro tips

* **Χρησιμοποιήστε points για συνέπεια** – Η εσωτερική μονάδα του Word είναι το point (1/72 inch). Η μετατροπή από pixels ή εκατοστά μπορεί να οδηγήσει σε απροσδόκητα μεγέθη.  
* **Ομαδοποιήστε πριν τοποθετήσετε** – Τοποθετήστε το `GroupShape` αφού έχετε προσθέσει όλα τα παιδιά του· διαφορετικά ίσως χρειαστεί να επαναϋπολογίσετε τις μετατοπίσεις.  
* **Επαναχρησιμοποιήστε το DocumentBuilder** – Μπορείτε να εισάγετε πολλαπλές ομάδες στο ίδιο έγγραφο μετακινώντας τον κέρσορα του builder (`builder.moveTo`) πριν από κάθε κλήση `insertGroupShape`.

## Συμπέρασμα

Τώρα έχετε ένα πλήρες, end‑to‑end παράδειγμα του **πώς να ομαδοποιήσετε σχήματα στο Word** και του **πώς να ορίσετε διαστάσεις σχήματος** χρησιμοποιώντας το Aspose.Words for Java. Ο οδηγός κάλυψε τη δημιουργία εγγράφου, την εισαγωγή ενός `GroupShape`, την προσθήκη ορθογωνίου και έλλειψης, τον ορισμό του ακριβούς μεγέθους τους και την αποθήκευση του αποτελέσματος.  

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη πλαισίων κειμένου ή εικόνων στην ίδια ομάδα.  
* Ανιμέωση ομαδοποιημένων σχημάτων με τις δυνατότητες smart art του Word (μέσω του API).  
* Εξαγωγή των ομαδοποιημένων σχημάτων σε PDF ή SVG για χρήση στο web.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους σχημάτων, μεγέθη και θέσεις—η ομαδοποίηση σας δίνει ισχυρό έλεγχο πάνω σε σύνθετες διατάξεις σε έγγραφα Word.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}