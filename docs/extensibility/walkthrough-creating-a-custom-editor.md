---
title: 'İzlenecek yol: özel düzenleyici oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9110e1c2ac6c39898f7dbbd6f9f4412ebcba278
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497443"
---
# <a name="walkthrough-create-a-custom-editor"></a>İzlenecek yol: özel düzenleyici oluşturma
VSPackage proje şablonu basit bir özel düzenleyici, C++'da oluşturabilirsiniz. VSPackage proje şablonu, artık C# veya Visual Basic projeleri destekler. Daha fazla bilgi için [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda takip etmek için Visual Studio SDK'yı yüklemeniz gerekir. Daha fazla bilgi için [Visual Studio SDK'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Visual Studio Paket projesi şablonu  
 Visual Studio Paket projesi şablon bulabilirsiniz **yeni proje** iletişim altında **C++ genişletilebilirlik** klasör.  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio Paket şablonu kullanarak bir VSPackage'ı oluşturmak için  
  
1.  Visual Studio Paketi şablonu ile bir proje oluşturun.  
  
2.  Seçin **özel düzenleyici** seçeneğini ve tıklayın **sonraki**. **Düzenleyici Seçenekleri** sayfası görüntülenir.  
  
3.  Düzenleyicinizde adı **Düzenleyici adı** kutusu. Düzenleyicinizde ilişkili olmasını istediğiniz dosya uzantısı türü **dosya uzantısı** kutusu. Düzenleyici, bu uzantılı dosyalar için kullanılabilir. Dosya uzantısı için Visual Studio, Windows için değil yalnızca kaydedilir. Düzenleyicinizde ile oluşturulan yeni belgeler için varsayılan dosya adı yazın **varsayılan dosya adı** kutusu.  
  
4.  Tıklayın **son** belirttiğiniz klasöre, VSPackage'ı oluşturmak için.  
  
### <a name="to-test-your-custom-editor"></a>Özel düzenleyiciniz test etmek için  
  
1.  Üzerinde **dosya** menüsünde **yeni** ve ardından **dosya**.  
  
2.  İçinde **yüklü şablonlar** bölmesinde **yeni dosya** dosya şablonu ve ardından dosyayı, kayıtlı iletişim kutusunda, türünü seçin.  
  
3.  Tıklayın **açık** görüntüleme ve belgeyi düzenleyebilir.  
  
     Düzenleyici açık yük Kes ve Yapıştır ve Bul ve Değiştir işlemleri destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage’lar](../extensibility/internals/vspackages.md)