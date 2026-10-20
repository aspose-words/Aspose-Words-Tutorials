---
category: general
date: 2026-08-23
description: Μάθετε πώς να εισάγετε κουμπί εντολής σε ένα έγγραφο Word χρησιμοποιώντας
  Java και Aspose.Words. Αυτός ο οδηγός δείχνει πώς να προσθέσετε έλεγχο φόρμας, να
  ορίσετε το όνομα του κουμπιού και να ενσωματώσετε ένα κουμπί ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: el
lastmod: 2026-08-23
og_description: Εισαγωγή κουμπιού εντολής σε έγγραφο Word χρησιμοποιώντας Java. Ακολουθήστε
  αυτόν τον οδηγό για να προσθέσετε έλεγχο φόρμας, να ορίσετε το όνομα του κουμπιού
  και να ενσωματώσετε ένα κουμπί ActiveX με το Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Εισαγωγή κουμπιού εντολής στο Word με Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να εισάγετε κουμπί εντολής σε έγγραφο Word χρησιμοποιώντας Java
url: /el/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισαγάγετε κουμπί εντολής σε έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε **εισαγωγή κουμπιού εντολής** σε αρχείο Word, αυτό το tutorial σας δείχνει μια πλήρη λύση με το Aspose.Words for Java. Θα δείτε πώς να προσθέσετε έλεγχο φόρμας, να διαμορφώσετε τη λεζάντα του και να ορίσετε το όνομα του κουμπιού χωρίς να αφήσετε το IDE σας.

Ο οδηγός καλύπτει όλα όσα χρειάζεστε για να δημιουργήσετε ένα `.docx` που περιέχει ένα κουμπί ActiveX έτοιμο για χρήση στο Microsoft Word. Δεν απαιτείται πρόσθετο λογισμικό, και το παράδειγμα λειτουργεί σε Java 8+.

## Τι θα μάθετε

* Πώς να προσθέσετε έλεγχο φόρμας τύπου **CommandButton** σε έγγραφο Word.  
* Τα ακριβή βήματα για **ορισμό ονόματος κουμπιού** και **πρόσθεση ιδιοτήτων ενεργού κουμπιού**.  
* Πώς να αποθηκεύσετε το έγγραφο ώστε το κουμπί να εμφανίζεται σωστά όταν ανοίξει στο Word.  

Θα πρέπει να έχετε ένα βασικό περιβάλλον ανάπτυξης Java και ένα έργο Maven ή Gradle που μπορεί να εισάγει τη βιβλιοθήκη Aspose.Words.

## Προαπαιτούμενα

| Απαίτηση | Αιτία |
|-------------|--------|
| Java 8 ή νεότερη | Το Aspose.Words for Java λειτουργεί σε Java 8+. |
| Maven ή Gradle | Απλοποιεί την προσθήκη της εξάρτησης Aspose.Words. |
| Άδεια Aspose.Words for Java (ή δωρεάν δοκιμή) | Απαιτείται για πλήρη σύνολο λειτουργιών· το API λειτουργεί σε λειτουργία αξιολόγησης. |
| IDE όπως IntelliJ IDEA ή Eclipse | Διευκολύνει την επεξεργασία και την εκτέλεση του παραδείγματος. |

## Βήμα 1: Προσθήκη Aspose.Words στο έργο σας

