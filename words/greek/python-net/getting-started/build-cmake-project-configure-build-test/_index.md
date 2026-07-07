---
category: general
date: 2026-07-06
description: Κατασκευάστε το έργο CMake βήμα‑βήμα. Μάθετε πώς να ρυθμίζετε το CMake,
  πώς να το χτίζετε και πώς να εκτελείτε το CTest για αξιόπιστες δοκιμές.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: el
og_description: Δομήστε γρήγορα ένα έργο CMake με σαφή βήματα. Αυτός ο οδηγός δείχνει
  πώς να ρυθμίσετε το CMake, πώς να το δημιουργήσετε και πώς να εκτελέσετε το CTest.
og_title: 'Δημιουργία έργου CMake: Οδηγός διαμόρφωσης, κατασκευής και δοκιμής'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'Δημιουργία έργου CMake: Διαμόρφωση, Κατασκευή & Δοκιμή'
url: /el/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία έργου CMake: Διαμόρφωση, Κατασκευή & Δοκιμή

Έχετε αναρωτηθεί ποτέ πώς να **build CMake project** χωρίς να περνάτε ώρες ψάχνοντας στο StackOverflow; Δεν είστε μόνοι. Οι περισσότεροι προγραμματιστές αντιμετωπίζουν το ίδιο πρόβλημα όταν προσπαθούν να μεταβούν από ένα απλό `CMakeLists.txt` σε μια επαναλήψιμη αλυσίδα κατασκευής. 

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία—*how to configure CMake*, *how to build CMake*, και *how to run CTest*—ώστε να καταλήξετε με μια καθαρή, επαναλήψιμη κατασκευή που μπορείτε να τρέξετε σε οποιοδήποτε μηχάνημα. Στο τέλος θα έχετε ένα λειτουργικό παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο δικό σας αποθετήριο, χωρίς επιπλέον scripts.

## Προαπαιτούμενα — Τι χρειάζεστε πριν ξεκινήσετε

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε:

- Μια πρόσφατη έκδοση του CMake (3.20 ή νεότερη) – οι παλαιότερες εκδόσεις λείπουν κάποιες από τις σημαίες που θα χρησιμοποιήσουμε.
- Έναν μεταγλωττιστή C++ που υποστηρίζεται από την πλατφόρμα σας (gcc, clang, MSVC, κλπ).
- Ένα τερματικό ή command‑prompt με πρόσβαση στα `cmake` και `ctest`.
- (Προαιρετικά) Git για κλωνοποίηση του παραδείγματος αποθετηρίου αν θέλετε να ακολουθήσετε ακριβώς τον κώδικα.

Αν κάποιο από αυτά λείπει, αποκτήστε το τώρα· διαφορετικά θα αντιμετωπίσετε σφάλματα “command not found” αργότερα, και αυτό δεν είναι ευχάριστο.

## Βήμα 1: Διαμόρφωση του έργου CMake (Διαμόρφωση Release)

Το πρώτο πράγμα που κάνετε όταν *how to configure CMake* είναι να πείτε στο CMake πού βρίσκεται η πηγή και πού θέλετε να τοποθετηθούν τα artefacts της κατασκευής. Η σημαία `-S` δείχνει τον φάκελο πηγής, το `-B` δημιουργεί έναν ξεχωριστό φάκελο κατασκευής, και το `-D CMAKE_BUILD_TYPE=Release` εξαναγκάζει μια βελτιστοποιημένη κατασκευή.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Γιατί είναι σημαντικό:** Η διατήρηση των αρχείων πηγής και κατασκευής ξεχωριστά (`out‑of‑source` builds) αποτρέπει τυχαίες τροποποιήσεις της πηγής και καθιστά εύκολο τον καθαρισμό του φακέλου κατασκευής αργότερα. Η σημαία `Release` επίσης λέει στον μεταγλωττιστή να ενεργοποιήσει βελτιστοποιήσεις, κάτι που συνήθως θέλετε για ένα τελικό binary.

