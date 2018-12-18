---
title: Dil yer alan | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9edaed1eef81d493bdd29311893caef93447e6f7
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231750"
---
# <a name="contained-languages"></a>Kapsanan dilleri

*Bulunan diller* diğer diller tarafından bulunan diller. Örneğin, HTML biçiminde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sayfalar içerebilir [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] veya [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] betikler. Bir çift dil mimarisi için gerekli olan *.aspx* HTML ve komut dosyası dili için IntelliSense, renklendirme ve diğer düzenleme sağlamak için dosya Düzenleyicisi özellikleri.

## <a name="implementation"></a>Uygulama

Uygulamanız için bağımsız dillerini en önemli arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimi. Bu arabirim, bir birincil dili içinde barındırılan herhangi bir dil tarafından uygulanır. Dil hizmetin Renklendirici, metin Görünümü Filtresi ve birincil dil hizmeti kimliği erişmenizi sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Oluşturmanızı sağlayan bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimi. Aşağıdaki adımlar nasıl uygulayacağınızı içindeki bir dil gösterir:

1.  Kullanım `QueryService()` dil hizmet kimliği ve arabirimi Kimliğini almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.

2.  Oluşturmak için bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirim, çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> yöntemi. Başarılı bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi, bir veya daha fazla [kimlikleri öğesi](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>)ve bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> arabirimi.

3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Metin arabelleği Düzenleyicisi nesnedir, arabirim, bir birincil dosya bir konumda ikincil dilin arabelleğine eşleştirmek için gereken temel hizmetleri sağlar.

     Örneğin, tek bir içinde *.aspx* dosya, birincil dosya ASP, HTML ve içerdiği tüm kod içerir. Ancak, ikincil arabellek yalnızca ikincil arabelleği geçerli kod dosyası yapmak için bir sınıf tanımları birlikte içindeki kodu içerir. Arabellek Düzenleyici bir arabellek düzenlemeleri birbirleriyle koordine işini gerçekleştirir.

4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Birincil dili olan yöntemi ilgili metin ikincil arabellekteki metni, arabellek içinde eşlendiği arabellek Düzenleyici söyler.

     Bir dizide dil geçirir <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> yapısı, şu anda yalnızca bir birincil ve ikincil bir yayılma içerir.

5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Yöntemi ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> yöntem birincil ikincil arabelleğe ve eşleme sağlar.