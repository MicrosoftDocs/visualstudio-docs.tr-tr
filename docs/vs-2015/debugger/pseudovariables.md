---
title: Sözde değişken | Microsoft Docs
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
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 79d2f47acfbd5a4b6adf6d5f679fb3b514679dab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789505"
---
# <a name="pseudovariables"></a>Sözde Değişkenler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sözde değişkenler, bir değişken penceresinde belirli bilgileri görüntülemek için kullanılan terimler veya **QuickWatch** iletişim kutusu. Normal bir değişken girebilirsiniz aynı şekilde sahte girebilirsiniz. Sözde değişken değil değişkenler, ancak ve programınızdaki değişken adlarına karşılık gelmez.  
  
## <a name="example"></a>Örnek  
 Yerel kod uygulaması yazdığınızı ve uygulamanızda ayrılan işleyicilerin sayısını görmek istediğinizi varsayalım. İçinde **Watch** penceresinde, aşağıdaki sözde değişkeni girebilirsiniz **adı** sütun sonra onu değerlendirmek için Return tuşuna basın:  
  
```  
$handles  
```  
  
 Yerel kod içinde bu tabloda gösterilen pseudovariables'ı kullanabilirsiniz:  
  
|Sözde değişkeni|İşlev|  
|--------------------|--------------|  
|`$err`|Ayarlama SetLastError işleviyle son hata değeri görüntüler. Görüntülenen değer GetLastError işlevi tarafından döndürülecek temsil eder.<br /><br /> Kullanım `$err,hr` bu değerin kodu çözülmüş biçimini görmek için. Örneğin, son hata 3 ise `$err,hr` görüntüler `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Uygulamanızda ayrılan işleyicilerin sayısını görüntüler.|  
|`$vframe`|Geçerli yığın çerçevesi adresini görüntüler.|  
|`$tid`|Geçerli iş parçacığı için iş parçacığı Kimliğini görüntüler.|  
|`$env`|Dize Görüntüleyicisindeki ortam bloğunu görüntüler.|  
|`$cmdline`|Programı başlatan komut satırı dizesini görüntüler.|  
|`$pid`|İşlem kimliğini görüntüler.|  
|`$` *RegisterName*<br /><br /> veya<br /><br /> `@` *RegisterName*|Kaydının içeriğini görüntüler *registername*.<br /><br /> Normalde, sadece kayıt adı girerek kayıt içeriğini görüntüleyebilirsiniz. Bu sözdizimini kullanmanız gereken yalnızca bir kez, kayıt adı bir değişken adını tekrar yüklediği zamandır. Kayıt adı geçerli kapsamdaki bir değişken adı ile aynı olduğunda, hata ayıklayıcı adı bir değişken adı olarak yorumlar. Bu durumda `$` *registername* veya `@` *registername* faydalı olur.|  
|`$clk`|Saat döngüsünde zamanı görüntüler.|  
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgileriyle bir yapıyı görüntüler. Güvenlik nedeniyle parola bilgisi görüntülenmez.|  
|`$exceptionstack`|Geçerli Windows çalışma zamanı özel durum yığın izleme görüntüler. `$ exceptionstack` Windows 8.1 veya üzeri çalıştıran Store uygulamalarında çalışır. `$ exceptionstack` C++ ve özel durumlar için desteklenmiyor|  
|`$ReturnValue`|.NET Framework yöntemi dönüş değerini görüntüler. Bkz: [yöntem çağrılarının dönüş değerlerini İnceleme](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f)|  
  
 C# ve Visual Basic'te bu tabloda gösterilen pseudovariables'ı kullanabilirsiniz:  
  
|Sözde değişkeni|İşlev|  
|--------------------|--------------|  
|`$exception`|Son özel durum bilgilerini görüntüler. Hiçbir özel durum oluştuysa, değerlendirme `$exception` bir hata iletisi görüntüler.<br /><br /> Visual C# içinde yalnızca, özel durum Yardımcısı'nı devre dışı bırakıldığında `$exception` otomatik olarak eklenir **Yereller** bir özel durum oluştuğunda penceresi.|  
|`$user`|Uygulamayı çalıştıran hesap için hesap bilgileriyle bir yapıyı görüntüler. Güvenlik nedeniyle parola bilgisi görüntülenmez.|  
  
 Visual Basic'te, aşağıdaki tabloda gösterilen pseudovariables'ı kullanabilirsiniz:  
  
|Sözde değişkeni|İşlev|  
|--------------------|--------------|  
|`$delete` veya `$$delete`|Oluşturulan örtük değişkeni siler **hemen** penceresi. Söz dizimi `$delete,` *değişkeni* veya`$delete,` *değişkeni*`.`|  
|`$objectids` veya `$listobjectids`|Tüm etkin nesne Kimlikleri'ni belirtilen ifadenin alt öğesi olarak görüntüler. Söz dizimi `$objectid,` *ifade* veya`$listobjectids,` *ifadesi*`.`|  
|`$` *N* `#`|Eşit nesne Kimliğine sahip nesneyi görüntüler *N*.|  
|`$dynamic`|Özel görüntüler **dinamik Görünüm** uygulayan bir nesne düğümü `IDynamicMetaObjectProvider`. Arabirim. Söz dizimi `$dynamic,` *nesne*. Bu özellik yalnızca .NET Framework sürüm 4 kullanan kod için geçerlidir. Bkz: [dinamik Görünüm](http://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Değişken Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)





