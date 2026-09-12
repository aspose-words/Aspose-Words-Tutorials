---
category: general
date: 2026-09-11
description: Μάθετε πώς να δημιουργείτε forms2olecontrol με κώδικα χρησιμοποιώντας
  το Aspose.Words DocumentBuilder. Αυτός ο οδηγός βήμα‑βήμα καλύπτει την εισαγωγή
  κουμπιού εντολής ActiveX, τη χρήση του setOleClassName και το μέγεθος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: el
lastmod: 2026-09-11
og_description: Δημιουργήστε το forms2olecontrol με κώδικα χρησιμοποιώντας το Aspose.Words.
  Ακολουθήστε αυτόν τον οδηγό για να εισάγετε ένα κουμπί εντολής ActiveX, να ορίσετε
  το όνομα της κλάσης του και να προσαρμόσετε το μέγεθός του.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Δημιουργία forms2olecontrol σε κώδικα – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Πώς να δημιουργήσετε το forms2olecontrol σε κώδικα με το Aspose.Words
url: /el/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε forms2olecontrol σε κώδικα με το Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε forms2olecontrol σε κώδικα**, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε χρησιμοποιώντας το Aspose.Words .NET API. Είτε αυτοματοποιείτε ένα πρότυπο που απαιτεί ένα κουμπί εντολών ActiveX είτε απλώς θέλετε να εμπλουτίσετε ένα έγγραφο Word προγραμματιστικά, τα παρακάτω βήματα καλύπτουν τα πάντα, από την εισαγωγή του ελέγχου μέχρι τη διαμόρφωση της εμφάνισής του.

Σε αυτό το tutorial θα μάθετε πώς να χρησιμοποιείτε το **Aspose.Words DocumentBuilder** για να εισάγετε ένα **ActiveX command button**, να ορίσετε την κλάση του με τη **setOleClassName method**, και να προσαρμόσετε το **Forms2OleControl size**. Δεν απαιτούνται εξωτερικά εργαλεία — μόνο ένα περιβάλλον ανάπτυξης .NET και η βιβλιοθήκη Aspose.Words.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Μια πρόσφατη έκδοση του πακέτου Aspose.Words for .NET NuGet
* Βασική εξοικείωση με τη C# και την έννοια των ελέγχων ActiveX σε έγγραφα Word

Αν λείπει κάποιο από τα παραπάνω, εγκαταστήστε το πακέτο NuGet με:

```bash
dotnet add package Aspose.Words
```

## Τι καλύπτει αυτό το tutorial

* Δημιουργία ενός αντικειμένου `DocumentBuilder`
* Εισαγωγή ενός `Forms2OleControl` (το υποκείμενο αντικείμενο για ένα κουμπί εντολών ActiveX)
* Ανάθεση του σωστού ονόματος κλάσης με `setOleClassName`
* Ορισμός του οπτικού πλάτους και ύψους χρησιμοποιώντας τις ιδιότητες **Forms2OleControl size**
* Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Στο τέλος του οδηγού θα έχετε ένα πλήρως λειτουργικό αρχείο Word που περιέχει ένα κλικ-μεγέθους κουμπί, το οποίο μπορείτε να προσαρμόσετε περαιτέρω ή να συνδέσετε με μακροεντολές VBA.

---

## Πώς να δημιουργήσετε forms2olecontrol σε κώδικα – βήμα‑βήμα

### Βήμα 1: Αρχικοποίηση του DocumentBuilder

Η κλάση `DocumentBuilder` είναι το σημείο εισόδου για τις περισσότερες εργασίες δημιουργίας εγγράφων στο Aspose.Words. Σας παρέχει μεθόδους για προσθήκη κειμένου, εικόνων, πινάκων και, σημαντικά για αυτό το tutorial, ελέγχων OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:**  
`DocumentBuilder` διατηρεί τη τρέχουσα θέση του δρομέα μέσα στο έγγραφο. Δημιουργώντας το νωρίς, εξασφαλίζετε ότι οποιαδήποτε επόμενη εισαγωγή — όπως το **ActiveX command button** — θα εμφανιστεί ακριβώς εκεί που το θέλετε.

### Βήμα 2: Εισαγωγή του Forms2OleControl

