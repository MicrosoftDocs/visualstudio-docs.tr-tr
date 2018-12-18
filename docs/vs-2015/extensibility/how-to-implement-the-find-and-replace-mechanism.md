---
title: 'Nasıl yapılır: uygulama Bul ve Değiştir mekanizması | Microsoft Docs'
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
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 34639c535be14b2bcead44631fb83cf46e4f0eb8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737223"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Nasıl yapılır: uygulama Bul ve Değiştir mekanizması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Bul/Değiştir kullanmanın iki yolu sağlar. Bir metin resim kabuğa geçirin ve, arama, vurgulama ve değiştirmeyi metin işlemek yoludur. Bu, kullanıcıların birden çok metin yayılma belirtmesine izin verir. Alternatif olarak, bu işlev, VSPackage'ı kontrol edebilirsiniz. Her iki durumda da geçerli hedef ve bütün açık belgeleri hedeflerini hakkında Kabuk bildirmeniz gerekir.  
  
### <a name="to-implement-findreplace"></a>Bul/Değiştir uygulamak için  
  
1.  Uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> çerçeve özellikleri tarafından döndürülen nesne bir arabirimdeki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> veya <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>. Özel bir düzenleyici oluşturuyorsanız, özel düzenleyici sınıfı bir parçası olarak bu arabirimi uygulamalıdır.  
  
2.  Kullanım <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> düzenleyiciniz destekleyen seçenekleri belirtin ve metin, görüntü arama uygulayıp uygulamadığını belirtmek için yöntemi.  
  
     Düzenleyici metin, görüntü arama destekliyorsa, uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.  
  
     Aksi takdirde uygulama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.  
  
3.  Uygularsanız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> yöntemleri çağırarak arama görevlerinizi basitleştirebilecek <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>

