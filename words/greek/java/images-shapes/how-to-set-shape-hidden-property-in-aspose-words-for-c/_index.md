---
category: general
date: 2026-08-20
description: Μάθετε πώς να ορίζετε την ιδιότητα κρυμμένου σχήματος στο Aspose.Words
  για C#. Αυτός ο οδηγός δείχνει πώς να εισάγετε μια εικόνα και να κρύψετε το σχήμα
  ώστε να μην εμφανίζεται ποτέ στη διεπαφή χρήστη ή στην έξοδο εκτύπωσης.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: el
lastmod: 2026-08-20
og_description: Ορίστε την ιδιότητα κρυφής μορφής στο Aspose.Words με C#. Εισάγετε
  μια εικόνα, κρύψτε το σχήμα και βεβαιωθείτε ότι δεν εμφανίζεται ποτέ στη διεπαφή
  χρήστη ή στην έξοδο εκτύπωσης.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Ορισμός της ιδιότητας κρυφής σχήματος στο Aspose.Words – πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Πώς να ορίσετε την ιδιότητα «κρυφό» του σχήματος στο Aspose.Words για C#
url: /el/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε την ιδιότητα κρυφής μορφής στο Aspose.Words για C#

Αν χρειάζεται να **ορίσετε την ιδιότητα κρυφής μορφής** σε ένα έγγραφο Word, αυτό το tutorial σας δείχνει τα ακριβή βήματα χρησιμοποιώντας το Aspose.Words για .NET. Είτε δημιουργείτε μια μηχανή προτύπων, παράγετε αναφορές ή ενσωματώνετε ένα λογότυπο που πρέπει να παραμείνει αόρατο, θα μάθετε πώς να εισάγετε μια εικόνα και να κρύψετε τη μορφή ώστε να μην εμφανίζεται ποτέ στη διεπαφή χρήστη ή στην εκτύπωση.

Σε αυτόν τον οδηγό καλύπτουμε επίσης **insert image into document**, εξηγούμε γιατί η απόκρυψη μιας μορφής είναι σημαντική για την εκτύπωση, και περπατάμε μέσα από τον πλήρη, εκτελέσιμο κώδικα. Δεν απαιτούνται εξωτερικές αναφορές — απλώς αντιγράψτε, επικολλήστε και εκτελέστε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερο (η τελευταία έκδοση του Aspose.Words στοχεύει στο .NET 6+)
* Έγκυρη άδεια Aspose.Words για .NET (ή χρησιμοποιήστε τη δωρεάν λειτουργία αξιολόγησης)
* Visual Studio 2022 ή οποιοδήποτε IDE C# προτιμάτε
* Ένα αρχείο εικόνας (π.χ., `logo.png`) τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε από τον κώδικα

## Βήμα 1: Δημιουργία νέου Document και DocumentBuilder

Η κλάση `DocumentBuilder` είναι το σημείο εισόδου για τη δημιουργία περιεχομένου Word προγραμματιστικά. Σας επιτρέπει να εισάγετε παραγράφους, πίνακες και σχήματα όπως εικόνες.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί αυτό το βήμα;*  
Δημιουργώντας ένα `Document` λαμβάνετε μια αναπαράσταση στη μνήμη ενός αρχείου .docx, ενώ το `DocumentBuilder` παρέχει το fluent API που εισάγει αντικείμενα. Χωρίς αυτά τα αντικείμενα δεν μπορείτε να τοποθετήσετε ένα σχήμα στο έγγραφο.

## Βήμα 2: Εισαγωγή της εικόνας ως σχήμα

Το Aspose.Words αντιμετωπίζει κάθε εικόνα ως `Shape`. Η μέθοδος `InsertImage` επιστρέφει το αντίστοιχο αντικείμενο `Shape`, το οποίο μπορείτε να χειριστείτε αργότερα.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Γιατί αυτό το βήμα;*  
Η χρήση του `InsertImage` όχι μόνο προσθέτει την εικόνα στη ροή του κειμένου, αλλά σας δίνει επίσης μια αναφορά (`picture`) που μπορείτε να διαμορφώσετε. Αυτό είναι ουσιώδες για την **C# shape hidden property** που θα ορίσουμε στη συνέχεια.

## Βήμα 3: Ορισμός της ιδιότητας κρυφής μορφής

Η ιδιότητα `Hidden` ελέγχει αν το σχήμα συμμετέχει στη διεπαφή χρήστη και στην εκτύπωση. Ορίζοντάς το σε `true` κάνει το σχήμα αόρατο στη διεπαφή του Word και εγγυάται ότι δεν θα εκτυπωθεί.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Γιατί αυτό το βήμα;*  
Όταν ένα σχήμα σημειώνεται ως κρυφό, το Word το αντιμετωπίζει όπως ένα σχόλιο — υπάρχει στη δομή του εγγράφου αλλά δεν αποδίδεται ποτέ. Αυτό αποτελεί τον πυρήνα του **set shape hidden property**.

