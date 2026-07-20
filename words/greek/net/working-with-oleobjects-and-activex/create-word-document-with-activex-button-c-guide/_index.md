---
category: general
date: 2026-07-19
description: Δημιουργήστε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words C# και
  μάθετε πώς να προσθέσετε ένα κουμπί εντολής ActiveX, να ορίσετε το μέγεθος του κουμπιού
  και να εισάγετε το κουμπί προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: el
lastmod: 2026-07-19
og_description: Δημιουργήστε έγγραφο Word με το Aspose.Words C# και ενσωματώστε ένα
  κουμπί εντολής ActiveX σε δευτερόλεπτα. Ακολουθήστε τον οδηγό βήμα‑προς‑βήμα για
  να ορίσετε το μέγεθος του κουμπιού και να το εισάγετε εύκολα.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Δημιουργία εγγράφου Word με κουμπί ActiveX – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Δημιουργία εγγράφου Word με κουμπί ActiveX – Οδηγός C#
url: /el/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Κουμπί ActiveX – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **δημιουργήσετε έγγραφο Word** που περιέχει ένα λειτουργικό κουμπί ActiveX; Ίσως αυτοματοποιείτε μια αναφορά και χρειάζεστε έναν κλικ‑μεγέθυνση “Έγκριση” απευθείας μέσα στο αρχείο. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από το ξεκίνημα—χρησιμοποιώντας το Aspose.Words for .NET για να προσθέσουμε ένα κουμπί εντολής ActiveX, να ορίσουμε το μέγεθός του και να το ενσωματώσουμε εκεί που το χρειάζεστε.  

Αν ποτέ σκεφτήκατε *πώς να προσθέσετε activex* στοιχεία χωρίς να ανοίξετε το Word χειροκίνητα, βρίσκεστε στο σωστό μέρος. Στο τέλος θα έχετε ένα εκτελέσιμο παράδειγμα, μια σαφή εξήγηση κάθε βήματος και συμβουλές για την αντιμετώπιση κοινών προβλημάτων.

## Τι Θα Μάθετε

- Πώς να ρυθμίσετε το Aspose.Words σε ένα έργο C#  
- Τον ακριβή κώδικα για **δημιουργία εγγράφου Word** και ενσωμάτωση ενός κουμπιού εντολής ActiveX  
- Τρόπους για **ορισμό μεγέθους κουμπιού** και προσαρμογή της λεζάντας και του ονόματος του  
- Τη σωστή μέθοδο για **εισαγωγή κουμπιού εντολής** και **πώς να εισάγετε κουμπί** σε οποιαδήποτε θέση του εγγράφου  
- Σκέψεις για ειδικές περιπτώσεις (έκδοση Word, περιορισμοί πλατφόρμας, προειδοποιήσεις ασφαλείας)

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+).  
- Ένα έγκυρο άδεια χρήσης Aspose.Words for .NET (ή ένα δωρεάν κλειδί αξιολόγησης).  
- Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε).  
- Βασική εξοικείωση με C# και αντικειμενοστραφή προγραμματισμό.

Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

---

## Βήμα 1: Δημιουργία Εγγράφου Word – Ρύθμιση Έργου

