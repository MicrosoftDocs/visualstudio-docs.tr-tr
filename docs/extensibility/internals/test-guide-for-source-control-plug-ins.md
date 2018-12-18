---
title: Test kaynak denetimi eklentileri için Kılavuzu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8df70ef5fcaffb7fe2e06df5b6d47e526ff5162f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828266"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Kaynak Denetimi Eklentileri için Test Kılavuzu
Bu bölümde, kaynak denetimi eklentisi ile test etmek için yönergeler sağlanmaktadır [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Test en yaygın alanlara ek olarak bazı sorunlu olabilecek daha karmaşık alanları kapsamlı bir bakış sağlanır. Bu genel bakış, test çalışmalarının kapsamlı bir liste olarak tasarlanmamıştır.  
  
> [!NOTE]
>  Bazı hata düzeltmeleri ve geliştirmeleri en son [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, var olan kaynak denetimi daha önce önceki sürümlerini kullanırken karşılaşılan değil eklentileri ile ilgili sorunlar ortaya [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Hiçbir eklenti için önceki sürümden itibaren yapılan değişiklikler olsa bile, var olan kaynak denetimi eklentisi Bu bölümde, numaralandırılan alanlarda test önemle tavsiye edilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="common-preparation"></a>Ortak hazırlama  
 Bir makine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ve yüklü, hedef kaynak denetimi eklentisi gereklidir. Benzer şekilde yapılandırılmış bir ikinci makine, açık kaynak denetimi testlerden bazıları için kullanılabilir.  
  
## <a name="definition-of-terms"></a>Koşulları tanımı  
 Bu test Kılavuzu amacıyla aşağıdaki terim tanımları kullanın:  
  
 İstemci projesi  
 Herhangi bir proje türü kullanılabilir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetimi tümleştirmesini destekleyen (örneğin, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], veya [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).  
  
 Web projesi  
 Web projeleri dört tür vardır: dosya sistemi, yerel IIS, uzak sitelerin ve FTP.  
  
- Dosya sistemi projeleri bir yerel yolda oluşturulur, ancak dahili olarak bir UNC yolu erişilen ve istemci projeleri gibi IDE içinde kaynak denetimi altında yerleştirilmiş olarak yüklenmesi için Internet Information Services (IIS) gerektirmez.  
  
- Yerel IIS projeleri aynı makineye yüklenir ve erişilen IIS yerel makineye işaret eden bir URL ile çalışın.  
  
- Uzak siteleri projeleri aynı zamanda bir IIS hizmetleri altında oluşturulan, ancak IIS sunucu makinesinde ve değil, kaynak denetimi altında yerleştirilmiş içinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
- FTP projeleri uzak bir FTP sunucusu üzerinden erişilen ancak kaynak denetimi altında yerleştirilemez.  
  
  Liste  
  Çözüm veya projeyi kaynak denetimi altında için başka bir terim.  
  
  Sürüm Store  
  Kaynak Denetimi Eklentisi API aracılığıyla erişilen kaynak denetimi veritabanı.  
  
## <a name="test-areas-covered-in-this-section"></a>Bu bölümde yer alan test alanlarını  
  
-   [Test Alanı 1: Kaynak Denetimine Ekleme/Kaynak Denetiminden Açma](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Case 1a: kaynak denetimine Çözüm Ekle  
  
    -   Case 1b: kaynak denetiminden çözüm Aç  
  
    -   Case 1c: kaynak denetiminden çözüm ekleyin  
  
-   [Test Alanı 2: Kaynak Denetiminden Alma](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Test Alanı 3: Kullanıma Alma/Kullanıma Almayı Geri Alma](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   3. durum: Kullanıma / kullanıma almayı geri al  
  
    -   Case 3a: gözden geçirin  
  
    -   3b durum: kullanıma alma bağlantısı kesildi  
  
    -   Case 3c: Sorgu düzenleme/sorgu kaydetme (QEQS)  
  
    -   3B case: Sessiz kullanıma alma  
  
    -   Case 3e: geri alma  
  
-   [Test Alanı 4: İade Etme](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Case 4a: öğeleri değiştirdiği  
  
    -   Case 4b: dosya ekleme  
  
    -   Case 4 c: Proje ekleme  
  
-   [Test Alanı 5: Kaynak Denetimini Değiştirme](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Case 5a: bağlama  
  
    -   Case 5b: Unbind  
  
    -   Case 5c: yeniden bağlayın  
  
-   [Test Alanı 6: Silme](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Test Alanı 7: Paylaşma](../../extensibility/internals/test-area-7-share.md)  
  
-   [Test Alanı 8: Eklenti Değiştirme](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Case 8a: otomatik değiştirme  
  
    -   Case 8b: Çözüm tabanlı Değiştir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri](../../extensibility/source-control-plug-ins.md)