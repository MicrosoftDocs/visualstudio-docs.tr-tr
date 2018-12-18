---
title: Clang Bağlayıcısı Özellikleri (Android C++) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
manager: douge
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 1b491257c561af337afdfd0d066c9ed8cd550c15
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39230954"
---
# <a name="clang-linker-properties-android-c"></a>Clang Bağlayıcısı Özellikleri (Android C++)

Özellik | Açıklama | Seçenekleri
--- | ---| ---
Çıkış dosyası | Seçeneği, varsayılan adı ve bağlayıcının oluşturduğu program konumunu geçersiz kılar. (-o).
İlerlemeyi Göster | Bağlayıcı ilerleme iletilerini yazdırır.
Sürüm | -Version seçeneği bağlayıcıya yürütülebilir dosya üst bilgisinde sürüm numarası yerleştirin.
Ayrıntılı çıkışı etkinleştir | Verbose seçeneği, sistemi, hata ayıklama için ayrıntılı iletiler çıkarmasını söyler.
Artımlı bağlamayı etkinleştir | Seçeneği artımlı bağlamayı etkinleştirmesini söyler.
Paylaşılan kitaplık arama yolu | Kullanıcının paylaşılan kitaplık arama yolunu doldurmasına izin verir.
Ek Kitaplık dizinleri | Kullanıcının ortam kitaplık yolunu geçersiz kılmasına izin verir. (-L klasör).
Çözümlenmeyen sembol başvurularını bildir | Bu seçenek etkinleştirildiğinde, çözümlenmeyen sembol başvurularını bildirir.
Bellek kullanımı için İyileştir | Gerekirse sembol tablolarını yeniden okuyarak bellek kullanımı için İyileştir.
Varsayılan özel kitaplıkları yoksay | Bir veya daha fazla varsayılan kitaplık adlarını belirtir.
Sembol başvurularını zorla | Çıkış dosyasına tanımsız bir sembol olarak girilmeye zorla.
Hata ayıklayıcı sembol bilgisi | Hata ayıklayıcı sembol bilgisi çıkış dosyasından'nı tıklatın. | **Tüm ekleme**<br>**Konum değiştirme işlemi için gerekli olmayan sembolleri atla**<br>**Yalnızca hata ayıklayıcı sembol bilgilerini çıkar**<br>**Tüm sembol bilgilerini çıkar**<br>
Paket hata ayıklayıcı sembol bilgisi | Hata ayıklayıcı sembol bilgilerini paketleme önce Şerit.  Hata ayıklama için özgün ikilinin bir kopyası kullanılacak.
Eşlem dosyası adı | Map seçeneği bağlayıcıya belirtilen kullanıcı adıyla bir eşleme dosyası oluşturmasını söyler.
Yeniden konumlandırmadan sonra değişkenleri ReadOnly işaretle | Bu seçenek, yeniden konumlandırmadan sonra değişkenleri salt okunur işaretler.
İşlevi hemen bağlamayı etkinleştir | Bu seçenek, nesne işlevi hemen bağlama için işaretler.
Yürütülebilir yığını iste | Bu seçenek, çıkışı, yürütülebilir yığını gerektirmiyor olarak işaretler.
Tüm arşiv | Tüm Arşiv, kaynaklar ve ek bağımlılıklar'daki tüm kodu kullanır.
Ek Seçenekler | Ek Seçenekler.
{1&gt;Ek Bağımlılıklar&lt;1} | Bağlama komut satırına eklenecek ek öğeleri belirtir.
Kitaplık bağımlılıkları | Bu seçenek, özel olarak bağlayıcı komut satırına eklenecek ek kitaplıklar belirtmeye izin verir. Ek kitaplıklar ile bağlayıcı komut satırı başlangıç sonuna eklenecek *LIB* ve ile sona erdi *.a* veya *.so* uzantısı.  (-Lfıle)
