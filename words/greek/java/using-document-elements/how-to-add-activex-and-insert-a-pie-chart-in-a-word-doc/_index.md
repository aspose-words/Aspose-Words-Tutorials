---
category: general
date: 2026-08-17
description: Πώς να προσθέσετε ελέγχους ActiveX και να εισαγάγετε ένα διάγραμμα πίτας
  σε έγγραφο Word χρησιμοποιώντας το Aspose.Words. Αποσπάστε ένα τμήμα και αποθηκεύστε
  το ως DOCX σε λίγα βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: el
lastmod: 2026-08-17
og_description: Πώς να προσθέσετε ελέγχους ActiveX, να εισάγετε διάγραμμα πίτας, να
  εκτοξεύσετε ένα κομμάτι και να αποθηκεύσετε ως DOCX με το Aspose.Words – πλήρης
  οδηγός βήμα‑προς‑βήμα.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Πώς να προσθέσετε ActiveX και να εισάγετε διάγραμμα πίτας σε ένα έγγραφο
  Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Πώς να προσθέσετε ActiveX και να εισάγετε ένα διάγραμμα πίτας σε ένα έγγραφο
  Word
url: /el/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε ActiveX και να εισάγετε ένα γράφημα πίτας σε έγγραφο Word

Αν χρειάζεστε **how to add ActiveX** ελέγχους και να ενσωματώσετε ένα γράφημα σε έγγραφο Word, αυτό το tutorial σας δείχνει μια πλήρη, εκτελέσιμη λύση. Χρησιμοποιώντας το Aspose.Words μπορείτε να τοποθετήσετε ένα ActiveX CommandButton, να δημιουργήσετε ένα γράφημα πίτας, να «ξεσπάσετε» ένα τμήμα για έμφαση, και τελικά **save as DOCX** με λίγες γραμμές C#.

Στις παρακάτω ενότητες θα δείτε όλες τις απαιτούμενες εισαγωγές, μια πλήρη λίστα κώδικα και εξηγήσεις για το γιατί κάθε βήμα είναι σημαντικό. Στο τέλος θα μπορείτε να ενσωματώσετε διαδραστικούς ελέγχους και οπτικά δεδομένα σε οποιοδήποτε αρχείο .docx που δημιουργείτε προγραμματιστικά.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Πακέτο Aspose.Words for .NET (διαθέσιμο μέσω NuGet)
* Περιβάλλον ανάπτυξης όπως το Visual Studio 2022 ή το VS Code
* Βασική εξοικείωση με C# και το Word object model

Δεν απαιτούνται πρόσθετες βιβλιοθήκες γραφημάτων τρίτων—το Aspose.Words παρέχει ενσωματωμένη δημιουργία γραφημάτων.

## Πώς να προσθέσετε ελέγχους ActiveX με το Aspose.Words

Οι έλεγχοι ActiveX σας επιτρέπουν να ενσωματώσετε διαδραστικά στοιχεία UI απευθείας σε αρχείο Word. Σε αυτόν τον οδηγό προσθέτουμε ένα **CommandButton** που μπορεί αργότερα να συνδεθεί με κώδικα VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Γιατί λειτουργεί αυτό:**  
`InsertForms2OleControl` δημιουργεί ένα κοντέινερ OLE που το UI του Word αναγνωρίζει ως έλεγχο ActiveX. Ορίζοντας τον τύπο ελέγχου σε `CommandButton` και δίνοντάς του μια λεζάντα, συμπεριφέρεται ως τυπικό κουμπί όταν ο χρήστης ανοίγει το αρχείο στο Word.

## Εισαγωγή γραφήματος πίτας και «ξεσπάσιμο» τμήματος

Τα γραφήματα είναι χρήσιμα για την οπτικοποίηση δεδομένων χωρίς να αφήνετε το έγγραφο. Τα παρακάτω βήματα δείχνουν **how to insert chart** και συγκεκριμένα ένα **pie chart** του οποίου το πρώτο τμήμα είναι «ξεσπασμένο».

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Γιατί να «ξεσπάσετε» το τμήμα:**  
Καλώντας το `SetExplode(0, true)` λέτε στο Aspose.Words να μετατοπίσει το πρώτο σημείο δεδομένων, προσελκύοντας το βλέμμα του θεατή σε αυτό το τμήμα. Αυτή είναι μια κοινή τεχνική σε παρουσιάσεις για να τονίσει μια σημαντική τιμή.

