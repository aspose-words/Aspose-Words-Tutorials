---
category: general
date: 2026-09-21
description: Δημιουργήστε έγγραφο Word προγραμματιστικά και μάθετε πώς να αποθηκεύσετε
  το κουμπί αποθήκευσης εγγράφου Word, να εισάγετε το κουμπί εντολής Word και να ορίσετε
  τη λεζάντα του κουμπιού εντολής χρησιμοποιώντας το DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words. Μάθετε
  πώς να αποθηκεύετε το έγγραφο Word με κουμπί, να εισάγετε κουμπί εντολής, να ορίζετε
  τη λεζάντα του κουμπιού εντολής και να χρησιμοποιείτε το DocumentBuilder για διαδραστικές
  φόρμες.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού
url: /el/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά και εισαγωγή κουμπιού

Αν χρειάζεστε να **δημιουργήσετε έγγραφο Word προγραμματιστικά**, το Aspose.Words παρέχει ένα ευέλικτο API που σας επιτρέπει να προσθέτετε διαδραστικούς ελέγχους όπως ένα CommandButton. Αυτό το tutorial εξηγεί επίσης **πώς να χρησιμοποιήσετε το DocumentBuilder**, πώς να **αποθηκεύσετε το κουμπί εγγράφου Word**, και πώς να **ορίσετε την λεζάντα του κουμπιού CommandButton** ώστε το κουμπί να εμφανίζεται ακριβώς όπως αναμένετε μέσα στο αρχείο .docx.

Θα μάθετε πώς να:

* Αρχικοποιήσετε ένα κενό έγγραφο με `Document`.
* Εργαστείτε με το `DocumentBuilder` για να επεξεργαστείτε το έγγραφο.
* Εισάγετε ένα **CommandButton** (`insert command button word`).
* Ορίσετε το όνομα του κουμπιού και την ορατή λεζάντα (`set command button caption`).
* Αποθηκεύσετε το αποτέλεσμα στο δίσκο (`save word document button`).

Τα βήματα είναι γραμμένα για προγραμματιστές .NET που χρησιμοποιούν C# και την πιο πρόσφατη έκδοση του Aspose.Words για .NET (v24.10). Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από το Aspose.Words.

---

## Τι χρειάζεστε πριν ξεκινήσετε

