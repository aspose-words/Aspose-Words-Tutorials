---
category: general
date: 2026-11-22
description: Προγραμματιστικά δημιουργήστε ένα έγγραφο Word σε C# και εισάγετε σχήμα
  ορθογωνίου, εισάγετε πολλαπλά σχήματα και γράψτε τα σχήματα στο Word χρησιμοποιώντας
  το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: el
lastmod: 2026-11-22
og_description: Δημιουργία εγγράφου Word προγραμματιστικά σε C# με εισαγωγή σχήματος
  ορθογωνίου, εισαγωγή πολλαπλών σχημάτων και εγγραφή των σχημάτων στο Word χρησιμοποιώντας
  το Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Δημιουργία εγγράφου Word με σχήματα προγραμματιστικά σε C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Προγραμματιστική δημιουργία εγγράφου Word με σχήματα σε C#
url: /el/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά με σχήματα σε C#

Αν χρειάζεστε **να δημιουργήσετε προγραμματιστικά ένα έγγραφο Word** που περιέχει προσαρμοσμένα γραφικά, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words for .NET. Θα μάθετε να εισάγετε ένα σχήμα ορθογωνίου, να προσθέσετε επιπλέον σχήματα, να τα ομαδοποιήσετε και τελικά να γράψετε τα σχήματα στο Word—όλα σε λίγες γραμμές C#.

Η δημιουργία ενός αρχείου Word με γραφικά δεν απαιτεί πλέον χειροκίνητη επεξεργασία ή μακροεντολές. Στο τέλος αυτού του οδηγού θα έχετε μια επαναχρησιμοποιήσιμη μέθοδο που παράγει ένα αρχείο `.docx` που περιέχει ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί, έτοιμα για επεξεργασία ή αναφορά.

