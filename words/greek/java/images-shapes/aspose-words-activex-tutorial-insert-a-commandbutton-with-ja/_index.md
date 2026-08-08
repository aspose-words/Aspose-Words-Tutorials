---
category: general
date: 2026-08-07
description: Το εκπαιδευτικό σεμινάριο Aspose.Words ActiveX δείχνει πώς να προσθέσετε
  έναν έλεγχο CommandButton σε ένα έγγραφο Word χρησιμοποιώντας Java. Μάθετε τον πλήρη
  κώδικα, τη διαμόρφωση και τα βήματα αποθήκευσης.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: el
lastmod: 2026-08-07
og_description: Το σεμινάριο Aspose.Words ActiveX εξηγεί πώς να ενσωματώσετε έναν
  έλεγχο CommandButton ActiveX σε ένα έγγραφο Word χρησιμοποιώντας Java. Ακολουθήστε
  το πλήρες παράδειγμα για να δημιουργήσετε, να διαμορφώσετε και να αποθηκεύσετε το
  έγγραφο.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Εκπαιδευτικό πρόγραμμα Aspose.Words ActiveX – Οδηγός βήμα‑βήμα για Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Οδηγός Aspose.Words ActiveX – εισαγωγή CommandButton με Java
url: /el/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutorial – εισαγωγή ενός CommandButton με Java

Αν χρειάζεται να ενσωματώσετε έναν έλεγχο ActiveX σε ένα αρχείο Word, αυτό το **Aspose.Words ActiveX tutorial** σας καθοδηγεί βήμα‑βήμα σε όλη τη διαδικασία. Θα δείτε πώς να δημιουργήσετε ένα κενό έγγραφο, να εισάγετε ένα CommandButton, να ορίσετε τις ιδιότητές του και να αποθηκεύσετε το αποτέλεσμα — όλα με απλό κώδικα Java.

Το παράδειγμα χρησιμοποιεί το Aspose.Words for Java API, το οποίο εξαλείφει την ανάγκη για Microsoft Office στον διακομιστή κατασκευής. Στο τέλος αυτού του οδηγού μπορείτε να δημιουργήσετε αρχεία .docx που περιέχουν πλήρως λειτουργικούς ελέγχους CommandButton, έτοιμους για χρήση σε περιβάλλοντα Windows.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- Java Development Kit (JDK) 8 ή νεότερο εγκατεστημένο.
- Maven ή άλλο εργαλείο κατασκευής για τη διαχείριση εξαρτήσεων.
- Άδεια Aspose.Words for Java (ή προσωρινό κλειδί αξιολόγησης) για να αποφύγετε τα υδατογραφήματα αξιολόγησης.
- Βασική εξοικείωση με τη σύνταξη της Java και τον αντικειμενοστραφή προγραμματισμό.

> **Pro tip:** Προσθέστε την εξάρτηση Aspose.Words Maven στο `pom.xml` σας ώστε το IDE να επιλύει τις κλάσεις αυτόματα:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Βήμα 1: Δημιουργία νέου κενό εγγράφου και ενός `DocumentBuilder`

Η κλάση `Document` αντιπροσωπεύει το αρχείο Word στη μνήμη, ενώ το `DocumentBuilder` παρέχει ένα ευέλικτο API για την επεξεργασία του εγγράφου. Η αρχικοποίηση και των δύο αντικειμένων προετοιμάζει το έγγραφο για περαιτέρω τροποποιήσεις.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Γιατί είναι σημαντικό:**  
Το `DocumentBuilder` παρακολουθεί τη θέση του τρέχοντος κέρσορα, έτσι οποιαδήποτε επακόλουθη ενέργεια εισαγωγής — όπως η προσθήκη ενός ελέγχου — εμφανίζεται ακριβώς εκεί που το προτίθεστε.

## Βήμα 2: Εισαγωγή ελέγχου ActiveX CommandButton