## Βήμα 4: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words (`.docx`, `.pdf`, `.html`, κλπ.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Γιατί αυτό το βήμα;*  
Η αποθήκευση ολοκληρώνει τις αλλαγές στη μνήμη. Ανοίγοντας το παραγόμενο `.docx` στο Microsoft Word δεν εμφανίζεται καμία ορατή εικόνα, και η εξαγωγή σε PDF επιβεβαιώνει ότι το σχήμα δεν εμφανίζεται ποτέ στην εκτύπωση.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**

* Ανοίγοντας το `HiddenImageDocument.docx` στο Microsoft Word δεν εμφανίζεται καμία ορατή εικόνα.
* Η εξαγωγή ή η εκτύπωση του εγγράφου (ή το άνοιγμα του PDF) επίσης δεν εμφανίζει εικόνα.
* Το κρυφό σχήμα εξακολουθεί να υπάρχει στο XML του εγγράφου, το οποίο μπορείτε να επαληθεύσετε ανοίγοντας το `.docx` ως zip και εξετάζοντας το `word/document.xml` — θα δείτε ένα στοιχείο `<w:pict>` με `w:hidden="true"`.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Τι πρέπει να κάνετε | Γιατί είναι σημαντικό |
|-----------|--------------------|------------------------|
| **Απουσία αρχείου εικόνας** | Τυλίξτε το `InsertImage` σε `try/catch` και χειριστείτε το `FileNotFoundException`. | Αποτρέπει την κατάρρευση της εφαρμογής και σας επιτρέπει να καταγράψετε ένα σαφές σφάλμα. |
| **Πολλαπλά κρυφά σχήματα** | Καλέστε `picture.Hidden = true` για κάθε `Shape` που εισάγετε, ή επαναλάβετε πάνω από `doc.GetChildNodes(NodeType.Shape, true)`. | Εξασφαλίζει ότι κάθε ανεπιθύμητο οπτικό στοιχείο παραμένει αόρατο. |
| **Απαιτείται το σχήμα ορατό μόνο σε λειτουργία επεξεργασίας** | Ορίστε `picture.Hidden = false` μετά την επεξεργασία, έπειτα επαναφέρετε πριν την αποθήκευση. | Σας επιτρέπει να εργάζεστε με το σχήμα στη διεπαφή χρήστη ενώ διατηρείτε το τελικό αποτέλεσμα καθαρό. |
| **Εκτύπωση σε παλαιότερες εκδόσεις του Word** | Επαληθεύστε το έγγραφο με Word 2010 ή νεότερο· η σημαία hidden υποστηρίζεται σε όλες τις σύγχρονες εκδόσεις. | Εξασφαλίζει συμβατότητα με τη βάση χρηστών σας. |
| **Χρήση διαφορετικής μορφής αρχείου (π.χ., PDF απευθείας)** | Η σημαία `Hidden` λειτουργεί το ίδιο· το Aspose.Words τη σέβεται κατά τη μετατροπή σε PDF. | Επιβεβαιώνει ότι **prevent shape from printing** λειτουργεί για όλους τους προορισμούς εξαγωγής. |

## Συμβουλή: Επαλήθευση της σημαίας hidden προγραμματιστικά

Αν χρειάζεται να επιβεβαιώσετε ότι ένα σχήμα είναι κρυφό πριν την αποθήκευση, μπορείτε να ελέγξετε την ιδιότητα:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Αυτός ο απλός έλεγχος είναι χρήσιμος σε αυτοματοποιημένες διαδικασίες όπου πρέπει να εγγυηθείτε τη συμμόρφωση με τις πολιτικές δημιουργίας εγγράφων.

## Συμπέρασμα

Τώρα ξέρετε πώς να **ορίσετε την ιδιότητα κρυφής μορφής** στο Aspose.Words για C#. Εισάγοντας μια εικόνα, εφαρμόζοντας `picture.Hidden = true` και αποθηκεύοντας το έγγραφο, το σχήμα παραμένει εκτός της διεπαφής χρήστη και δεν εμφανίζεται ποτέ στην εκτύπωση. Αυτή η τεχνική είναι απαραίτητη όταν χρειάζεστε placeholders, υδατογραφήματα ή στοιχεία branding που πρέπει να παραμείνουν αόρατα για τους τελικούς χρήστες.

### Τι θα ακολουθήσει;

* Εξερευνήστε άλλες ιδιότητες σχήματος όπως `picture.WrapType`, `picture.Rotation` και `picture.RelativeHorizontalPosition`.
* Μάθετε πώς να **κρύψετε σχήμα στο Aspose.Words** υπό όρους, βάσει εισόδου χρήστη ή ρυθμίσεων.
* Συνδυάστε κρυφά σχήματα με βρόχους **insert image into document** για να δημιουργήσετε δυναμικούς, αόρατους δείκτες για επεξεργασία αργότερα (π.χ., πεδία mail‑merge).

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικές μορφές εικόνας, διατάξεις εγγράφων και προορισμούς εξαγωγής. Η απόκρυψη σχημάτων σας δίνει λεπτομερή έλεγχο πάνω σε ό,τι βλέπουν οι αναγνώστες σας — και ό,τι παραμένει στο παρασκήνιο. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Δημιουργία ομαδικού σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Εισαγωγή ενσωματωμένης εικόνας σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}