---
category: general
date: 2026-07-23
description: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε σχήμα ορθογωνίου σε
  C#. Μάθετε πώς να εισάγετε σχήματα και να ομαδοποιείτε σχήματα στο Word χρησιμοποιώντας
  το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: el
lastmod: 2026-07-23
og_description: Δημιουργήστε κενό έγγραφο Word σε C# και μάθετε πώς να εισάγετε σχήματα,
  να προσθέσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word με το Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένα ορθογώνια – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένα ορθογώνια – Οδηγός C#
url: /el/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word με ομαδοποιημένα ορθογώνια – Οδηγός C#

Έχετε χρειαστεί ποτέ να **δημιουργήσετε κενό έγγραφο Word** που ήδη περιέχει ένα σύνολο σχημάτων, αλλά δεν ήσασταν σίγουροι πώς να τα ομαδοποιήσετε όμορφα; Δεν είστε ο μόνος. Σε πολλές περιπτώσεις αναφοράς ή δημιουργίας προτύπων θέλετε έναν καθαρό καμβά με μερικά ορθογώνια που λειτουργούν ως σύμβολα κράτησης θέσης, και θα θέλατε να μετακινούνται μαζί ως μία μονάδα.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για **δημιουργία κενής εγγράφου Word**, **προσθήκη σχήματος ορθογωνίου**, και στη συνέχεια **ομαδοποίηση σχημάτων Word** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words. Στο τέλος θα έχετε ένα έτοιμο προς χρήση αρχείο `.docx` όπου τα δύο ορθογώνια είναι μέρος μιας ομάδας, ώστε οποιαδήποτε μετακίνηση ή αλλαγή μεγέθους να επηρεάζει και τα δύο ταυτόχρονα.  

Θα απαντήσουμε επίσης στις συχνές ερωτήσεις «**πώς να εισαγάγετε σχήματα**» και «**πώς να ομαδοποιήσετε σχήματα**» που εμφανίζονται σε φόρουμ και στο Stack Overflow. Δεν απαιτούνται εξωτερικά έγγραφα — όλα όσα χρειάζεστε είναι εδώ.

---

## Προαπαιτούμενα

- .NET 6 ή νεότερο (ο κώδικας μεταγλωττίζεται και με .NET Core)  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)  
- Βασική κατανόηση της σύνταξης C# (αν έχετε γράψει ένα “Hello World”, είστε έτοιμοι)  

Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Αυτό είναι όλο — χωρίς επιπλέον DLL, χωρίς COM interop, μόνο μια καθαρή αναφορά NuGet.

---

## Βήμα 1: Δημιουργία κενής εγγράφου Word και αρχικοποίηση του builder

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα κενό αντικείμενο `Document`. Σκεφτείτε το ως ένα φρέσκο φύλλο χαρτί. Στη συνέχεια συνδέουμε ένα `DocumentBuilder`, το πρακτικό εργαλείο που παρέχει η Aspose για την εισαγωγή περιεχομένου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Γιατί είναι σημαντικό:** Χωρίς ένα `DocumentBuilder` θα έπρεπε να χειριστείτε το δέντρο κόμβων χαμηλού επιπέδου χειροκίνητα, κάτι που είναι επιρρεπές σε σφάλματα. Ο builder αφαιρεί τις πολυπλοκότητες του XML ενός αρχείου `.docx`.

---

## Βήμα 2: Πώς να εισαγάγετε σχήματα – προσθέστε πρώτα ένα κοντέινερ ομάδας

Η Aspose σας επιτρέπει να εισάγετε ένα *group shape* που μπορεί αργότερα να φιλοξενήσει άλλα σχήματα. Αυτό αποτελεί τη βάση για **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro tip:** Η ομάδα είναι αόρατη μέχρι να προσθέσετε παιδικά σχήματα, οπότε δεν θα δείτε κανένα αποτύπωμα στο τελικό έγγραφο μέχρι το επόμενο βήμα.

---

## Βήμα 3: Προσθήκη σχήματος ορθογωνίου – τα πραγματικά ορατά αντικείμενα

