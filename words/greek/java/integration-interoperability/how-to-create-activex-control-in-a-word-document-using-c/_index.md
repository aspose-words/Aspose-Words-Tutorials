---
category: general
date: 2026-08-20
description: Μάθετε πώς να δημιουργήσετε έναν έλεγχο ActiveX, να ορίσετε το μέγεθος
  του κουμπιού και να προσθέσετε κουμπί στο Word με ένα πλήρες παράδειγμα C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: el
lastmod: 2026-08-20
og_description: Δημιουργήστε έλεγχο ActiveX σε αρχείο Word με C#. Αυτό το σεμινάριο
  δείχνει πώς να ορίσετε το μέγεθος του κουμπιού, να προσθέσετε το κουμπί στο Word
  και να δημιουργήσετε ένα κλικ-δυνατό κουμπί.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Δημιουργήστε έναν έλεγχο ActiveX στο Word – βήμα‑βήμα οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Πώς να δημιουργήσετε έλεγχο ActiveX σε έγγραφο Word με C#
url: /el/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έλεγχο ActiveX σε έγγραφο Word χρησιμοποιώντας C#

Αν χρειάζεστε **να δημιουργήσετε έλεγχο ActiveX** μέσα σε αρχείο Microsoft Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να **προσθέσετε κουμπί στο Word**, να ορίσετε τις διαστάσεις του κουμπιού και να κάνετε τον έλεγχο κλικ‑δυνατό—όλα με ένα σύντομο, αυτόνομο πρόγραμμα C#.

Σε αυτό το tutorial θα:

* Κατανοήσετε γιατί ένας έλεγχος ActiveX είναι χρήσιμος για διαδραστικά έγγραφα Word.  
* Μάθετε τον ακριβή κώδικα που απαιτείται για **ορισμό μεγέθους κουμπιού** και ανάθεση λεζάντας.  
* Δείτε πώς να **δημιουργήσετε κλικ‑δυνατό κουμπί** που μπορεί αργότερα να συνδεθεί με μακροεντολή ή εξωτερική λογική.  

Τα βήματα λειτουργούν με Aspose.Words .NET 23.12 ή νεότερη έκδοση και απαιτούν μόνο ένα .NET περιβάλλον ανάπτυξης.

> **Προαπαιτούμενο** – Διαθέτετε έγκυρη άδεια Aspose.Words (ή χρησιμοποιείτε την έκδοση αξιολόγησης) και Visual Studio 2022 ή οποιοδήποτε IDE C#.

---

## Πώς να δημιουργήσετε έλεγχο ActiveX σε έγγραφο Word

Το πρώτο βήμα είναι να δημιουργήσετε ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder παρέχει το υψηλού επιπέδου API για την εισαγωγή αντικειμένων όπως έλεγχοι ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Η μέθοδος `InsertActiveXButton` (ορίζεται παρακάτω) περιέχει τη λογική για **πώς να εισάγετε κουμπί** και να το διαμορφώσετε.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί **ActiveXButton.docx**. Το άνοιγμα του αρχείου στο Word εμφανίζει ένα κουμπί με την ετικέτα **Submit**. Ο έλεγχος είναι πλήρως λειτουργικός—κάνοντας κλικ θα ενεργοποιηθεί το τυπικό συμβάν `CommandButton_Click`, το οποίο μπορείτε αργότερα να συνδέσετε με μια μακροεντολή VBA.

### Γιατί λειτουργεί αυτό

* `InsertForms2OleControl` λέει στο Word να ενσωματώσει ένα αντικείμενο OLE τύπου **CommandButton**, που είναι η κλασική κλάση κουμπιού ActiveX.  
* Τα επιχειρήματα πλάτους και ύψους ορίζουν άμεσα **το μέγεθος του κουμπιού**· το Word μετατρέπει τις τιμές από points (1 pt ≈ 1/72 in).  
* Η ονομασία του ελέγχου (`Name = "btnSubmit"`) το κάνει εύκολο να εντοπιστεί από VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Ορίστε το μέγεθος και τη λεζάντα του κουμπιού

Αν χρειάζεστε διαφορετική εμφάνιση, προσαρμόστε τα αριθμητικά επιχειρήματα στην κλήση `InsertForms2OleControl`. Η υπογραφή της μεθόδου είναι:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – Ο προγραμματιστικός αναγνωριστής της κλάσης ActiveX (`"CommandButton"` για ένα τυπικό κουμπί).  
* **width / height** – Μέγεθος σε points. Για κουμπί πλάτους 2 cm, χρησιμοποιήστε `width = 56.7` (2 cm ≈ 56.7 pt).  

Μπορείτε επίσης να τροποποιήσετε τη λεζάντα μετά την εισαγωγή:

```csharp
commandButton.Caption = "Send Request";
```

Η αλλαγή της λεζάντας δεν επηρεάζει το μέγεθος, αλλά επηρεάζει την οπτική ανατροφοδότηση για τον χρήστη.

### Συμβουλή επαγγελματία

Αν θέλετε τετράγωνο κουμπί, ορίστε και τις δύο διαστάσεις στην ίδια τιμή:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Προσθέστε κουμπί στο Word και κάντε το κλικ‑δυνατό

