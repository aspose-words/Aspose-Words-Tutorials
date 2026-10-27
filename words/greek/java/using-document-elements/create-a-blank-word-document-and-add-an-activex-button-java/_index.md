---
category: general
date: 2026-10-16
description: Δημιουργήστε ένα κενό έγγραφο Word με Java και μάθετε πώς να προσθέσετε
  ένα κουμπί ActiveX, να ορίσετε τη λεζάντα του και να προσαρμόσετε τις διαστάσεις
  του χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: el
lastmod: 2026-10-16
og_description: Δημιουργήστε ένα κενό έγγραφο Word με Java, στη συνέχεια προσθέστε
  ένα κουμπί ActiveX, ορίστε την λεζάντα του και καθορίστε τις διαστάσεις του χρησιμοποιώντας
  το Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Δημιουργήστε ένα κενό έγγραφο Word και ενσωματώστε ένα κουμπί ActiveX –
  Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα κουμπί ActiveX (Java)
url: /el/java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα κουμπί ActiveX (Java)

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με Java και Aspose.Words. Θα μάθετε επίσης πώς να **προσθέσετε ένα κουμπί ActiveX**, **ορίσετε τη λεζάντα του κουμπιού** και **ορίσετε τις διαστάσεις του κουμπιού** ώστε ο έλεγχος να εμφανίζεται ακριβώς όπως το περιμένετε.

Αυτό το tutorial καλύπτει:

* Αρχικοποίηση ενός κενό αρχείου Word με Aspose.Words for Java.  
* Εισαγωγή ενός ελέγχου ActiveX `CommandButton`.  
* Διαμόρφωση της λεζάντας και του μεγέθους του κουμπιού.  
* Αποθήκευση του τελικού αρχείου `.docx`.

Θα πρέπει να έχετε βασικές γνώσεις Java και μια πρόσφατη έκδοση της βιβλιοθήκης Aspose.Words for Java (ο κώδικας λειτουργεί με 23.9 και νεότερες). Δεν απαιτούνται πρόσθετες εξαρτήσεις.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Δημιουργήστε ένα κενό έγγραφο Word με ένα κουμπί ActiveX"}

## Δημιουργήστε ένα κενό έγγραφο Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός κενό αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη και παρέχει την κλάση `DocumentBuilder` για επεξεργασία.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Γιατί είναι σημαντικό:**  
Η δημιουργία ενός κενό εγγράφου σας δίνει έναν καθαρό καμβά, αποφεύγοντας τυχόν κρυφά στυλ ή ενότητες που θα μπορούσαν να επηρεάσουν τους υπολογισμούς διάταξης αργότερα.

## Προσθήκη κουμπιού ActiveX στο έγγραφο

Το Aspose.Words σας επιτρέπει να ενσωματώσετε παλαιότερους ελέγχους ActiveX μέσω της κλάσης `Forms2OleControl`. Ο παρακάτω κώδικας εισάγει έναν έλεγχο `CommandButton` στην τρέχουσα θέση του δρομέα.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Συμβουλή:** Η τιμή `setOleClassName` `"Forms.CommandButton.1"` είναι το ProgID για το τυπικό κουμπί Microsoft Forms. Η χρήση διαφορετικού ProgID (π.χ., `"Forms.CheckBox.1"`) θα εισάγει διαφορετικό τύπο ελέγχου.

## Ορισμός λεζάντας κουμπιού

Η λεζάντα είναι το κείμενο που εμφανίζεται στην επιφάνεια του κουμπιού. Μπορείτε να την αλλάξετε οποτεδήποτε πριν αποθηκεύσετε το έγγραφο.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Γιατί το χρειάζεστε:** Οι χρήστες καταλαβαίνουν έναν έλεγχο μόνο όταν ο σκοπός του είναι σαφής. Η ρύθμιση μιας περιγραφικής λεζάντας βελτιώνει τη χρηστικότητα, ειδικά όταν το έγγραφο ανοίγει στο Word στα Windows.

## Ορισμός διαστάσεων κουμπιού

Η θέση και το μέγεθος καθορίζονται σε points (1 point = 1/72 ίντσα). Προσαρμόστε τις τιμές ώστε να ταιριάζουν στη διάταξή σας.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Κοινές παραλλαγές:**

