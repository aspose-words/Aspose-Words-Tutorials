---
category: general
date: 2026-10-07
description: Μάθετε πώς να προσθέσετε έλεγχο περιεχομένου σε ένα έγγραφο Word με το
  Aspose.Words. Αυτός ο οδηγός εξηγεί επίσης πώς να δημιουργήσετε έλεγχο περιεχομένου
  για το πεδίο ταυτότητας υπαλλήλου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: el
lastmod: 2026-10-07
og_description: Προσθέστε έλεγχο περιεχομένου σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words. Ακολουθήστε αυτό το πλήρες σεμινάριο για να μάθετε πώς να δημιουργήσετε
  έλεγχο περιεχομένου και να προσθέσετε ένα πεδίο ταυτότητας υπαλλήλου.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Προσθήκη ελέγχου περιεχομένου στο Word με το Aspose.Words – οδηγός βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Πώς να προσθέσετε έλεγχο περιεχομένου σε ένα έγγραφο Word χρησιμοποιώντας το
  Aspose.Words
url: /el/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε content control word σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε **add content control word** σε ένα αρχείο Word, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με τη βιβλιοθήκη Aspose.Words for .NET. Είτε δημιουργείτε ένα έγγραφο τύπου φόρμας είτε αυτοματοποιείτε την εισαγωγή δεδομένων, θα μάθετε **how to create content control** που καταγράφει το ID ενός υπαλλήλου σε ένα μόνο βήμα.

Σε αυτόν τον οδηγό θα:
* Δημιουργήσετε ένα κενό έγγραφο Word προγραμματιστικά.  
* Εισάγετε ένα plain‑text Structured Document Tag (SDT) που λειτουργεί ως content control.  
* Συμπληρώσετε το control με ένα employee ID και αποθηκεύσετε το αρχείο.  

Οι μόνοι προαπαιτούμενοι είναι μια πρόσφατη έκδοση του .NET (συνιστάται 4.6+) και μια άδεια Aspose.Words (ή η δωρεάν δοκιμή). Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από `Aspose.Words`.

## Προσθήκη content control word με Aspose.Words

Το πρώτο σημαντικό βήμα είναι η δημιουργία του content control. Στο Aspose.Words ένα **content control** αντιπροσωπεύεται από την κλάση `StructuredDocumentTag`. Προσθέτοντας ένα SDT στο έγγραφο, ουσιαστικά **adding content control word** που μπορεί να επεξεργαστεί αργότερα στο Microsoft Word ή να υποβληθεί σε επεξεργασία προγραμματιστικά.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: `DocumentBuilder` σας παρέχει μια διεπαφή τύπου cursor που σας επιτρέπει να εισάγετε κόμβους (παράγραφοι, πίνακες, SDTs κ.λπ.) στην τρέχουσα θέση. Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζει ότι το content control εμφανίζεται ακριβώς όπου το θέλετε.

## Πώς να δημιουργήσετε content control για πεδίο employee ID

Στη συνέχεια, διαμορφώστε το SDT ώστε να λειτουργεί ως plain‑text content control που θα κρατά το employee identifier. Η ιδιότητα `Title` είναι αυτή που εμφανίζει το Word στο παράθυρο **Properties**, ενώ το `PlaceholderName` παρέχει μια υπόδειξη στον χρήστη.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Γιατί είναι σημαντικό*: Ορίζοντας το `Title` σε **EmployeeID** κάνει το control αυτοπεριγραφικό, κάτι που είναι χρήσιμο όταν αργότερα εξάγετε τιμές με `StructuredDocumentTag.GetText()`. Η placeholder βελτιώνει την εμπειρία του τελικού χρήστη υποδεικνύοντας τη ζητούμενη μορφή.

### Προσθήκη πεδίου employee id μέσα στο content control

Τώρα εισάγετε το SDT στο έγγραφο στην τρέχουσα θέση του builder και γράψτε τον προεπιλεγμένο αριθμό υπαλλήλου.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Γιατί είναι σημαντικό*: `InsertNode` τοποθετεί το SDT στο δέντρο του εγγράφου. Το επακόλουθο `Writeln` γράφει περιεχόμενο **inside** το control επειδή ο cursor του builder είναι ακόμα μέσα στον κόμβο SDT. Αν είχατε καλέσει `Writeln` πριν την εισαγωγή του SDT, το κείμενο θα εμφανιζόταν έξω από το control.

## Αποθήκευση του εγγράφου και επαλήθευση του content control

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Το αποθηκευμένο αρχείο `.docx` θα περιέχει το content control που μπορείτε να ανοίξετε στο Microsoft Word για να δείτε το placeholder και το προεπιλεγμένο employee ID.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Γιατί είναι σημαντικό*: Η χρήση απόλυτης ή σχετικής διαδρομής σας επιτρέπει να ελέγχετε πού αποθηκεύεται το αρχείο. Το Aspose.Words γράφει αυτόματα τα απαραίτητα XML μέρη για το content control, οπότε δεν απαιτούνται επιπλέον βήματα.

### Γρήγορα βήματα επαλήθευσης

1. Ανοίξτε το `EmployeeForm.docx` στο Word.  
2. Κάντε κλικ στο γκρι πλαίσιο που γράφει **Enter ID** – θα πρέπει να αντικατασταθεί από **12345**.  
3. Ανοίξτε την καρτέλα **Developer** → **Design Mode** για να δείτε τις ιδιότητες του control (Title = *EmployeeID*).

Αν το control δεν εμφανιστεί, ελέγξτε ξανά ότι χρησιμοποιείτε Aspose.Words ≥ 23.10· οι προηγούμενες εκδόσεις είχαν διαφορετική υπογραφή κατασκευής για το `StructuredDocumentTag`.

## Προαιρετικές παραλλαγές και ειδικές περιπτώσεις

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Use a rich‑text control** αντί για plain‑text | Change `SdtType.PlainText` to `SdtType.RichText`. |
| **Add the control to an existing document** | Load the file with `new Document("Existing.docx")` and place the builder at the desired bookmark before inserting the SDT. |
| **Lock the content control so users cannot edit the value** | Set `sdt.LockContentControl = true;` after creating the SDT. |
| **Apply a custom tag for later extraction** | Use `sdt.Tag = "EmpIdTag";` and later retrieve it with `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Set a repeating content control (multiple IDs)** | Create the SDT inside a table row and duplicate the row as needed. |

**Pro tip**: Πάντα απελευθερώνετε το αντικείμενο `Document` (ή τυλίξτε το σε ένα μπλοκ `using`) όταν εργάζεστε σε μια υπηρεσία μακράς διάρκειας ώστε να ελευθερώνονται άμεσα οι εγγενείς πόροι.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **add content control word** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words, πώς να **how to create content control** που καταγράφει ένα employee identifier, και πώς να **add employee id field** προγραμματιστικά. Ακολουθώντας τα παραπάνω βήματα μπορείτε να ενσωματώσετε δομημένα, επεξεργάσιμα πεδία σε οποιοδήποτε παραγόμενο έγγραφο, καθιστώντας εύκολο το συλλέγοντας ή εμφανίζοντας δεδομένα σε συνεπή μορφή.

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **binding content controls to XML data**, **creating repeating content controls for tables**, ή **using the Aspose.Words API to extract values from filled‑in controls**. Αυτές οι επεκτάσεις σας επιτρέπουν να δημιουργήσετε πλήρως εξοπλισμένες, δεδομενο‑οδηγούμενες φόρμες Word χωρίς ποτέ να ανοίξετε το αρχείο χειροκίνητα. Καλή προγραμματιστική!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}