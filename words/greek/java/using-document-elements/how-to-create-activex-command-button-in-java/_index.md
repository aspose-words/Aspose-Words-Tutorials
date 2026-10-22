---
category: general
date: 2026-10-07
description: Δημιουργήστε κουμπί εντολής ActiveX σε Java και προσθέστε προγραμματιστικά
  το κουμπί εντολής σε έγγραφα Word. Μάθετε πώς να ορίζετε τις αριστερές και άνω θέσεις
  του κουμπιού.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: el
lastmod: 2026-10-07
og_description: Δημιουργήστε κουμπί εντολής ActiveX σε Java για να ενσωματώσετε διαδραστικούς
  ελέγχους στα έγγραφα Word. Μάθετε πώς να προσθέτετε προγραμματιστικά το κουμπί εντολής,
  να ορίζετε τη θέση του και να προσαρμόζετε την εμφάνισή του.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Δημιουργία κουμπιού εντολής ActiveX σε Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Πώς να δημιουργήσετε κουμπί εντολής ActiveX σε Java
url: /el/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κουμπί εντολής ActiveX σε Java

Αν χρειάζεστε να **δημιουργήσετε κουμπί εντολής ActiveX** σε ένα έγγραφο Word χρησιμοποιώντας Java, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που **προσθέτει προγραμματιστικά ένα κουμπί εντολής**, το τοποθετεί με `setLeft` και `setTop`, και αποθηκεύει το αποτέλεσμα ως αρχείο `.docx`.

Η ενσωμάτωση ενός διαδραστικού κουμπιού σας επιτρέπει να δημιουργήσετε φόρμες, να αυτοματοποιήσετε ροές εργασίας ή να συλλέξετε εισροές χρήστη απευθείας μέσα σε ένα αρχείο Word. Τα παρακάτω βήματα καλύπτουν τα πάντα, από τη ρύθμιση του έργου μέχρι την τελική επαλήθευση, ώστε να μπορείτε να αντιγράψετε τον κώδικα στο δικό σας έργο χωρίς να χάσετε καμία λεπτομέρεια.

## Προαπαιτούμενα

- JDK 17 ή νεότερο εγκατεστημένο  
- Maven 3.8+ (ή το προτιμώμενο εργαλείο κατασκευής σας)  
- Aspose.Words for Java 23.9 ή νεότερο – η βιβλιοθήκη που παρέχει `DocumentBuilder` και υποστήριξη ελέγχου OLE  
- Βασική εξοικείωση με τη σύνταξη της Java και τις αντικειμενοστραφείς έννοιες  

Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Συμβουλή:** Χρησιμοποιήστε την πιο πρόσφατη έκδοση του Aspose.Words για να επωφεληθείτε από διορθώσεις σφαλμάτων και νέες δυνατότητες OLE.

## Βήμα 1: Δημιουργήστε ένα νέο κενό έγγραφο και έναν DocumentBuilder

Το πρώτο βήμα για **να δημιουργήσετε κουμπί εντολής ActiveX** είναι να δημιουργήσετε ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder σας παρέχει μια ευέλικτη API για την εισαγωγή περιεχομένου, συμπεριλαμβανομένων ελέγχων OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει το αρχείο Word στη μνήμη, ενώ το `DocumentBuilder` λειτουργεί ως κέρσορας που σας επιτρέπει να τοποθετείτε στοιχεία ακριβώς εκεί που τα χρειάζεστε.

## Βήμα 2: Εισάγετε έναν έλεγχο κουμπιού εντολής OLE

Οι έλεγχοι ActiveX εισάγονται ως αντικείμενα OLE. Το Aspose.Words παρέχει την κλάση `Forms2OleControl` για αυτόν τον σκοπό.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Όταν καλείτε τη μέθοδο `insertForms2OleControl()`, το Aspose δημιουργεί αυτόματα ένα σχήμα placeholder που θα φιλοξενήσει το κουμπί ActiveX.

## Βήμα 3: Διαμορφώστε τις ιδιότητες του κουμπιού

