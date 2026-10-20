---
category: general
date: 2026-10-20
description: Δημιουργήστε ένα κενό αρχείο DOCX προγραμματιστικά και ενσωματώστε ένα
  κουμπί εντολής χρησιμοποιώντας Java. Μάθετε τον πλήρη κώδικα δημιουργίας εγγράφου
  Word για να αποθηκεύσετε το Word με το κουμπί και να ορίσετε τη λεζάντα του κουμπιού
  εντολής.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: el
lastmod: 2026-10-20
og_description: Δημιουργήστε ένα κενό αρχείο DOCX προγραμματιστικά και ενσωματώστε
  ένα κουμπί εντολής. Ακολουθήστε αυτόν τον βήμα‑βήμα οδηγό Java για να αποθηκεύσετε
  το Word με το κουμπί και να ορίσετε τη λεζάντα του κουμπιού εντολής.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Δημιουργήστε ένα κενό αρχείο DOCX προγραμματιστικά – προσθέστε ένα κουμπί
  εντολής
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Δημιουργήστε ένα κενό DOCX προγραμματιστικά και προσθέστε ένα κουμπί εντολής
url: /el/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής DOCX προγραμματιστικά και προσθήκη κουμπιού εντολής

Αν χρειάζεστε **να δημιουργήσετε μια κενή DOCX προγραμματιστικά**, αυτό το tutorial σας δείχνει πώς να ενσωματώσετε ένα κουμπί εντολής απευθείας στο αρχείο. Θα λάβετε τον πλήρη *create word document code* που αποθηκεύει ένα έγγραφο Word με κουμπί, σας επιτρέπει να **ορίσετε τη λεζάντα του κουμπιού εντολής**, και λειτουργεί με τη νεότερη βιβλιοθήκη Aspose.Words for Java.

Η ενσωμάτωση διαδραστικών ελέγχων σε ένα αρχείο DOCX είναι χρήσιμη όταν θέλετε να διανείμετε πρότυπα που ενεργοποιούν μακροεντολές, εκκινούν εξωτερικά προγράμματα ή απλώς καθοδηγούν τους χρήστες με ένα κλικ «Click Me». Τα παρακάτω βήματα καλύπτουν τα πάντα, από την αρχικοποίηση ενός κενού εγγράφου μέχρι τη διατήρηση του τελικού αρχείου στο δίσκο.

## Προαπαιτούμενα

* Java 17 ή νεότερο εγκατεστημένο.
* Maven (ή το προτιμώμενο εργαλείο κατασκευής) για διαχείριση εξαρτήσεων.
* Aspose.Words for Java 23.9 ή νεότερο. Προσθέστε την εξάρτηση στο `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Ένα IDE όπως IntelliJ IDEA ή VS Code (οποιοσδήποτε επεξεργαστής που υποστηρίζει Java λειτουργεί).

## Δημιουργία κενής DOCX προγραμματιστικά – βήμα‑βήμα

Οι παρακάτω ενότητες χωρίζουν τη διαδικασία σε σαφή, αριθμημένα βήματα. Κάθε βήμα εξηγεί **γιατί** είναι απαραίτητο, όχι μόνο **τι** πρέπει να πληκτρολογήσετε.

### Βήμα 1: Αρχικοποίηση νέου κενού εγγράφου

Ένα κενό έγγραφο είναι ο καμβάς στον οποίο θα τοποθετήσετε το κουμπί εντολής. Η Aspose.Words παρέχει την κλάση `Document` για αυτόν τον σκοπό.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Γιατί είναι σημαντικό*: Ξεκινώντας με ένα κενό `Document` εξασφαλίζετε ότι δεν υπάρχουν κρυφές μορφοποιήσεις ή υπάρχοντες έλεγχοι που να παρεμβαίνουν στο κουμπί που θα προσθέσετε αργότερα.

### Βήμα 2: Ρύθμιση ενός `DocumentBuilder`

`DocumentBuilder` είναι ένας βοηθός που σας επιτρέπει να εισάγετε περιεχόμενο, συμπεριλαμβανομένων ελέγχων OLE, χωρίς να ασχοληθείτε με χαμηλού επιπέδου χειρισμό κόμβων.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί είναι σημαντικό*: Ο builder διατηρεί τη θέση του τρέχοντος κέρσορα, έτσι το κουμπί θα τοποθετηθεί ακριβώς εκεί που το ορίζετε.

### Βήμα 3: Εισαγωγή κουμπιού εντολής OLE

Το Word αντιμετωπίζει τους διαδραστικούς ελέγχους ως αντικείμενα OLE (Object Linking and Embedding). Η Aspose.Words εκθέτει το `Forms2OleControl` για αυτό.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Γιατί είναι σημαντικό*: Η εισαγωγή του ελέγχου δημιουργεί έναν χώρο κράτησης που μπορείτε αργότερα να διαμορφώσετε (τύπο, λεζάντα, θέση).

### Βήμα 4: Διαμόρφωση του κουμπιού – τύπος, λεζάντα και θέση

Πρέπει να ορίσετε τον τύπο του ελέγχου (`COMMANDBUTTON`), να θέσετε μια λεζάντα ορατή στον χρήστη και να το τοποθετήσετε στη σελίδα.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Γιατί είναι σημαντικό*:  
* **Type** λέει στο Word ότι ο έλεγχος λειτουργεί ως κλικable κουμπί.  
* **Caption** είναι το κείμενο που βλέπει ο χρήστης· η αλλαγή του είναι ο τρόπος με τον οποίο **set command button caption**.  
* **Left** και **Top** ελέγχουν την ακριβή τοποθέτηση, κάτι που είναι ουσιώδες όταν **add command button word** έγγραφα που απαιτούν ακριβή διάταξη.

### Βήμα 5: Αποθήκευση του εγγράφου με το ενσωματωμένο κουμπί

Τέλος, γράψτε το αρχείο στο δίσκο. Το προκύπτον αρχείο μπορεί να ανοιχθεί στο Microsoft Word, όπου το κουμπί θα είναι πλήρως λειτουργικό.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Γιατί είναι σημαντικό*: Αυτό το βήμα **saves Word with button** ώστε ο έλεγχος να παραμένει σε διαφορετικούς υπολογιστές. Το αρχείο μπορεί να διανεμηθεί ως πρότυπο ή να χρησιμοποιηθεί σε αυτοματοποιημένες αλυσίδες δημιουργίας αναφορών.

## Πλήρες λειτουργικό παράδειγμα

Αντιγράψτε ολόκληρη την κλάση παρακάτω σε ένα αρχείο με όνομα `CommandButtonDemo.java`, προσαρμόστε το `YOUR_DIRECTORY` σε πραγματική διαδρομή και εκτελέστε το με `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `CommandButton.docx` στο Microsoft Word:

