---
title: Eski dil hizmetinde deyim tamamlama | Microsoft Docs
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
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d88ebe84ec3ec5efb1d7c4ac04ebaee50ac65b97
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796499"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Deyim Tamamlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Deyim tamamlama tarafından dil hizmeti bir dil anahtar sözcüğü veya çekirdek Düzenleyicisi'nde yazarak başlatılan öğenin son kullanıcılara yardımcı olur işlemidir. Bu konuda, deyim tamamlama nasıl çalıştığını ve dil hizmetinizde nasıl ele alır.  
  
 Eski dil Hizmetleri bir VSPackage'ı bir parçası olarak uygulanır, ancak dil hizmeti özellikleri uygulamak için daha yeni MEF uzantıları kullanmaktır. Deyim tamamlama uygulamak için en yeni yolu hakkında daha fazla bilgi için bkz: [izlenecek yol: deyim tamamlamayı görüntüleme](../../extensibility/walkthrough-displaying-statement-completion.md).  
  
> [!NOTE]
>  Yeni bir düzenleyici API hemen kullanmaya başlamak öneririz. Bu dil hizmetinizin performansını ve yeni düzenleyici özellikleri yararlanmanıza olanak tanır.  
  
## <a name="implementing-statement-completion"></a>Deyim tamamlama uygulama  
 Çekirdek Düzenleyicisi'nde, deyim tamamlama etkileşimli olarak daha kolay yardımcı olur ve hızlı bir şekilde kod yazan özel bir kullanıcı arabirimini etkinleştirir. Deyim tamamlama, gerektiğinde, ilgili nesneleri veya sınıflar, belirli öğeleri anımsamak veya bir Yardım başvuru konusundaki aramak zorunda kalmadan önler görüntüleyerek yardımcı olur.  
  
 Deyim tamamlama uygulamak için kendi dilinizde ayrıştırılabilir bir deyim tamamlanma tetikleyici olmalıdır. Örneğin, [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] bir nokta (.) işlecini kullanır ancak [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] okun kullanır (->) işleci. Dil hizmeti, birden fazla tetikleyici, deyim tamamlama başlatmak için kullanabilirsiniz. Komut filtreye programlanmış tetikler.  
  
## <a name="command-filters-and-triggers"></a>Komut filtreleri ve tetikleyiciler  
 Tetikleyici veya tetikleyicileri oluşumlarını komutunu filtreleri müdahale. Görünüme komut filtre eklemek için uygulama <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirim ve çağırarak görünümüne eklemek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi. Aynı komutu filtresini kullanabilirsiniz (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) deyim tamamlama, hata işaretçileri ve yöntemi ipuçları gibi dil hizmetinizi tüm yönleri için. Daha fazla bilgi için [kesintiye eski dil hizmeti komutlarını](../../extensibility/internals/intercepting-legacy-language-service-commands.md).  
  
 Tetikleyici düzenleyicide girilen zaman — özellikle metin arabelleğini — daha sonra dil hizmetinizi çağırır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> yöntemi. Bu, kullanıcı deyim tamamlama aday arasından seçebilir böylece UI'yi getirmek Düzenleyici neden olur. Bu yöntem, uygulamak gerektirir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> ve <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> parametre olarak bayrakları. Tamamlama öğeleri listesi, kayan bir liste kutusunda görüntülenir. Kullanıcı yazmaya devam ettikçe seçim liste kutusu içinde en yakın eşleşme en son karakter için yazılan yansıtacak şekilde güncelleştirilir. Çekirdek Düzenleyici deyim tamamlama için kullanıcı arabirimini uygular, ancak dil hizmeti uygulamalıdır <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> deyimi için aday tamamlama öğeleri kümesini tanımlamak için arabirim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski Dil Hizmeti Komutlarını Kesme](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

