---
category: general
date: 2026-10-10
description: Ορίστε το κείμενο του κουμπιού και προσθέστε ένα κουμπί ActiveX σε C#
  χρησιμοποιώντας το Aspose.Words. Μάθετε πώς να εισάγετε κουμπί, να δημιουργήσετε
  έλεγχο κουμπιού και να προσαρμόσετε τη λεζάντα σε ένα έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: el
lastmod: 2026-10-10
og_description: Ορίστε το κείμενο του κουμπιού και προσθέστε ένα κουμπί ActiveX σε
  C# με το Aspose.Words. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να εισαγάγετε ένα
  κουμπί, να δημιουργήσετε έλεγχο κουμπιού και να προσαρμόσετε τη λεζάντα του.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Ορίστε το κείμενο του κουμπιού και προσθέστε ένα κουμπί ActiveX σε C# –
  πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Ορισμός κειμένου κουμπιού και προσθήκη κουμπιού ActiveX σε C#
url: /el/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός κειμένου κουμπιού και προσθήκη κουμπιού ActiveX σε C#

Αν χρειάζεστε να **ορίσετε κείμενο κουμπιού** σε ένα κουμπί ActiveX μέσα σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Στο τέλος του tutorial θα μπορείτε να **εισάγετε κουμπί**, να δημιουργήσετε ένα **κουμπί ελέγχου** και να προσαρμόσετε τη λεζάντα του με λίγες μόνο γραμμές κώδικα C#.

Η εργασία με ελέγχους ActiveX είναι συχνή όταν θέλετε διαδραστικές φόρμες στο Word — είτε δημιουργείτε ένα πρότυπο σύμβασης, μια έρευνα ή ένα εσωτερικό εργαλείο. Το παράδειγμα χρησιμοποιεί το Aspose.Words for .NET, μια βιβλιοθήκη που επιτρέπει τη διαχείριση αρχείων Word χωρίς την εγκατάσταση του Microsoft Office.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)  
* Άδεια Aspose.Words for .NET (η δωρεάν αξιολόγηση λειτουργεί για εκμάθηση)  

Χρειάζεστε επίσης μια αναφορά στο πακέτο NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Πώς να εισάγετε κουμπί σε έγγραφο Word

Το πρώτο βήμα είναι να δημιουργήσετε ένα νέο `Document` και ένα `DocumentBuilder`. Ο builder είναι το σημείο εισόδου για την προσθήκη περιεχομένου, συμπεριλαμβανομένων των ελέγχων ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:** Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει μεθόδους υψηλού επιπέδου όπως `InsertParagraph` και `InsertFormField`. Ξεκινώντας με ένα καθαρό έγγραφο διασφαλίζετε ότι το κουμπί θα εμφανιστεί ακριβώς εκεί που το θέλετε.

## Δημιουργία ελέγχου κουμπιού με Forms2OleControl

Τώρα δημιουργούμε τον πραγματικό έλεγχο κουμπιού. Η `Forms2OleControl` είναι η κλάση που χρησιμοποιεί το Aspose.Words για όλα τα αντικείμενα ActiveX, και ο τύπος `COMMANDBUTTON` αποδίδει ένα κλικ-μεγαλύτερο κουμπί στο Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Επεξήγηση:**  
* Η `InsertForms2OleControl` τοποθετεί τον έλεγχο στις ακριβείς συντεταγμένες που παρέχετε.  
* Το μέγεθος ορίζεται σε points (1 point = 1/72 ίντσα). Προσαρμόστε αυτούς τους αριθμούς ώστε να ταιριάζουν με τη διάταξή σας.

## Προσθήκη ελέγχου ActiveX και ανάθεση μοναδικού ονόματος