Η μέθοδος `insertForms2OleControl` επιστρέφει ένα αντικείμενο `Forms2OleControl`. Αυτό το αντικείμενο αντιπροσωπεύει το placeholder του ελέγχου OLE που το Word θα αποδώσει ως κουμπί ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Γιατί είναι σημαντικό:**  
Χωρίς αυτήν την κλήση δεν μπορείτε να χειριστείτε τις ιδιότητες του ελέγχου. Το επιστρεφόμενο `Forms2OleControl` σας δίνει πλήρη πρόσβαση στη **setOleClassName method**, στα χαρακτηριστικά μεγέθους και σε άλλες ρυθμίσεις ειδικές για OLE.

### Βήμα 3: Καθορισμός της κλάσης ActiveX με setOleClassName

Το Word πρέπει να γνωρίζει ποιος τύπος ελέγχου ActiveX θα αποδείξει. Το όνομα κλάσης για ένα τυπικό κουμπί εντολών είναι `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Γιατί είναι σημαντικό:**  
Η μέθοδος `setOleClassName` είναι η γέφυρα μεταξύ του γενικού placeholder OLE και του συγκεκριμένου **ActiveX command button**. Η χρήση λανθασμένου ονόματος κλάσης οδηγεί σε κενό αντικείμενο ή σφάλμα χρόνου εκτέλεσης όταν ανοίγει το έγγραφο.

### Βήμα 4: Προσαρμογή του μεγέθους Forms2OleControl

Ένα κουμπί που είναι πολύ μικρό ή πολύ μεγάλο φαίνεται ακατάλληλο. Μπορείτε να ελέγξετε τις διαστάσεις του με `setWidth` και `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Γιατί είναι σημαντικό:**  
Αυτές οι ιδιότητες αποτελούν το **Forms2OleControl size**. Επηρεάζουν την εμφάνιση του κουμπιού στη διεπαφή του Word και διασφαλίζουν ότι οποιαδήποτε συνδεδεμένη μακροεντολή έχει επαρκή εμβέλεια κλικ.

### Βήμα 5: Αποθήκευση του εγγράφου και δοκιμή

Μετά τη διαμόρφωση του ελέγχου, αποθηκεύστε το έγγραφο στην τοποθεσία της επιλογής σας.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Ανοίξτε το `ActiveXButton.docx` στο Microsoft Word. Θα πρέπει να δείτε ένα κουμπί με την ετικέτα “CommandButton1” (η προεπιλεγμένη λεζάντα). Το κλικ δεν θα κάνει τίποτα εκτός αν προσθέσετε μια μακροεντολή VBA, αλλά ο έλεγχος από μόνος του είναι πλήρως λειτουργικός.

**Αναμενόμενο αποτέλεσμα:**  

![Έγγραφο Word με ένα εισαχθέν κουμπί ActiveX](/images/activeX-button.png "Screenshot of a Word document showing a newly created ActiveX command button")

*Το κείμενο alt της εικόνας περιέχει τη βασική λέξη-κλειδί για προσβασιμότητα και SEO.*

---

## Κατανόηση της κλάσης ActiveX Forms2OleControl

Η κλάση `Forms2OleControl` τυλίγει την υποδομή OLE χαμηλού επιπέδου που χρησιμοποιεί το Word για στοιχεία ActiveX. Κληρονομεί από την `Shape`, πράγμα που σημαίνει ότι μπορείτε επίσης να εφαρμόσετε τυπική μορφοποίηση σχήματος (π.χ., περιγράμματα, περιστροφή) αν χρειαστεί.

