---
title: Performans veri dosyalarıyla birlikte sembol bilgilerini kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b5a485baaa1fdeab4a0d4c61b82f5381a931ac85
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897192"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans veri dosyalarıyla kaydetme sembol bilgisi

Dosyalarını analiz etmek için Visual Studio IDE kullanarak ve, VSP dosyası farklı bir bilgisayara taşımak planlama, proje ayarları kaydetmek için performans ayarlamanız gerekir veya *serileştirmek* rapor dosyanızdaki semboller. Bu rapor dosyasının boyutu artar. Semboller serileştirmek iki nedenden dolayı gereklidir:

- Eklemek için bir performans raporu hedef derlemelere önce kod sembolleri geçici depolama konumlarından kaybolur.

- Performans Raporu profili oluşturulmuş bilgisayarı taşınabilir ve analiz farklı simgeler olabilir başka bir bilgisayarda rapor açılırsa, aynı bilgileri çıkarır sembolleri korumak için.

Visual Studio IDE'den veya komut satırından semboller serileştirebiliyorsa:

- Semboller serileştirmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, noktasına **Araçları** menü çubuğu ve ardından **seçenekleri**. İçinde **seçenekleri** penceresinde **performans araçları**ve ardından **sembol bilgisini otomatik serileştir** onay kutusu.

- Rapor dosyaları kaydettiğinizde PACKSYMBOLS eşdeğer komut satırı seçeneğini ' dir. Semboller serileştirmek için şunu yazın **vsperfreport userrulesdirectory packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Sembol sorunlarını giderme

Kendi kodunuzda simgeleri görmüyorsanız, bazı yaygın çözümleri mevcuttur:

- Vsperfreport /debugsympath, burada sembol bilgilerini profil oluşturucu bileşenleri yükleniyor ve olup kullanılan sembol dosyalarını projenizde dosyalarla eşleşmesini konumları tam bir listesini görüntülemek için komut satırında çalıştırın.

- Vsperfreport packsymbols bayrağıyla ya da çalıştırdığınızdan emin olun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genel performans Gezgini seçeneklerinde serileştirme sembol bilgileri seçeneğe sahip bir IDE.

- Tür veri topladıysanız /SUMMARY:TYPE vsperfreport komut satırına ekleyin.

  Windows veya başka Microsoft programlarını sembolleri görmüyorsanız:

- Windows sembol önbelleğinizi yolunu ayarladığınızdan emin olun. Sembol önbellek yolunu ayarlamak için aşağıdakilerden birini yapın:

  - Kümesi hata ayıklayıcısı -> Semboller seçeneğini [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doğru yola bir IDE.

  - -Symbolpath seçeneği VSPerfReport, semboller içeren için komut satırına ekleyin.

- Semboller görmüyorsanız [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], sembol sunucusu ASP sunucu için doğru bir şekilde ayarlandığından emin olun.

## <a name="repacking-symbols"></a>Repacking semboller

Bir rapora simgeleri yeniden paketleyin istiyorsanız VsPerfReport komut satırı aracını kullanarak bunu yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:

VsPerfReport - clearpackedsymbols filename.vsp

VsPerfReport - packsymbols-summary: all filename.vsp

## <a name="see-also"></a>Ayrıca bkz.

[Performans Araçları Verilerini Kaydetme ve Dışarı Aktarma](../profiling/saving-and-exporting-performance-tools-data.md)  
[Nasıl Yapılır: Başvuru Pencereleri Sembol Bilgileri](../profiling/how-to-reference-windows-symbol-information.md)  
[VSPerfReport](../profiling/vsperfreport.md)