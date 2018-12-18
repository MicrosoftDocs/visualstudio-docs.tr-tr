---
title: Hata ayıklama için .NET Framework sürümü belirtme | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 86289c9a93a0bb9e0f7756443d79f4a1a6dd38a6
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53056014"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Nasıl yapılır: hata ayıklama için bir .NET Framework sürümü belirtme (C#, Visual Basic F#)

Visual Studio hata ayıklayıcısını destekleyen Microsoft eski sürümlerini hata ayıklama [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] geçerli sürümü yanı sıra. Visual Studio'dan bir uygulamayı başlatırsanız, hata ayıklayıcı her zaman doğru sürümünü tanımlayabilirsiniz [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] ayıkladığınız uygulama için. Uygulama zaten varsa ancak çalışan ve kullanarak hata ayıklamayı Başlat **ekleme**, hata ayıklayıcı her zaman daha eski bir sürümünü belirlemek mümkün olmayabilir [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Böyle bir durumda bildiren bir hata iletisi alırsınız,  

``` cmd 
The debugger has made an incorrect assumption about the [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] version your application is going to use.  
```

Bu hata göründüğü nadir durumlarda, hata ayıklayıcı için hangi sürümün kullanılacağını belirtmek için bir kayıt defteri anahtarı ayarlayabilirsiniz.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Hata ayıklama için bir .NET Framework sürümünü belirtmek için  
  
1. ' % S'dizini, makinenizde yüklü .NET Framework sürümlerini bulmak için Windows\Microsoft.NET\Framework bakın. Sürüm numaraları aşağıdaki gibi görünmelidir:  
  
    `V1.1.4322`  
  
    Doğru sürüm numarasını belirleyin ve bir not edin.  
  
2. Başlangıç **Kayıt Defteri Düzenleyicisi'ni** (regedit).  
  
3. İçinde **Kayıt Defteri Düzenleyicisi'ni**, HKEY_LOCAL_MACHINE klasörü açın.  
  
4. Gidin: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
    Anahtar mevcut değilse HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine sağ tıklayın ve **yeni anahtar**. Yeni anahtar adı `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. {449EC4CC-30D2-4032-9256-EE18EB41B62B için} ayrıldıktan sonra konum **adı** sütun ve bulma CLRVersionForDebugging anahtarı.  
  
   1.  Anahtar mevcut değilse {449EC4CC-30D2-4032-9256-EE18EB41B62B} sağ tıklayın ve **yeni bir dize değeri**. Ardından yeni bir dize değeri sağ tıklayın, **Yeniden Adlandır**ve türü `CLRVersionForDebugging`.  
  
6. Çift **CLRVersionForDebugging**.  
  
7. İçinde **dize Düzenle** .NET Framework sürüm numarasını yazın **değer** kutusu. Örneğin: V1.1.4322  
  
8. **Tamam**'ı tıklatın.  
  
9. Kapat **Kayıt Defteri Düzenleyicisi'ni**.  
  
     Hata ayıklama başlattığınızda doğrulayın almaya devam ediyorsanız bir hata iletisi kayıt defterinde sürüm numarası doğru girdiniz. Ayrıca, bir sürümünü kullandığınızı doğrulayın [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Visual Studio tarafından desteklenir. Hata ayıklayıcı geçerli .NET Framework sürümünü ve önceki sürümleri ile uyumludur, ancak gelecekteki sürümleri ile ileri doğru uyumlu olmayabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)