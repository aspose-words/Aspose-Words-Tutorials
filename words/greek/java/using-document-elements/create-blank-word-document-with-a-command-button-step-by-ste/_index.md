---
category: general
date: 2026-08-04
description: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε κουμπί εντολής χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να ορίσετε το μέγεθος του κουμπιού και να προσθέσετε
  ένα κλικ-δυνατό κουμπί σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: el
lastmod: 2026-08-04
og_description: Δημιουργήστε ένα κενό έγγραφο Word με το Aspose.Words και εισάγετε
  ένα κουμπί εντολής. Αυτός ο οδηγός δείχνει πώς να ορίσετε το μέγεθος του κουμπιού,
  να προσθέσετε ένα κλικαρίσιμο κουμπί και να αποθηκεύσετε το αρχείο.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Δημιουργήστε κενό έγγραφο Word και προσθέστε ένα κουμπί εντολής – πλήρες
  σεμινάριο C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργία κενού εγγράφου Word με κουμπί εντολής – βήμα‑βήμα οδηγός
url: /el/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word με κουμπί εντολής – οδηγός βήμα‑βήμα

Αν χρειάζεστε **create blank word document** που περιέχει ένα διαδραστικό κουμπί, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Θα μάθετε να **insert command button**, να προσαρμόσετε την εμφάνισή του και να το κάνετε κλικ‑αξιό—όλα σε λίγες γραμμές C#.

Ο οδηγός καλύπτει τα πάντα, από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε τη πλήρη λύση στην εφαρμογή σας. Στο δρόμο θα εξηγήσουμε επίσης πώς να **add clickable button**, **set button size**, και **create command button** προγραμματιστικά.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη.
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET).
* Πακέτο NuGet Aspose.Words for .NET (`Aspose.Words` έκδοση 23.12 ή νεότερη).
* Βασική εξοικείωση με C# και αντικειμενοστραφή προγραμματισμό.

Δεν απαιτούνται πρόσθετα assemblies Office interop, επειδή το Aspose.Words λειτουργεί εντελώς ανεξάρτητα από το Microsoft Word.

## Βήμα 1: Ρύθμιση του έργου .NET

Δημιουργήστε μια εφαρμογή κονσόλας που θα φιλοξενήσει τον κώδικα αυτοματοποίησης του Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Αυτή η εντολή δημιουργεί ένα νέο φάκελο `WordButtonDemo` με ένα έτοιμο‑για‑εκτέλεση `Program.cs` και προσθέτει τη βιβλιοθήκη Aspose.Words.

## Βήμα 2: Δημιουργία κενής εγγράφου Word

Η πρώτη ενέργεια είναι η **create blank word document**. Το Aspose.Words παρέχει μια κλάση `Document` που αντιπροσωπεύει ένα κενό αρχείο Word αμέσως.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Η δημιουργία ενός κεννού εγγράφου σας δίνει έναν καθαρό καμβά στον οποίο μπορείτε να προσθέσετε παραγράφους, πίνακες ή, σε αυτήν την περίπτωση, ένα κουμπί εντολής OLE.

## Βήμα 3: Αρχικοποίηση του DocumentBuilder

`DocumentBuilder` είναι ο βοηθός που σας επιτρέπει να εισάγετε περιεχόμενο στο έγγραφο. Πρέπει να το συνδέσετε με το έγγραφο που μόλις δημιουργήσατε.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder διατηρεί τη τρέχουσα θέση του δρομέα, έτσι οποιαδήποτε επακόλουθη εισαγωγή γίνεται ακριβώς εκεί που το θέλετε.

## Βήμα 4: Εισαγωγή κουμπιού εντολής

Τώρα **insert command button** (ένα OLE `Forms2OleControl`) στο έγγραφο. Η μέθοδος `InsertForms2OleControl` απαιτεί τρία ορίσματα:

1. Το ProgID του ελέγχου OLE – `"CommandButton"` για ένα τυπικό κουμπί.  
2. `Rectangle` που ορίζει το **set button size** και τη θέση.  
3. Τον τίτλο που εμφανίζεται στο κουμπί.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Όταν το έγγραφο ανοίξει στο Word, το κουμπί συμπεριφέρεται όπως οποιοδήποτε ενσωματωμένο στοιχείο φόρμας—μπορείτε να το κάνετε κλικ και το Word θα εκτελέσει το σχετικό μακροεντολή (αν υπάρχει). Αυτό ικανοποιεί την απαίτηση **add clickable button**.

### Γιατί να χρησιμοποιήσετε το Forms2OleControl;

`Forms2OleControl` ενσωματώνει ένα αντικείμενο OLE απευθείας στο αρχείο DOCX, διατηρώντας τις ιδιότητες του ελέγχου χωρίς την ανάγκη του assembly Word Interop. Είναι ο πιο αξιόπιστος τρόπος για **create command button** που λειτουργεί σε όλες τις εκδόσεις του Word.

## Βήμα 5: Προσαρμογή του κουμπιού (προαιρετικό)

