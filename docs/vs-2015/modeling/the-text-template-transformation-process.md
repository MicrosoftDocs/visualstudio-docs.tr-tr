---
title: Metin şablonu dönüştürme süreci | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, transformation process
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 146d391cc843291b79dc34af29851cfed4c80a46
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203781"
---
# <a name="the-text-template-transformation-process"></a>Metin Şablonu Dönüştürme Süreci
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin şablonu dönüştürme süreci, bir metin şablonu dosyasını girdi olarak alır ve çıktı olarak yeni bir metin dosyası oluşturur. Örneğin, Visual Basic veya C# kodu oluşturmak için metin şablonlarını kullanabilir veya bir HTML raporu oluşturabilirsiniz.  
  
 Üç bileşeni, bu işlemde bölümü yararlanın: altyapısı, konak ve yönerge işlemcilerine. Altyapı işlemi denetler; Çıkış dosyası üretmek için konak ve yönerge işlemcisinin ile etkileşime girer. Ana bilgisayar dosyaları ve derlemeleri bulma gibi ortamı, herhangi bir etkileşim sağlar. Yönerge işlemcisini bir XML dosyasına veya bir veritabanından veri okuma gibi işlevler ekler.  
  
 Metin şablonu dönüştürme süreci iki adımda gerçekleştirilir. İlk olarak, motorun oluşturulan dönüştürme sınıfına bilinen bir geçici sınıf oluşturur. Bu sınıf yönergeleri ve denetim blokları tarafından oluşturulan kodu içerir. Bundan sonra altyapısı derler ve çıktı dosyası üretmek için oluşturulan dönüştürme sınıfına yürütür.  
  
## <a name="components"></a>Bileşenler  
  
|Bileşen|Açıklama|Özelleştirilebilir (Evet/Hayır)|  
|---------------|-----------------|------------------------------|  
|Altyapısı|Metin şablonu dönüştürme süreci motorunda denetler|Hayır.|  
|Ana bilgisayar|Konak, altyapısı ve kullanıcı ortamını arasındaki arabirimdir. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metin dönüştürme işleminin bir ana bilgisayardır.|Evet. Özel bir ana bilgisayar yazabilirsiniz.|  
|Yönerge işlemcileri|Yönerge işlemcileri yönergeleri metin şablonlarında işleyen sınıflardır. Bir metin şablonu için bir giriş kaynağından veri sağlamak yönergeleri kullanabilirsiniz.|Evet. Özel yönerge işlemcilerinizi yazabilirsiniz.|  
  
## <a name="the-engine"></a>Altyapısı  
 Altyapı şablonu dönüştürme işleminde kullanılan tüm dosyaları işler ana bilgisayarından bir dize olarak alır. Altyapı sonra herhangi bir özel yönerge işlemcileri ve ortam diğer yönlerini bulmak için ana ister. Altyapı derler ve oluşturulan dönüştürme sınıfına çalıştırır. Altyapı, normalde bir dosyaya metin kaydeder barındırmak için oluşturulan metni döndürür.  
  
## <a name="the-host"></a>Ana bilgisayar  
 Konak, ortamın dışında aşağıdakiler dahil olmak üzere dönüştürme işlemi, ilgili her şeyin sorumludur:  
  
-   Metin ve ikili dosyaları altyapısı veya bir yönerge işlemcisi tarafından istenen bulunuyor. Konak, dizinler ve genel derleme önbelleğinde derlemeleri bulmak için arama yapabilirsiniz. Özel yönerge işlemcisi kod altyapısı için konak bulabilirsiniz. Konak ayrıca bulun ve metin dosyalarını okuma ve içeriklerini dize olarak döndürür.  
  
-   Standart derlemeler ve altyapı tarafından oluşturulan dönüştürme sınıfına oluşturmak için kullanılan ad alanları listesi sağlama.  
  
-   Altyapı derler ve oluşturulan dönüştürme sınıfına çalıştırdığında kullanılan uygulama etki alanı sağlama. Ayrı uygulama etki alanı, şablon kodunun hataları konak uygulama korumak için kullanılır.  
  
-   Oluşturulan çıktı dosyası yazılıyor.  
  
-   Oluşturulan çıktı dosyası için varsayılan uzantı ayarlanıyor.  
  
-   Metin şablonu dönüştürme hataları işleme. Örneğin, ana bilgisayar hataları kullanıcı arabiriminde görüntülemek veya bunları bir dosyaya yazma. (İçinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], hatalar, hata iletisi penceresinde görüntülenir.)  
  
-   Bir kullanıcı bir değer sağlamadan bir yönerge olarak adlandırılan, gerekli parametre değerini sağlama. Yönerge işlemcisini, yönerge ve parametre adını belirtin ve varsa varsayılan değer sağlamak için konak isteyin.  
  
## <a name="directives-and-directive-processors"></a>Yönergeleri ve yönerge işlemcileri  
 Bir yönerge, metin şablonunuza bir komuttur. Bu, oluşturma işlemi parametrelerini sağlar. Genellikle kaynak ve türü modeli veya başka bir giriş ve çıkış dosyasının dosya adı uzantısı yönergeleri tanımlar.  
  
 Bir yönerge işlemcisi, bir veya daha fazla yönergeleri işleyebilir. Bir şablon dönüştürdüğünüzde, şablonunuzda yönergeleri ile giderebilirsiniz bir yönerge işlemcisi yüklemiş olmanız gerekir.  
  
 Yönergesi oluşturulan dönüştürme sınıfına kod ekleyerek çalışır. Oluşturulan dönüştürme sınıfına oluşturduğunda, bir metin şablonu ve Makinesi'nin yönerge tüm çağrıları yönergeleri çağırın. Bir yönergeyi başarıyla çağırdıktan sonra metin şablonunuza yazdığınız kodun geri kalanını yönergenin sağladığı işlevselliğe dayanabilir. Örneğin, aşağıdaki çağrısını yapabileceğiniz `import` yönergesinde, şablonda:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Standart bir yönerge işlemcisi için dönüştürür bir `using` oluşturulan dönüştürme sınıfına deyiminde. Ardından `StringBuilder` sınıfı olarak niteleme olmadan şablon kodunuzun geri kalanında `System.Text.StringBuilder`.