Αν χρησιμοποιείτε Maven, προσθέστε την ακόλουθη εξάρτηση στο `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Για Gradle, τοποθετήστε αυτή τη γραμμή στο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Αφού η εξάρτηση λυθεί, μπορείτε να εισάγετε τις κλάσεις της βιβλιοθήκης στο αρχείο πηγαίου κώδικα Java.

## Βήμα 2: Εισαγωγή κουμπιού εντολής – ο κεντρικός κώδικας

Δημιουργήστε μια νέα κλάση Java με όνομα `InsertCommandButtonDemo`. Ο παρακάτω κώδικας εκτελεί όλες τις τέσσερις ενέργειες που απαιτούνται για **εισαγωγή κουμπιού εντολής**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Γιατί είναι σημαντική κάθε γραμμή

* **Document & DocumentBuilder** – Παρέχουν την αναπαράσταση σε μνήμη ενός αρχείου Word και το API για την τροποποίηση του περιεχομένου του.  
* **insertForms2OleControl** – Αυτή η μέθοδος **προσθέτει έλεγχο φόρμας** τύπου `COMMAND_BUTTON`. Το αντικείμενο `Forms2OleControl` που επιστρέφεται αντιπροσωπεύει τον έλεγχο ActiveX.  
* **setName** – Αναθέτει ένα προγραμματιστικό αναγνωριστικό (`btnSubmit`). Μακροεντολές ή VBA του Word μπορούν να αναφέρονται σε αυτό το όνομα αργότερα.  
* **setCaption** – Ορίζει το κείμενο που βλέπει ο χρήστης στο κουμπί, απαντώντας στην ερώτηση “πώς να προσθέσετε κουμπί”.  
* **save** – Γράφει το `.docx` στο δίσκο, διατηρώντας το ενσωματωμένο κουμπί ActiveX.

Η εκτέλεση του προγράμματος δημιουργεί το `CommandButtonDemo.docx` στον τρέχοντα φάκελο εργασίας. Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει ένα κουμπί με την ετικέτα **Submit** που μπορείτε να πατήσετε (θα εμφανίσει έναν προεπιλεγμένο διάλογο ActiveX σε λειτουργία αξιολόγησης).

## Βήμα 3: Επαλήθευση του εισαχθέντος κουμπιού στο Word

1. Ανοίξτε το `CommandButtonDemo.docx` με το Microsoft Word (2016 ή νεότερο).  
2. Το κουμπί **Submit** εμφανίζεται εκεί που ήταν ο δρομέας κατά την εισαγωγή.  
3. Κάντε δεξί‑κλικ στο κουμπί και επιλέξτε **Properties** για να δείτε ότι το πεδίο **Name** περιέχει `btnSubmit`.  

Αν το κουμπί δεν εμφανίζεται, βεβαιωθείτε ότι οι **έλεγχοι ActiveX** είναι ενεργοποιημένοι στις ρυθμίσεις του Trust Center του Word.

## Βήμα 4: Προσαρμογή του κουμπιού (προαιρετικό)

Μπορείτε να προσαρμόσετε περαιτέρω το κουμπί ρυθμίζοντας το μέγεθος, τη θέση ή προσθέτοντας μια μακροεντολή VBA. Η κλάση `Forms2OleControl` εκθέτει πρόσθετες ιδιότητες όπως `setWidth`, `setHeight` και `setLeft`. Παρακάτω υπάρχει ένα παράδειγμα που κάνει το κουμπί μεγαλύτερο:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Αυτές οι γραμμές μπορούν να τοποθετηθούν μετά την κλήση `setCaption`. Δείχνουν **πρόσθεση προσαρμογών ενεργού κουμπιού** πέρα από την βασική εισαγωγή.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Συμπτωμα | Αιτία | Διόρθωση |
|---------|-------|-----|
| Το κουμπί δεν εμφανίζεται στο Word | Το έγγραφο αποθηκεύτηκε πριν προστεθεί ο έλεγχος | Βεβαιωθείτε ότι το `insertForms2OleControl` καλείται πριν το `doc.save`. |
| Η λεζάντα του κουμπιού είναι κενή | Δεν κλήθηκε `setCaption` ή κλήθηκε με κενή συμβολοσειρά | Παρέχετε μια μη‑κενή συμβολοσειρά, π.χ. `"Submit"`. |
| Η VBA δεν μπορεί να βρει το κουμπί | Ασυμφωνία ονόματος μεταξύ κώδικα VBA και τιμής `setName` | Διατηρήστε το όνομα συνεπές· χρησιμοποιήστε `setName("btnSubmit")` και αναφερθείτε στο `btnSubmit` στη VBA. |
| Προειδοποίηση ασφαλείας κατά το άνοιγμα του αρχείου | Η ασφάλεια μακροεντολών του Word αποκλείει ελέγχους ActiveX | Ρυθμίστε Trust Center > Macro Settings, ή υπογράψτε το έγγραφο με αξιόπιστο πιστοποιητικό. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες αρχείο πηγαίου κώδικα, έτοιμο για αντιγραφή‑επικόλληση στο IDE σας. Περιλαμβάνει τις δηλώσεις import, τη διαχείριση εξαιρέσεων και ένα μπλοκ σχολίων που εξηγεί κάθε κύριο βήμα.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση του προγράμματος, το `CommandButtonDemo.docx` περιέχει ένα μόνο κουμπί **Submit**. Το άνοιγμα του αρχείου στο Word εμφανίζει το κουμπί ακριβώς στη θέση που βρισκόταν ο δρομέας του `DocumentBuilder`.

## Επόμενα βήματα

* **Προσθήκη περισσότερων ελέγχων φόρμας** – Χρησιμοποιήστε `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` ή `TEXT_BOX` για να δημιουργήσετε πλήρεις φόρμες Word.  
* **Συνδυασμός με mail merge** – Εισάγετε κουμπιά σε έγγραφο mail‑merged για να δημιουργήσετε εξατομικευμένες διαδραστικές φόρμες.  
* **Συμπλήρωση VBA μακροεντολών** – Ενσωματώστε προγραμματιστικά VBA που αντιδρά στο γεγονός `Click` του κουμπιού για προηγμένη αυτοματοποίηση.  

Αυτά τα θέματα επεκτείνουν φυσικά την τεχνική **πρόσθεσης ελέγχου φόρμας** που μόλις κατακτήσατε.

---

### Ανακεφαλαίωση

Τώρα ξέρετε πώς να **εισάγετε κουμπί εντολής** σε έγγραφο Word χρησιμοποιώντας Java, πώς να **προσθέσετε έλεγχο φόρμας**, πώς να **ορίσετε όνομα κουμπιού** και πώς να **προσαρμόσετε ενεργό κουμπί**. Το πλήρες παράδειγμα λειτουργεί αμέσως, και μπορείτε να το προσαρμόσετε σε οποιαδήποτε ροή δημιουργίας εγγράφων. Καλό προγραμματισμό!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Insert Combo Box Form Field in Word Document](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}