Τώρα θα **προσθέσουμε σχήμα ορθογωνίου** δύο φορές, το καθένα με το δικό του μέγεθος. Η μέθοδος `InsertShape` δέχεται ένα `ShapeType` και διαστάσεις σε points (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Γιατί ορθογώνια;** Είναι το πιο απλό γεωμετρικό σχήμα, ιδανικό για σύμβολα κράτησης θέσης, mock UI τύπου κουμπιού ή απλά γραφικά στοιχεία.

---

## Βήμα 4: Πώς να ομαδοποιήσετε σχήματα – συνδέστε τα ορθογώνια στην ομάδα

Με τα ορθογώνια δημιουργημένα, τώρα **πώς να ομαδοποιήσετε σχήματα** προσθέτοντάς τα ως παιδιά του group shape που εισάγαμε νωρίτερα.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Τι συμβαίνει στο παρασκήνιο;** Το group shape γίνεται ο γονικός κόμβος στο XML δέντρο του εγγράφου. Η μετακίνηση της ομάδας μετακινεί και τα δύο ορθογώνια μαζί, διατηρώντας τις σχετικές τους θέσεις.

---

## Βήμα 5: Αποθήκευση του εγγράφου – έχετε τώρα ένα αρχείο Word με ομαδοποιημένα σχήματα

Τέλος, αποθηκεύουμε το έγγραφο στο δίσκο. Αλλάξτε τη διαδρομή σε μια τοποθεσία που υπάρχει στον υπολογιστή σας.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Αυτό είναι όλο το πρόγραμμα. Εκτελέστε το, ανοίξτε το `GroupShape.docx` και θα δείτε δύο ορθογώνια να κάθονται μαζί. Αν επιλέξετε ένα, ολόκληρη η ομάδα επισημαίνεται — ακριβώς αυτό που πρέπει να κάνει το **group shapes word**.

---

## Πλήρης κώδικας σε ένα μέρος

Για ευκολία, εδώ είναι το πλήρες, έτοιμο για αντιγραφή παράδειγμα:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `GroupShape.docx` εμφανίζει μια κενή σελίδα με δύο ορθογώνια ομαδοποιημένα μαζί. Η επιλογή ενός ορθογωνίου επιλέγει αυτόματα και το άλλο, επιβεβαιώνοντας ότι η ομαδοποίηση πέτυχε.

---

## Συχνές ερωτήσεις & αντιμετώπιση ειδικών περιπτώσεων

### Τι γίνεται αν χρειάζομαι περισσότερα από δύο σχήματα;

Απλώς συνεχίστε να καλείτε `builder.InsertShape(...)` και `group.AppendChild(...)` για κάθε νέο σχήμα. Η ομάδα μπορεί να περιέχει οποιονδήποτε αριθμό παιδιών.

### Μπορώ να ορίσω χρώμα γεμίσματος ή περιθώριο στα ορθογώνια;

Απόλυτα. Μετά τη δημιουργία ενός ορθογωνίου μπορείτε να ρυθμίσετε το `FillColor`, `OutlineColor` και `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Πώς μετακινώ ολόκληρη την ομάδα μετά τη δημιουργία της;

Χρησιμοποιήστε τις ιδιότητες `Left` και `Top` της ομάδας, μετρημένες σε points:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Τι γίνεται με την κλιμάκωση της ομάδας;

Ορίστε `group.Width` και `group.Height` ή χρησιμοποιήστε `group.ScaleX` / `group.ScaleY`. Τα παιδικά ορθογώνια διατηρούν τις αναλογίες τους σε σχέση με την ομάδα.

### Λειτουργεί αυτό με παλαιότερα αρχεία .doc;

Η Aspose.Words αφαιρεί τις λεπτομέρειες του φορμάτ, έτσι ο ίδιος κώδικας λειτουργεί για `.doc` και `.docx`. Ο μόνος περιορισμός είναι ότι ορισμένα νεότερα χαρακτηριστικά σχήματος μπορεί να υποβαθμιστούν κατά την αποθήκευση σε παλαιότερη δυαδική μορφή.

---

## Συμβουλές για κώδικα έτοιμο για παραγωγή

- **Dispose of resources** – Τυλίξτε το `Document` σε ένα `using` block αν εργάζεστε με μεγάλα αρχεία για να ελευθερώσετε μνήμη άμεσα.  
- **Error handling** – Πιάστε `Aspose.Words.Fonts.FontSettingsException` αν σκοπεύετε να ενσωματώσετε προσαρμοσμένες γραμματοσειρές.  
- **Performance** – Όταν εισάγετε πολλά σχήματα, απενεργοποιήστε προσωρινά τις ενημερώσεις διάταξης με `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` και ενεργοποιήστε ξανά μετά.

---

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να δημιουργήσετε κενό έγγραφο Word**, **πώς να προσθέσετε σχήμα ορθογωνίου**, και **πώς να ομαδοποιήσετε σχήματα Word** χρησιμοποιώντας το Aspose.Words σε C#. Το παράδειγμα καλύπτει τα βασικά βήματα «**πώς να εισαγάγετε σχήματα**» και «**πώς να ομαδοποιήσετε σχήματα**», εξηγεί γιατί υπάρχει κάθε γραμμή κώδικα, και αγγίζει προσαρμογές, ειδικές περιπτώσεις και βέλτιστες πρακτικές.

Στη συνέχεια, μπορείτε να εξερευνήσετε **πώς να εισάγετε εικόνες**, **πώς να προσθέσετε κείμενο μέσα σε ομαδοποιημένα σχήματα**, ή **πώς να εξάγετε το έγγραφο σε PDF** — όλα ακολουθούν το ίδιο μοτίβο χρήσης του `DocumentBuilder` και της διαχείρισης σχημάτων. Συνεχίστε να πειραματίζεστε· το Aspose API είναι τόσο πλούσιο που μπορεί να χειριστεί σχεδόν κάθε σενάριο αυτοματοποίησης του Word που μπορείτε να φανταστείτε.

Καλή προγραμματιστική δουλειά, και μη διστάσετε να αφήσετε ένα σχόλιο αν συναντήσετε κάποιο πρόβλημα!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}