Το Aspose.Words εκθέτει το `Forms2OleControl` για αντικείμενα ActiveX. Η μέθοδος `insertForms2OleControl` απαιτεί τον τύπο του ελέγχου, ο οποίος καθορίζεται μέσω της απαρίθμησης `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Εξήγηση:**  
Ο εισαχθείς έλεγχος είναι ένα αντικείμενο βασισμένο σε COM που το Word θα αποδώσει ως ένα κλικ‑αξιό κουμπί όταν το έγγραφο ανοιχθεί σε περιβάλλον Windows.

## Βήμα 3: Διαμόρφωση των ιδιοτήτων του κουμπιού

Μετά την εισαγωγή, μπορείτε να προσαρμόσετε το όνομα, την ετικέτα, το μέγεθος και τη θέση του κουμπιού. Αυτές οι ιδιότητες επηρεάζουν την εμφάνιση και τη συμπεριφορά του ελέγχου μέσα στο Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Γιατί είναι σημαντικές αυτές οι ρυθμίσεις:**  

- **Name** – Επιτρέπει στα VBA macros να αναφέρονται στον έλεγχο (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Καθορίζει την ορατή ετικέτα που οι χρήστες κάνουν κλικ.
- **Left / Top** – Ελέγχει την τοποθέτηση σε σχέση με τα περιθώρια της σελίδας.
- **Width / Height** – Εξασφαλίζει σταθερό οπτικό μέγεθος σε διαφορετικές αναλύσεις οθόνης.

## Βήμα 4: Αποθήκευση του εγγράφου

Η κλήση `save` γράφει την αναπαράσταση στη μνήμη σε ένα φυσικό αρχείο. Μπορείτε να επιλέξετε οποιαδήποτε υποστηριζόμενη μορφή (`.docx`, `.doc`, `.pdf`, κ.λπ.). Για αυτό το tutorial διατηρούμε τη γονική μορφή Word.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Αποτέλεσμα:**  
Ανοίγοντας το `ActiveXDemo.docx` στο Microsoft Word εμφανίζεται ένα CommandButton με ετικέτα **Submit** στην καθορισμένη θέση. Το κλικ στο κουμπί ενεργοποιεί τη προεπιλεγμένη συμπεριφορά (δεν έχει προσαρτηθεί κώδικας VBA από προεπιλογή).

## Πλήρης κώδικας

Συνδυάζοντας όλα τα κομμάτια, το πλήρες, εκτελέσιμο πρόγραμμα φαίνεται ως εξής:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Αναμενόμενη έξοδος

- Ένα αρχείο με όνομα **ActiveXDemo.docx** στο φάκελο `output`.
- Όταν ανοίξει στο Microsoft Word (Windows), το έγγραφο εμφανίζει ένα κλικ‑αξιό κουμπί **Submit** στην καθορισμένη θέση.
- Το κουμπί μπορεί να επιλεγεί, να μετακινηθεί ή να συνδεθεί με κώδικα VBA μέσω του UI του Word (Developer → Properties).

## Διαχείριση κοινών παραλλαγών

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Αποθήκευση ως .doc** (παραδοσιακή μορφή) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Προσθήκη χειριστή συμβάντος** | Το Word δεν εκθέτει γεγονότα ActiveX μέσω του Aspose.Words. Πρέπει να προσθέσετε κώδικα VBA χειροκίνητα μετά τη δημιουργία του εγγράφου. |
| **Πολλαπλοί έλεγχοι** | Επαναλάβετε το μπλοκ εισαγωγής/διαμόρφωσης με διαφορετικές τιμές `setName` και `setCaption`. |
| **Διαφορετικός τύπος ελέγχου (π.χ., CheckBox)** | Χρησιμοποιήστε `Forms2OleControlType.CHECKBOX` στην κλήση `insertForms2OleControl`. |
| **Μη‑Windows πλατφόρμες** | Οι έλεγχοι ActiveX αποδίδονται μόνο σε Word για Windows. Για λύσεις跨‑πλατφόρμα, εξετάστε τους ελέγχους περιεχομένου (`StructuredDocumentTag`). |

## Καλές πρακτικές και παγίδες

- **Άδεια νωρίς** – Καταχωρίστε την άδεια Aspose.Words πριν δημιουργήσετε το `Document` για να αποφύγετε προτροπές αξιολόγησης.
- **Σύστημα συντεταγμένων** – Οι θέσεις μετριούνται σε points (1 pt = 1/72 in). Μετατρέψτε από pixels ή εκατοστά αν το UI σας χρησιμοποιεί αυτές τις μονάδες.
- **Διαδρομές αρχείων** – Χρησιμοποιήστε απόλυτες διαδρομές ή το API `Paths` της Java για να αποφύγετε `FileNotFoundException` όταν ο φάκελος εξόδου δεν υπάρχει.
- **Ασφάλεια νήματος** – Τα `Document` και `DocumentBuilder` δεν είναι thread‑safe. Δημιουργήστε ξεχωριστές παρουσίες ανά νήμα αν παράγετε έγγραφα παράλληλα.
- **Δοκιμές** – Επαληθεύστε το παραγόμενο έγγραφο στην έκδοση Word-στόχο (π.χ., Word 2016, Word 365) επειδή παλαιότερες εκδόσεις μπορεί να εμφανίζουν τους ελέγχους ActiveX διαφορετικά.

## Συμπέρασμα

Αυτό το **Aspose.Words ActiveX tutorial** δείχνει πώς να προσθέσετε προγραμματιστικά έναν έλεγχο CommandButton σε ένα έγγραφο Word χρησιμοποιώντας Java. Μάθατε πώς να:

1. Αρχικοποιήσετε ένα `Document` και ένα `DocumentBuilder`.
2. Εισάγετε ένα `Forms2OleControl` τύπου `COMMAND_BUTTON`.
3. Ορίσετε το όνομα, την ετικέτα, το μέγεθος και τη θέση του κουμπιού.
4. Αποθηκεύσετε το έγγραφο ως αρχείο .docx που περιέχει τον έλεγχο ActiveX.

Από εδώ μπορείτε να εξερευνήσετε πρόσθετους τύπους ελέγχων, να αυτοματοποιήσετε την ενσωμάτωση κώδικα VBA ή να συνδυάσετε ελέγχους ActiveX με άλλες δυνατότητες του Aspose.Words, όπως mail‑merge και ελέγχους περιεχομένου. Πειραματιστείτε με διαφορετικές διατάξεις και ενσωματώστε τα παραγόμενα έγγραφα στην ευρύτερη Java‑βασισμένη αλυσίδα αναφορών σας.

---

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Χρήση OLE Objects και ActiveX Controls στο Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Μετατροπή Word σε RTF με το Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}