Πριν μπορέσουμε να **εισάγουμε κουμπί εντολής**, χρειαζόμαστε ένα κενό αρχείο Word για να εργαστούμε. Αυτό το βήμα δείχνει επίσης το κλασικό μοτίβο “δημιουργία εγγράφου Word” χρησιμοποιώντας το Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Γιατί είναι σημαντικό:** `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρακολουθεί τη θέση του κέρσορα. Όλες οι επόμενες εισαγωγές (συμπεριλαμβανομένου του ελέγχου ActiveX) γίνονται σε σχέση με αυτόν τον builder.

---

## Βήμα 2: Πώς να Προσθέσετε ActiveX – Δημιουργία του Controls CommandButton

Τώρα που υπάρχει το έγγραφο, ας αντιμετωπίσουμε το **πώς να προσθέσετε activex** μέρος. Το Aspose.Words εκθέτει την κλάση `Forms2OleControl` για αντικείμενα ActiveX. Εδώ θα δημιουργήσουμε ένα κουμπί εντολής και θα ρυθμίσουμε τις ιδιότητές του, συμπεριλαμβανομένης της απαίτησης **ορισμού μεγέθους κουμπιού**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** Το μέγεθος μετριέται σε points (1 point = 1/72 ίντσα). Προσαρμόστε τις τιμές ώστε να ταιριάζουν στο layout σας· για ένα τυπικό κουμπί γραμμής εργαλείων, 120 × 30 λειτουργεί άψογα.

---

## Βήμα 3: Εισαγωγή Κουμπιού Εντολής – Ο Πυρήνας του **Insert Command Button**

Με το control έτοιμο, τώρα **εισάγουμε κουμπί εντολής** στο έγγραφο στη τρέχουσα θέση του builder. Μπορείτε να μετακινήσετε τον builder οπουδήποτε (π.χ. μετά από μια παράγραφο) πριν καλέσετε αυτή τη μέθοδο.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Αν χρειάζεται να **πώς να εισάγετε κουμπί** σε συγκεκριμένο σελιδοδείκτη, απλώς μετακινήστε πρώτα τον builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Τι συμβαίνει στο παρασκήνιο;** Το Aspose.Words γράφει τα απαραίτητα ροές αντικειμένων OLE στο πακέτο .docx, ώστε το Word να μπορεί να αποδώσει το κουμπί χωρίς επιπλέον μακροεντολές.

---

## Βήμα 4: Αποθήκευση Εγγράφου – Ολοκλήρωση του Κύκλου **Create Word Document**

Το τελευταίο βήμα είναι απλό: αποθηκεύστε το αρχείο στο δίσκο. Αυτό ολοκληρώνει το round‑trip του **δημιουργία εγγράφου Word**, ενσωμάτωσης του ActiveX και αποθήκευσης.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word (μόνο Windows). Θα πρέπει να δείτε ένα κλικ‑μεγέθυνση κουμπί με την ετικέτα “Click Me”. Το κλικ θα ενεργοποιήσει την προεπιλεγμένη ενέργεια για ένα CommandButton—δεν συμβαίνει τίποτα εκτός αν συνδέσετε κώδικα VBA, αλλά το control είναι πλήρως λειτουργικό.

> **Αναμενόμενο αποτέλεσμα:** Ένα αρχείο .docx με μία σελίδα, ένα κουμπί κεντραρισμένο στο σημείο εισαγωγής, μεγέθους 120 × 30 pt, με λεζάντα “Click Me”.  
> ![Κουμπί ActiveX που εισήχθη σε έγγραφο Word](placeholder-image.png)  
> *Κείμενο alt εικόνας:* **Κουμπί ActiveX που εισήχθη σε έγγραφο Word χρησιμοποιώντας C#** (ταιριάζει με `og_image_alt`).

---

## Βήμα 5: Ειδικές Περιπτώσεις, Ασφάλεια και Καλές Πρακτικές

### Περιορισμοί Πλατφόρμας
- Τα ActiveX controls λειτουργούν μόνο στην έκδοση Windows του Word. Αν το κοινό σας περιλαμβάνει χρήστες macOS ή Word Online, το κουμπί θα εμφανίζεται ως στατική εικόνα.  
- Σε ορισμένα εταιρικά περιβάλλοντα απενεργοποιούνται τα ActiveX για λόγους ασφαλείας· ίσως χρειαστεί να υπογράψετε το έγγραφο ή να ενημερώσετε τους χρήστες να ενεργοποιήσουν το περιεχόμενο.

### Αλληλεπίδραση με VBA (Προαιρετικό)
Αν θέλετε το κουμπί να εκτελεί μια μακροεντολή, θα πρέπει να προσθέσετε ένα VBA project στο έγγραφο μετά την αποθήκευση. Το Aspose.Words δεν δημιουργεί αυτόματα κώδικα VBA, αλλά μπορείτε να χρησιμοποιήσετε το API `Document.VbaProject` για να τον ενσωματώσετε.

### Συγκρούσεις Ονομάτων
Πάντα δίνετε σε κάθε control ένα μοναδικό `Name`. Η επαναχρησιμοποίηση του ίδιου ονόματος μπορεί να προκαλέσει σφάλματα χρόνου εκτέλεσης όταν το Word προσπαθεί να επιλύσει το control.

### Συμβουλή Απόδοσης
Όταν εισάγετε πολλά controls, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` και αποφύγετε την κλήση `doc.Save` μέσα σε βρόχο. Ομαδοποιήστε τις εισαγωγές και αποθηκεύστε μία φορά στο τέλος.

---

## Πλήρες Παράδειγμα Λειτουργικού Προγράμματος

Συνδυάζοντας τα παραπάνω, εδώ είναι ένα πλήρες, έτοιμο‑για‑αντιγραφή πρόγραμμα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το αποθηκευμένο αρχείο και θα δείτε το κουμπί ακριβώς εκεί όπου ήταν τοποθετημένος ο builder.

---

## Συμπέρασμα

Μόλις **δημιουργήσαμε έγγραφο Word** από το μηδέν, μάθαμε **πώς να προσθέσουμε activex** διαμορφώνοντας ένα `Forms2OleControl`, κατακτήσαμε τις ιδιότητες **ορισμού μεγέθους κουμπιού**, και δείξαμε τον σωστό τρόπο **εισαγωγής κουμπιού εντολής** και **πώς να εισάγετε κουμπί** σε οποιοδήποτε σημείο του αρχείου.  

Από ένα μόνο δείγμα κώδικα έχετε τώρα μια σταθερή βάση για πιο πλούσια αυτοματοποίηση Word—είτε δημιουργείτε πρότυπα με διαδραστικές φόρμες, παράγετε συμβόλαια που απαιτούν επιβεβαίωση χρήστη, ή απλώς προσθέτετε μερικά χρήσιμα controls σε μια αναφορά.

### Τι Ακολουθεί;

- **Στυλ του κουμπιού** – αλλαγή γραμματοσειρών, χρωμάτων ή προσθήκη εικόνας φόντου.  
- **Σύνδεση VBA μακροεντολών** – κάντε το κουμπί να εκτελεί υπολογισμούς ή να εκκινεί εξωτερικά προγράμματα.  
- **Συνδυασμός με άλλα controls** – checkboxes, list boxes ή ακόμη και ενσωματωμένα φύλλα Excel.  

Πειραματιστείτε ελεύθερα, και αν συναντήσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω. Καλό προγραμματισμό και καλή αυτοματοποίηση Word με το Aspose.Words!

## Τι Θα Μάθετε Στη Σειρά Επόμενη;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}