---
title: 'İzlenecek yol: özel düzenleyici oluşturma | Microsoft Docs'
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
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b7c8bd8643b6c670e614f4745650f42ccca35f5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809746"
---
# <a name="walkthrough-creating-a-custom-editor"></a>İzlenecek Yol: Özel Düzenleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage proje şablonu basit bir özel düzenleyici, C++'da oluşturabilirsiniz.  VSPackage proje şablonu, artık C# veya Visual Basic projeleri destekler. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'sını yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio Paket projesi şablonu  
 Visual Studio Paketi proje şablonunu bulunabilir **yeni proje** C++ genişletilebilirlik klasöründe iletişim  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio Paketi şablonu kullanarak bir VSPackage'ı oluşturmak için  
  
1.  Visual Studio Paketi şablonu ile bir proje oluşturun.  
  
2.  Seçin **özel düzenleyici** seçeneğini ve tıklayın **sonraki**. **Düzenleyici Seçenekleri** sayfası görüntülenir.  
  
3.  Düzenleyicinizde adı **Düzenleyici adı** kutusu. Düzenleyicinizde ilişkili olmasını istediğiniz dosya uzantısı türü **dosya uzantısı** kutusu. Düzenleyici, bu uzantılı dosyalar için kullanılabilir. Dosya uzantısı için Visual Studio, Windows için değil yalnızca kaydedilir. Düzenleyicinizde ile oluşturulan yeni belgeler için varsayılan dosya adı yazın **varsayılan dosya adı** kutusu.  
  
4.  Tıklayın **son** belirttiğiniz klasöre, VSPackage'ı oluşturmak için.  
  
### <a name="to-test-your-custom-editor"></a>Özel düzenleyiciniz test etmek için  
  
1.  Üzerinde **dosya** menüsünde **yeni** ve ardından **dosya**.  
  
2.  İçinde **yüklü şablonlar** bölmesinde **yeni dosya** dosya şablonu ve ardından dosyayı, yalnızca kayıtlı iletişim kutusunda, türünü seçin.  
  
3.  Tıklayın **açık** görüntüleme ve belgeyi düzenleyebilir.  
  
     Düzenleyici açık yük Kes ve Yapıştır ve Bul ve Değiştir işlemleri destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)

