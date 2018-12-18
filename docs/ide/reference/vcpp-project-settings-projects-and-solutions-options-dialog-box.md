---
title: VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu
ms.date: 08/02/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 966b51c0522a65641edc2f602bb27849bfabfe77
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33103443"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>VC++ Proje Ayarları, Projeler ve Çözümler, Seçenekler İletişim Kutusu
Bu iletişim kutusunu tanımlamanıza izin verir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] yapı ve proje günlüğü, performans ve dosya türlerini desteklemek için ilgili ayarları.

### <a name="to-access-this-dialog-box"></a>Bu iletişim kutusunu erişmek için

1.  Üzerinde **Araçları** menüsünde tıklatın **seçenekleri**.

2.  Seçin **projeler ve çözümler**ve ardından **VC ++ proje ayarları**.

## <a name="build-logging"></a>Günlük kaydı oluşturma
 **Evet**

  Yapı günlük dosyasının üretilmesi açar. Bu seçenek projenin Ara files dizininde bulunabilir BuildLog.htm oluşturur. Her yeni derleme önceki BuildLog.htm dosyasının üzerine yazar.

 **Yok**

  Yapı günlük dosyası oluşturma devre dışı bırakır.

## <a name="show-environment-in-log"></a>Ortam günlüğünde Göster
 **Evet**

 Ortam değişkenlerini yapı günlük dosyasında listeler. Bu seçenek, tüm ortam değişkenlerini yapı sırasında echo belirtir [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projelere yapı günlük dosyası.

 **Yok**

 Ortam değişkenlerini yapı günlük dosyasından dışlayın.

## <a name="build-timing"></a>Zamanlama oluşturma
 **Evet**

  Yapı zamanlama üzerinde etkinleştirir. Seçili olduğunda, derleme tamamlamak geçen süreyi çıkış penceresine nakledilir. Daha fazla bilgi için bkz: [çıktı penceresi](../../ide/reference/output-window.md).

 **Yok**

 Yapı zamanlama devre dışı bırakır.

## <a name="maximum-concurrent-c-compilations"></a>Maksimum eşzamanlı C++ derlemeleri
  Paralel C++ derleme için kullanılacak CPU çekirdeği sayısını belirtir.

## <a name="extensions-to-include"></a>Dahil etmek için uzantıları
  Projenize bağlantı noktalı dosyalarının dosya adı uzantılarını belirtir.

## <a name="extensions-to-hide"></a>Gizleme için Uzantılar
  İçinde görüntülenmez dosyalarının dosya adı uzantılarını belirtir **Çözüm Gezgini** zaman **tüm dosyaları göster** etkinleştirilir.

## <a name="build-customization-search-path"></a>Özelleştirme arama yolu oluştur
  Yardımcı .rules dosyaları içeren dizinler listesinde projeleriniz için derleme kuralları tanımlamak belirtir.

## <a name="solution-explorer-mode"></a>Çözüm Gezgini modu
 **Projede yalnızca dosyaları göster**

  Yapılandırır **Çözüm Gezgini** yalnızca projedeki dosyaları görüntülemek için.

 **Tüm dosyaları göster**

  Yapılandırır **Çözüm Gezgini** proje ve proje klasöründeki diskteki dosyaları dosyaları göstermek için.

## <a name="enable-project-caching"></a>Proje önbelleğe almayı etkinleştir
**Evet**

Böylece sonraki projeyi açtığınızda, proje dosyalarını yeniden hesaplama yerine verileri önbelleğe yükleyebilir Visual Studio Proje verileri önbelleğe almak için etkinleştirir. Önbelleğe alınan verileri kullanarak proje yük zamanı önemli ölçüde hızlandırılabilir.

**Yok**

Önbelleğe alınan proje verilerini kullanmayın. Proje her zaman yüklenir proje dosyalarını ayrıştırma.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ Programları Oluşturma](/cpp/build/building-c-cpp-programs)
- [C/C++ Derleme Başvurusu](/cpp/build/reference/c-cpp-building-reference)