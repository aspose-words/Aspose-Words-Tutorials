---
category: general
date: 2026-10-20
description: Απόκρυψη/Εμφάνιση ενός σχήματος με τη νέα ιδιότητα `Hidden` χρησιμοποιώντας
  το Aspose.Words για C#. Μάθετε πώς να εναλλάσσετε την ορατότητα του σχήματος, να
  διαχειρίζεστε ειδικές περιπτώσεις και να αποθηκεύετε το αποτέλεσμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: el
lastmod: 2026-10-20
og_description: Απόκρυψη/Εμφάνιση σχήματος με τη νέα ιδιότητα `Hidden` χρησιμοποιώντας
  το Aspose.Words για C#. Κατακτήστε την εναλλαγή ορατότητας του σχήματος και αποφύγετε
  κοινά προβλήματα.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Απόκρυψη/Εμφάνιση Σχήματος με τη νέα ιδιότητα `Hidden` στο Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Απόκρυψη/Εμφάνιση σχήματος με τη νέα ιδιότητα `Hidden` στο Aspose.Words για
  C#
url: /el/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Απόκρυψη/Εμφάνιση ενός Σχήματος με τη νέα ιδιότητα `Hidden` στο Aspose.Words για C#

Αν χρειάζεστε να **Απόκρυψη/Εμφάνιση ενός Σχήματος με τη νέα ιδιότητα `Hidden`** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words για .NET. Είτε δημιουργείτε αναφορές, δημιουργείτε πρότυπα, είτε καθαρίζετε εισαγόμενα έγγραφα, ο προγραμματιστικός έλεγχος της ορατότητας των σχημάτων σας εξοικονομεί χρόνο από τη χειροκίνητη επεξεργασία.

Σε αυτό το tutorial θα μάθετε πώς να φορτώσετε ένα έγγραφο, να εντοπίσετε ένα σχήμα, να αλλάξετε την ιδιότητα `Hidden` και να αποθηκεύσετε το τροποποιημένο αρχείο. Τα βήματα καλύπτουν επίσης κοινές παραλλαγές, όπως η διαχείριση πολλαπλών σχημάτων και η αντιμετώπιση γραφικών inline έναντι floating.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερη) εγκατεστημένη – το Aspose.Words υποστηρίζει .NET Standard 2.0 και .NET Core.  
* Μια αδειοδοτημένη έκδοση του **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για εξερεύνηση).  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code.  
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα σχήμα (π.χ. μια εικόνα, SmartArt ή καμβά σχεδίασης).

## Βήμα 1: Φόρτωση του εγγράφου Word

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document` που αντιπροσωπεύει το αρχείο .docx στο δίσκο.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί αυτό το βήμα είναι σημαντικό*: `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες του Aspose.Words. Η φόρτωση του αρχείου στη μνήμη σας δίνει πλήρη πρόσβαση στο δέντρο κόμβων, συμπεριλαμβανομένων των σχημάτων.

## Βήμα 2: Ανάκτηση του στόχου σχήματος

Για να αλλάξετε την ορατότητα πρέπει να αποκτήσετε μια αναφορά στον κόμβο του σχήματος. Το παρακάτω παράδειγμα παίρνει το πρώτο σχήμα στο έγγραφο, αλλά μπορείτε να προσαρμόσετε τη λογική ώστε να εντοπίζει σχήματα με βάση το όνομα, τον τύπο ή το δείκτη.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Γιατί αυτό το βήμα είναι σημαντικό*: `GetChild` με `true` εκτελεί αναζήτηση σε βάθος, εξασφαλίζοντας ότι θα βρείτε σχήματα ακόμη και όταν είναι ενσωματωμένα σε πίνακες ή κεφαλίδες. Ο έλεγχος για `null` αποτρέπει ένα `NullReferenceException` όταν το έγγραφο δεν περιέχει σχήματα.

## Βήμα 3: Απόκρυψη του σχήματος με την ιδιότητα `Hidden`

