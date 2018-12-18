---
title: Deyim tamamlama eski dil hizmetindeki | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d76face8f43bcb428a9c3b997083f8299d332cc8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131333"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Eski dil hizmetindeki deyim tamamlama
Deyim tamamlama dil anahtar sözcüğü veya çekirdek Düzenleyicisi'nde yazmaya başladı öğesi son kullanıcılara yardımcı dil hizmeti tarafından işlemidir. Deyim tamamlama nasıl çalıştığını ve nasıl dil hizmetinizi uygulamak bu konuda açıklanmaktadır.  
  
 Eski dil hizmetler bir VSPackage bir parçası olarak uygulanır, ancak dil hizmet özellikleri uygulamak için daha yeni MEF uzantıları kullanmak için bir yoludur. Deyim tamamlama uygulamak için yeni yolu hakkında daha fazla bilgi için bkz: [izlenecek yol: deyim tamamlama görüntüleme](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Yeni Düzenleyicisi API mümkün olan en kısa sürede kullanmaya başlamanızı öneriyoruz. Bu dil hizmetinizin performansını ve yeni Düzenleyicisi özelliklerden yararlanmak sağlar.  
  
## <a name="implementing-statement-completion"></a>Deyim tamamlama uygulama  
 Çekirdek Düzenleyicisi'nde, deyim tamamlama, etkileşimli olarak daha kolay yardımcı olur ve hızlı bir şekilde kod yazma özel bir kullanıcı arabirimini etkinleştirir. Deyim tamamlama, gerektiğinde, ilgili nesneleri veya sınıfları, belirli öğeleri anımsamak veya bir Yardım Başvurusu konusuna bakarak gerek kalmadan önler görüntüleyerek yardımcı olur.  
  
 Deyim tamamlama uygulamak için dilinizi ayrıştırılabilir bir deyim tamamlama tetikleyici olması gerekir. Örneğin, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] bir nokta (.) işlecini kullanan sırada [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] bir ok kullanır (->) işleci. Bir dil hizmeti birden çok tetikleyici deyim tamamlama başlatmak için kullanabilirsiniz. Bu tetikleyicileri komutu filtrede programlanmış.  
  
## <a name="command-filters-and-triggers"></a>Komut filtreleri ve Tetikleyicileri  
 Komutunu filtreleri tetikleyici veya tetikleyicileri oluşumları kesebilir. Komut filtresi görünümüne eklemek için uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim ve çağırarak görünümüne ekleyin <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi. Aynı komutu filtresini kullanabilirsiniz (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) tüm yönlerini deyim tamamlama, hata işaretçileri ve yöntemi ipuçları gibi dil hizmetiniz için. Daha fazla bilgi için bkz: [kesintiye uğratan eski dil hizmeti komutları](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Tetikleyici Düzenleyicisi'nde girilen zaman — özellikle metin arabelleğini — dil hizmetinizi sonra çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi. Bu, böylece kullanıcı deyimi tamamlama aday arasından UI'yi getirmek Düzenleyicisi neden olur. Bu yöntem, uygulamanızı gerektirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ve <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> bayrakları parametre olarak. Tamamlama öğeleri listesi kayan bir liste kutusunda görüntülenir. Kullanıcı yazmaya devam ettikçe, seçim liste kutusu içinde en yakın bir eşleşme en son karakter yazılan yansıtacak şekilde güncelleştirilir. Deyim tamamlama ilişkin kullanıcı Arabirimi çekirdek Düzenleyicisi'ni uygular, ancak dil hizmeti uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> deyim için aday tamamlama öğeleri tanımlamak için arabirim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Komutlarını Kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)