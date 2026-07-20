---
category: general
date: 2026-07-19
description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να προσθέσετε σχήμα ορθογωνίου, να ορίσετε σχήμα έλλειψης και να εισάγετε σχήμα
  σε έγγραφα Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: el
lastmod: 2026-07-19
og_description: Ομαδοποίηση σχημάτων στο Word με το Aspose.Words. Δημιουργία προσθήκης
  σχήματος ορθογωνίου, ορισμός σχήματος έλλειψης και εισαγωγή σχήματος σε έγγραφα
  Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Ομαδοποίηση Σχημάτων στο Word – Βήμα‑βήμα Εγχειρίδιο C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Ομαδοποίηση Σχημάτων στο Word με το Aspose.Words – Πλήρης Οδηγός C#
url: /el/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ομαδοποίηση Σχημάτων στο Word – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **ομαδοποιήσετε σχήματα στο Word** χωρίς να παίζετε με το UI; Δεν είστε μόνοι. Είτε δημιουργείτε συμβόλαια, φυλλάδια ή διαγράμματα προγραμματιστικά, η δυνατότητα **προσθήκης ορθογώνιου σχήματος**, **ορισμού ελλειπτικού σχήματος** και στη συνέχεια **ομαδοποίησης σχημάτων στο Word** μπορεί να σας εξοικονομήσει ώρες χειροκίνητης εργασίας.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα χρησιμοποιώντας **Aspose.Words for .NET**. Στο τέλος θα ξέρετε ακριβώς πώς να **εισάγετε σχήμα στο Word**, να τα συνδυάσετε και να δημιουργήσετε ένα επαγγελματικό έγγραφο που μπορείτε να στείλετε σε πελάτες ή συνεργάτες.

---

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα εξής:

- **Aspose.Words for .NET** (τελευταία έκδοση, π.χ. 24.9). Μπορείτε να το κατεβάσετε από το NuGet με `Install-Package Aspose.Words`.
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio 2022 ή VS Code με την επέκταση C# λειτουργούν άψογα).
- Βασική εξοικείωση με τη σύνταξη C#—τίποτα περίπλοκο, μόνο οι συνήθεις δηλώσεις `using` και η δημιουργία αντικειμένων.

Αυτό είναι όλο. Καμία πρόσθετη βιβλιοθήκη, καμία COM διασύνδεση, μόνο καθαρός διαχειριζόμενος κώδικας.

---

## Πώς να Ομαδοποιήσετε Σχήματα στο Word Χρησιμοποιώντας Aspose.Words

Παρακάτω υπάρχει μια βήμα‑βήμα ανάλυση που αντικατοπτρίζει τον κώδικα που ήδη έχετε. Κάθε βήμα εξηγεί **γιατί** το κάνουμε, όχι μόνο **τι** κάνει η γραμμή, ώστε να μπορείτε να προσαρμόσετε το μοτίβο σε οποιοδήποτε σχήμα θέλετε.

### Βήμα 1: Ρύθμιση Εγγράφου και Builder

Ξεκινάμε δημιουργώντας ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder είναι το «μολύβι» μας που μας επιτρέπει να εισάγουμε περιεχόμενο όπου το χρειαζόμαστε.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Γιατί;** Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει ένα βολικό API για την εισαγωγή κόμβων (όπως σχήματα) χωρίς να ασχολείστε με το υποκείμενο δέντρο κόμβων.

### Βήμα 2: Προσθήκη Ορθογώνιου Σχήματος (add rectangle shape)

Τώρα **προσθέτουμε ορθογώνιο σχήμα** στο έγγραφο. Ορίζουμε το μέγεθος, τη θέση και το χρώμα γεμίσματος ώστε να ξεχωρίζει.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Συμβουλή:** Μπορείτε να αλλάξετε το `FillColor` σε οποιοδήποτε `System.Drawing.Color` προτιμάτε. Αυτό είναι χρήσιμο όταν χρειάζεστε τμηματικές ενότητες με χρωματική κωδικοποίηση σε μια αναφορά.

### Βήμα 3: Ορισμός Ελλειπτικού Σχήματος (define ellipse shape)

Στη συνέχεια, **ορίζουμε ελλειπτικό σχήμα**. Παρατηρήστε τον διαφορετικό `ShapeType` και την μετατόπιση (`Left = 120`) ώστε το έλλειπτο να βρίσκεται δίπλα στο ορθογώνιο.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Γιατί είναι σημαντικό:** Με την ρητή τοποθέτηση των σχημάτων, ελέγχετε πώς εμφανίζονται πριν τα ομαδοποιήσετε. Αν βασιστείτε σε αυτόματο layout, η ομαδοποίηση μπορεί να φαίνεται εκτός κέντρου.

### Βήμα 4: (Προαιρετικό) Εισαγωγή Ατομικών Σχημάτων για Προεπισκόπηση

Αν θέλετε να δείτε κάθε σχήμα πριν το ομαδοποιήσετε, μπορείτε **να εισάγετε σχήμα στο Word** ξεχωριστά. Αυτό το βήμα είναι προαιρετικό αλλά χρήσιμο για εντοπισμό σφαλμάτων.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Σχολιάστε αυτές τις δύο γραμμές μόλις είστε σίγουροι ότι τα σχήματα φαίνονται σωστά· διαφορετικά θα καταλήξετε με διπλότυπες εικόνες μετά την ομαδοποίηση.

### Βήμα 5: Πώς να Ομαδοποιήσετε Σχήματα – Δημιουργία GroupShape