| Σενάριο | Προσαρμογή |
|----------|------------|
| Μεγαλύτερο κουμπί για οθόνες αφής | Αυξήστε αναλογικά τα `setWidth` και `setHeight` |
| Κεντραρισμένο κουμπί στη σελίδα | Υπολογίστε `left = (pageWidth - width) / 2` |
| Πολλαπλά κουμπιά σε στήλη | Αυξήστε το `setTop` για κάθε νέο κουμπί |

## Αποθήκευση του εγγράφου που περιέχει το κουμπί ActiveX

Τέλος, γράψτε το έγγραφο στο δίσκο. Η μορφή `.docx` διατηρεί τον έλεγχο ActiveX για τις εκδόσεις Microsoft Word στα Windows.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `ActiveXCommandButton.docx` στο Word (Windows) εμφανίζει μια κενή σελίδα με ένα κλικ-με-κουμπί με την ετικέτα **Click Me** τοποθετημένο 100 pt από το αριστερό περιθώριο και 200 pt από το πάνω περιθώριο.

## Πλήρες, εκτελέσιμο παράδειγμα

Αντιγράψτε ολόκληρη την κλάση παρακάτω στο IDE σας, προσθέστε το JAR του Aspose.Words for Java στο classpath του έργου και εκτελέστε το.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `ActiveXCommandButton.docx` στον τρέχοντα φάκελο εργασίας. Ανοίξτε το με το Microsoft Word (Windows) για να επαληθεύσετε ότι το κουμπί εμφανίζεται ακριβώς όπως έχει ρυθμιστεί.

## Γιατί αυτή η προσέγγιση συνιστάται

* **Απλότητα:** Χρησιμοποιείται μόνο το βασικό API του Aspose.Words· δεν απαιτείται COM interop ή πρόσθετες βιβλιοθήκες.  
* **Φορητότητα:** Ο κώδικας εκτελείται σε οποιαδήποτε πλατφόρμα υποστηρίζει Java, αν και ο έλεγχος ActiveX λειτουργεί μόνο σε εκδόσεις Word για Windows.  
* **Διατηρησιμότητα:** Όλες οι ιδιότητες (λεζάντα, διαστάσεις, θέση) ορίζονται μέσω σαφών, αυτο‑τεκμηριωτικών μεθόδων, καθιστώντας τις μελλοντικές προσαρμογές απλές.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Λύση |
|---------|------------|
| Το κουμπί δεν εμφανίζεται στο Word σε macOS ή Linux | Οι έλεγχοι ActiveX είναι μόνο για Windows. Χρησιμοποιήστε διαφορετικό έλεγχο (π.χ., ένα content control) για έγγραφα πολλαπλών πλατφορμών. |
| Η λεζάντα περικόπτεται | Βεβαιωθείτε ότι το πλάτος του κουμπιού είναι αρκετό για το κείμενο· αυξήστε το `setWidth` ή χρησιμοποιήστε πιο σύντομη λεζάντα. |
| Το κουμπί επικαλύπτει άλλο περιεχόμενο | Ρυθμίστε τις τιμές `setTop` και `setLeft`, ή εισάγετε μια νέα παράγραφο πριν από τον έλεγχο για να του δώσετε δικό του χώρο. |

## Επόμενα βήματα

Τώρα που μπορείτε να **δημιουργήσετε ένα κενό έγγραφο Word**, **προσθέσετε ένα κουμπί ActiveX**, **ορίσετε τη λεζάντα του κουμπιού** και **ορίσετε τις διαστάσεις του κουμπιού**, μπορείτε να εξερευνήσετε:

* Προσθήκη κώδικα διαχείρισης συμβάντων μέσω μακροεντολών VBA (απαιτεί ενσωμάτωση μονάδας μακροεντολών).  
* Εισαγωγή πολλαπλών ελέγχων σε διάταξη πίνακα για έγγραφα τύπου φόρμας.  
* Χρήση των API **FormField** του Aspose.Words για λύσεις φόρμας πολλαπλών πλατφορμών.

Πειραματιστείτε με διαφορετικά μεγέθη, θέσεις και λεζάντες για να ταιριάζουν στο δικό σας σχέδιο εγγράφου. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}