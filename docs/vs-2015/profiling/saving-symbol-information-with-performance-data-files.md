---
title: Performans veri dosyalarıyla birlikte sembol bilgilerini kaydetme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbe05d345e54a900fcdd5568aa898b80417bb68d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761260"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Performans veri dosyalarıyla kaydetme sembol bilgisi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanıyorsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ve tümleşik geliştirme ortamı (IDE) dosyalarını analiz etmek için planlama, VSP dosyası farklı bir bilgisayara taşımak, proje ayarları kaydetmek için performansı ayarlayın veya *serileştirmek* içindeki semboller Rapor dosyanız. Bu rapor dosyasının boyutu artar. Semboller serileştirmek iki nedenden dolayı gereklidir:  
  
- Eklemek için bir performans raporu hedef derlemelere önce kod sembolleri geçici depolama konumlarından kaybolur.  
  
- Performans Raporu profili oluşturulmuş bilgisayarı taşınabilir ve analiz farklı simgeler olabilir başka bir bilgisayarda rapor açılırsa, aynı bilgileri çıkarır sembolleri korumak için.  
  
  **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Sembolleri buradan serileştirebiliyorsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE veya komut satırından:  
  
- Semboller serileştirmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, noktasına **Araçları** menü çubuğu ve ardından **seçenekleri**. İçinde **seçenekleri** penceresinde **performans araçları**ve ardından **sembol bilgisini otomatik serileştir** onay kutusu.  
  
- Rapor dosyaları kaydettiğinizde PACKSYMBOLS eşdeğer komut satırı seçeneğini ' dir. Semboller serileştirmek için şunu yazın **vsperfreport userrulesdirectory packsymbols filename.vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Sembol sorunlarını giderme  
 Kendi kodunuzda simgeleri görmüyorsanız, bazı yaygın çözümleri mevcuttur:  
  
- Vsperfreport /debugsympath, burada sembol bilgilerini profil oluşturucu bileşenleri yükleniyor ve olup kullanılan sembol dosyalarını projenizde dosyalarla eşleşmesini konumları tam bir listesini görüntülemek için komut satırında çalıştırın.  
  
- Vsperfreport packsymbols bayrağıyla ya da çalıştırdığınızdan emin olun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genel performans Gezgini seçeneklerinde serileştirme sembol bilgileri seçeneğe sahip bir IDE.  
  
- Tür veri topladıysanız /SUMMARY:TYPE vsperfreport komut satırına ekleyin.  
  
  Windows veya başka Microsoft programlarını sembolleri görmüyorsanız:  
  
- Windows sembol önbelleğinizi yolunu ayarladığınızdan emin olun. Sembol önbellek yolunu ayarlamak için aşağıdakilerden birini yapın:  
  
  -   Kümesi hata ayıklayıcısı -> Semboller seçeneğini [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] doğru yola bir IDE.  
  
  -   -Symbolpath seçeneği VSPerfReport, semboller içeren için komut satırına ekleyin.  
  
- Semboller görmüyorsanız [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], sembol sunucusu ASP sunucu için doğru bir şekilde ayarlandığından emin olun.  
  
## <a name="repacking-symbols"></a>Repacking semboller  
 Bir rapora simgeleri yeniden paketleyin istiyorsanız VsPerfReport komut satırı aracını kullanarak bunu yapabilirsiniz. Aşağıdaki komut satırlarını kullanın:  
  
 VsPerfReport - clearpackedsymbols filename.vsp  
  
 VsPerfReport - packsymbols-summary: all filename.vsp  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Verileri kaydetme ve dışarı aktarma performans araçları](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Nasıl yapılır: başvuru Windows sembol bilgileri](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