Εδώ είναι ο πυρήνας του tutorial: **πώς να ομαδοποιήσετε σχήματα**. Δημιουργούμε ένα `GroupShape`, προσθέτουμε το ορθογώνιο και το έλλειπτο, και αποφασίζουμε πώς η ομάδα θα συμπεριφέρεται με το κείμενο γύρω της.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Εξήγηση:** Το `GroupShape` είναι ουσιαστικά ένας μικρός καμβάς που κρατά άλλα σχήματα. Ορίζοντας το `WrapType` σε `Inline`, ολόκληρη η ομάδα κινείται ως ενιαία μονάδα όταν προσθέτετε ή διαγράφετε κείμενο.

### Βήμα 6: Εισαγωγή του Ομαδοποιημένου Σχήματος στο Έγγραφο (insert shape into word)

Τώρα **εισάγουμε σχήμα στο Word**—αλλά αυτή τη φορά είναι το ομαδοποιημένο κοντέινερ, όχι τα μεμονωμένα κομμάτια.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Τι συμβαίνει στο παρασκήνιο;** Η κλήση `InsertNode` προσθέτει το `GroupShape` στη συλλογή κόμβων του εγγράφου. Επειδή η ομάδα περιέχει ήδη το ορθογώνιο και το έλλειπτο, εμφανίζονται μαζί ως ένα αντικείμενο.

### Βήμα 7: Αποθήκευση του Εγγράφου

Τέλος, γράφουμε το αρχείο στο δίσκο. Μπορείτε να αλλάξετε τη διαδρομή ώστε να ταιριάζει με τη δομή του έργου σας.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Αποτέλεσμα:** Ανοίξτε το `GroupShape.docx` στο Microsoft Word και θα δείτε ένα ανοιχτό-μπλε ορθογώνιο και ένα κοραλί έλλειπτο δεμένα μαζί. Η μετακίνηση του ενός μετακινεί και το άλλο—ακριβώς αυτό που υπόσχεται η «ομαδοποίηση σχημάτων στο word».

---

## Οπτική Επιβεβαίωση

Παρακάτω είναι μια προσομοίωση του πώς φαίνονται τα ομαδοποιημένα σχήματα μέσα στο αρχείο Word.  

![Στιγμιότυπο ομαδοποιημένων σχημάτων σε έγγραφο Word που δημιουργήθηκε με Aspose.Words](grouped_shapes_placeholder.png "ομαδοποίηση σχημάτων στο word")

*Το κείμενο alt της εικόνας περιέχει τη βασική λέξη‑κλειδί για προσβασιμότητα και SEO.*

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειαστώ περισσότερα από δύο σχήματα;

Απλώς συνεχίστε να καλείτε `groupShape.AppendChild(yourNewShape);` πριν εισάγετε την ομάδα. Το API δεν επιβάλλει όριο στον αριθμό των παιδικών σχημάτων.

### Μπορώ να περιστρέψω ή να αλλάξω το μέγεθος ολόκληρης της ομάδας;

Απόλυτα. Το `GroupShape` κληρονομεί από το `Shape`, οπότε μπορείτε να ορίσετε ιδιότητες όπως `RotationAngle`, `Width` ή `Height` στην ίδια την ομάδα, και όλα τα παιδικά σχήματα θα ακολουθήσουν.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Πώς αλλάζω το χρώμα φόντου της ομάδας;

Χρησιμοποιήστε `groupShape.FillColor`. Αυτό γεμίζει το αόρατο πλαίσιο περιβάλλοντος· μπορεί να είναι χρήσιμο για επισήμανση.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Λειτουργεί αυτό με παλαιότερες μορφές Word (.doc);

Το `Aspose.Words` μπορεί επίσης να αποθηκεύσει σε `.doc`—απλώς αντικαταστήστε την επέκταση αρχείου στην κλήση `Save`. Ωστόσο, ορισμένα προχωρημένα χαρακτηριστικά σχήματος (όπως η ομαδοποίηση) υποστηρίζονται πλήρως μόνο στη μορφή OOXML `.docx`.

---

## Πλήρες Παράδειγμα Εργασίας

Αντιγράψτε‑και‑επικολλήστε το παρακάτω μπλοκ σε μια νέα εφαρμογή console για να δείτε όλη τη διαδικασία σε δράση. Δεν λείπουν κομμάτια· αυτό είναι ένα **πλήρες, εκτελέσιμο παράδειγμα**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν ανοίξετε το `GroupShape.docx`, θα δείτε ένα ενιαίο ομαδοποιημένο αντικείμενο που αποτελείται από ένα ανοιχτό‑μπλε ορθογώνιο και ένα ανοιχτό‑κοραλί έλλειπτο, ευθυγραμμισμένα τέλεια πλάι‑πλάι.

---

## Ανακεφαλαίωση

Καλύψαμε όλα όσα χρειάζεστε για να **ομαδοποιήσετε σχήματα στο Word** με το Aspose.Words:

1. Δημιουργήστε έγγραφο και builder.  
2. **Προσθέστε ορθογώνιο σχήμα** και **ορίστε ελλειπτικό σχήμα** με ρητές διαστάσεις.  
3. (Προαιρετικά) **εισάγετε σχήμα στο Word** για γρήγορη προεπισκόπηση.  
4. Χρησιμοποιήστε `GroupShape` για **πώς να ομαδοποιήσετε σχήματα**—προσθέστε κάθε παιδί, ορίστε την αναδίπλωση και εισάγετε.  
5. Αποθηκεύστε το αρχείο και επαληθεύστε το.

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}