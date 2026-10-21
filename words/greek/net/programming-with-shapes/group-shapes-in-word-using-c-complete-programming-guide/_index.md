---
category: general
date: 2026-10-13
description: Ομαδοποίηση σχημάτων στο Word με C# – μάθετε πώς να ομαδοποιείτε σχήματα
  και να προσθέτετε σχήματα σε ομάδα χρησιμοποιώντας το Aspose.Words σε λίγα εύκολα
  βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: el
lastmod: 2026-10-13
og_description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας C# και Aspose.Words.
  Ακολουθήστε αυτόν τον οδηγό για να μάθετε πώς να ομαδοποιείτε σχήματα και να προσθέτετε
  σχήματα σε ομάδα σε ένα έγγραφο Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Ομαδοποίηση σχημάτων στο Word με C# – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Ομαδοποίηση σχημάτων στο Word με χρήση C# – πλήρης οδηγός προγραμματισμού
url: /el/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ομαδοποίηση σχημάτων στο Word με C# – πλήρης προγραμματιστικός οδηγός

Αν χρειάζεστε **ομαδοποίηση σχημάτων στο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Μέχρι το τέλος των πρώτων δύο προτάσεων θα γνωρίζετε τον απαιτούμενο κώδικα, τη λογική πίσω από κάθε βήμα και πώς να **προσθέσετε σχήματα σε ομάδα** χωρίς εκπλήξεις.

Θα καλύψουμε τα πάντα, από τη φόρτωση ενός αρχείου `.docx` μέχρι την αποθήκευση του ενημερωμένου εγγράφου. Το tutorial υποθέτει ότι έχετε βασικές γνώσεις C# και μια αναφορά στη βιβλιοθήκη Aspose.Words for .NET. Δεν απαιτείται εξωτερική τεκμηρίωση—απλώς αντιγράψτε, επικολλήστε και τρέξτε.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Ένα έγγραφο Word (`input.docx`) που περιέχει ήδη τουλάχιστον δύο σχήματα (π.χ. εικόνες, AutoShapes)

> **Pro tip:** Αν κάνετε δοκιμές, δημιουργήστε ένα απλό αρχείο Word με δύο ορθογώνια μέσω του UI του Word. Αποθηκεύστε το ως `input.docx` σε φάκελο που ελέγχετε.

## Ομαδοποίηση σχημάτων στο Word – οδηγός βήμα‑βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε πέντε λογικά βήματα. Κάθε βήμα περιλαμβάνει τον ακριβή κώδικα C#, εξήγηση του *γιατί* χρειάζεται η γραμμή, και μια σύντομη σημείωση για κοινά προβλήματα.

### Βήμα 1: Φόρτωση του εγγράφου Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Γιατί:** Η `Document` είναι το σημείο εισόδου για οποιαδήποτε επεξεργασία Word. Παρέχοντας το πλήρες μονοπάτι αρχείου φορτώνει το έγγραφο στη μνήμη, επιτρέποντάς μας να ερωτήσουμε και να τροποποιήσουμε το δέντρο κόμβων του.

**Πιθανό πρόβλημα:** Η χρήση σχετικού μονοπατιού μπορεί να αποτύχει όταν ο τρέχων φάκελος εργασίας διαφέρει. Χρησιμοποιήστε απόλυτο μονοπάτι ή `Path.Combine` με `AppContext.BaseDirectory`.

### Βήμα 2: Ανάκτηση των σχημάτων που θέλετε να ομαδοποιήσετε

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Γιατί:** Η `GetChild` διασχίζει το δέντρο του εγγράφου και επιστρέφει τον *n‑ο* κόμβο του ζητούμενου τύπου. Ορίζοντας `isDeep` σε `true` γίνεται αναζήτηση σε όλο το έγγραφο, όχι μόνο στην τρέχουσα ενότητα.

**Ακραία περίπτωση:** Αν το έγγραφο περιέχει λιγότερα από δύο σχήματα, το `firstShape` ή το `secondShape` θα είναι `null` και θα προκληθεί εξαίρεση όταν προσπαθήσουμε να κάνουμε cast. Προστατέψτε τον κώδικα:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Βήμα 3: Δημιουργία νέου κοντέινερ `GroupShape`

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Γιατί:** Η `GroupShape` λειτουργεί ως γονικός κόμβος που μπορεί να κρατήσει πολλαπλά αντικείμενα `Shape`. Κληρονομεί από την `Shape`, οπότε μπορεί να εισαχθεί οπουδήποτε επιτρέπεται ένα κανονικό σχήμα (π.χ. μέσα σε παράγραφο).

### Βήμα 4: Προσθήκη των μεμονωμένων σχημάτων στην ομάδα

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Γιατί:** Η `AppendChild` μετακινεί τα σχήματα από τις αρχικές τους θέσεις στο νέο group. Μετά από αυτήν την κλήση, τα αρχικά σχήματα δεν υπάρχουν πια ως ανεξάρτητοι κόμβοι· γίνονται μέρος του `groupShape`.