Μπορεί να θέλετε να **set button size** πιο ακριβώς ή να αλλάξετε πρόσθετες ιδιότητες όπως η γραμματοσειρά ή το χρώμα φόντου. Το Aspose.Words εκθέτει το υποκείμενο αντικείμενο OLE, επιτρέποντας περαιτέρω ρυθμίσεις.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Αν χρειάζεστε διαφορετικό μέγεθος, απλώς προσαρμόστε τις τιμές του `Rectangle` στο Βήμα 4. Οι συντεταγμένες μετρώνται σε σημεία (1 pt = 1/72 inch), έτσι το `120` αντιστοιχεί περίπου σε 1,67 ίντσες πλάτος.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Το παραγόμενο αρχείο περιέχει ένα **blank word document** με πλήρως λειτουργικό κουμπί εντολής.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Όταν ανοίξετε το `CommandButtonDemo.docx` στο Microsoft Word, θα δείτε ένα κουμπί με την ετικέτα “Click Me”. Κάνοντας κλικ στο κουμπί θα εμφανιστεί το προεπιλεγμένο παράθυρο διαλόγου μακροεντολής, εκτός αν προσθέσετε μια προσαρμοσμένη μακροεντολή.

## Πλήρης πηγαίος κώδικας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε στο `Program.cs`. Περιλαμβάνει όλα τα παραπάνω βήματα και μεταγλωττίζεται χωρίς τροποποιήσεις.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος παράγει το `CommandButtonDemo.docx`. Το άνοιγμα του αρχείου στο Word εμφανίζει:

* Μία σελίδα που περιέχει ένα κουμπί με την ετικέτα **Click Me**.  
* Το κουμπί τηρεί το **set button size** (120 × 30 σημεία).  
* Κάνοντας κλικ στο κουμπί ενεργοποιείται η προεπιλεγμένη συμπεριφορά του κουμπιού εντολής του Word, επιβεβαιώνοντας ότι η λειτουργία **add clickable button** ολοκληρώθηκε επιτυχώς.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Λειτουργεί αυτό με αρχεία .doc;** | Ναι. Αλλάξτε την επέκταση αρχείου στο `doc.Save("file.doc")`. Ο έλεγχος OLE αποθηκεύεται επίσης στη παλαιότερη δυαδική μορφή. |
| **Τι γίνεται αν χρειάζομαι πολλαπλά κουμπιά;** | Καλέστε το `InsertForms2OleControl` επανειλημμένα, προσαρμόζοντας το `Rectangle` για κάθε νέο κουμπί ώστε να αποφεύγεται η επικάλυψη. |
| **Μπορώ να προσθέσω μακροεντολή στο κουμπί;** | Το κουμπί από μόνο του δεν περιέχει κώδικα μακροεντολής. Πρέπει να προσθέσετε μια VBA μακροεντολή στο έγγραφο χειροκίνητα ή μέσω της συλλογής `Modules` του αντικειμένου `Document`. |
| **Εμφανίζεται το κουμπί στην εξαγωγή PDF;** | Όταν εξάγετε το DOCX σε PDF χρησιμοποιώντας το Aspose.Words, το κουμπί αποδίδεται ως στατική εικόνα, όχι ως διαδραστικό στοιχείο. |
| **Ποιες εκδόσεις του Word υποστηρίζονται;** | Το κουμπί εντολής OLE λειτουργεί σε Word 2007 και μεταγενέστερες, καθώς ακολουθεί το πρότυπο Forms2.0. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **create blank word document**, **insert command button**, **add clickable button**, και **set button size** χρησιμοποιώντας το Aspose.Words for .NET. Το πλήρες παράδειγμα δείχνει τη ροή **create command button** από την αρχή μέχρι το τέλος, παρέχοντάς σας μια σταθερή βάση για πιο προχωρημένες εργασίες αυτοματοποίησης του Word.

## Επόμενα βήματα

* Εξερευνήστε άλλα στοιχεία OLE (π.χ., `CheckBox`, `ListBox`) αλλάζοντας το ProgID στο `InsertForms2OleControl`.  
* Συνδυάστε το κουμπί με μια μακροεντολή VBA για να εκτελεί προσαρμοσμένες ενέργειες όταν ο χρήστης κάνει κλικ.  
* Χρησιμοποιήστε το `DocumentBuilder` του Aspose.Words για να προσθέσετε επιπλέον περιεχόμενο όπως πίνακες, εικόνες ή υποσημειώσεις πριν την εισαγωγή του κουμπιού.  
* Πειραματιστείτε με τιμές **set button size** ώστε να ταιριάζουν στις απαιτήσεις διάταξης του εγγράφου σας.

Καλή προγραμματιστική δουλειά, και απολαύστε τη δημιουργία πιο πλούσιων εγγράφων Word με διαδραστικά στοιχεία!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Δημιουργία ομάδας σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία κενής εγγράφου Word με σχήμα ορθογωνίου με σκιά – οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Δημιουργία εγγράφου Word με Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}