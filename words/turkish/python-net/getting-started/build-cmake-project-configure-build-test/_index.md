---
category: general
date: 2026-07-06
description: CMake projesini adım adım oluşturun. CMake'i nasıl yapılandıracağınızı,
  CMake'i nasıl derleyeceğinizi ve güvenilir testler için CTest'i nasıl çalıştıracağınızı
  öğrenin.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: tr
og_description: CMake projesini net adımlarla hızlıca oluşturun. Bu kılavuz, CMake'i
  nasıl yapılandıracağınızı, CMake'i nasıl derleyeceğinizi ve CTest'i nasıl çalıştıracağınızı
  gösterir.
og_title: 'CMake Projesi Oluşturma: Yapılandırma, Derleme ve Test Rehberi'
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
title: 'CMake Projesini Derle: Yapılandır, Derle ve Test Et'
url: /tr/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# CMake Projesi Oluşturma: Yapılandırma, Derleme ve Test

Saatlerce StackOverflow’da arama yapmadan **CMake projesi oluşturmayı** merak ettiniz mi? Tek başınıza değilsiniz. Çoğu geliştirici, basit bir `CMakeLists.txt` dosyasından tekrarlanabilir bir derleme hattına geçmeye çalışırken aynı sorunu yaşıyor. 

Bu öğreticide tüm süreci adım adım inceleyeceğiz—*CMake’i nasıl yapılandırılır*, *CMake nasıl derlenir* ve *CTest nasıl çalıştırılır*—böylece herhangi bir makinede çalıştırabileceğiniz temiz, tekrarlanabilir bir derleme elde edeceksiniz. Sonunda, ekstra betiklere ihtiyaç duymadan kendi deponuza kopyalayıp yapıştırabileceğiniz çalışan bir örnek elde edeceksiniz.

## Önkoşullar — Başlamadan Önce Gerekenler

Başlamadan önce şunların kurulu olduğundan emin olun:

- Güncel bir CMake sürümü (3.20 veya daha yeni) – eski sürümler kullanacağımız bazı bayrakları içermez.
- Platformunuz tarafından desteklenen bir C++ derleyicisi (gcc, clang, MSVC vb.).
- `cmake` ve `ctest` komutlarına erişebilen bir terminal veya komut istemcisi.
- (İsteğe bağlı) Örnek depoyu klonlamak isterseniz Git.

Bu öğelerden biri eksikse, şimdi edinin; aksi takdirde daha sonra “command not found” hataları alırsınız ve bu hiç eğlenceli olmaz.

## Adım 1: CMake Projesini Yapılandırma (Release yapılandırması)

*CMake’i nasıl yapılandırılır* sorusuna yanıt verirken ilk yapmanız gereken, CMake’e kaynakların nerede olduğunu ve derleme artefaktlerinin nereye gitmesini istediğinizi söylemektir. `-S` bayrağı kaynak dizinine işaret eder, `-B` ayrı bir derleme klasörü oluşturur ve `-D CMAKE_BUILD_TYPE=Release` optimize edilmiş bir derleme zorlar.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Neden önemli:** Kaynak ve derleme dosyalarını ayrı tutmak (`out‑of‑source` derlemeleri) yanlışlıkla kaynak değişikliklerini önler ve derleme dizinini sonradan temizlemeyi çok kolaylaştırır. `Release` bayrağı ayrıca derleyiciye optimizasyonları etkinleştirmesini söyler; bu genellikle son ikili dosya için istediğiniz şeydir.

> **Pro ipucu:** Sorun giderme için bir Debug derlemesine ihtiyacınız varsa, sadece `Release` yerine `Debug` yazın. Aynı komut çalışır—CMake geri kalanını halleder.

## Adım 2: Yapılandırılmış Projeyi Derleme

Yapılandırma adımı gerekli tüm makefile’ları veya Visual Studio proje dosyalarını ürettikten sonra, kodu gerçekten derleyebilirsiniz. `--build` seçeneği altındaki derleme aracını (`make`, `ninja`, `MSBuild` vb.) soyutlar, böylece aynı komut Linux, macOS ve Windows’ta çalışır.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Arka planda ne oluyor?** CMake, önceki adımda oluşturulan `CMakeCache.txt` dosyasını okur, uygun derleme aracını belirler ve doğru bayraklarla onu çağırır. Bu, *CMake nasıl derlenir* sorusunun özüdür—`make` mi yoksa `ninja` mı kullandığınızı hatırlamanıza gerek yok; CMake sizin yerinize halleder.

Çok çekirdekli makinelerde işleri hızlandırmak isterseniz, komuttan sonra `-- -j$(nproc)` (Linux/macOS) veya `-- /m` (Windows) ekleyin:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Adım 3: Örnek Testleri Ayrıntılı Çıktı ile Çalıştırma