* Το έγγραφο είναι εντελώς κενό εκτός από ένα κουμπί με την ετικέτα **Click Me**.
* Κάνοντας κλικ στο κουμπί θα εμφανιστεί η προεπιλεγμένη συμπεριφορά του Word (δεν κάνει τίποτα εκτός αν συνδεθεί μια μακροεντολή), επιβεβαιώνοντας ότι ο έλεγχος OLE ενσωματώθηκε σωστά.

## Συχνές ερωτήσεις & ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Can I change the button size?** | Ναι. Χρησιμοποιήστε `commandButton.setWidth(double)` και `commandButton.setHeight(double)` για να προσαρμόσετε τις διαστάσεις σε points. |
| **What if I need a macro attached to the button?** | Το κουμπί είναι απλώς ένας έλεγχος OLE. Πρέπει να προσθέσετε μια μακροεντολή VBA στο έγγραφο χειροκίνητα ή μέσω των βοηθητικών λειτουργιών `addMacro` του API `Document` της Aspose.Words. |
| **Will the button work in LibreOffice?** | Το LibreOffice υποστηρίζει περιορισμένους ελέγχους OLE. Το κουμπί εμφανίζεται, αλλά η συμπεριφορά του κλικ μπορεί να διαφέρει. |
| **How to add multiple buttons?** | Επαναλάβετε τα Βήματα 3‑4 με ένα νέο αντικείμενο `Forms2OleControl`. Προσαρμόστε `setLeft`/`setTop` για κάθε κουμπί ώστε να μην επικαλύπτονται. |
| **Is the code compatible with .NET?** | Η ίδια λογική ισχύει, αλλά θα χρησιμοποιούσατε τις κλάσεις του `Aspose.Words` για .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Συμβουλές από την πράξη

* **Pro tip:** Χρησιμοποιήστε `builder.moveToDocumentEnd()` πριν την εισαγωγή του κουμπιού εάν θέλετε να βρίσκεται στο πολύ τέλος του εγγράφου, ανεξάρτητα από το προηγούμενο περιεχόμενο.
* **Watch out for:** Πολύ μικρές τιμές `Left`/`Top` μπορούν να τοποθετήσουν το κουμπί εκτός της εκτυπώσιμης περιοχής, καθιστώντας το αόρατο στην προβολή διάταξης του Word.
* **Performance note:** Η εισαγωγή πολλών ελέγχων OLE μπορεί να αυξήσει το μέγεθος του αρχείου. Εάν χρειάζεστε μόνο οπτική ένδειξη, σκεφτείτε να χρησιμοποιήσετε ένα απλό `Shape` με υπερσύνδεσμο.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε μια κενή DOCX προγραμματιστικά** και να ενσωματώσετε ένα πλήρως λειτουργικό κουμπί εντολής χρησιμοποιώντας Java. Το tutorial κάλυψε όλη τη ροή εργασίας *create word document code*, έδειξε πώς να **save Word with button**, παρουσίασε τον σωστό τρόπο για **add command button word** στοιχεία και εξήγησε πώς να **set command button caption**.

Από εδώ μπορείτε:

* Να προσθέσετε περισσότερους ελέγχους OLE (checkboxes, combo boxes) για πιο πλούσιες φόρμες.
* Να συνδέσετε μακροεντολές VBA ώστε το κουμπί να εκτελεί προσαρμοσμένες ενέργειες.
* Να συνδυάσετε αυτήν την τεχνική με συγχώνευση εγγράφων (mail‑merge) για δυναμικά, διαδραστικά πρότυπα.

Μη διστάσετε να πειραματιστείτε με στυλ κουμπιών, θέσεις και επιπλέον ελέγχους ώστε να ταιριάζουν στις συγκεκριμένες επιχειρηματικές σας απαιτήσεις. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create blank word document with a command button – step‑by‑step guide](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Create Blank Word Document with Java – Full Aspose.Words Guide](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}