Ο παραπάνω κώδικας ήδη **προσθέτει κουμπί στο Word**. Για να κάνει το κουμπί μια ενέργεια, πρέπει να γράψετε μια μακροεντολή VBA που διαχειρίζεται το συμβάν `Click`. Ακολουθεί μια ελάχιστη μακροεντολή που μπορείτε να επικολλήσετε στον επεξεργαστή VBA του Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Επειδή ο έλεγχος ονομάζεται `btnSubmit`, το Word αυτόματα αντιστοιχίζει το συμβάν `Click` στο `btnSubmit_Click`. Αυτός είναι ο τυπικός τρόπος για **να δημιουργήσετε κλικ‑δυνατό κουμπί** χωρίς εξωτερικές βιβλιοθήκες.

> **Σημείωση:** Οι ρυθμίσεις ασφαλείας μακροεντολών στο Word μπορεί να εμποδίζουν τους ελέγχους ActiveX. Βεβαιωθείτε ότι είναι επιλεγμένο “Enable all macros” ή “Enable VBA macros” για το έγγραφο, ή υπογράψτε ψηφιακά τη μακροεντολή για παραγωγική χρήση.

---

## Συχνές ερωτήσεις: πώς να εισάγετε κουμπί και αντιμετώπιση προβλημάτων

### 1. Τι γίνεται αν το κουμπί δεν εμφανίζεται μετά την αποθήκευση;

* Επαληθεύστε ότι η έκδοση του Aspose.Words υποστηρίζει το `InsertForms2OleControl`. Εκδόσεις πριν από το 22.5 δεν διαθέτουν αυτή τη δυνατότητα.  
* Βεβαιωθείτε ότι η μορφή αρχείου προορισμού είναι `.docx` ή `.doc`. Παλαιότερες μορφές όπως `.rtf` δεν μπορούν να αποθηκεύσουν αντικείμενα ActiveX.

### 2. Μπορώ να εισάγω το κουμπί σε συγκεκριμένο σελιδοδείκτη;

Ναι. Μετακινήστε τον builder στον σελιδοδείκτη πριν καλέσετε το `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Πώς να **ορίσετε το μέγεθος του κουμπιού** δυναμικά βάσει του μήκους του κειμένου;

Υπολογίστε το απαιτούμενο πλάτος χρησιμοποιώντας τη μέθοδο `Graphics.MeasureString` (από το `System.Drawing`) και μετατρέψτε τα pixel σε points (`points = pixels * 72 / DPI`). Στη συνέχεια περάστε το υπολογισμένο πλάτος στο `InsertForms2OleControl`.

### 4. Υπάρχει τρόπος να προσθέσετε πολλαπλά κουμπιά σε βρόχο;

Απολύτως. Τυλίξτε τη λογική εισαγωγής μέσα σε βρόχο `for` και προσαρμόστε τις ιδιότητες `Left` και `Top` για κάθε επανάληψη:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Αναμενόμενο αποτέλεσμα

Όταν εκτελέσετε το πρόγραμμα και ανοίξετε **ActiveXButton.docx**:

* Εμφανίζεται ένα μόνο **Submit** κουμπί κοντά στην πάνω‑αριστερή γωνία της πρώτης σελίδας.  
* Το μέγεθος του κουμπιού ταιριάζει με τις διαστάσεις που δώσατε (`100 pt × 30 pt`).  
* Αν προσθέσατε τη μακροεντολή VBA, το κλικ στο κουμπί εμφανίζει ένα παράθυρο μηνύματος: “You clicked the Submit button!”.

Έχετε πλέον δημιουργήσει επιτυχώς **έλεγχο ActiveX**, **ορίσει το μέγεθος του κουμπιού** και **προσθέσει κουμπί στο Word**, ενώ μάθατε επίσης **πώς να εισάγετε κουμπί** και **να δημιουργήσετε κλικ‑δυνατό κουμπί** για μελλοντικές εργασίες αυτοματοποίησης.

---

## Συμπέρασμα

Σε αυτό το tutorial μάθατε πώς να **δημιουργήσετε έλεγχο ActiveX** μέσα σε έγγραφο Word με C#. Ακολουθώντας τα βήματα μπορείτε να **ορίσετε το μέγεθος του κουμπιού**, να δώσετε στον έλεγχο ένα σημασιολογικό όνομα και να **προσθέσετε κουμπί στο Word** ώστε να γίνει ένα **κλικ‑δυνατό κουμπί** συνδεδεμένο με μακροεντολή VBA.  

Από εδώ μπορείτε να εξερευνήσετε:

* Σύνδεση του κουμπιού με ένα .NET COM add‑in αντί για VBA.  
* Χρήση άλλων κλάσεων ActiveX όπως `CheckBox` ή `ComboBox`.  
* Αυτοματοποίηση της δημιουργίας πλήρων φορμών με πολλαπλούς ελέγχους.

Αισθανθείτε ελεύθεροι να πειραματιστείτε με διαφορετικά μεγέθη


## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με αιωρούμενη εικόνα σε .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Δημιουργία εγγράφου Word με κεφαλίδα και υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Δημιουργία προσβάσιμου PDF από Word – Πλήρης οδηγός](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}