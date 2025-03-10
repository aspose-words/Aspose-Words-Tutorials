---
title: Χρήση αντικειμένων OLE και στοιχείων ελέγχου ActiveX στο Aspose.Words για Java
linktitle: Χρήση αντικειμένων OLE και στοιχείων ελέγχου ActiveX
second_title: Aspose.Words Java Document Processing API
description: Μάθετε να χρησιμοποιείτε αντικείμενα OLE και στοιχεία ελέγχου ActiveX στο Aspose.Words για Java. Δημιουργήστε διαδραστικά έγγραφα με ευκολία. Ξεκινήστε τώρα!
weight: 21
url: /el/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση αντικειμένων OLE και στοιχείων ελέγχου ActiveX στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο εργασίας με αντικείμενα OLE (Σύνδεση και ενσωμάτωση αντικειμένων) και στοιχεία ελέγχου ActiveX στο Aspose.Words για Java. Τα αντικείμενα OLE και τα στοιχεία ελέγχου ActiveX είναι ισχυρά εργαλεία που σας επιτρέπουν να βελτιώσετε τα έγγραφά σας ενσωματώνοντας ή συνδέοντας εξωτερικό περιεχόμενο, όπως υπολογιστικά φύλλα, αρχεία πολυμέσων ή διαδραστικά στοιχεία ελέγχου. Ακολουθήστε καθώς εμβαθύνουμε στα παραδείγματα κώδικα και μάθετε πώς να χρησιμοποιείτε αποτελεσματικά αυτές τις δυνατότητες.

### Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

1.  Aspose.Words για Java: Βεβαιωθείτε ότι έχετε εγκαταστήσει τη βιβλιοθήκη Aspose.Words στο έργο σας Java. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/).

2. Περιβάλλον ανάπτυξης Java : Θα πρέπει να έχετε ρυθμίσει ένα λειτουργικό περιβάλλον ανάπτυξης Java στο σύστημά σας.

### Εισαγωγή αντικειμένου OLE

Ας ξεκινήσουμε με την εισαγωγή ενός αντικειμένου OLE σε ένα έγγραφο του Word. Θα δημιουργήσουμε ένα απλό έγγραφο του Word και στη συνέχεια θα εισαγάγουμε ένα αντικείμενο OLE που αντιπροσωπεύει μια ιστοσελίδα.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Σε αυτόν τον κώδικα, δημιουργούμε ένα νέο έγγραφο και εισάγουμε ένα αντικείμενο OLE που εμφανίζει τον ιστότοπο Aspose. Μπορείτε να αντικαταστήσετε τη διεύθυνση URL με το επιθυμητό περιεχόμενο.

### Εισαγωγή αντικειμένου OLE με OlePackage

Στη συνέχεια, ας εξερευνήσουμε πώς να εισαγάγετε ένα αντικείμενο OLE χρησιμοποιώντας ένα OlePackage. Αυτό σας επιτρέπει να ενσωματώσετε εξωτερικά αρχεία ως αντικείμενα OLE στο έγγραφό σας.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

Σε αυτό το παράδειγμα, εισάγουμε ένα αντικείμενο OLE χρησιμοποιώντας ένα OlePackage, επιτρέποντάς σας να συμπεριλάβετε εξωτερικά αρχεία ως ενσωματωμένα αντικείμενα.

### Εισαγωγή αντικειμένου OLE ως εικονίδιο

Τώρα, ας δούμε πώς να εισαγάγετε ένα αντικείμενο OLE ως εικονίδιο. Αυτό είναι χρήσιμο όταν θέλετε να εμφανίσετε ένα εικονίδιο που αντιπροσωπεύει ένα ενσωματωμένο αρχείο.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

Σε αυτόν τον κώδικα, εισάγουμε ένα αντικείμενο OLE ως εικονίδιο, παρέχοντας μια πιο ελκυστική οπτικά αναπαράσταση του ενσωματωμένου περιεχομένου.

### Ανάγνωση ιδιοτήτων ελέγχου ActiveX

Τώρα, ας εστιάσουμε στα στοιχεία ελέγχου ActiveX. Θα μάθουμε πώς να διαβάζουμε τις ιδιότητες των στοιχείων ελέγχου ActiveX σε ένα έγγραφο του Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

Σε αυτόν τον κώδικα, επαναλαμβάνουμε τα σχήματα σε ένα έγγραφο του Word, αναγνωρίζουμε στοιχεία ελέγχου ActiveX και ανακτούμε τις ιδιότητές τους.

### Σύναψη

Συγχαρητήρια! Έχετε μάθει πώς να εργάζεστε με αντικείμενα OLE και στοιχεία ελέγχου ActiveX στο Aspose.Words για Java. Αυτές οι δυνατότητες ανοίγουν έναν κόσμο δυνατοτήτων για τη δημιουργία δυναμικών και διαδραστικών εγγράφων.

### Συχνές ερωτήσεις

### Ποιος είναι ο σκοπός των αντικειμένων OLE σε ένα έγγραφο του Word; 
   - Τα αντικείμενα OLE σάς επιτρέπουν να ενσωματώνετε ή να συνδέετε εξωτερικό περιεχόμενο, όπως αρχεία ή ιστοσελίδες, μέσα σε ένα έγγραφο του Word.

### Μπορώ να προσαρμόσω την εμφάνιση των αντικειμένων OLE στο έγγραφό μου; 
   - Ναι, μπορείτε να προσαρμόσετε την εμφάνιση των αντικειμένων OLE, συμπεριλαμβανομένων των εικονιδίων ρυθμίσεων και των ονομάτων αρχείων.

### Τι είναι τα στοιχεία ελέγχου ActiveX και πώς μπορούν να βελτιώσουν τα έγγραφά μου; 
   - Τα στοιχεία ελέγχου ActiveX είναι διαδραστικά στοιχεία που μπορούν να προσθέσουν λειτουργικότητα στα έγγραφα του Word, όπως στοιχεία ελέγχου φορμών ή προγράμματα αναπαραγωγής πολυμέσων.

### Είναι το Aspose.Words για Java κατάλληλο για αυτοματοποίηση εγγράφων σε επίπεδο επιχείρησης; 
   - Ναι, το Aspose.Words για Java είναι μια ισχυρή βιβλιοθήκη για την αυτοματοποίηση της δημιουργίας και χειρισμού εγγράφων σε εφαρμογές Java.

### Πού μπορώ να αποκτήσω πρόσβαση στο Aspose.Words για Java; 
   -  Μπορείτε να κάνετε λήψη του Aspose.Words για Java από[εδώ](https://releases.aspose.com/words/java/).

Ξεκινήστε με το Aspose.Words για Java σήμερα και ξεκλειδώστε όλες τις δυνατότητες αυτοματισμού και προσαρμογής εγγράφων!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
