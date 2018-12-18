---
title: Visual Studio için etkileşim desenleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142438"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio için etkileşim desenleri
## <a name="overview"></a>Genel Bakış  
 Genel olarak, bir tasarım deseni kısıtlamaların benzer kümeleriyle sorunları çözmek için belirli durumlarda uygulanabilir bir tasarım çekirdek ' dir. Özellik ve sistem tasarımcıları bu tasarım desenleri başlangıç sonra kendi özel durum uyarlanabilir noktaları olarak kullanın.  
  
 Visual Studio yeni özellikler oluştururken düşünülmesi gereken ortak etkileşim desenler kitaplığının sahiptir. Bizim tasarım modelleri için iki çekirdek bağlamları vardır: Visual Studio istemcisi (devenv) ve Visual Studio Online. Bazı tasarım sorunları için tüm durumlarda iyi çalışır bulunabilen bir desen yoktur. Çoğu durumda, ancak, çözüm bir tarayıcı ile olan bir istemci uygulaması barındırılan içinde sunulan kullanıcı Arabirimi için farklı olabilir.  
  
### <a name="visual-studio-client-pattern-types"></a>Visual Studio istemcisi deseni türleri  
  
|Desen türü|Açıklama|Örnekler|  
|------------------|-----------------|--------------|  
|**Uygulama düzeyi desenleri**|Üst düzey desenlerini belirlemek veya uygulama içeriği görüntüleme ve bunların içindeki bileşik ve denetim düzenleri içeren uygulama, genel|-Araç pencereleri<br />-Belge pencereleri|  
|**Bileşik desenleri**|Uygulama düzenleri yayılabilir ortak desenler ya da farklı bir yapılandırma birkaç denetimlerinde oluşan tanınan bir düzeni|-Görünüm değiştirme<br />-LIST oluşturucular<br />-Verileri görüntüleme<br />-Bildirimler<br />-Doğrulama<br />-Seçimi modelleri|  
|**Denetim desenleri**|Özellikleri nasıl alt düzey denetimleri hakkında olması beklenir|-Ağacı görünümleri<br />-Izgara denetimine düzenleme|  
  
## <a name="application-patterns"></a>Uygulama düzenleri  
 Yüksek bir düzeyde birden çok windows, iletişim kutuları, komutları ve araç çubuklarını tek bir IDE içinde Visual Studio arabirimi oluşur. Visual Studio hiyerarşi bağlamını ve sürücüleri menüleri belirler. Anahtar tümleştirme kullanıcı arabiriminde IDE belge windows, aracı windows, projeler, komut yapısını, metin düzenleyici, araç, Özellikler penceresini ve araçları noktalarıdır > Seçenekler.  
  
 Her kullanıcı arabiriminde anahtar tümleştirme noktaları IDE için temel kullanım desenlerini vardır:  
  
-   [Menüleri ve Visual Studio komutları](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Visual Studio için uygulama düzenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Pencere etkileşimleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Araç pencereleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Belge Düzenleyicisi kuralları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [İletişim Kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)  
  
    -   [Projeler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Ortak denetim desenleri  
 Denetim desenleri nasıl ayrı ayrı denetimler hakkında davranır beklenen esas alır. Bu tutarlılık en önemli bir noktadır.  
  
 Visual Studio'da en yaygın denetimleri Masaüstü Windows yönergeleri izlemelidir. Bizim yönergeleri yalnızca, Visual Studio özgü etkileşimleri veya yerler, biz yönergeleri tamamen Gelişmiş kullanıcılarımızın ihtiyaçlarını karşılamak üzere Visual Studio uyarlamak için yerine geçen ortak kurallarına büyütmek için ihtiyacımız alanları içerir.  
  
-   [Visual Studio için ortak denetim desenleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Ortak Denetimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [Düğmeleri ve bağlar](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Bileşik desenleri  
 Çeşitli görevleri gerçekleştirmek için kullanıcıların beklediğiniz yollarla vardır. Mümkün olduğunda, özellikler bu düzenlere hem etkileşim ve görsel tasarım için kullanmak üzere tasarlanmalıdır.  
  
 En önemli bazı Visual Studio içinde birçok bileşik desenleri varken göre tutarlılık şunlardır:  
  
-   [Visual Studio için bileşik desenleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Nesne üzerinde kullanıcı Arabirimi ve gözatma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Kalıcılığı ve ayarları kaydediliyor](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Dokunmatik giriş](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)