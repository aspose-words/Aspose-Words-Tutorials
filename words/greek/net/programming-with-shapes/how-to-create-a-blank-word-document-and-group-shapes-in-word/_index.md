---
category: general
date: 2026-10-20
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word, να ομαδοποιήσετε σχήματα
  στο Word, να ορίσετε το χρώμα γεμίσματος του σχήματος και να χρησιμοποιήσετε τον
  τύπο περιτύλιξης inline με ένα πλήρες παράδειγμα C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: el
lastmod: 2026-10-20
og_description: Δημιουργήστε ένα κενό έγγραφο Word, ομαδοποιήστε σχήματα στο Word
  και ορίστε το χρώμα γεμίσματος του σχήματος με τύπο αναδίπλωσης ενσωματωμένο χρησιμοποιώντας
  το Aspose.Words και τη C#. Ακολουθήστε το πλήρες σεμινάριο.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Δημιουργήστε ένα κενό έγγραφο Word και ομαδοποιήστε σχήματα στο Word – οδηγός
  βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να ομαδοποιήσετε σχήματα στο
  Word χρησιμοποιώντας το Aspose.Words
url: /el/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να ομαδοποιήσετε σχήματα στο Word

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word** που περιέχει πολλαπλά σχήματα που λειτουργούν ως μία ενιαία μονάδα, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε πώς να **ομαδοποιήσετε σχήματα στο Word**, να ορίσετε το χρώμα γεμίσματος ενός σχήματος και να εφαρμόσετε **wrap type inline**—όλα με ένα σύντομο, εκτελέσιμο πρόγραμμα C#.

Ο οδηγός περνάει βήμα‑βήμα από κάθε γραμμή κώδικα, εξηγεί γιατί κάθε βήμα είναι σημαντικό και επισημαίνει κοινά λάθη. Στο τέλος θα έχετε ένα αρχείο .docx που εμφανίζει ένα ορθογώνιο και ένα πλαίσιο κειμένου ομαδοποιημένα μαζί, έτοιμα για περαιτέρω αυτοματοποίηση.

## Τι θα μάθετε

* Πώς να αρχικοποιήσετε ένα κενό αρχείο Word με το Aspose.Words.
* Ο σωστός τρόπος δημιουργίας ενός **GroupShape** και προσθήκης παιδικών σχημάτων.
* Τεχνικές για **set shape fill color** και έλεγχο τοποθέτησης.
* Χρήση του **wrap type inline** ώστε η ομάδα να συμπεριφέρεται ως ένα ενιαίο inline αντικείμενο.
* Πώς να αποθηκεύσετε και να επαληθεύσετε το αποτέλεσμα.

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose.Words, αλλά θα πρέπει να είστε εξοικειωμένοι με τη βασική σύνταξη C# και να έχετε εγκατεστημένο το Visual Studio (ή άλλο IDE).

## Προαπαιτούμενα

| Απαίτηση | Λόγος |
|----------|-------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για το έργο C#. |
| Aspose.Words for .NET (τελευταία έκδοση) | Παρέχει τις κλάσεις `Document`, `DocumentBuilder` και shape που χρησιμοποιούνται στο παράδειγμα. |
| Διαδρομή φακέλου με δικαιώματα εγγραφής | Η κλήση `doc.Save` χρειάζεται έναν έγκυρο φάκελο για να γράψει το αρχείο εξόδου. |
| Βασικές γνώσεις C# | Σας επιτρέπει να ακολουθήσετε τον κώδικα και να τον τροποποιήσετε για τις δικές σας περιπτώσεις. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Βήμα 1: Δημιουργία κενού εγγράφου Word

Η πρώτη ενέργεια είναι να **δημιουργήσετε ένα κενό έγγραφο Word**. Η κλάση `Document` του Aspose.Words αντιπροσωπεύει ένα Word αρχείο στη μνήμη, και το `DocumentBuilder` παρέχει ένα βολικό API για την επεξεργασία του.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: Η έναρξη με ένα καθαρό έγγραφο εγγυάται ότι το group shape που προσθέτετε θα είναι το μοναδικό περιεχόμενο, κάνοντας την επαλήθευση απλή.

