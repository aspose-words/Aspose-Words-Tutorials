---
category: general
date: 2026-09-11
description: Μάθετε πώς να δημιουργείτε έγγραφο Word με C# και να προσθέτετε προγραμματιστικά
  ένα κουμπί εντολής χρησιμοποιώντας το Aspose.Words σε λίγα απλά βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: el
lastmod: 2026-09-11
og_description: Δημιουργήστε έγγραφο Word με C# και προσθέστε προγραμματιστικά ένα
  κουμπί εντολής με το Aspose.Words. Ακολουθήστε αυτόν τον πλήρη οδηγό για μια λειτουργική
  λύση.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Δημιουργία εγγράφου Word με C# – προσθήκη κουμπιού εντολής προγραμματιστικά
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: Πώς να δημιουργήσετε έγγραφο Word σε C# και να προσθέσετε προγραμματιστικά
  ένα κουμπί εντολής
url: /el/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word c# και να προσθέσετε προγραμματιστικά ένα κουμπί εντολής

Αν χρειάζεστε **create word document c#** και να ενσωματώσετε ένα διαδραστικό κουμπί, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Χρησιμοποιώντας το Aspose.Words μπορείτε προγραμματιστικά να προσθέσετε ένα κουμπί εντολής με λίγες μόνο γραμμές κώδικα, εξαλείφοντας την ανάγκη για χειροκίνητη εργασία UI στο Word.

Σε αυτό το tutorial θα μάθετε πώς να:

