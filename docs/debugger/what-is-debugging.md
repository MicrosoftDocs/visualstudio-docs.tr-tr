---
title: Hata ayıklama nedir?
description: Bir uygulamanın hatalarını ayıklamak geldiğini anlayın
ms.custom: debug-experiments
ms.date: 10/17/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8f0aa6cbe09f902ef69e1fd5cb3a2d9712cabf28
ms.sourcegitcommit: d7f232a7596420e40ff8051d42cdf90203af4a74
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52821454"
---
# <a name="what-is-debugging"></a>Hata ayıklama nedir?

Visual Studio hata ayıklayıcısını güçlü bir araçtır. Nasıl kullanılacağını göstereceğiz önce gibi bazı terimler hakkında konuşmak istiyoruz *hata ayıklayıcı*, *hata ayıklama*, ve *hata ayıklama modu*. Biz daha sonra bulma ve hataları düzeltme hakkında konuşurken, böylece biz hakkında aynı şeyi insanlarla konuşmalısınız.

## <a name="debugger-vs-debugging"></a>Hata ayıklayıcı, hata ayıklama karşılaştırması

Terim *hata ayıklama* birçok farklı şey anlamına gelebilir, ancak en başka bir deyişle, hataları kodunuzdan kaldırma anlamına gelir. Şimdi, bunu yapmanın yollarından biri çok vardır. Örneğin, kodunuzda için yazım hatalarını tarama veya kod Çözümleyicisi kullanarak hata ayıklama. Performans profili oluşturucu kullanılarak kodda hata ayıklama. Ya da kullanarak hata ayıklama bir *hata ayıklayıcı*.

Bir hata ayıklayıcı çalışan uygulamanıza ekler ve kod İnceleme sağlar bir çok özel Geliştirici aracıdır. Visual Studio hata ayıklama belgelerinde genellikle "hata ayıklama" dediğimiz olduğunda ne demek isteriz budur.

## <a name="debug-mode-vs-running-your-app"></a>Hata ayıklama modu, uygulamanızı çalıştıran karşılaştırması

Uygulamanızı Visual Studio'da ilk kez çalıştırdığınızda, yeşil ok düğmesine basarak başlattığınızda ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat") araç çubuğunda (veya **F5**). Varsayılan olarak, **hata ayıklama** sola açılan değer görünür. Visual Studio'yu kullanmaya yeni başladıysanız, bu uygulamanızı hata ayıklama ile çalışan bir şey olduğunu izlenim bırakabilirsiniz uygulamanız--hangi BT yok--ancak iki çok farklı görev temelden şunlardır.

![Hata ayıklama derlemesi seçin](../debugger/media/what-is-debugging-debug-build.png)

A **hata ayıklama** değeri bir hata ayıklama yapılandırmasını gösterir. Uygulamayı başlattığınızda (yeşil ok tuşlarına basın veya **F5**) bir hata ayıklama yapılandırması, uygulama içinde başlattığınız *hata ayıklama modu*, anlamına gelen bir hata ayıklayıcısı ekli uygulamanızı çalışıyor. Bu, hata ayıklama uygulamanızda hataları bulmak için kullanabileceğiniz özelliklerinin tam kümesi sağlar.

Açık bir projeniz varsa, burada yazan açılan seçicisinde **hata ayıklama** ve **yayın** yerine.

![Yayın derlemesi seçin](../debugger/media/what-is-debugging-release-build.png)

Bu ayarı değiştirdiğinizde, projeniz için bir yayın yapılandırması hata ayıklama yapılandırmasından değiştirin. Visual Studio projeleri ayrı sürümü ve hata ayıklama yapılandırması, programınız için. Hata ayıklama sürümünün hata ayıklama ve yayın sürümünü son sürüm dağıtımı oluşturun. Yayın derlemesi performans için iyileştirilmiştir, ancak hata ayıklama derlemesi hata ayıklama için daha iyidir.

## <a name="when-to-use-a-debugger"></a>Ne zaman bir hata ayıklayıcı kullanılır?

Hata ayıklayıcı, uygulamalarınızda hataları bulmalarına ve önemli bir araçtır. Ancak bağlam king ve tüm araçları, hızlı bir şekilde hata veya arıza ortadan kaldırmanıza yardımcı olmak için atılabilir yararlanmak önemlidir. Bazı durumlarda, "aracı" sağ daha iyi kodlama uygulaması olabilir. Ne zaman başka bir araç ve hata ayıklayıcının kullanılacağını öğrenerek, hata ayıklayıcı daha etkili bir şekilde kullanmayı öğreneceksiniz. Hata ayıklayıcı hakkında bilgi edinmek gereksinim bildiğiniz olup [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md). Aksi takdirde bağlantıdaki izleyin **sonraki adımlar**.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, birkaç genel hata ayıklama kavramları öğrendiniz. Ardından, Visual Studio ile hata ayıklama ve daha az hata ile kodunun nasıl yazılacağını öğrenmeye başlayabilirsiniz. Şu makale gösterir C# Visual Studio tarafından desteklenen tüm dillerde kod örnekleri, ancak kavramlar geçerlidir.

> [!div class="nextstepaction"]
> [Daha iyi yazarak hataları düzeltmek C# kod](../debugger/write-better-code-with-visual-studio.md)