**Συμβουλή:** Η ομαδοποίηση ρυθμίζει αυτόματα τις σχετικές θέσεις των παιδικών σχημάτων. Αν χρειάζεστε συγκεκριμένη διάταξη, ορίστε την ιδιότητα `GroupShape.Bounds` *πριν* προσθέσετε τα παιδιά.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Βήμα 5: Εισαγωγή του group shape στο σώμα του εγγράφου

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Γιατί:** Ένα `GroupShape` πρέπει να τοποθετηθεί μέσα σε παράγραφο (ή κελί πίνακα) για να αποδοθεί. Προσθέτοντάς το στην πρώτη παράγραφο εξασφαλίζουμε ορατή τοποθέτηση χωρίς να διαταράξουμε την υπάρχουσα διάταξη.

### Βήμα 6: Αποθήκευση του τροποποιημένου εγγράφου

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Γιατί:** Η `Save` γράφει τις αλλαγές στη μνήμη πίσω σε αρχείο `.docx`. Μπορείτε επίσης να αποθηκεύσετε σε ροή ή σε PDF αλλάζοντας το overload.

**Επαλήθευση αποτελέσματος:** Ανοίξτε το `output.docx` στο Microsoft Word. Θα δείτε τα δύο αρχικά σχήματα τώρα συνδυασμένα σε ένα ενιαίο ομαδοποιημένο αντικείμενο. Επιλέγοντας την ομάδα θα εμφανιστούν τα τυπικά χειριστήρια ομαδοποίησης του Word.

## Πώς να ομαδοποιήσετε σχήματα προγραμματιστικά – βαθύτερες γνώσεις

- **Ιδιοκτησία κόμβου:** Όταν καλείτε την `AppendChild`, η αναφορά `ParentNode` του σχήματος αλλάζει αυτόματα. Αυτό αποτρέπει «ορφανά» κόμβους που θα μπορούσαν να καταστρέψουν το έγγραφο.
- **Διατήρηση μορφοποίησης:** Η ομαδοποίηση **δεν** χάνει καμία μορφοποίηση σχήματος (χρώμα γεμίσματος, στυλ γραμμής κ.λπ.). Όλα τα παιδικά σχήματα διατηρούν τις αρχικές τους ιδιότητες.
- **Φωλιασμένες ομάδες:** Η `GroupShape` μπορεί να περιέχει άλλα αντικείμενα `GroupShape`, επιτρέποντας ιεραρχίες πολλαπλών επιπέδων. Απλώς αντιμετωπίστε την εσωτερική ομάδα όπως κάθε άλλο σχήμα.

## Προσθήκη σχημάτων στην ομάδα και διαχείριση τους αργότερα

Αν χρειαστεί να προσθέσετε περισσότερα σχήματα μετά τη δημιουργία της αρχικής ομάδας, μπορείτε να επαναχρησιμοποιήσετε το ίδιο αντικείμενο `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Όταν αργότερα χρειαστεί να αποομαδοποιήσετε, επαναλάβετε πάνω από `groupShape.GetChildNodes(NodeType.Shape, true)` και ξαναεισάγετε κάθε παιδί εκεί που θέλετε.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Γιατί είναι σημαντικό:** Ορισμένες ροές εργασίας απαιτούν προσωρινή ομαδοποίηση (π.χ. στοίχιση πολλαπλών αντικειμένων) ακολουθούμενη από αποομαδοποίηση για περαιτέρω ατομικές επεξεργασίες.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να μεταγλωττίσετε και να τρέξετε όπως είναι. Αντικαταστήστε το `YOUR_DIRECTORY` με το πραγματικό μονοπάτι φακέλου στο σύστημά σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν ανοίξετε το `output.docx`, τα δύο αρχικά σχήματα εμφανίζονται ως ένα ενιαίο ομαδοποιημένο αντικείμενο. Επιλέγοντας την ομάδα θα δείτε τα γνωστά χειριστήρια ομαδοποίησης του Word, επιτρέποντάς σας να μετακινήσετε, να αλλάξετε μέγεθος ή να περιστρέψετε ολόκληρο το σύνολο μαζί.

## Συμπέρασμα

Τώρα ξέρετε πώς να **ομαδοποιήσετε σχήματα στο Word** χρησιμοποιώντας C# και Aspose.Words, και έχετε δει τα ακριβή βήματα για **προσθήκη σχημάτων σε ομάδα** και μετέπειτα διαχείριση ή αποομαδοποίησή τους. Αυτή η τεχνική είναι ιδανική για αυτοματοποίηση διατάξεων αναφορών, δημιουργία σύνθετων διαγραμμάτων ή προετοιμασία προτύπων Word που απαιτούν ακριβή τοποθέτηση πολλαπλών αντικειμένων.

Στη συνέχεια, εξερευνήστε σχετικές θεματικές όπως **πώς να ομαδοποιήσετε σχήματα** με διαφορετικούς τύπους αγκύρωσης, εφαρμογή **προηγμένης μορφοποίησης** σε ομαδοποιημένα αντικείμενα, ή εξαγωγή του ομαδοποιημένου αποτελέσματος σε PDF. Πειραματιστείτε με φωλιασμένες ομάδες για να δημιουργήσετε πολύπλογα γραφικά προγραμματιστικά.

Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}