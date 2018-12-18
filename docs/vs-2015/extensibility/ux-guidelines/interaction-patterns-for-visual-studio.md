---
title: Etkileşim Desenleri
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f77848babfbddc4d12ac6d599c8e77d2b598534
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053311"
---
# <a name="interaction-patterns-for-visual-studio"></a>Visual Studio için etkileşim desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="overview"></a>Genel Bakış
 Bir tasarım deseni, genel olarak, çekirdeği kısıtlamaları benzer kümeleriyle ilgili sorunları çözmek için belirli durumlarda uygulanabilir bir tasarım olur. Özellik ve sistem tasarımcılarına bu tasarım desenleri, ardından kendi özel durum için uyarlanabilir noktaları, başlangıç olarak kullanın.

 Visual Studio, kitaplığa yeni özellikler oluştururken dikkate alınması ortak etkileşim düzeni sahiptir. Bizim tasarım modelleri için iki çekirdek bağlamları vardır: Visual Studio istemcisi (devenv) ve Visual Studio Online. Bazı tasarım sorunlar için tüm durumlarda düzgün çalışıyor bulunabilen bir düzeni vardır. Çoğu durumda, ancak çözüm bir tarayıcısı ve bir istemci uygulamasında barındırılan, içinde sunulan kullanıcı arabirimi farklı olabilir.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio istemci Deseni türleri

|Desen türü|Açıklama|Örnekler|
|------------------|-----------------|--------------|
|**Uygulama düzeyi desenleri**|Belirleme veya uygulama içeriği görüntüleme ve bunların içindeki bileşik ve denetim desenleri içeren uygulama için ortak üst düzey desenleri|-Araç pencereleri<br />-Belge pencereleri|
|**Bileşik desenler**|Uygulama desenleri arasında yayılabilir ortak desenler veya farklı bir yapılandırmada çeşitli denetimler oluşan tanınan bir deseni|-Görünümü değiştirme<br />-List oluşturucular<br />-Verileri görüntüleme<br />-Bildirimler<br />-Doğrulama<br />-Seçimi modelleri|
|**Denetim desenleri**|Özellikleri nasıl alt düzey denetimleri hakkında davranış beklenir|-Ağaç görünümleri<br />-Bir kılavuz denetimi içinde düzenleme|

## <a name="application-patterns"></a>Uygulama desenleri
 Yüksek düzeyde, Visual Studio arabirimini birden çok windows, iletişim kutuları, komutları ve araç çubukları tek bir IDE içinde oluşur. Visual Studio hiyerarşisi bağlam ve sürücüleri menüleri belirler. Belge pencerelerini, araç pencerelerini, projeler, komut yapısını, metin düzenleyici, araç, Özellikler penceresinde ve araçları kullanıcı arabiriminde anahtar tümleştirme noktaları IDE olan > Seçenekleri.

 Her bir kullanıcı arabiriminde anahtar tümleştirme noktası IDE için temel kullanım desenlerini vardır:

-   [Visual Studio İçin Menüler ve Komutlar](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

-   [Visual Studio İçin Uygulama Desenleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

    -   [Pencere etkileşimleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

    -   [Araç pencereleri](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

    -   [Belge Düzenleyicisi kuralları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

    -   [İletişim Kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

    -   [Projeler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Yaygın denetim desenleri
 Denetim desenleri, çoğunlukla tek denetimleri hakkında davranış beklenir alır. Bu tutarlılık en önemli bir noktadır.

 Visual Studio'da ortak denetimleri Masaüstü Windows yönergeleri izlemelidir. Koşullarımıza yalnızca, Visual Studio özgü etkileşimleri veya basamak, biz yönergeleri tamamen Gelişmiş kullanıcılarımızın gereksinimlerini karşılamak için Visual Studio uyarlamak için yerine geçen genel kurallar genişletmek ihtiyacımız olan alanları içerir.

-   [Visual Studio İçin Yaygın Denetim Desenleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

    -   [Ortak Denetimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

    -   [Metin denetimi](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

    -   [Düğmeler ve köprüleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Bileşik desenler
 Çeşitli görevleri gerçekleştirmek üzere kullanıcıların beklediğiniz yollar vardır. Mümkün olduğunda, bu desenleri hem etkileşim ve görsel tasarım için kullanılacak özellikleri tasarlanmalıdır.

 En önemli bazı Visual Studio içinde birçok bileşik desenler varken bakımından tutarlılık şunlardır:

-   [Visual Studio İçin Bileşik Desenler](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

    -   [Nesne üzerinde kullanıcı Arabirimi ve gözatma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

    -   [Seçimi modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

    -   [Kalıcılığı ve ayarları kaydediliyor](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

    -   [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