* **ActiveX command button** – Η πιο κοινή περίπτωση χρήσης· μπορείτε να το συνδέσετε με μια μακροεντολή μέσω των εργαλείων προγραμματιστή του Word.
* **setOleClassName method** – Καθορίζει ποια κλάση COM θα φορτώσει το Word· άλλες έγκυρες τιμές περιλαμβάνουν `"Forms.TextBox.1"` και `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Ελέγχεται μέσω `SetWidth`/`SetHeight`. Αυτές οι μέθοδοι δέχονται μονάδες points (1 pt = 1/72 in).

### Πότε να χρησιμοποιήσετε Forms2OleControl vs. Content Controls

Αν χρειάζεστε μόνο απλή εισαγωγή δεδομένων (π.χ., ένα απλό πεδίο κειμένου), τα ενσωματωμένα content controls του Word είναι ελαφρύτερα. Χρησιμοποιήστε `Forms2OleControl` όταν απαιτείται πλήρης λειτουργικότητα ActiveX, όπως διαχείριση συμβάντων ή προσαρμοσμένη αλληλεπίδραση VBA.

---

## Ορισμός πρόσθετων ιδιοτήτων (προαιρετικό)

Αν και τα βασικά βήματα αρκούν για **να δημιουργήσετε forms2olecontrol σε κώδικα**, συχνά θέλετε να βελτιώσετε την εμφάνιση ή τη συμπεριφορά του κουμπιού.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Γιατί είναι σημαντικό:**  
`SetOleData` σας επιτρέπει να γράψετε αυθαίρετες τιμές ιδιοτήτων απευθείας στο ρεύμα OLE. Αυτή είναι η πιο ευέλικτη μέθοδος για προσαρμογή ενός **ActiveX command button** χωρίς να χρειάζεται VBA.

---

## Συχνά προβλήματα και αντιμετώπιση

| Συμπτωμα | Πιθανή αιτία | Διόρθωση |
|----------|--------------|----------|
| Το κουμπί εμφανίζεται ως γκρι πλαίσιο | Λανθασμένο όνομα κλάσης που περάστηκε στη `setOleClassName` | Επαληθεύστε ότι η συμβολοσειρά είναι ακριβώς `"Forms.CommandButton.1"` (διάκριση πεζών‑κεφαλαίων) |
| Το μέγεθος δεν αλλάζει | Το πλάτος/ύψος ορίστηκε πριν από την εισαγωγή του ελέγχου | Πάντα καλέστε `SetWidth`/`SetHeight` **μετά** το `InsertForms2OleControl` |
| Το έγγραφο εμφανίζει σφάλμα “OLE object not found” κατά το άνοιγμα | Λείπει η άδεια Aspose.Words (η έκδοση evaluation μπορεί να περιορίζει το OLE) | Εφαρμόστε έγκυρη άδεια ή χρησιμοποιήστε τη δωρεάν δοκιμή με πλήρη υποστήριξη OLE |
| Η λεζάντα του κουμπιού παραμένει “CommandButton1” | Δεν χρησιμοποιήθηκε `SetOleData` ή η μακροεντολή δεν διαβάζει την ιδιότητα | Χρησιμοποιήστε μια μακροεντολή VBA για να διαβάσετε την ιδιότητα `"Caption"` ή ορίστε τη λεζάντα μέσω του UI του Word |

---

## Πλήρες, εκτελέσιμο παράδειγμα

Ακολουθεί μια πλήρης εφαρμογή κονσόλας που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε. Δείχνει όλα όσα καλύφθηκαν σε αυτό το tutorial.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Επεξήγηση κάθε τμήματος**

* **Using directives** – Εισάγει το namespace Aspose.Words που απαιτείται για `Document`, `DocumentBuilder` και `Forms2OleControl`.
* **Document creation** – Δημιουργεί ένα κενό αρχείο Word.
* **InsertForms2OleControl** – Τοποθετεί τον έλεγχο OLE στην τρέχουσα θέση του δρομέα του builder.
* **SetOleClassName** – Λέει στο Word ότι ο έλεγχος είναι ένα **ActiveX command button**.
* **SetWidth / SetHeight** – Ρυθμίζει το **Forms2OleControl size** για επαγγελματική εμφάνιση.
* **SetOleData (optional)** – Δείχνει πώς να γράψετε επιπλέον ιδιότητες όπως μια λεζάντα.
* **Save** – Αποθηκεύει το τελικό αρχείο `.docx` στο δίσκο.

Τρέξτε το πρόγραμμα (`dotnet run`) και ανοίξτε το `ActiveXButton.docx`. Θα πρέπει να δείτε ένα κουμπί που μπορείτε αργότερα να συνδέσετε με μια μακροεντολή.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε forms2olecontrol σε κώδικα** χρησιμοποιώντας το Aspose.Words, από την αρχικοποίηση του `DocumentBuilder` μέχρι τη διαμόρφωση του **ActiveX command button** με `setOleClassName` και τον έλεγχο του **Forms2OleControl size**. Αυτή η προσέγγιση σας επιτρέπει να αυτοματοποιήσετε σύνθετα έγγραφα Word, να ενσωματώσετε διαδραστικά στοιχεία UI και να διατηρήσετε όλη τη λογική μέσα

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words για Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία σχήματος ορθογωνίου σε Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}