Test, gerçek dünyada projenin nasıl davrandığını görmenizi sağlar. CMake, `ctest` adlı bir test sürücüsüyle birlikte gelir; bu sürücü `CMakeLists.txt` içinde `add_test()` ile eklenen tüm testleri keşfedip çalıştırabilir. Testleri çalıştırıp ayrıntılı çıktıyı görmek için önce `-E chdir` yardımcı komutunu kullanarak derleme dizinine geçin:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Neden `--verbose` kullanmalı?** Her testin komut satırını, çıkış kodunu ve testin kendisinin yazdığı herhangi bir çıktıyı yazdırır. *CTest nasıl çalıştırılır* öğrenirken bu çok önemlidir çünkü sahne arkasında tam olarak ne olduğunu gösterir.

Tipik bir çıktı şöyle görünür:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Bir test başarısız olursa, ayrıntılı günlük başarısız komutu ve hata mesajlarını içerir, bu da hata ayıklamayı çok daha hızlı hale getirir.

## Adım 4: Tüm İş Akışını Otomatikleştirme (İsteğe Bağlı)

Birçok proje için, yapılandırma, derleme ve testi tek bir satırda gerçekleştiren bir komut istersiniz. Bunu basit bir Bash (veya PowerShell) betiğiyle yapabilirsiniz:

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

Betiği `run_all.sh` olarak kaydedin, çalıştırılabilir yapın (`chmod +x run_all.sh`) ve **cmake build and test** adlı tekrarlanabilir bir pipeline elde edin; bu betiği herhangi bir CI sistemine (GitHub Actions, GitLab CI, Azure Pipelines vb.) ekleyebilirsiniz.

## Kenar Durumları ve Yaygın Tuzaklar

| Situation | What to Watch For | Fix |
|-----------|-------------------|-----|
| **Missing compiler** | CMake aborts with “No CMAKE_CXX_COMPILER could be found.” | Install a compiler (`sudo apt install build-essential` on Ubuntu, `xcode-select --install` on macOS). |
| **Out‑of‑source folder already exists** | CMake may refuse to reconfigure if the folder contains stale files. | Delete the `build` directory (`rm -rf build`) or run `cmake --fresh` (CMake 3.24+). |
| **CTest cannot find tests** | `add_test()` was never called or the test executable failed to compile. | Verify that `add_test(NAME MyTest COMMAND MyTestExe)` appears in `CMakeLists.txt` and that the target builds. |
| **Parallel builds race on custom commands** | Some custom commands are not marked as `DEPENDS`, leading to nondeterministic failures. | Add proper `add_custom_command(... DEPENDS ...)` entries. |

Bu nüansları anlamak, kırılgan bir derleme ile sağlam bir CI pipeline arasındaki farkı yaratır.

## Görsel Genel Bakış (Alt metin ana anahtar kelimeyi içerir)

![CMake projesinin yapılandırma, derleme ve test akışını gösteren diyagram](/images/cmake-workflow.png "CMake Projesi Oluşturma iş akışı diyagramı")

## Özet – Öğrendikleriniz

Başlangıçta temel soruya odaklandık: *CMake projesi nasıl oluşturulur* sorusu. Artık **CMake’i temiz bir out‑of‑source derleme ile yapılandırmayı**, **evrensel `--build` bayrağıyla CMake’i derlemeyi** ve **her şeyin çalıştığını doğrulamak için CTest’i ayrıntılı çıktı ile çalıştırmayı** biliyorsunuz. Ayrıca üç adımı birleştiren hazır bir betiğiniz var; bu da tam bir **cmake build and test** iş akışı sağlar.

## Sıradaki Adım?

- **Kod kapsamı raporlaması ekleyin** – `gcov` veya `llvm-cov` entegrasyonu yapın ve CTest sonuçlarını yayınlayın.
- **Çapraz derleme** – gömülü cihazlarda derleme yapmak için `-DCMAKE_TOOLCHAIN_FILE` keşfedin.
- **Paket oluşturma** – ikili dosyalarınızı dağıtmak için `cpack` kullanın.
- **CI entegrasyonu** – betiği bir GitHub Actions iş akışına kopyalayın ve her pull request’te otomasyonun çalışmasını izleyin.

Farklı derleme tipleriyle denemeler yapmaktan, daha fazla test eklemekten veya örnek kaynağı kendi projenizle değiştirmekten çekinmeyin. Bugün kapsadığımız kalıplar, CMake tabanlı herhangi bir kod tabanına uygulanabilir; ister küçük bir yardımcı program, ister devasa çok modüllü bir sistem olsun.

İyi derlemeler, ve CMake derlemeleriniz her zaman tekrarlanabilir olsun!

## Sonra Ne Öğrenmelisiniz?

Aşağıdaki öğreticiler, bu kılavuzda gösterilen tekniklere dayanan ve yakından ilgili konuları kapsar. Her kaynak, ek API özelliklerini ustalaşmanıza ve kendi projelerinizde alternatif uygulama yaklaşımlarını keşfetmenize yardımcı olacak tam çalışan kod örnekleri ve adım adım açıklamalar içerir.

- [Word'den LaTeX'e Aktarma – Adım Adım Kılavuz](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [DOCX'ten Markdown Kaydetme – Adım Adım Kılavuz](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Python ve .NET'te Aspose.Words Sürümünü Görüntüleme – Adım Adım Kılavuz](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}