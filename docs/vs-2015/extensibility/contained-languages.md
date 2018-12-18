---
title: Dil yer alan | Microsoft Docs
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
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4ff50fe0fe156c548351c378ba3a256e230ec43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772033"
---
# <a name="contained-languages"></a>Kapsanan dilleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

  
*Bulunan diller* diğer diller tarafından bulunan diller. Örneğin, HTML biçiminde [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] sayfalar içerebilir [!INCLUDE[csprcs](../includes/csprcs-md.md)] veya [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] betikler. Bir çift dil mimarisi, .aspx dosyası Düzenleyicisi HTML ve komut dosyası dili için IntelliSense, renklendirme ve diğer düzenleme özellikleri sağlamak için gereklidir.  
  
## <a name="implementation"></a>Uygulama  
 Uygulamanız için bağımsız dillerini en önemli arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimi. Bu arabirim, bir birincil dili içinde barındırılan herhangi bir dil tarafından uygulanır. Dil hizmetin Renklendirici, metin Görünümü Filtresi ve birincil dil hizmeti kimliği erişmenizi sağlar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Oluşturmanızı sağlayan bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimi. Aşağıdaki adımlar nasıl uygulayacağınızı içindeki bir dil gösterir:  
  
1.  Kullanım `QueryService()` dil hizmet kimliği ve arabirimi Kimliğini almak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> yöntemi oluşturmak için bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> arabirimi. Başarılı bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> arabirimi, bir veya daha fazla [kimlikleri öğesi](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> arabirimi.  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Metin arabelleği Düzenleyicisi nesnedir, arabirim, bir birincil dosya bir konumda ikincil dilin arabelleğine eşleştirmek için gereken temel hizmetleri sağlar.  
  
     Örneğin, bir tek bir .aspx dosyasına ASP, HTML ve içerdiği tüm kod birincil dosya içerir. Ancak, ikincil bir arabellek ikincil arabelleği geçerli kod dosyası yapmak için bir sınıf tanımları ile birlikte yalnızca kapsanan kod içerir. Arabellek Düzenleyici bir arabellek düzenlemeleri birbirleriyle koordine işini gerçekleştirir.  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Birincil dili olan yöntemi ilgili metin ikincil arabellekteki metni, arabellek içinde eşlendiği arabellek Düzenleyici söyler.  
  
     Bir dizide dil geçirir <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> yapısı, şu anda yalnızca bir birincil ve ikincil bir yayılma içerir.  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Yöntemi ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> yöntem birincil ikincil arabelleğe ve eşleme sağlar.

