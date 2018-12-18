---
title: RequireJS için IntelliSense'i özelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7b1c32d0096742c2364e5ac3b8afe59b39152b2b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49246720"
---
# <a name="customizing-intellisense-for-requirejs"></a>RequireJS için IntelliSense'i özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2013 güncelleştirme 4 ile başlayarak, popüler RequireJS JavaScript dosyası ve modüler Yükleyicisi için destek desteklenir. RequireJS kod modülleri arasındaki bağımlılıkları tanımlayın ve dinamik olarak yalnızca gerektiğinde modülleri yüklemek için daha kolay hale getirir. Modüller için bilgisayarınızda modülü tanımınızdan başvurulan veya kullanılarak başvurulan olması için sağlanan RequireJS kullanan bir JavaScript kodu yazarken IntelliSense önerileri olacaktır `require()` gelen kod içinde.  
  
 Varsayılan olarak, Visual Studio RequireJS desteklemek için çok basit bir yapılandırma destekler, ancak kendi özel yapılandırma ayarları ayarlamak için yaygın bir uygulamadır (diğer bir deyişle, diğer adlar kitaplıkları tanımlamak için). Bu konuda, Visual Studio projenizin benzersiz kurulum ile çalışmak için özelleştirebileceğiniz farklı yollarını açıklar.  
  
 Bu konu açıklar nasıl yapılır:  
  
-   RequireJS ASP.NET projelerinde özelleştirme  
  
-   Apache Cordova uygulamaları, Windows Store uygulamaları ve LightSwitch HTML uygulamaları oluşturmak için kullanılan JSProj projelerinde RequireJS özelleştirme  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>RequireJS ASP.NET projelerinde özelleştirme  
 RequireJS için destek require.js adlı bir dosya, geçerli bir JavaScript dosyası tarafından başvurulduğunda otomatik olarak etkinleştirilir (daha fazla bilgi için bkz: IntelliSense bağlamını belirleme bölümünde [JavaScript IntelliSense](../ide/javascript-intellisense.md)). ASP.NET projelerinde require.js başvuran genellikle yapılır kullanarak bir / / / \<başvuru / > _references.js dosyasındaki bir yönerge.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Ana veri özniteliği'te ASP.NET projesi yapılandırma  
 Doğru bir şekilde uygulamanızı çalıştırdığınızda nasıl çalışacağını benzetimini yapmak için JavaScript Düzenleyicisi ilk require.js ayarlarken yüklemek için hangi dosya bilmek ister. Bu genellikle, HTML kullanılarak uygulama dosyasında yapılandırılan `data-main` require.js, burada gösterildiği gibi başvuran betik öğesindeki özniteliği.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 Bu örnekte, veri-main (js/app.js) başvurulan betik hemen sonra require.js yüklenir. Hemen yüklenen ilk RequireJS kullanımını yapılandırmak için en iyi yeri dosyasıdır (kullanarak `require.config()`). JavaScript Düzenleyicisi'ni kullanmak için hangi dosya bildirmek için `data-main` uygulamanıza ekleme bir `data-main` özniteliği ve ardından değişiklik bir / / / \<başvuru / > uygulamanızda require.js başvuran yönergesi. Örneğin, bu yönerge kullanabilirsiniz:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Uygulama Başlangıç Sayfası'te ASP.NET projesi yapılandırma  
 Uygulama çalıştırıldığında RequireJS göreli varsayar dosyalara olan yolları (örneğin, ".. \\"require.js kitaplığı HTML dosyası göreli yolları) olan. Bir ASP.NET projesi için Visual Studio Düzenleyicisi'nde kod yazarken, bu başlangıç sayfası bilinmiyor ve hangi başlangıç sayfası göreli dosya yolları kullanılırken kullanılacak düzenleyici bağlanacaklarını kullanıcılarınıza anlatmanız gerekiyor. Bunu yapmak için bir `start-page` özniteliği, / / / için \<başvuru / > yönergesi.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 `start-page` Öznitelik, bir tarayıcı içinde uygulamayı çalıştırırken gördüklerinizle sayfanın URL'sini belirtir.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>RequireJS JSProj projelerinde özelleştirme  
 Apache Cordova, Windows Store Apps HTML tabanlı veya LightSwitch HTML uygulamaları için uygulama oluştururken JSProj projeleri (proje dosyaları bir .jsproj uzantılı) kullanılır. ASP.NET projelerin aksine, bu projelerin .js dosyası için bir başvuru projede mevcut HTML dosyalarından okuyun. Bu nedenle, JavaScript JSProj projesinde düzenlerken, destek RequireJS JavaScript dosyası şu anda düzenlenmekte olan satırdaysa etkinleştirilmişse başvuruluyor require.js başvuran başka bir HTML dosyası görürsünüz.  
  
 ASP.NET projeleri için gerekli olan özelleştirme adımları JSProj proje dosyasında gerekli değildir. Diğer bir deyişle, komut dosyalarını tarafından kullanılan `data-main` require.js başvurduğu komut dosyası etiketi özniteliği yüklenir otomatik olarak require.js yapılandırmak için. Require.js başvuran HTML dosyası, uygulama için başlangıç sayfası olarak da kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)