Το Aspose.Words εισήγαγε την ιδιότητα `Hidden` για να ελέγχει αν ένα σχήμα θα αποδοθεί ή θα εκτυπωθεί. Ορίζοντάς το σε `true` κρύβει το σχήμα· ορίζοντάς το σε `false` το κάνει ξανά ορατό.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Αν χρειάζεστε να **εμφανίσετε** ένα προηγουμένως κρυμμένο σχήμα, απλώς ορίστε `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Γιατί αυτό το βήμα είναι σημαντικό*: Η ιδιότητα `Hidden` λειτουργεί τόσο για floating όσο και για inline σχήματα και ενσωματώνεται με τη φυσική μορφοποίηση “Hidden” του Word. Αυτή η προσέγγιση είναι πιο αξιόπιστη από την αφαίρεση του σχήματος, επειδή ο κόμβος παραμένει στο δέντρο του εγγράφου, διατηρώντας τη διάταξη και τις αναφορές.

## Βήμα 4: Αποθήκευση του τροποποιημένου εγγράφου

Αφού προσαρμόσετε την ορατότητα, γράψτε τις αλλαγές σε ένα νέο αρχείο (ή αντικαταστήστε το αρχικό, αν το προτιμάτε).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Γιατί αυτό το βήμα είναι σημαντικό*: `Save` σειριοποιεί το δέντρο κόμβων στη μνήμη σε ένα πακέτο .docx που μπορεί να ανοίξει το Word. Η σημαία κρυψίματος διατηρείται, ώστε το άνοιγμα του αρχείου στο Microsoft Word να εμφανίζει το σχήμα σύμφωνα με τη ρύθμιση `Hidden`.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα βήματα παίρνετε ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Αναμενόμενο αποτέλεσμα** όταν εκτελέσετε το πρόγραμμα:

```
Document saved. Shape hidden = True
```

Το άνοιγμα του `ShapeHidden.docx` στο Microsoft Word εμφανίζει το έγγραφο χωρίς το στοχευμένο σχήμα. Αν ορίσετε `shape.Hidden = false;` πριν αποθηκεύσετε, το σχήμα εμφανίζεται ξανά.

## Διαχείριση πολλαπλών σχημάτων

Το παραπάνω παράδειγμα λειτουργεί για ένα μόνο σχήμα. Στην πραγματικότητα, τα έγγραφα συχνά περιέχουν πολλά γραφικά. Χρησιμοποιήστε έναν βρόχο για να κρύψετε ή να εμφανίσετε όλα τα σχήματα που πληρούν μια συνθήκη (π.χ. συγκεκριμένο όνομα ή τύπο).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Συμβουλή*: Η φιλτράρισμα με `ShapeType` αποτρέπει το ακούσιο κρύψιμο διακοσμητικών στοιχείων όπως πλαίσια κειμένου ή SmartArt.

## Περιπτώσεις άκρων και βέλτιστες πρακτικές

| Κατάσταση | Συνιστώμενη αντιμετώπιση |
|-----------|--------------------------|
| **Το σχήμα βρίσκεται σε κεφαλίδα/υποσέλιδο** | Πρώτα ανακτήστε τον κόμβο κεφαλίδας/υποσέλιδου, μετά καλέστε `GetChild(NodeType.Shape, …)` σε αυτό το υπο‑έγγραφο. |
| **Το έγγραφο δεν περιέχει σχήματα** | Πάντα ελέγχετε για `null` μετά το `GetChild` ή επαληθεύστε `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Πρέπει να διατηρήσετε τη σημαία κρυψίματος σε διαφορετικές εκδόσεις του Word** | Η ιδιότητα `Hidden` αποθηκεύεται στο XML του σχήματος ως `<w:hidden/>`, που υποστηρίζεται από το Word 2007 και μεταγενέστερα. |
| **Απόδοση με μεγάλα έγγραφα** | Χρησιμοποιήστε `doc.GetChildNodes(NodeType.Shape, true)` μία φορά και επαναχρησιμοποιήστε τη συλλογή αντί να καλείτε επανειλημμένα το `GetChild`. |

## Pro tip: Συνδυάστε το `Hidden` με το `WrapType`

Όταν ένα σχήμα είναι κρυμμένο, το Word εξακολουθεί να διατηρεί τον χώρο που θα κατείχε εκτός αν αλλάξετε και τη συμπεριφορά περιτύλιξης. Ορίζοντας `WrapType = WrapType.None` αφαιρεί την περιοχή κράτησης.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Αυτό εξασφαλίζει ότι η διάταξη συμπτύσσεται σαν να μην υπήρχε ποτέ το σχήμα, κάτι χρήσιμο για τη δημιουργία καθαρών αναφορών.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **Απόκρυψη/Εμφάνιση ενός Σχήματος με τη νέα ιδιότητα `Hidden`** χρησιμοποιώντας το Aspose.Words για C#. Η λύση καλύπτει τη φόρτωση ενός εγγράφου, την εντόπιση ενός σχήματος, την αλλαγή της ιδιότητας `Hidden` και την αποθήκευση της αλλαγής. Ακολουθώντας τις βέλτιστες πρακτικές—έλεγχο για `null`, διαχείριση πολλαπλών σχημάτων και προσαρμογή των ρυθμίσεων περιτύλιξης—μπορείτε αξιόπιστα να ελέγχετε την ορατότητα των σχημάτων σε οποιοδήποτε σενάριο αυτοματοποίησης του Word.

Έτοιμοι να εξερευνήσετε περισσότερα; Σκεφτείτε τα επόμενα βήματα:

* **Απόκρυψη/Εμφάνιση πολλαπλών σχημάτων** βάσει προσαρμοσμένων μεταδεδομένων (χρησιμοποιεί την τεχνική “προγραμματιστική απόκρυψη σχήματος”).  
* **Συνδυάστε το `Hidden` με περιεχόμενο υπό όρους** χρησιμοποιώντας πεδία Aspose.Words για δυναμική δημιουργία αναφορών.  
* **Εξερευνήστε άλλες ιδιότητες κόμβων**, όπως `Visible` για αντικείμενα διαγραμμάτων ή `IsDeleted` για έλεγχο σε επίπεδο παραγράφου.

Καλή προγραμματιστική δουλειά και απολαύστε τον ακριβή έλεγχο που παρέχει το Aspose.Words στην ορατότητα σχημάτων σε έγγραφα Word!

## Τι πρέπει να μάθετε επόμενα;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}