> **Pro tip:** Αν χρειάζεστε μια Debug κατασκευή για εντοπισμό σφαλμάτων, απλώς αντικαταστήστε το `Release` με `Debug`. Η ίδια εντολή λειτουργεί—το CMake διαχειρίζεται τα υπόλοιπα.

## Βήμα 2: Κατασκευή του διαμορφωμένου έργου

Τώρα που το βήμα διαμόρφωσης έχει δημιουργήσει όλα τα απαραίτητα makefiles ή αρχεία έργου Visual Studio, μπορείτε πραγματικά να μεταγλωττίσετε τον κώδικα. Η επιλογή `--build` αφαιρεί την εξάρτηση από το υποκείμενο εργαλείο κατασκευής (`make`, `ninja`, `MSBuild`, κλπ), έτσι η ίδια εντολή λειτουργεί σε Linux, macOS και Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Τι συμβαίνει στο παρασκήνιο;** Το CMake διαβάζει το `CMakeCache.txt` που δημιουργήθηκε στο προηγούμενο βήμα, καθορίζει το κατάλληλο εργαλείο κατασκευής και το εκτελεί με τις σωστές σημαίες. Αυτό είναι το βασικό μέρος του *how to build CMake*—δεν χρειάζεται να θυμάστε αν χρησιμοποιείτε `make` ή `ninja`; το CMake το κάνει για εσάς.

Αν θέλετε να επιταχύνετε σε μηχανές πολλαπλών πυρήνων, προσθέστε `-- -j$(nproc)` (Linux/macOS) ή `-- /m` (Windows) μετά την εντολή:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Βήμα 3: Εκτέλεση των παραδειγματικών δοκιμών με λεπτομερή έξοδο

Η δοκιμή είναι το σημείο όπου το λαστιχένιο συναντά το δρόμο. Το CMake περιλαμβάνει το `ctest`, ένα πρόγραμμα εκτέλεσης δοκιμών που μπορεί να ανακαλύψει και να τρέξει οποιαδήποτε δοκιμή προστέθηκε μέσω `add_test()` στο `CMakeLists.txt`. Για να εκτελέσετε τις δοκιμές και να δείτε λεπτομερή έξοδο, χρησιμοποιήστε το βοηθητικό `-E chdir` για να μεταβείτε πρώτα στον φάκελο κατασκευής:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Γιατί να χρησιμοποιήσετε `--verbose`;** Εκτυπώνει τη γραμμή εντολής κάθε δοκιμής, τον κωδικό εξόδου και οποιαδήποτε έξοδο γράφει η ίδια η δοκιμή. Αυτό είναι ουσιώδες όταν μαθαίνετε *how to run CTest* επειδή δείχνει ακριβώς τι συμβαίνει στο παρασκήνιο.

Τυπική έξοδος μοιάζει με αυτή:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Αν μια δοκιμή αποτύχει, το verbose log θα περιλαμβάνει την αποτυχημένη εντολή και τυχόν μηνύματα σφάλματος, κάνοντας το debugging πολύ πιο γρήγορο.

## Βήμα 4: Αυτοματοποίηση ολόκληρης της ροής εργασίας (Προαιρετικό)

Για πολλά έργα θα θέλετε μια εντολή‑μιας γραμμής που διαμορφώνει, κατασκευάζει και δοκιμάζει σε ένα βήμα. Μπορείτε να το πετύχετε με ένα απλό script Bash (ή PowerShell):

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

Αποθηκεύστε το ως `run_all.sh`, κάντε το εκτελέσιμο (`chmod +x run_all.sh`), και έχετε μια επαναλήψιμη **cmake build and test** pipeline που μπορείτε να ενσωματώσετε σε οποιοδήποτε σύστημα CI (GitHub Actions, GitLab CI, Azure Pipelines, όπως το θέλετε).