* Αρχικοποιήσετε ένα κενό αρχείο Word με C#.
* Εισάγετε έναν έλεγχο ActiveX **CommandButton**.
* Ορίσετε τις ιδιότητες του κουμπιού όπως όνομα και λεζάντα.
* Αποθηκεύσετε το έγγραφο ώστε το κουμπί να εμφανίζεται όταν το αρχείο ανοίξει στο Microsoft Word.

Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words for .NET, και τα βήματα λειτουργούν με .NET 6+ ή .NET Framework 4.6.2 και νεότερες εκδόσεις.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Λόγος |
|------------|--------|
| .NET 6 SDK (ή .NET Framework 4.6.2+) | Παρέχει το runtime για το έργο C#. |
| Visual Studio 2022 (ή οποιοδήποτε IDE C#) | Διευκολύνει τη συγγραφή, τη δημιουργία και την εκτέλεση του κώδικα. |
| Aspose.Words for .NET NuGet package | Παρέχει τις κλάσεις `Document`, `DocumentBuilder` και `Forms2OleControl` που χρησιμοποιούνται στο παράδειγμα. |
| Βασικές γνώσεις σύνταξης C# | Σας επιτρέπει να ακολουθήσετε τον κώδικα χωρίς πρόσθετες καμπύλες εκμάθησης. |

Μπορείτε να προσθέσετε το πακέτο Aspose.Words μέσω του NuGet console:

```powershell
Install-Package Aspose.Words
```

## Βήμα 1: Ρύθμιση νέου έργου κονσόλας C#

Δημιουργήστε μια εφαρμογή κονσόλας που θα δημιουργεί το αρχείο Word. Ανοίξτε ένα τερματικό και εκτελέστε:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Το παραγόμενο αρχείο `Program.cs` θα φιλοξενήσει τον κώδικα που εμφανίζεται στα επόμενα βήματα.

## Βήμα 2: Δημιουργία κεντού εγγράφου και DocumentBuilder

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document`, το οποίο αντιπροσωπεύει ένα κενό αρχείο `.docx`, και ενός `DocumentBuilder` που σας επιτρέπει να επεξεργαστείτε το περιεχόμενο του εγγράφου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:**  
`Document` είναι το δοχείο για όλα τα στοιχεία του Word (παράγραφοι, πίνακες, έλεγχοι). `DocumentBuilder` παρέχει ένα fluent API για την εισαγωγή αντικειμένων στην τρέχουσα θέση του δρομέα χωρίς να χρειάζεται να χειρίζεστε συλλογές κόμβων χαμηλού επιπέδου.

## Βήμα 3: Εισαγωγή ελέγχου ActiveX CommandButton

Το Aspose.Words υποστηρίζει την εισαγωγή παλαιών ελέγχων ActiveX μέσω της μεθόδου `InsertForms2OleControl`. Η μέθοδος απαιτεί τον τύπο του ελέγχου και το επιθυμητό μέγεθος σε points.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Τι συμβαίνει στο παρασκήνιο:**  
Το Word αντιμετωπίζει έναν έλεγχο ActiveX ως αντικείμενο OLE (Object Linking and Embedding). Η κλάση `Forms2OleControl` τυλίγει τα δεδομένα OLE και εκθέτει ιδιότητες όπως `Name` και `Caption`.

## Βήμα 4: Διαμόρφωση του ονόματος και της λεζάντας του κουμπιού

Αφού τοποθετηθεί ο έλεγχος, μπορείτε να προσαρμόσετε τις ιδιότητες χρόνου εκτέλεσης του. Ο ορισμός ενός περιγραφικού `Name` σας βοηθά να εντοπίζετε το κουμπί αργότερα, ενώ το `Caption` καθορίζει το κείμενο που εμφανίζεται πάνω στο κουμπί.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro tip:**  
Αν σκοπεύετε να διαχειριστείτε το γεγονός κλικ του κουμπιού με VBA, το `Name` γίνεται το όνομα της μακροεντολής που θα αναφέρετε, π.χ. `Sub btnSubmit_Click()`.

## Βήμα 5: Αποθήκευση του εγγράφου στο δίσκο

Τέλος, γράψτε το έγγραφο σε ένα αρχείο `.docx`. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής· το παράδειγμα χρησιμοποιεί σχετική διαδρομή, η οποία λύνει στο φάκελο εξόδου του έργου.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `CommandButton.docx`. Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει ένα κλικ-μεγαλύτερο κουμπί **Submit**:

![Έγγραφο Word με κουμπί εντολής Submit](/images/command-button.png "Στιγμιότυπο οθόνης ενός εγγράφου Word που περιέχει κουμπί εντολής Submit που δημιουργήθηκε με C#")

*Κείμενο alt εικόνας (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Επαλήθευση του αποτελέσματος

1. Εκκινήστε το Word και ανοίξτε το `CommandButton.docx`.  
2. Θα πρέπει να δείτε ένα κουμπί με την ετικέτα **Submit** στο σώμα του εγγράφου.  
3. Με το ποντίκι πάνω από το κουμπί εμφανίζεται το όνομα `btnSubmit` στο πάνελ **Properties** (καρτέλα Developer → Properties).  

Αν το κουμπί δεν εμφανίζεται, βεβαιωθείτε ότι η καρτέλα **Developer** είναι ενεργοποιημένη στο Word (File → Options → Customize Ribbon → τσεκάρετε *Developer*). Οι έλεγχοι ActiveX κρύβονται όταν η καρτέλα είναι απενεργοποιημένη.

## Διαχείριση κοινών παραλλαγών και ειδικών περιπτώσεων

| Κατάσταση | Προτεινόμενη προσαρμογή |
|-----------|------------------------|
| **Διαφορετικό μέγεθος κουμπιού** | Αλλάξτε τα επιχειρήματα πλάτους και ύψους στη `InsertForms2OleControl`. Για παράδειγμα, `150, 40` δημιουργεί μεγαλύτερο κουμπί. |
| **Πολλαπλά κουμπιά** | Καλέστε τη `InsertForms2OleControl` επανειλημμένα, μετακινώντας τον δρομέα του builder μεταξύ των κλήσεων (`builder.Writeln();`). |
| **Κουμπί χωρίς ActiveX** | Χρησιμοποιήστε `InsertFormField` για να προσθέσετε ένα κληροδοτημένο πεδίο φόρμας (π.χ. ένα checkbox) εάν χρειάζεστε συμβατότητα με παλαιότερες εκδόσεις του Word που αποκλείουν το ActiveX. |
| **Πλατφόρμα-διασυνοριακή χρήση** | Οι έλεγχοι ActiveX λειτουργούν μόνο σε εκδόσεις του Word για Windows. Για Mac ή web‑based προβολείς, σκεφτείτε την εισαγωγή ενός υπερσυνδέσμου μορφοποιημένου ως κουμπί. |
| **Προειδοποιήσεις ασφαλείας** | Το Word μπορεί να εμφανίσει προτροπή ασφαλείας κατά το άνοιγμα εγγράφου που περιέχει ελέγχους ActiveX. Η υπογραφή του εγγράφου με αξιόπιστο πιστοποιητικό μειώνει αυτή την τριβή. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο `Program.cs`. Συγκεντώνεται και εκτελείται χωρίς τροποποιήσεις μετά την προσθήκη του πακέτου Aspose.Words NuGet.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Το άνοιγμα του παραγόμενου αρχείου εμφανίζει το κουμπί **Submit** έτοιμο για αλληλεπίδραση.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create word document c#** και να **προγραμματιστικά προσθέσετε κουμπιά εντολής** χρησιμοποιώντας το Aspose.Words. Η διαδικασία περιορίζεται στην αρχικοποίηση ενός `Document`, την εισαγωγή ενός `Forms2OleControl`, τη διαμόρφωση των ιδιοτήτων του και την αποθήκευση του αρχείου. Από εδώ μπορείτε:

* Να προσθέσετε περισσότερους ελέγχους (π.χ. checkboxes, πεδία κειμένου) αλλάζοντας το `ControlType`.
* Να συνδέσετε μακροεντολές VBA στο κουμπί για προσαρμοσμένη λογική.
* Να συνδυάσετε αυτήν την τεχνική με άλλες δυνατότητες του Aspose.Words όπως mail merge ή συμπλήρωση προτύπων.

Πειραματιστείτε με διαφορετικά μεγέθη, λεζάντες και πολλαπλά κουμπιά για να ταιριάξουν στο σενάριο αυτοματοποίησής σας. Καλή κωδικοποίηση!

## Τι Θα Μάθετε Στη Σειρά Επόμενη;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με κεφαλίδα και υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Δημιουργία εγγράφου Word με Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}