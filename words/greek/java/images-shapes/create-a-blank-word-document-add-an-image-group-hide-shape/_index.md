---
category: general
date: 2026-10-10
description: Δημιουργήστε ένα κενό έγγραφο Word, εισάγετε εικόνα στο Word, προσθέστε
  μια ομάδα εικόνων και κρύψτε το σχήμα στο αποθηκευμένο αρχείο. Ακολουθήστε αυτόν
  τον οδηγό βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: el
lastmod: 2026-10-10
og_description: Δημιουργήστε ένα κενό έγγραφο Word, εισάγετε εικόνα στο Word, προσθέστε
  μια ομάδα εικόνων και κρύψτε το σχήμα. Αυτός ο οδηγός δείχνει τον πλήρη κώδικα C#.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε μια ομάδα εικόνων, κρύψτε
  το σχήμα
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε μια ομάδα εικόνων, κρύψτε το
  σχήμα
url: /el/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε μια ομάδα εικόνων, κρύψτε το σχήμα

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο Word** και αργότερα να κρύψετε οπτικά στοιχεία, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα μάθετε πώς να εισάγετε εικόνα στο Word, να προσθέσετε ομάδα εικόνων και να κρύψετε το σχήμα σε έγγραφο Word με μια ενιαία, επαναχρησιμοποιήσιμη ρουτίνα C#.

Θα χρησιμοποιήσουμε τη βιβλιοθήκη Aspose.Words for .NET, η οποία σας επιτρέπει να χειρίζεστε αρχεία .docx χωρίς να έχετε εγκατεστημένο το Microsoft Word. Στο τέλος αυτού του οδηγού θα έχετε ένα εκτελέσιμο πρόγραμμα που παράγει ένα αρχείο Word που περιέχει μια κρυφή ομάδα εικόνων, έτοιμο για επεξεργασία downstream ή για υπό όρους εμφάνιση.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Ένας φάκελος στο δίσκο όπου μπορείτε να διαβάσετε ένα αρχείο εικόνας και να γράψετε το παραγόμενο έγγραφο
- Βασική εξοικείωση με C# και Visual Studio (ή οποιοδήποτε IDE προτιμάτε)

## Δημιουργία κενού εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι **να δημιουργήσετε κενό έγγραφο Word**. Η Aspose.Words παρέχει την κλάση `Document` που αντιπροσωπεύει ένα έγγραφο Word στη μνήμη. Η δημιουργία της χωρίς ορίσματα σας δίνει ένα κενό έγγραφο έτοιμο για περιεχόμενο.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό:* Ξεκινώντας με κενό έγγραφο εξασφαλίζετε ότι δεν υπάρχουν κρυφές μορφοποιήσεις ή υπόλοιπες ενότητες που θα μπορούσαν να επηρεάσουν το σχήμα που θα προσθέσετε αργότερα.

## Εισαγωγή εικόνας στο Word χρησιμοποιώντας DocumentBuilder

Στη συνέχεια **εισάγουμε εικόνα στο Word** δημιουργώντας πρώτα ένα group shape που θα κρατήσει την εικόνα. Τα group shapes σας επιτρέπουν να αντιμετωπίζετε πολλά αντικείμενα σχεδίασης ως μία ενότητα, κάτι που είναι χρήσιμο όταν θέλετε αργότερα να τα κρύψετε ή να τα μετακινήσετε μαζί.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Η μέθοδος `InsertGroupShape` δημιουργεί ένα κενό container. Οι διαστάσεις δίνονται σε points (1 point = 1/72 ίντσα). Προσαρμόστε το μέγεθος ώστε να ταιριάζει στην ανάλυση της εικόνας που σκοπεύετε να ενσωματώσετε.

## Προσθήκη ομάδας εικόνων στο έγγραφο

Τώρα **προσθέτουμε την ομάδα εικόνων** μετακινώντας τον κέρσορα του builder μέσα στη νεοδημιουργημένη ομάδα και εισάγοντας την εικόνα. Όλες οι επόμενες εισαγωγές θα είναι μέρος της ομάδας.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Συμβουλή:* Χρησιμοποιήστε απόλυτη ή σωστά escaped σχετική διαδρομή· διαφορετικά η `InsertImage` ρίχνει `FileNotFoundException`.

