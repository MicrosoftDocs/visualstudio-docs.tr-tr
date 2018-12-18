---
title: Sözde değişkenler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: af106709ca578abeab19c4f474548476efbeea57
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057693"
---
# <a name="pseudovariables-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısında sözde değişkenler
Sözde değişkenler olan bir değişken penceresinde belirli bilgileri görüntülemek için kullanılan terimler veya **QuickWatch** iletişim kutusu. Normal bir değişken girersiniz aynı şekilde bir pseudovariable girebilirsiniz. Sözde değişkenler değil değişkenleri, ancak ve değişken adlarıyla programınızdaki karşılık.  
  
## <a name="example"></a>Örnek  
 Yerel kod uygulamasına yazma ve uygulamanızda ayrılan tanıtıcı sayısı görmek istediğinizi varsayalım. İçinde **izleme** penceresinde, aşağıdaki pseudovariable girebilirsiniz **adı** sütun sonra değerlendirmek için Return tuşuna basın:  
  
`$handles`
  
 Yerel kodda bu tabloda gösterilen sözde değişkenler kullanabilirsiniz:  
  
|Pseudovariable|İşlev|  
|--------------------|--------------|  
|`$err`|Set SetLastError işlevi ile en son hata değeri görüntüler. Görüntülenen değer GetLastError işlevi tarafından döndürülen temsil eder.<br /><br /> Kullanım `$err,hr` kodu çözülmüş formun bu değer görmek için. Örneğin, son hata 3 ise `$err,hr` görüntüler `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`|  
|`$handles`|Uygulamanızda ayrılan tanıtıcı sayısını görüntüler.|  
|`$vframe`|Geçerli yığın çerçevesini adresini görüntüler.|  
|`$tid`|Geçerli iş parçacığı için iş parçacığı kimliği görüntüler.|  
|`$env`|Ortam bloğu dize Görüntüleyicisi'nde görüntüler.|  
|`$cmdline`|Başlatılan program komut satırı dizesi görüntüler.|  
|`$pid`|İşlem kimliğini görüntüler.|  
|`$` *RegisterName*<br /><br /> veya<br /><br /> `@` *RegisterName*|Kayıt içeriğini görüntüler *registername*.<br /><br /> Normalde, yalnızca kayıt adı girerek yazmaç içerikleri görüntüleyebilirsiniz. Yazmaç adı bir değişken adı overloads şu sözdizimini kullanmanız gereken yalnızca bir kez durumdur. Yazmaç adı geçerli kapsamdaki bir değişken adı ile aynı olduğunda, hata ayıklayıcı adı değişken adı olarak yorumlar. Ne zaman olan `$` *registername* veya `@` *registername* faydalı olur.|  
|`$clk`|Saat döngüleri süreyi görüntüler.|  
|`$user`|Uygulama çalıştıran hesabın hesap bilgileriyle yapısını görüntüler. Güvenlik nedenleriyle, parola bilgilerini görüntülenmez.|  
|`$exceptionstack`|Geçerli Windows çalışma zamanı özel durum yığın izlemesi görüntüler. `$ exceptionstack` yalnızca UWP uygulamalarında çalışır. `$ exceptionstack` C++ ve SEH özel durumlar için desteklenmiyor|  
|`$ReturnValue`|.NET Framework yönteminin dönüş değeri görüntüler.|  
  
 C# ve Visual Basic bu tabloda gösterilen sözde değişkenler kullanabilirsiniz:  
  
|Pseudovariable|İşlev|  
|--------------------|--------------|  
|`$exception`|Son özel durum bilgilerini görüntüler. Hiçbir özel durum oluştu, değerlendirme `$exception` bir hata iletisi görüntüler.<br /><br /> Visual C# içinde yalnızca, özel durum Yardımcısı'nı devre dışı bırakıldığında `$exception` otomatik olarak eklenen **Yereller** bir özel durum oluştuğunda penceresi.|  
|`$user`|Uygulama çalıştıran hesabın hesap bilgileriyle yapısını görüntüler. Güvenlik nedenleriyle, parola bilgilerini görüntülenmez.|  
  
 Visual Basic'te, aşağıdaki tabloda gösterilen sözde değişkenler kullanabilirsiniz:  
  
|Pseudovariable|İşlev|  
|--------------------|--------------|  
|`$delete` veya `$$delete`|Oluşturulan bir örtük değişkeni siler **hemen** penceresi. Sözdizimi `$delete,` *değişkeni* veya`$delete,` *değişken*`.`|  
|`$objectids` veya `$listobjectids`|Tüm etkin nesne kimlikleri, belirtilen ifade alt olarak görüntüler. Sözdizimi `$objectid,` *ifade* veya`$listobjectids,` *ifadesi*`.`|  
|`$` *N* `#`|Nesne Kimliği eşit görüntüler nesnesiyle *N*.|  
|`$dynamic`|Özel görüntüler **dinamik Görünüm** uygulayan bir nesne için düğüm `IDynamicMetaObjectProvider`. arabirim. Sözdizimi `$dynamic,` *nesne*. Bu özellik .NET Framework sürüm 4 kullanan kodu geçerlidir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme ve QuickWatch Windows](../debugger/watch-and-quickwatch-windows.md)   
 [Değişken pencereler](../debugger/debugger-windows.md)