## Βήμα 2: Ορισμός group shape με wrap type inline

Ένα **GroupShape** λειτουργεί ως κοντέινερ για άλλα σχήματα. Ορίζοντας το `WrapType` του σε `Inline` διασφαλίζουμε ότι η ομάδα συμπεριφέρεται ως ένα ενιαίο inline αντικείμενο στη ροή της παραγράφου.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Γιατί είναι σημαντικό*: Η χρήση του **wrap type inline** αποτρέπει την ομάδα από το να «πλέει» μακριά από το περιβάλλον κείμενο, κάτι που είναι απαραίτητο όταν θέλετε η ομάδα να κινείται ως μονάδα.

## Βήμα 3: Προσθήκη ορθογωνίου και ορισμός χρώματος γεμίσματος σχήματος

Το ορθογώνιο είναι ένα συχνό οπτικό στοιχείο. Ο κατασκευαστής `Shape` δέχεται ένα `ShapeType`; στη συνέχεια καθορίζουμε διαστάσεις και χρώμα γεμίσματος.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Γιατί είναι σημαντικό*: Η ιδιότητα `FillColor` δείχνει στην πράξη το **set shape fill color**, δίνοντας στο ορθογώνιο ένα ανοιχτό‑μπλε φόντο που ξεχωρίζει στο τελικό έγγραφο.

## Βήμα 4: Προσθήκη πλαισίου κειμένου – πώς να ομαδοποιήσετε σχήματα αποτελεσματικά