## Τι θα χρειαστείτε

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)
- Ένα IDE όπως το Visual Studio 2022 (οποιοσδήποτε επεξεργαστής που μπορεί να μεταγλωττίσει C# είναι εντάξει)

> **Συμβουλή:** Εγκαταστήστε το πακέτο με την εντολή CLI `dotnet add package Aspose.Words` πριν ξεκινήσετε τον κώδικα.

## Δημιουργία εγγράφου Word προγραμματιστικά – επισκόπηση

Η συνολική ροή αποτελείται από τρία λογικά στάδια:

1. **Initialize** ένα νέο `Document` και ένα `DocumentBuilder`.  
2. **Insert multiple shapes** (ένα ορθογώνιο και μια έλλειψη) και τοποθετήστε τα μέσα σε ένα `GroupShape`.  
3. **Write shapes to Word** αποθηκεύοντας το `Document` σε αρχείο `.docx`.

Κάθε στάδιο είναι ενσωματωμένο σε ένα αφιερωμένο βήμα παρακάτω, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε τον κώδικα απευθείας στο έργο σας.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Δημιουργία εγγράφου Word προγραμματιστικά με ομαδοποιημένα σχήματα"}

## Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` παρέχει μια fluent API για την προσθήκη περιεχομένου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί είναι σημαντικό:* Η δημιουργία του `Document` πρώτα σας δίνει έναν καθαρό καμβά. Το `DocumentBuilder` παρακολουθεί το τρέχον σημείο εισαγωγής, κάτι που είναι ουσιώδες όταν αργότερα συνδέετε σχήματα σε μια ιεραρχία παραγράφων.

## Βήμα 2: Εισαγωγή ενός container ομαδικού σχήματος

Ένα `GroupShape` σας επιτρέπει να αντιμετωπίζετε πολλά μεμονωμένα σχήματα ως μία ενιαία μονάδα. Αυτό είναι χρήσιμο όταν θέλετε να τα μετακινήσετε ή να αλλάξετε το μέγεθός τους μαζί.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Εξήγηση:* Η `InsertGroupShape` εισάγει ένα κενό container και το ορίζει αυτόματα ως το τρέχον σχήμα. Όλες οι επόμενες εισαγωγές σχημάτων θα προστεθούν σε αυτό το container μέχρι να κλείσετε την ομάδα.

## Εισαγωγή σχήματος ορθογωνίου

Τώρα προσθέτουμε το πρώτο γραφικό—ένα ορθογώνιο. Αυτό ικανοποιεί την απαίτηση **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Το ορθογώνιο κληρονομεί το πλαίσιο μορφοποίησης της ομάδας, έτσι εμφανίζεται μέσα στο `GroupShape`. Μπορείτε επίσης να ορίσετε χρώμα γραμμής, γέμισμα ή κείμενο αργότερα αν χρειαστεί.

## Εισαγωγή πολλαπλών σχημάτων

Για να δείξουμε τη δυνατότητα **insert multiple shapes**, προσθέτουμε μια έλλειψη αμέσως μετά το ορθογώνιο. Μπορείτε να συνεχίσετε να προσθέτετε όποιον αριθμό σχημάτων (π.χ. τρίγωνα, αστέρια) πριν κλείσετε την ομάδα.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Σε αυτό το σημείο η ομάδα περιέχει δύο διακριτά σχήματα: ένα ορθογώνιο και μια έλλειψη. Επειδή μοιράζονται τον ίδιο γονέα, μπορείτε να τα μετακινήσετε ως ενιαία μονάδα.

## Βήμα 3: Συγκόλληση του ομαδικού σχήματος στην ιεραρχία παραγράφων

Τα έγγραφα Word αποθηκεύουν το περιεχόμενο σε ένα δέντρο παραγράφων. Για να γίνει η ομάδα ορατή στο τελικό αρχείο, πρέπει να την συνδέσουμε με την τρέχουσα παράγραφο.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Γιατί απαιτείται αυτό το βήμα:* Χωρίς την προσθήκη της ομάδας σε μια παράγραφο, τα σχήματα υπάρχουν μόνο στη μνήμη και παραλείπονται όταν αποθηκευτεί το έγγραφο.

## Βήμα 4: Αποθήκευση του εγγράφου – εγγραφή σχημάτων στο Word

Τέλος, αποθηκεύουμε το `Document` που βρίσκεται στη μνήμη στο δίσκο. Αυτό εκπληρώνει τον στόχο **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `GroupShape.docx` στο Microsoft Word, θα δείτε ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί, ακριβώς όπως εισήχθη από τον κώδικα.

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο με όνομα **GroupShape.docx** τοποθετημένο στο φάκελο εξόδου του έργου.
- Μέσα στο αρχείο Word: μια ενιαία παράγραφος που περιέχει ένα ομαδοποιημένο ορθογώνιο (100 pt × 50 pt) και μια έλλειψη (80 pt × 40 pt). Η επιλογή οποιουδήποτε σχήματος επιλέγει ολόκληρη την ομάδα.

## Διαχείριση κοινών περιπτώσεων άκρων

| Κατάσταση | Σύσταση |
|-----------|----------|
| **Διαφορετικό DPI ή μέγεθος σελίδας** | Ορίστε ρητά `builder.PageSetup.PaperSize` πριν την εισαγωγή σχημάτων για να αποφύγετε απρόσμενη κλιμάκωση. |
| **Ανάγκη ακριβούς τοποθέτησης σχημάτων** | Χρησιμοποιήστε `builder.MoveTo` για να μετακινήσετε το σημείο εισαγωγής, έπειτα ορίστε τις ιδιότητες `groupShape.Left` και `groupShape.Top` (οι τιμές είναι σε points). |

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word – Εισαγωγή Σχήματος Ορθογωνίου & Σκιά σε C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Δημιουργία εγγράφου Word προγραμματιστικά και ομαδοποίηση σχημάτων σε C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Δημιουργία εγγράφου Word προγραμματιστικά με ομαδικό σχήμα](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}