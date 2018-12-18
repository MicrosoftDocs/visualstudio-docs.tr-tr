---
title: Metin Şablonu Dönüştürme Süreci
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, transformation process
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ace7528eb1685765fe5c7ff11ce9b3c3234a941
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919162"
---
# <a name="the-text-template-transformation-process"></a>Metin Şablonu Dönüştürme Süreci
Metin şablonu dönüştürme süreci, bir metin şablonu dosyasını girdi olarak alır ve çıktı olarak yeni bir metin dosyası oluşturur. Örneğin, Visual Basic veya C# kodu oluşturmak için metin şablonlarını kullanabilir veya bir HTML raporu oluşturabilirsiniz.

 Üç bileşeni, bu işlemde bölümü yararlanın: altyapısı, konak ve yönerge işlemcilerine. Altyapı işlemi denetler; Çıkış dosyası üretmek için konak ve yönerge işlemcisinin ile etkileşime girer. Ana bilgisayar dosyaları ve derlemeleri bulma gibi ortamı, herhangi bir etkileşim sağlar. Yönerge işlemcisini bir XML dosyasına veya bir veritabanından veri okuma gibi işlevler ekler.

 Metin şablonu dönüştürme süreci iki adımda gerçekleştirilir. İlk olarak, motorun oluşturulan dönüştürme sınıfına bilinen bir geçici sınıf oluşturur. Bu sınıf yönergeleri ve denetim blokları tarafından oluşturulan kodu içerir. Bundan sonra altyapısı derler ve çıktı dosyası üretmek için oluşturulan dönüştürme sınıfına yürütür.

## <a name="components"></a>Bileşenler

|Bileşen|Açıklama|Özelleştirilebilir (Evet/Hayır)|
|-|-|-|
|Altyapısı|Metin şablonu dönüştürme süreci motorunda denetler|Hayır.|
|Ana bilgisayar|Konak, altyapısı ve kullanıcı ortamını arasındaki arabirimdir. Visual Studio, metin dönüştürme işleminin bir ana bilgisayardır.|Evet. Özel bir ana bilgisayar yazabilirsiniz.|
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

-   Metin şablonu dönüştürme hataları işleme. Örneğin, ana bilgisayar hataları kullanıcı arabiriminde görüntülemek veya bunları bir dosyaya yazma. (Visual Studio'da, hatalar hata iletisi penceresinde görüntülenir.)

-   Bir kullanıcı bir değer sağlamadan bir yönerge olarak adlandırılan, gerekli parametre değerini sağlama. Yönerge işlemcisini, yönerge ve parametre adını belirtin ve varsa varsayılan değer sağlamak için konak isteyin.

## <a name="directives-and-directive-processors"></a>Yönergeleri ve yönerge işlemcileri
 Bir yönerge, metin şablonunuza bir komuttur. Bu, oluşturma işlemi parametrelerini sağlar. Genellikle kaynak ve türü modeli veya başka bir giriş ve çıkış dosyasının dosya adı uzantısı yönergeleri tanımlar.

 Bir yönerge işlemcisi, bir veya daha fazla yönergeleri işleyebilir. Bir şablon dönüştürdüğünüzde, şablonunuzda yönergeleri ile giderebilirsiniz bir yönerge işlemcisi yüklemiş olmanız gerekir.

 Yönergesi oluşturulan dönüştürme sınıfına kod ekleyerek çalışır. Oluşturulan dönüştürme sınıfına oluşturduğunda, bir metin şablonu ve Makinesi'nin yönerge tüm çağrıları yönergeleri çağırın. Bir yönergeyi başarıyla çağırdıktan sonra metin şablonunuza yazdığınız kodun geri kalanını yönergenin sağladığı işlevselliğe dayanabilir. Örneğin, aşağıdaki çağrısını yapabileceğiniz `import` yönergesinde, şablonda:

 `<#@ import namespace="System.Text" #>`

 Standart bir yönerge işlemcisi için dönüştürür bir `using` oluşturulan dönüştürme sınıfına deyiminde. Ardından `StringBuilder` sınıfı olarak niteleme olmadan şablon kodunuzun geri kalanında `System.Text.StringBuilder`.