---
title: Clang projesi özellikleri (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 663140ea-a568-472b-a79a-dfea8818e06a
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCClangCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCClangCompilerTool.DebugInformationFormat
- VC.Project.VCClangCompilerTool.ObjectFile
- VC.Project.VCClangCompilerTool.WarningLevel
- VC.Project.VCClangCompilerTool.WarnAsError
- VC.Project.VCClangCompilerTool.Verbose
- VC.Project.VCClangCompilerTool.Optimization
- VC.Project.VCClangCompilerTool.StrictAliasing
- VC.Project.VCClangCompilerTool.OmitFramePointers
- VC.Project.VCClangCompilerTool.ExceptionHandling
- VC.Project.VCClangCompilerTool.EnableFunctionLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.DataLevelLinking
- VC.Project.VCClangCompilerTool.FloatABI
- VC.Project.VCClangCompilerTool.BufferSecurityCheck
- VC.Project.VCClangCompilerTool.PIC
- VC.Project.VCClangCompilerTool.UseShortEnums
- VC.Project.VCClangCompilerTool.RuntimeTypeInfo
- VC.Project.VCClangCompilerTool.CLanguageStandard
- VC.Project.VCClangCompilerTool.CppLanguageStandard
- VC.Project.VCClangCompilerTool.PreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCClangCompilerTool.UndefineAllPreprocessorDefinitions
- VC.Project.VCClangCompilerTool.ShowIncludes
- VC.Project.VCClangCompilerTool.PrecompiledHeader
- VC.Project.VCClangCompilerTool.PrecompiledHeaderFile
- VC.Project.VCClangCompilerTool.PrecompiledHeaderOutputFileDirectory
- VC.Project.VCClangCompilerTool.PrecompiledHeaderCompileAs
- VC.Project.VCClangCompilerTool.CompileAs
- VC.Project.VCClangCompilerTool.ForcedIncludeFiles
- VC.Project.VCClangCompilerTool.MultiProcessorCompilation
- vc.project.AdditionalOptionsPage
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: efceeb201a7f1afcbf7cc2c6d46619301284d823
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232123"
---
# <a name="clang-project-properties-android-c"></a>Clang projesi özellikleri (Android C++)

Özellik | Açıklama | Seçenekleri
--- | ---| ---
Ek içeren dizinler | Ekleme yoluna eklenecek bir veya daha fazla dizin belirtir; birden fazla ise noktalı virgülle ayırın. (-I[Path]).
Hata ayıklama bilgi biçimi | Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. | **Hiçbiri** -derleme daha hızlı olacak şekilde, hata ayıklama bilgisi üretir.<br>**Tam hata ayıklama bilgileri (DWARF2)** -Oluştur DWARF2 hata ayıklama bilgileri.<br>**Satır numarası bilgisi** -yalnızca oluşturmak satır numarası bilgisi.<br>
Nesne dosyası adı | Varsayılan nesne dosyası adını geçersiz kılacak bir ad belirtir; Dosya veya dizin adı olabilir. (/ FO[ad]).
Uyarı düzeyi | Nasıl katı derleyicinin kod hataları hakkında olmasını istediğinizi seçin.  Diğer bayraklar doğrudan ek seçenekler eklenmesi gerekir. (/ w, / weverything). | **Tüm uyarıları Kapat Kapat** -tüm Derleyici uyarılarını devre dışı bırakır.<br>**EnableAllWarnings** -varsayılan olarak devre dışı dahil olmak üzere tüm uyarıları etkinleştirir.<br>
Uyarıları hata olarak değerlendir | Tüm Derleyici uyarılarını hata olarak değerlendirir. Yeni bir proje için tüm derlemelerde /WX kullanmak iyi bir çözüm olabilir; Tüm uyarıların çözümlenmesi, en az sayıda olası bulunur zor kod kusurlarını sağlayacaktır.
Ayrıntılı modu etkinleştir | Ayrıntılı çıkış kullan ve çalıştırma komutları göster.
En iyi duruma getirme | Uygulama için iyileştirme düzeyini belirtir. | **Özel** -özel iyileştirme.<br>**Devre dışı bırakılmış** -iyileştirme devre dışı bırakın.<br>**Boyutu en aza indir** -boyutu için İyileştir.<br>**Hızı en** -hız için İyileştir.<br>**Tam iyileştirme** -pahalı iyileştirmeler.<br>
Katı örtüşme | En katı örtüşme kurallarını varsayın.  Bir türde bir nesne hiçbir zaman farklı türde bir nesne olarak aynı adreste bulunan olduğu kabul edilir.
Çerçeve işaretçisini atlama | Çağrı yığınında çerçeve işaretçilerinin oluşturulmasını engeller.
C++ özel durumlarını etkinleştir | Derleyici tarafından kullanılması için özel durum işleme modelini belirtir. | **Hayır** -özel durum işleme devre dışı bırakın.<br>**Evet** -özel durum işlemeyi etkinleştirin.<br>**Tabloları Aç** - gerekli tüm statik verileri oluşturur, ancak oluşturulan kodu etkilemez.<br>
İşlev düzeyi bağlamayı etkinleştir | Derleyicinin ayrı ayrı işlevleri paketlenmiş işlevler (Comdat'lar) biçiminde sağlar. Düzenleme için gereken ve çalışmaya devam edin.     (ffunction-sections).
Veri düzeyi bağlamayı etkinleştir | Kullanılmayan verileri her veri öğesini ayrı bir bölümde çıkarma yoluyla kaldırarak yapılan bağlayıcı iyileştirmelerine sağlar.
Gelişmiş sımd'yi(neon) etkinleştir | NEON kayan nokta donanımı için kod oluşturmayı etkinleştirir. Bu, yalnızca arm mimarisi için geçerlidir.
Kayan nokta ABI'si | Kayan nokta ABI'sini seçmek için seçenek. | **Yazılım** -'Soft' neden içeren kitaplık çağrıları kayan nokta işlemleri için çıktı üretmek derleyici.<br>**SoftFP** - 'SoftFP', donanım kayan nokta yönergeleri kullanan kod oluşturulmasını sağlar, ancak yine soft-float çağırma kurallarını kullanır.<br>**Sabit** -kayan nokta yönergeleri ve kullanımları FPU'ya özgü çağırma kuralları oluşturma 'Sabit' oluşturulmasına izin verir.<br>
Güvenlik denetimi | Güvenlik denetimi, yığın arabelleği üst çalışır, bir ortak bir saldırı denemesi bir programın güvenlik algılamaya yardımcı olur. (fstack-protector). | **Güvenlik denetimini devre dışı bırak** -güvenlik denetimini devre dışı bırakın.<br>**Güvenlik denetimini etkinleştir** -güvenlik denetimini etkinleştir. (fstack-protector)<br>
Konumdan bağımsız kod | Paylaşılan bir kitaplık kullanmak için konum bağımsız kod (PIC) oluştur.
Kısa sabit listeleri kullan | Sabit listesi türünü kullanan yalnızca giriş muhtemel değerler kümesini gerektirdiği sayıda bayt.
Çalışma zamanı tür bilgisini etkinleştir | Çalışma zamanında (çalışma zamanı tür bilgisi) C++ nesne türlerini denetlemek için kod ekler.     (frtti, fno-rtti)
C dil standardı | C dil standardını belirler. | **Default**<br>**C89** -C89 dil standardı.<br>**C99** -C99 dil standardı.<br>**C11** -C11 dil standardı.<br>**C99 (GNU diyalekti)** -C99 (GNU diyalekti) dil standardı.<br>**C11 (GNU diyalekti)** -C11 (GNU diyalekti) dil standardı.<br>
C++ dil standardı | C++ dil standardını belirler. | **Default**<br>**C ++ 03** -C ++ 03 dil standardı.<br>**C ++ 11** -C ++ 11 dil standardı.<br>**C ++ 14** -C ++ 14 dil standardı.<br>**C ++ 03 (GNU diyalekti)** - C ++ 03 (GNU diyalekti) dil standardı.<br>**C ++ 11 (GNU diyalekti)** - C ++ 11 (GNU diyalekti) dil standardı.<br>**C ++ 14 (GNU diyalekti)** - C ++ 14 (GNU diyalekti) dil standardı.<br>
Önişlemci tanımları | Kaynak dosyanız için ön işleme sembollerini tanımlar. (-D)
Ön İşlemci tanımlarını Kaldır | Bir veya daha çok önişlemci tanımsızı belirtir.  (-U [macro])
Tüm önişlemci tanımlarını Kaldır | Önceden tanımlanmış tüm önişlemci değerlerini Kaldır.  (-undef)
Ekleme kodlarını Göster | Derleyici çıkışıyla ekleme kodu dosyalarının bir listesini oluşturur.  (-H)
Önceden derlenmiş üst bilgi | Oluştur/Kullan önceden derlenmiş üst bilgi: oluşturmayı veya kullanmayı etkinleştirir, derleme sırasında önceden derlenmiş üstbilgi. | **Kullanım** -Ön derlenmiş üstbilgi kullanın.<br>**Önceden derlenmiş üst bilgiler kullanmayan** -önceden derlenmiş üst bilgi kullanılmıyor.<br>
Önceden derlenmiş üst bilgi dosyası | Önceden derlenmiş üst bilgi dosyası için kullanılacak üst bilgi dosyası adını belirtir. Bu dosya aynı zamanda 'Zorunlu ekleme dosyaları için' yapı sırasında eklenecek
Önceden derlenmiş üst bilgi çıkış dosyası dizini | Oluşturulan önceden derlenmiş üst bilgi dizinini belirtir. Bu dizin aynı zamanda 'Ek ekleme Dizinleri'ne' derleme sırasında eklenir
Önceden derlenmiş üst bilgi olarak derleme | Derleme önceden derlenmiş üst bilgi dosyası için derleme dili tercihini seçin (- x c-header, - x c ++ - üst bilgisi). | **C kodu olarak derle** -C kodu olarak derle.<br>**C++ kodu olarak derle** -C++ kodu olarak derle.<br>
Olarak derleme | .C ve .cpp dosyaları için derleme dili tercihini seçin.  'Default' göre .c veya .cpp uzantı algılar. (-x c, -x c++) | **Varsayılan** -varsayılan.<br>**C kodu olarak derle** -C kodu olarak derle.<br>**C++ kodu olarak derle** -C++ kodu olarak derle.<br>
Zorlanmış dosyaları Ekle | bir veya daha çok zorunlu dosyaları içerir.     (-include [ad])
Çok işlemci derlemesi | Çok işlemci derlemesi.
Ek Seçenekler | Ek Seçenekler.