Κάθε αντικείμενο ActiveX πρέπει να έχει ένα διακριτό όνομα ώστε να μπορείτε να το αναφέρετε αργότερα (π.χ. όταν διαχειρίζεστε συμβάντα σε VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Συμβουλή:** Αποφύγετε κενά ή ειδικούς χαρακτήρες στο όνομα· το Word το θεωρεί ως αναγνωριστικό στο εσωτερικό μοντέλο φόρμας.

## Ορισμός κειμένου κουμπιού (λεζάντας) στο κουμπί ActiveX

Εδώ έρχεται σε εφαρμογή η κύρια λέξη‑κλειδί **ορίσετε κείμενο κουμπιού**. Η ιδιότητα `Caption` ορίζει την ετικέτα που βλέπουν οι χρήστες στο κουμπί.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Μπορείτε να αλλάξετε τη λεζάντα οποτεδήποτε πριν αποθηκεύσετε το έγγραφο. Αν αργότερα χρειαστεί να τοποθετήσετε το UI σε άλλη γλώσσα, απλώς καλέστε ξανά το `SetCaption` με διαφορετικό string.

## Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Τέλος, γράψτε το έγγραφο στο δίσκο. Ανοίγοντας το αρχείο στο Microsoft Word θα δείτε το κουμπί με την προσαρμοσμένη λεζάντα.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν ανοίξετε *ActiveXButton.docx* στο Word, θα δείτε ένα κουμπί τοποθετημένο στις καθορισμένες συντεταγμένες, με την ετικέτα **Click Me**. Κάνοντας κλικ στο κουμπί θα ενεργοποιηθεί η προεπιλεγμένη συμπεριφορά του κουμπιού εντολής του Word (που μπορείτε αργότερα να προσαρμόσετε με VBA).

![Set button text example](https://example.com/activex-button.png){alt="Παράδειγμα ορισμού κειμένου κουμπιού"}

## Προσθήκη κουμπιού ActiveX και διαχείριση συμβάντων (προαιρετικό)

Αν χρειάζεστε το κουμπί να εκτελεί μια προσαρμοσμένη ενέργεια, μπορείτε να προσθέσετε μια μακροεντολή VBA που αντιδρά στο συμβάν `Click`. Η μακροεντολή μπορεί να ενσωματωθεί προγραμματιστικά, αλλά αυτό υπερβαίνει το πεδίο αυτού του οδηγού. Το σημαντικό είναι ότι το κουμπί είναι ήδη παρόν και η λεζάντα του έχει οριστεί — έτοιμο για οποιαδήποτε διαχείριση συμβάντων επιλέξετε.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Το κουμπί εμφανίζεται μη ευθυγραμμισμένο | Οι συντεταγμένες είναι σε points, όχι pixels | Μετατρέψτε τις τιμές pixel σε points (`points = pixels * 72 / DPI`) |
| Η λεζάντα δεν αλλάζει μετά την αποθήκευση | `SetCaption` κλήθηκε μετά το `Save` | Πάντα ορίστε τη λεζάντα **πριν** καλέσετε `doc.Save` |
| Ο έλεγχος δεν είναι ορατός σε παλαιότερες εκδόσεις Word | Ορισμένες παλαιότερες εκδόσεις Word δεν υποστηρίζουν πλήρως το ActiveX | Δοκιμάστε στην έκδοση στόχο· εξετάστε το ενδεχόμενο χρήσης `CheckBox` ή `DropDownList` ως εναλλακτική |
| Προειδοποίηση άδειας στην έξοδο | Η αξιολογική άδεια λήγει | Εφαρμόστε έγκυρη άδεια Aspose.Words μέσω `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using` και δείχνει ολόκληρη τη ροή εργασίας από τη δημιουργία του εγγράφου μέχρι την αποθήκευση.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Τρέξτε το πρόγραμμα με `dotnet run`. Μετά την εκτέλεση, ανοίξτε *ActiveXButton.docx* για να επιβεβαιώσετε ότι η λεζάντα του κουμπιού εμφανίζει **Click Me**.

## Ανακεφαλαίωση όσων μάθατε

* Μάθατε πώς να **ορίσετε κείμενο κουμπιού** σε ένα κουμπί ActiveX χρησιμοποιώντας το Aspose.Words.  
* Είδατε τα ακριβή βήματα για **πώς να εισάγετε κουμπί**, **να δημιουργήσετε έλεγχο κουμπιού** και **να προσθέσετε έλεγχο activex** σε έγγραφο Word.  
* Διαθέτετε τώρα ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορείτε να προσαρμόσετε σε οποιοδήποτε έργο αυτοματοποίησης Word βασισμένο σε φόρμες.

## Επόμενα βήματα

* Εξερευνήστε άλλες τιμές `Forms2OleControlType` όπως `CHECKBOX` ή `LISTBOX` για να δημιουργήσετε πιο πλούσιες φόρμες.  
* Συνδυάστε το κουμπί με μια μακροεντολή VBA για να εκτελεί υπολογισμούς ή έλεγχο δεδομένων.  
* Χρησιμοποιήστε το API `FormField` του Aspose.Words για να διαβάσετε τις εισροές του χρήστη μετά τη συμπλήρωση του εγγράφου.

Νιώστε ελεύθεροι να πειραματιστείτε με το μέγεθος, τη θέση και τη λεζάντα ώστε να ταιριάζουν στις απαιτήσεις του σχεδίου σας. Αν αντιμετωπίσετε προβλήματα, η τεκμηρίωση του Aspose.Words παρέχει λεπτομερείς αναφορές για κάθε κλάση που χρησιμοποιείται σε αυτόν τον οδηγό.

Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία κενής εγγράφου Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Προσθήκη σκιάς σε σχήμα στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Προσθήκη αριθμών σελίδας στο υποσέλιδο εγγράφου Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}