Τώρα **προσθέτετε προγραμματιστικά το κουμπί εντολής** με λεπτομέρειες όπως το ProgID, τη λεζάντα και το μέγεθος. Το πιο κοινό ProgID για ένα κουμπί εντολής είναι `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Πώς να ορίσετε την αριστερή και άνω θέση του κουμπιού

Η τοποθέτηση του κουμπιού είναι το σημείο όπου η δευτερεύουσα λέξη-κλειδί **how to set button left top** γίνεται σχετική. Οι μέθοδοι `setLeft` και `setTop` δέχονται τιμές μετρημένες σε points (1 point = 1/72 ίντσες).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Ρυθμίστε αυτούς τους αριθμούς ώστε να ταιριάζουν με τη διάταξή σας. Για παράδειγμα, για να ευθυγραμμίσετε το κουμπί με ένα κελί πίνακα, υπολογίστε τις συντεταγμένες του κελιού και περάστε τις στις `setLeft`/`setTop`.

## Βήμα 4: Αποθηκεύστε το έγγραφο

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα περιέχει το κουμπί ActiveX έτοιμο για αλληλεπίδραση όταν ανοίξει στο Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Η εκτέλεση της μεθόδου `main` παράγει το `CommandButton.docx`. Ανοίξτε το αρχείο στο Word, ενεργοποιήστε το περιεχόμενο αν σας ζητηθεί, και θα δείτε ένα κλικ-μεγαλό κουμπί με την ετικέτα **Click Me** τοποθετημένο στις συντεταγμένες που καθορίσατε.

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Στιγμιότυπο δημιουργίας κουμπιού εντολής ActiveX σε Java που δείχνει το κουμπί μέσα στο έγγραφο Word"}

## Κοινές παραλλαγές και ειδικές περιπτώσεις

### Προσθήκη πολλαπλών κουμπιών

Αν χρειάζεστε πολλά κουμπιά, επαναλάβετε το **Βήμα 2** και το **Βήμα 3** για κάθε έλεγχο. Θυμηθείτε να προσαρμόσετε τις `setLeft` και `setTop` ώστε τα κουμπιά να μην επικαλύπτονται.

### Αλλαγή συμπεριφοράς κουμπιού

Τα κουμπιά ActiveX μπορούν να εκτελούν μακροεντολές VBA όταν πατιούνται. Για να συνδέσετε μια μακροεντολή, ορίστε την ιδιότητα `setOnAction` με το όνομα της μακροεντολής:

```java
commandButton.setOnAction("MyMacro");
```

Βεβαιωθείτε ότι το έγγραφο-στόχος περιέχει το αντίστοιχο μοντέλο VBA· διαφορετικά το Word θα εμφανίσει σφάλμα.

### Σημειώσεις συμβατότητας

- Το κουμπί λειτουργεί μόνο σε εκδόσεις desktop του Word που υποστηρίζουν ActiveX (π.χ., Word για Windows). Θα εμφανίζεται ως στατική εικόνα στο Word για Mac ή σε διαδικτυακούς επεξεργαστές.  
- Αν στοχεύετε σε μικτό περιβάλλον, σκεφτείτε τη χρήση ενός **content control** (`RichTextContentControl`) αντί για έλεγχο ActiveX.

## Πλήρης πηγαίος κώδικας για αναφορά

Παρακάτω βρίσκεται το πλήρες, αυτόνομο παράδειγμα που μπορείτε να αντιγράψετε σε ένα νέο έργο Maven και να το εκτελέσετε αμέσως.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση, θα βρείτε το `CommandButton.docx` στον φάκελο εργασίας του έργου σας. Ανοίγοντας το αρχείο στο Microsoft Word εμφανίζεται ένα κουμπί στην καθορισμένη θέση με τη λεζάντα “Click Me”.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κουμπί εντολής ActiveX** σε Java, **να προσθέσετε προγραμματιστικά κουμπί εντολής** σε ένα έγγραφο Word, και να ελέγχετε με ακρίβεια τη διάταξή του χρησιμοποιώντας τις μεθόδους **how to set button left top**. Αυτή η τεχνική ανοίγει το δρόμο για πλούσιες, διαδραστικές φόρμες Word που μπορούν να εκκινήσουν μακροεντολές, να ξεκινήσουν εξωτερικές εφαρμογές ή να συλλέξουν εισροές χρήστη απευθείας μέσα στο έγγραφο.

### Επόμενα βήματα

- Εξερευνήστε άλλους ελέγχους ActiveX όπως `Forms.TextBox.1` ή `Forms.CheckBox.1`.  
- Συνδυάστε πολλαπλούς ελέγχους με ένα μοντέλο VBA για να υλοποιήσετε πλήρεις φόρμες.  
- Αντικαταστήστε το ActiveX με content controls εάν χρειάζεστε συμβατότητα μεταξύ πλατφορμών.  

Μη διστάσετε να πειραματιστείτε με το μέγεθος, τη λεζάντα και τη θέση για να ταιριάζει με το UI design σας. Αν αντιμετωπίσετε προβλήματα, ελέγξτε ξανά ότι η έκδοση του Aspose.Words που χρησιμοποιείτε υποστηρίζει ελέγχους OLE και βεβαιωθείτε ότι οι ρυθμίσεις ασφαλείας του Word επιτρέπουν την εκτέλεση ActiveX. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ενσωμάτωση αντικειμένων OLE και ελέγχων ActiveX σε έγγραφα Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}