Ένα πλαίσιο κειμένου παρέχει επεξεργάσιμο κείμενο μέσα στην ομάδα. Το τοποθετείτε σχετικά με το σύστημα συντεταγμένων της ομάδας ρυθμίζοντας την ιδιότητα `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Γιατί είναι σημαντικό*: Αυτό το βήμα απαντά στο **how to group shapes**—με την προσθήκη κάθε παιδικού σχήματος στην ίδια παρουσία `GroupShape`. Η μετατόπιση `Top` εξασφαλίζει ότι το πλαίσιο κειμένου εμφανίζεται κάτω από το ορθογώνιο, δείχνοντας ακριβή έλεγχο διάταξης.

## Βήμα 5: Εισαγωγή του ολοκληρωμένου group shape στο έγγραφο

Τώρα που η ομάδα περιέχει και τα δύο παιδικά σχήματα, την εισάγουμε στη τρέχουσα θέση του builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Γιατί είναι σημαντικό*: Η εισαγωγή της ομάδας ως ενιαίου κόμβου εγγυάται ότι το Word αντιμετωπίζει το ορθογώνιο και το πλαίσιο κειμένου ως ένα λογικό αντικείμενο, διατηρώντας τις σχετικές τους θέσεις κατά την επεξεργασία.

## Βήμα 6: Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Τέλος, γράφουμε το έγγραφο στο δίσκο. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή στο σύστημά σας.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Όταν ανοίξετε το `GroupShape.docx` στο Microsoft Word, θα πρέπει να δείτε ένα ανοιχτό‑μπλε ορθογώνιο με ένα πλαίσιο κειμένου που φέρει την ετικέτα “Grouped text” τοποθετημένο ακριβώς κάτω από αυτό. Η επιλογή οποιουδήποτε σχήματος θα επιλέξει ολόκληρη την ομάδα, επιβεβαιώνοντας ότι **group shapes in Word** λειτουργεί όπως προβλέπεται.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο .docx που περιέχει μία παράγραφο.
* Μέσα στην παράγραφο, μια inline ομάδα που φαίνεται ως ένα ενιαίο σύνθετο αντικείμενο.
* Το ορθογώνιο είναι γεμάτο με ανοιχτό μπλε και το πλαίσιο κειμένου εμφανίζει το κείμενο “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Στιγμιότυπο του παραγόμενου εγγράφου Word με ορθογώνιο και πλαίσιο κειμένου ομαδοποιημένα, δημιουργημένα με το Aspose.Words"}

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

### Τι γίνεται αν χρειαστεί η ομάδα να «πλέει» αντί να είναι inline;

Αντικαταστήστε το `WrapType.Inline` με `WrapType.TopBottom` (ή οποιαδήποτε άλλη τιμή του enum `WrapType`). Οι ομάδες που «πλέουν» μπορούν να τοποθετηθούν ανεξάρτητα από τη ροή της παραγράφου, αλλά χάνουν την αυτόματη ευθυγράμμιση inline.

### Μπορώ να προσθέσω περισσότερα σχήματα, όπως κύκλους ή εικόνες;

Ναι. Δημιουργήστε επιπλέον αντικείμενα `Shape` με `ShapeType.Ellipse` ή `ShapeType.Image`, ρυθμίστε τις ιδιότητές τους και καλέστε `group.AppendChild(newShape)`. Η ομάδα θα επεκταθεί αυτόματα για να φιλοξενήσει τα νέα όρια εάν ενημερώσετε το `group.Bounds` αναλόγως.

### Πώς αλλάζω το συνολικό μέγεθος της ομάδας μετά την προσθήκη παιδιών;

Ρυθμίστε το `group.Bounds` αφού προστεθούν όλα τα παιδικά σχήματα, ή υπολογίστε προγραμματιστικά την ένωση των ορίων των παιδιών. Αυτό διασφαλίζει ότι η περιοχή hit‑test της ομάδας ταιριάζει με το οπτικό περιεχόμενο.

### Τι γίνεται αν ο φάκελος εξόδου δεν υπάρχει;

Το Aspose.Words ρίχνει μια `DirectoryNotFoundException`. Δημιουργήστε πρώτα τον φάκελο:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Λειτουργεί αυτό με .NET Framework αντί για .NET Core;

Όλες οι χρησιμοποιημένες API (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) είναι διαθέσιμες στην έκδοση .NET Framework του Aspose.Words, οπότε ο ίδιος κώδικας λειτουργεί αμετάβλητος.

## Pro tips

* **Performance tip** – Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` όταν εισάγετε πολλές ομάδες· η δημιουργία νέου builder ανά ομάδα προσθέτει επιβάρυνση.
* **Visual consistency** – Ορίστε το `rectangle.StrokeColor` ώστε να ταιριάζει με το `FillColor` για ομοιόμορφη εμφάνιση, ή ορίστε `rectangle.LineWidth = 0` για να κρύψετε το περίγραμμα.
* **Debugging** – Καλέστε το `doc.UpdatePageLayout()` πριν την αποθήκευση εάν τροποποιείτε πολλά σχήματα· αυτό αναγκάζει το Word να επανυπολογίσει τη διάταξη και μπορεί να αποτρέψει απρόσμενο αποκοπή.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **ομαδοποιήσετε σχήματα στο Word**, **ορίσετε χρώμα γεμίσματος σχήματος** και να εφαρμόσετε **wrap type inline** χρησιμοποιώντας το Aspose.Words για .NET. Το πλήρες παράδειγμα δείχνει την τυπική προσέγγιση για τη δημιουργία σύνθετων γραφικών που συμπεριφέρονται ως ένα ενιαίο αντικείμενο στο Word.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη επιπλέον σχημάτων όπως εικόνες ή διαγράμματα.
* Πειραματισμό με διαφορετικές τιμές `WrapType` για ομάδες που «πλέουν».
* Αυτοματοποίηση μαζικής δημιουργίας ομαδοποιημένων διαγραμμάτων σε πολλά έγγραφα.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα στις δικές σας περιπτώσεις αυτοματοποίησης και να μοιραστείτε τα αποτελέσματά σας στα σχόλια!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}