## Περιπτώσεις Άκρων & Συνηθισμένα Πιθανά Σφάλματα

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Λείπει μεταγλωττιστής** | Το CMake διακόπτεται με το μήνυμα “No CMAKE_CXX_COMPILER could be found.” | Εγκαταστήστε έναν μεταγλωττιστή (`sudo apt install build-essential` στο Ubuntu, `xcode-select --install` στο macOS). |
| **Ο φάκελος out‑of‑source υπάρχει ήδη** | Το CMake μπορεί να αρνηθεί την επαναδιαμόρφωση αν ο φάκελος περιέχει παλιά αρχεία. | Διαγράψτε τον φάκελο `build` (`rm -rf build`) ή τρέξτε `cmake --fresh` (CMake 3.24+). |
| **Το CTest δεν μπορεί να βρει δοκιμές** | `add_test()` δεν κλήθηκε ποτέ ή το εκτελέσιμο της δοκιμής απέτυχε να μεταγλωττιστεί. | Επαληθεύστε ότι το `add_test(NAME MyTest COMMAND MyTestExe)` εμφανίζεται στο `CMakeLists.txt` και ότι ο στόχος κατασκευάζεται. |
| **Παράλληλες κατασκευές συγκρούονται σε custom commands** | Ορισμένες custom commands δεν είναι σημειωμένες ως `DEPENDS`, οδηγώντας σε μη-προβλεπτικές αποτυχίες. | Προσθέστε σωστές καταχωρήσεις `add_custom_command(... DEPENDS ...)`. |

Η κατανόηση αυτών των λεπτομερειών κάνει τη διαφορά μεταξύ μιας ασταθούς κατασκευής και μιας αξιόπιστης CI pipeline.

## Οπτική Επισκόπηση (Alt text περιλαμβάνει την κύρια λέξη-κλειδί)

![Διάγραμμα που δείχνει τη ροή διαμόρφωσης, κατασκευής και δοκιμής ενός έργου CMake](/images/cmake-workflow.png "Build CMake Project workflow diagram")

## Ανακεφαλαίωση – Τι Έχετε Μάθει

Ξεκινήσαμε με την κεντρική ερώτηση: *how to build CMake project* από την αρχή. Στο τέλος γνωρίζετε πώς να **configure CMake** με μια καθαρή out‑of‑source κατασκευή, **build CMake** χρησιμοποιώντας τη γενική σημαία `--build`, και **run CTest** με verbose έξοδο για να επαληθεύσετε ότι όλα λειτουργούν. Έχετε επίσης ένα έτοιμο script που συνδέει τα τρία βήματα, παρέχοντάς σας μια πλήρη **cmake build and test** ροή εργασίας.

## Τι Ακολουθεί;

- **Add coverage reporting** – ενσωματώστε το `gcov` ή `llvm-cov` και αφήστε το CTest να δημοσιεύσει τα αποτελέσματα.
- **Cross‑compilation** – εξερευνήστε το `-DCMAKE_TOOLCHAIN_FILE` για κατασκευή σε ενσωματωμένες συσκευές.
- **Package creation** – χρησιμοποιήστε το `cpack` για να συσκευάσετε τα binaries σας για διανομή.
- **CI integration** – αντιγράψτε το script σε ένα workflow GitHub Actions και παρακολουθήστε την αυτοματοποίηση σε κάθε pull request.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικούς τύπους κατασκευής, να προσθέσετε περισσότερες δοκιμές, ή να αντικαταστήσετε την παραδειγματική πηγή με το δικό σας έργο. Τα πρότυπα που καλύψαμε σήμερα ισχύουν για οποιοδήποτε κώδικα βασισμένο σε CMake, είτε είναι ένα μικρό εργαλείο είτε ένα τεράστιο σύστημα πολλαπλών μονάδων.

Καλή κατασκευή, και εύχομαι οι CMake κατασκευές σας να είναι πάντα επαναλήψιμες!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να εξάγετε LaTeX από το Word – Οδηγός βήμα‑βήμα](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Πώς να αποθηκεύσετε Markdown από DOCX – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Πώς να εμφανίσετε την έκδοση Aspose.Words σε Python και .NET: Οδηγός βήμα‑βήμα](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}