| Προαπαιτούμενο | Λόγος |
|----------------|-------|
| Visual Studio 2022 (ή οποιοδήποτε IDE C#) | Για να μεταγλωττίσετε και να εκτελέσετε το δείγμα κώδικα. |
| .NET 6.0 SDK ή νεότερο | Παρέχει το runtime για το παράδειγμα. |
| Aspose.Words for .NET (v24.10 ή νεότερο) | Η βιβλιοθήκη που σας επιτρέπει να **δημιουργήσετε έγγραφο Word προγραμματιστικά** και να διαχειριστείτε στοιχεία φόρμας. |
| Βασική εξοικείωση με C# και έννοιες OOP | Απαιτείται για την κατανόηση της ροής του κώδικα. |

Μπορείτε να εγκαταστήσετε το Aspose.Words μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Δημιουργία εγγράφου Word προγραμματιστικά

Το πρώτο βήμα είναι η δημιουργία ενός κενό `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Η δημιουργία του εγγράφου προγραμματιστικά σας δίνει έναν καθαρό καμβά στον οποίο μπορείτε να προσθέσετε παραγράφους, πίνακες ή διαδραστικούς ελέγχους.  

---

## Πώς να χρησιμοποιήσετε το DocumentBuilder

`DocumentBuilder` είναι η κύρια κλάση για την επεξεργασία ενός `Document`. Παρέχει μεθόδους για την εισαγωγή κειμένου, εικόνων και πεδίων φόρμας. Σε αυτό το tutorial το χρησιμοποιούμε για να τοποθετήσουμε ένα CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder διατηρεί έναν εσωτερικό κέρσορα που δείχνει στην τρέχουσα θέση εισαγωγής. Από προεπιλογή ξεκινά στην αρχή της πρώτης ενότητας, κάτι που είναι ιδανικό για το παράδειγμά μας.

---

## Εισαγωγή κουμπιού CommandButton στο Word

Το Aspose.Words αντιμετωπίζει ένα CommandButton ως έλεγχο ActiveX. Η μέθοδος `InsertForms2OleControl` δημιουργεί έναν γενικό έλεγχο OLE που στη συνέχεια διαμορφώνουμε ως κουμπί.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

Σε αυτό το σημείο ο έλεγχος υπάρχει στο έγγραφο αλλά δεν έχει οπτική αναπαράσταση μέχρι να ορίσουμε τον τύπο του.

---

## Ορισμός λεζάντας κουμπιού CommandButton

Τώρα λέμε στον έλεγχο OLE ότι πρέπει να συμπεριφέρεται ως CommandButton και του δίνουμε μια φιλική ετικέτα.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Η ρύθμιση της **λεζάντας του κουμπιού CommandButton** είναι απαραίτητη επειδή το Word εμφανίζει αυτό το κείμενο στην επιφάνεια του κουμπιού. Αν παραλείψετε το `SetCaption`, το κουμπί θα εμφανιστεί με μια γενική ετικέτα.

---

## Αποθήκευση εγγράφου Word με κουμπί

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Η μέθοδος `Save` γράφει ολόκληρο το πακέτο Word, συμπεριλαμβανομένου του νεοεισαγμένου κουμπιού, σε ένα αρχείο .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Το αρχείο `CommandButton.docx` τώρα περιέχει ένα πλήρως λειτουργικό κουμπί με την ετικέτα **Submit**. Όταν ο χρήστης ανοίξει το αρχείο στο Microsoft Word και κάνει κλικ στο κουμπί, θα εκτελεστεί η προεπιλεγμένη ενέργεια (που μπορείτε αργότερα να συνδέσετε μέσω VBA).

---

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε. Δείχνει ολόκληρη τη ροή εργασίας από τη δημιουργία του εγγράφου μέχρι την αποθήκευση του κουμπιού.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα**

* Ένα αρχείο με όνομα `CommandButton.docx` στο μονοπάτι που καθορίσατε.
* Ανοίγοντας το αρχείο στο Microsoft Word εμφανίζεται ένα μόνο κουμπί **Submit** στην πρώτη σελίδα.
* Το κουμπί μπορεί να επιλεγεί, να αλλάξει μέγεθος ή να συνδεθεί με μια μακροεντολή από την καρτέλα **Developer** του Word.

---

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|----------|
| *Τι γίνεται αν χρειάζομαι περισσότερα από ένα κουμπί;* | Επαναλάβετε τα βήματα 3–6 με διαφορετικά ονόματα και λεζάντες. Κάθε κουμπί πρέπει να έχει μια μοναδική τιμή `SetName`. |
| *Μπορώ να ορίσω το μέγεθος του κουμπιού;* | Ναι. Μετά την εισαγωγή του ελέγχου, μπορείτε να τροποποιήσετε τις ιδιότητες `Width` και `Height` μέσω του αντικειμένου `OleFormat`. |
| *Θα λειτουργήσει το κουμπί σε όλες τις εκδόσεις του Word;* | Οι έλεγχοι ActiveX υποστηρίζονται στην επιτραπέζια έκδοση του Word (Windows). Δεν εμφανίζονται στο Word Online ή σε macOS. |
| *Πώς να προσθέσω έναν χειριστή κλικ;* | Πρέπει να γράψετε κώδικα VBA που αναφέρεται στο όνομα του κουμπιού (`btnSubmit`). Η μακροεντολή VBA μπορεί να ενσωματωθεί χρησιμοποιώντας `doc.VbaProject`. |
| *Τι γίνεται αν χρειαστεί να εισάγω το κουμπί μέσα σε κελί πίνακα;* | Μετακινήστε τον κέρσορα του builder στο επιθυμητό κελί (`builder.MoveTo(cell.FirstParagraph)`) πριν καλέσετε το `InsertForms2OleControl`. |

---

## Pro συμβουλές

* **Pro tip:** Πάντα ορίστε ένα περιγραφικό όνομα με `SetName`. Απλοποιεί την αυτοματοποίηση VBA και κάνει την αποσφαλμάτωση πιο εύκολη.
* **Watch out for:** Ξεχάνοντας να καλέσετε το `SetControlType`. Χωρίς αυτήν την κλήση το αντικείμενο OLE εμφανίζεται ως γενική θέση κράτησης αντί για κλικαρίσιμο κουμπί.
* **Performance tip:** Αν δημιουργείτε πολλά έγγραφα σε βρόχο, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` και καλέστε `builder.MoveToDocumentEnd()` πριν από κάθε εισαγωγή για να αποφύγετε περιττές επαναρυθμίσεις του κέρσορα.

---

## Επόμενα βήματα

Τώρα που γνωρίζετε πώς να **δημιουργήσετε έγγραφο Word προγραμματιστικά**, **εισάγετε κουμπί CommandButton στο Word**, **ορίσετε τη λεζάντα του κουμπιού CommandButton**, και **αποθηκεύσετε το έγγραφο Word με κουμπί**, μπορείτε να εξερευνήσετε πιο προχωρημένα σενάρια:

* Προσθέστε στοιχεία **TextFormField** για είσοδο χρήστη.
* Συνδυάστε κουμπιά με πεδία **MacroButton** για άμεση εκτέλεση VBA.
* Χρησιμοποιήστε **DocumentBuilder.InsertImage** για να τοποθετήσετε εικονίδια στα κουμπιά σας.
* Ενσωματώστε με ASP.NET για τη δημιουργία φορμών Word στο

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Δημιουργία νέου εγγράφου Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Δημιουργία εγγράφου Word με Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Εισαγωγή ενσωματωμένης εικόνας σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}