## Αποθήκευση ως DOCX

Αφού προσθέσετε το κουμπί ActiveX και το γράφημα, αποθηκεύστε το έγγραφο στο δίσκο. Αυτό το βήμα δείχνει **save as DOCX** χρησιμοποιώντας τη στάνταρ μέθοδο.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Το αρχείο `Output.docx` τώρα περιέχει ένα διαδραστικό κουμπί, ένα γράφημα πίτας με «ξεσπασμένο» τμήμα, και μπορεί να ανοιχτεί στο Microsoft Word χωρίς πρόσθετα plugins.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα, εδώ είναι ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε σε μια εφαρμογή κονσόλας και να το εκτελέσετε αμέσως.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Ανοίγοντας το `Output.docx` στο Word εμφανίζεται ένα κουμπί με την ετικέτα *Click Me* και ένα γράφημα πίτας όπου το πρώτο τμήμα (January) είναι μετατοπισμένο από τα υπόλοιπα. Το κουμπί είναι έτοιμο για διαχείριση συμβάντων VBA, και το γράφημα μπορεί να επεξεργαστεί χρησιμοποιώντας τα ενσωματωμένα εργαλεία γραφημάτων του Word.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

* **Μπορώ να προσθέσω άλλους τύπους ActiveX;**  
  Ναι. Αντικαταστήστε το `Forms2OleControlType.CommandButton` με οποιαδήποτε τιμή από το enum `Forms2OleControlType` (π.χ., `CheckBox`, `OptionButton`). Η ίδια διαδικασία εισαγωγής ισχύει.

* **Τι γίνεται αν χρειάζομαι διαφορετικό τύπο γραφήματος;**  
  Χρησιμοποιήστε `ChartType.Bar`, `ChartType.Line`, κλπ., στην κλήση `InsertChart`. Το βήμα **how to insert chart** παραμένει ίδιο· μόνο η τιμή του enum αλλάζει.

* **Πώς να ελέγξετε το μέγεθος του «ξεσπασμένου» τμήματος;**  
  Το Aspose.Words αυτή τη στιγμή υποστηρίζει μια δυαδική σημαία explode (true/false). Για πιο ακριβή έλεγχο (π.χ., απόσταση μετατόπισης) θα πρέπει να επεξεργαστείτε το υποκείμενο OOXML μετά την αποθήκευση.

* **Είναι το έγγραφο συμβατό με παλαιότερες εκδόσεις του Word;**  
  Η αποθήκευση ως DOCX εξασφαλίζει συμβατότητα με Word 2007 και μεταγενέστερα. Για Word 2003 μπορείτε να αλλάξετε σε `SaveFormat.Doc`, αλλά η υποστήριξη ActiveX είναι περιορισμένη σε αυτή τη μορφή.

* **Χρειάζεται να αναφερθώ στο `System.Drawing`;**  
  Όχι. Όλα τα αντικείμενα σχεδίασης παρέχονται από το Aspose.Words, έτσι το μόνο απαιτούμενο πακέτο NuGet είναι το `Aspose.Words`.

## Συμπέρασμα

Τώρα ξέρετε **how to add ActiveX**, **insert a pie chart**, **explode a pie slice**, και **save as DOCX** χρησιμοποιώντας το Aspose.Words για .NET. Το πλήρες παράδειγμα καλύπτει κάθε βήμα από τη δημιουργία του εγγράφου μέχρι την τελική αποθήκευση, και εξηγεί τη λογική πίσω από κάθε κλήση API.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη μακροεντολών VBA που ανταποκρίνονται στο κλικ του CommandButton (**how to insert chart** και αυτοματοποίηση ενημερώσεων δεδομένων)
* Προσαρμογή εμφάνισης γραφήματος (χρώματα, ετικέτες δεδομένων) ώστε να ταιριάζει με το εταιρικό branding
* Ενσωμάτωση επιπλέον ελέγχων ActiveX όπως **ComboBox** ή **ListBox** για πιο πλούσιες φόρμες

Μη διστάσετε να πειραματιστείτε με τον κώδικα, να αντικαταστήσετε τα δείγμα δεδομένων, και να ενσωματώσετε τη λύση στις δικές σας διαδικασίες δημιουργίας εγγράφων. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή γραφήματος στήλης σε Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Εισαγωγή απλού γραφήματος στήλης σε Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Εισαγωγή γραφήματος φυσαλίδων σε Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}