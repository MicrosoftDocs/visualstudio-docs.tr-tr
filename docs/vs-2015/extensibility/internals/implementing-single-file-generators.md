---
title: Tek dosya oluşturucular ekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 36aa6df6c0b904ad11f0027c4e01368a9c864b8a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781679"
---
# <a name="implementing-single-file-generators"></a>Tek Dosya Oluşturucular Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Özel araç — bazen tek dosya oluşturucu olarak da adlandırılır — genişletmek için kullanılan [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ve [!INCLUDE[csprcs](../../includes/csprcs-md.md)] proje sistemleri [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Özel araç uygulayan bir COM bileşenidir <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimi. Bu arabirim kullanarak özel bir araç tek çıktı dosyasına tek bir giriş dosyası dönüştürür. Dönüştürme sonucunu kaynak kodu olabilir veya diğer yararlı olan çıktı. İki örnek özel aracı tarafından oluşturulan kodu dosyalarının bir görsel tasarımcı ve Web Hizmetleri Açıklama Dili (WSDL) kullanılarak oluşturulan dosyaları değişikliklere yanıt olarak oluşturulan kodu verilmiştir.  
  
 Özel bir aracı yüklenir ve giriş dosyası kaydedilir, proje sistemi çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> yöntemi ve bir başvuru geçirir bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> yapabildiği aracın rapor edebilir, ilerleme durumunu kullanıcıya geri çağırma arabirimi.  
  
 Özel aracının oluşturduğu çıkış dosyası bağımlılığı bulunan Giriş dosyası projeye eklenir. Proje sistemi otomatik olarak özel aracın uygulaması tarafından döndürülen dize göre çıktı dosyası adını belirleyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.  
  
 Özel araç uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> arabirimi. İsteğe bağlı olarak, özel araçları desteği <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> giriş dosyası dışındaki bir kaynaktan bilgi almak için arabirim. Özel araç kullanabilmeniz için herhangi bir durumda, sistem veya kaydetmelisiniz [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] yerel kayıt defteri. Özel Araçlar kaydetme ile ilgili daha fazla bilgi için bkz: [tek dosya oluşturucuları kaydetme](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir projenin varsayılan Namespace belirleme](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Türleri Görsel Tasarımcıların Kullanımına Sunma](../../extensibility/internals/exposing-types-to-visual-designers.md)

