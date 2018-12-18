---
title: 'Nasıl yapılır: hata ayıklama için bir .NET Framework sürümü belirtme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c6d6601c5b3affdd57d49d0461c4f3d8e487c67
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769058"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Nasıl Yapılır: Hata Ayıklama İçin .NET Framework Sürümü Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Hata ayıklayıcı, hata ayıklama Microsoft eski sürümlerini destekler [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] geçerli sürümü yanı sıra. Visual Studio'dan bir uygulamayı başlatırsanız, hata ayıklayıcı her zaman doğru sürümünü tanımlayabilirsiniz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ayıkladığınız uygulama için. Uygulama zaten çalışıyor ve kullanırsanız **ekleme**, hata ayıklayıcı her zaman daha eski bir sürümünü belirlemek mümkün olmayabilir [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Böyle bir durumda bildiren bir hata iletisi alırsınız,  
  
 Hata ayıklayıcı hakkında yanlış bir varsayım yaptı [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] uygulamanızı kullanmak geçmeye sürümü.  
  
 Bu nadiren de olsa, hata ayıklayıcı için hangi sürümün kullanılacağını belirtmek için bir kayıt defteri anahtarını ayarlayabilirsiniz.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için bir .NET Framework sürümünü belirtmek için  
  
1.  ' % S'dizini, makinenizde yüklü .NET Framework sürümlerini bulmak için Windows\Microsoft.NET\Framework bakın. Sürüm numaraları aşağıdaki gibi görünmelidir:  
  
     `V1.1.4322`  
  
     Doğru sürüm numarasını belirleyin ve bir not edin.  
  
2.  Başlangıç **Kayıt Defteri Düzenleyicisi'ni** (regedit).  
  
3.  İçinde **Kayıt Defteri Düzenleyicisi'ni**, HKEY_LOCAL_MACHINE klasörü açın.  
  
4.  Gidin: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Anahtar mevcut değilse HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine sağ tıklayın ve **yeni anahtar**. Yeni anahtar adı `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  {449EC4CC-30D2-4032-9256-EE18EB41B62B için} ayrıldıktan sonra konum **adı** sütun ve bulma CLRVersionForDebugging anahtarı.  
  
    1.  Anahtar mevcut değilse {449EC4CC-30D2-4032-9256-EE18EB41B62B} sağ tıklayın ve **yeni bir dize değeri**. Ardından yeni bir dize değeri sağ tıklayın, **Yeniden Adlandır**ve türü `CLRVersionForDebugging`.  
  
6.  Çift **CLRVersionForDebugging**.  
  
7.  İçinde **dize Düzenle** .NET Framework sürüm numarasını yazın **değer** kutusu. Örneğin: V1.1.4322  
  
8.  **Tamam**'ı tıklatın.  
  
9. Kapat **Kayıt Defteri Düzenleyicisi'ni**.  
  
     Hata ayıklama başlattığınızda doğrulayın almaya devam ediyorsanız bir hata iletisi kayıt defterinde sürüm numarası doğru girdiniz. Ayrıca, bir sürümünü kullandığınızı doğrulayın [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Visual Studio tarafından desteklenir. Hata ayıklayıcı geçerli .NET Framework sürümünü ve önceki sürümleri ile uyumludur, ancak gelecekteki sürümleri ile ileri doğru uyumlu olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)