## Απόκρυψη σχήματος σε έγγραφο Word

Τέλος, **κρύβουμε το σχήμα** στο έγγραφο Word ορίζοντας την ιδιότητα `Hidden` της ομάδας σε `true`. Τα κρυφά σχήματα δεν εμφανίζονται όταν το έγγραφο ανοίγει στο Word, αλλά παραμένουν στο αρχείο και μπορούν να αποκαλυφθούν προγραμματιστικά αργότερα.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Όταν ανοίξετε το *GroupHidden.docx* στο Microsoft Word, θα δείτε μια εντελώς κενή σελίδα επειδή η ομάδα εικόνων είναι κρυφή. Το αρχείο εξακολουθεί να περιέχει τα δεδομένα της εικόνας, τα οποία μπορείτε να αποκαλύψετε αργότερα με `group.Hidden = false` εάν χρειαστεί.

## Πλήρες, εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα νέο console project:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**

- Ένα αρχείο με όνομα `GroupHidden.docx` δημιουργείται στο `YOUR_DIRECTORY`.
- Το άνοιγμα του αρχείου στο Word εμφανίζει μια κενή σελίδα.
- Η κρυφή εικόνα μπορεί να αποκαλυφθεί αλλάζοντας `group.Hidden = false` και αποθηκεύοντας ξανά.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να προσαρμόσετε τον κώδικα |
|-----------|------------------------------|
| **Πολλαπλές εικόνες** | Εισάγετε επιπλέον κλήσεις `InsertImage` μετά το `builder.MoveTo(group)`. Όλες οι εικόνες παραμένουν μέσα στην ίδια ομάδα και μοιράζονται τη σημαία κρυψίματος. |
| **Διαφορετικές μορφές εικόνας** | Η Aspose.Words υποστηρίζει PNG, JPEG, BMP, GIF, TIFF. Απλώς αλλάξτε την επέκταση του αρχείου· δεν απαιτείται αλλαγή κώδικα. |
| **Υπό όρους ορατότητα** | Αποθηκεύστε μια προσαρμοσμένη μεταβλητή εγγράφου (`doc.Variables.Add("ShowImages", "true")`) και εναλλάξτε το `group.Hidden` με βάση την τιμή της κατά την εκτέλεση. |
| **Μεγάλα έγγραφα** | Δημιουργήστε την ομάδα σε συγκεκριμένη σελίδα (`builder.InsertBreak(BreakType.PageBreak)`) πριν την εισαγωγή της ομάδας, ώστε να αποφύγετε μετατοπίσεις διάταξης. |
| **Συμβατότητα με παλαιότερες εκδόσεις Word** | Αποθηκεύστε ως `doc.Save("output.doc", SaveFormat.Doc)` εάν χρειάζεστε τη μορφή legacy `.doc`; τα κρυφά σχήματα συμπεριφέρονται με τον ίδιο τρόπο. |

**Pro tip:** Πάντα ορίζετε `group.Hidden = true` *μετά* την εισαγωγή όλων των παιδικών στοιχείων. Η αλλαγή της σημαίας πριν την προσθήκη περιεχομένου μπορεί να προκαλέσει ανεπιθύμητη απόδοση σε παλαιότερες εκδόσεις του Word.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο Word**, **να εισάγετε εικόνα στο Word**, **να προσθέσετε ομάδα εικόνων** και **να κρύψετε σχήμα σε έγγραφο Word** χρησιμοποιώντας την Aspose.Words for .NET. Το πλήρες παράδειγμα δείχνει κάθε βήμα, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση ενός αρχείου που περιέχει μια κρυφή ομάδα εικόνων.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

- Προσθήκη πλαισίων κειμένου ή διαγραμμάτων στην ίδια ομάδα
- Χρήση `DocumentBuilder.StartBookmark` / `EndBookmark` για σήμανση κρυφών τμημάτων
- Προγραμματιστική εναλλαγή ορατότητας βάσει εισόδου χρήστη ή μεταβλητών εγγράφου

Μη διστάσετε να πειραματιστείτε με διαφορετικά σχήματα, μεγέθη και κανόνες ορατότητας ώστε να ταιριάζουν στο σενάριο αυτοματοποίησής σας. Καλός κώδικας!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}