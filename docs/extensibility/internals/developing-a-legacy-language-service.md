---
title: Eski dil hizmeti geliştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d92c07742dcc4433aa96071d655f58d938a1f80
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497836"
---
# <a name="develop-a-legacy-language-service"></a>Eski dil hizmeti geliştirme
Bu bölüm yardımcı olacak konulara bağlantılar eski dil hizmeti oluşturun.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Dil hizmeti uygulamak için en yeni yolu hakkında daha fazla bilgi için bkz: [düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="in-this-section"></a>Bu bölümde  
 [Eski dil hizmetinin modeli](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Minimal dil hizmeti için modeli sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] çekirdek Düzenleyici. Bu model, kendi dil hizmeti oluşturmak için bir kılavuz olarak kullanabilirsiniz.  
  
 [Eski dil Hizmeti Arabirimleri](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Dil hizmeti uygulamak için gereken nesneleri açıklanır ve söz dizimi vurgulama, yöntem verileri ve diğer özellikleri sağlamak için kullanabileceğiniz ek nesnelerin bir listesini sağlar.  
  
 [Eski dil hizmeti komutlarını ıntercept](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Dil hizmetinize metin görünümünü aksi işlemek ıntercept komutları komut filtre eklemek açıklar.  
  
 [Eski dil hizmeti kaydedin](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Dil hizmetinizi kullanarak kaydetme hakkında bilgi sağlar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Hata ayıklama için dil hizmeti desteği](../../extensibility/internals/language-service-support-for-debugging.md)  
 Dil hizmeti bir hata ayıklayıcı destekleyecek şekilde süreçlerinizi nasıl sağlayabilirsiniz açıklar.  
  
 [Denetim listesi: eski dil hizmeti oluşturma](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Oluşturma ve çekirdek Düzenleyicisi için bir dil hizmeti tümleştirmek için adım adım yönergeler sağlar.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [Eski dil hizmetinde söz dizimi renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Uygulama, dil hizmetinde söz dizimi vurgulama anlatılmaktadır.  
  
 [Eski dil hizmetinde deyim tamamlama](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Deyim tamamlama, bir dil anahtar sözcüğü veya yazarak başlatılan öğenin son kullanıcılara yardımcı olan tarafından bir dil hizmeti işlemi açıklanır.  
  
 [Eski dil hizmetinde parametre bilgisi](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Aşırı yüklenmiş işlevlere ve metotlara için yöntemi ipuçları sağlanacağı anlatılmaktadır.  
  
 [Nasıl yapılır: gizli metin sağlayın eski dil hizmetinde desteği](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Gizli metin alanının amacını ve gizli metin bölge ekleme hakkında yönergeler sağlar.  
  
 [Nasıl yapılır: eski dil hizmetinde genişletilmiş ana hat oluşturma desteği sağlar](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Ana hat oluşturma desteği destekleyen ötesinde dil genişleten iki seçenek açıklanır *tanımlara Daralt* komutu.