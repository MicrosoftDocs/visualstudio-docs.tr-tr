---
title: C++ kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları bakın
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 6e2925eb3bfaf64a48b36c3c7205dce36538123c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823606"
---
# <a name="code-maps-for-c-projects"></a>C++ projeleri için kod haritaları

C++ projeleri için daha eksiksiz eşlemeleri oluşturmak istiyorsanız, bilgi derleyiciye gözatma seçeneği ayarlayın (**/FR**) bu projelerde. Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. Seçerseniz **Tamam**, bu seçeneği yalnızca geçerli eşlemesi için ayarlar. Tüm sonraki haritalar için iletiyi gizleyebilirsiniz seçebilirsiniz.

Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca, üst bilgisi için kod haritaları oluşturmak mümkün olmayabilir (*.h* veya `#include`) IntelliSense veritabanı güncelleştirmeyi bitirinceye kadar dosyaları. Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz.

- Tüm kaynak dosyaları ve çözümünüzdeki üstbilgi dosyaları arasındaki bağımlılıkları görmek için seçin **mimarisi** > **oluşturmak grafiği, dosyaları içerir**.

   ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral_nativecode.png)

- Şu anda açık dosya ve ilgili kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosya veya üstbilgi dosyasını açın. Dosyayı herhangi bir yeri içinde dosyanın kısayol menüsünü açın. Seçin **ekleme dosyalarının Grafını Oluştur**.

   ![.H dosyası birinci düzey bağımlılık grafiği](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>C ve C++ kodu için kod haritalarını sorunlarını giderme

Bu öğeler, C ve C++ kodu için desteklenmez:

- Temel türler üst hiyerarşiyi içeren ve haritalar üzerinde görünmez.

- Çoğu **Göster** menü öğeleri C ve C++ kodunda kullanılmaz.

C ve C++ kodu için kod haritaları oluşturduğunuzda, bu sorunları ortaya çıkabilir:

|**Sorunu**|**Olası nedeni**|**Çözümleme**|
|-|-|-|
|Kod Haritası oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan yapı hatalarını düzeltin ve sonra haritanın yeniden.|
|Bir kod eşlemden oluşturmaya çalıştığınızda Visual Studio yanıt vermemeye başlıyor **mimarisi** menüsü.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|Visual Studio'da belirli IntelliSense ayarları devre dışı bırakılabilir **seçenekleri** iletişim kutusu.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz: [seçenekler, metin düzenleyici, C/C++, Gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|İleti **bilinmeyen yöntemler** bir yöntem düğümünde görünür.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Açma **/FIXED: No** bağlayıcı seçeneği.|
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Açma **/DEBUG** bağlayıcı seçeneği.|
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|Varsa **/pdbstrıpped** bağlayıcıda seçeneği kullanıldıysa, bunun yerine tam .pdb dosyasını dahil edin.|
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Arayan bir dönüştürücü olduğunda, kullanmayı deneyin `_declspec(dllimport)` dönüştürücüden kaçınmak için.|

## <a name="see-also"></a>Ayrıca bkz.

- [Kod haritaları ile bağımlılıkları eşleştirme](../modeling/map-dependencies-across-your-solutions.md)