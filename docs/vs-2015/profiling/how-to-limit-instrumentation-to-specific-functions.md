---
title: 'Nasıl yapılır: izlemeyi belirli araçlarla sınırlama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c7fa666c42d31035bd42841a2bbb41221bc16b5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782576"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>Nasıl yapılır: Belirli İşlevler için İzlemeyi Sınırlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veya daha fazla işlev için izleme ve veri toplama seçeneklerini ayarlayarak sınırlayabilirsiniz **Gelişmiş** sayfasının **performans oturumu** veya hedef ikili özellik sayfaları:  
  
- Performans oturumu özelliği sayfasında işlevleri belirtirseniz, bu işlevler yalnızca oturumun tüm izleme eklenmiş ikili dosyalarda algılayıcılarla donatılmıştır.  
  
- İkili bir hedef özellik sayfasında işlevleri belirtirseniz, belirli bir ikili izleme eklenmiş, bu işlevler yalnızca bu şekilde çalışır. Diğer ikili performans işlevlerde zamanki algılayıcılarla donatılmıştır.  
  
  Yalnızca izleme profili oluşturma metodu seçildiğinde, bu şekilde veri toplama sınırlaması desteklenir.  
  
> [!NOTE]
>  Ayrıca **Gelişmiş** sayfasının **performans oturumu** profil oluşturma araçları için kullanılabilir diğer seçenekleri ayarlamak için özellik sayfaları [Vsınstr](../profiling/vsinstr.md) komut satırı izleme aracı.  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>Performans oturumu içinde belirli işlevler için izlemeyi sınırlama  
  
1. İçinde **performans Gezgini**oturum adına sağ tıklayın ve ardından **özellikleri**.  
  
    **Özellik sayfaları** iletişim kutusu görüntülenir.  
  
2. Üzerinde **özellik sayfaları** iletişim kutusu, tıklayın **Gelişmiş**.  
  
3. İçinde **ek izleme seçeneklerini** metin kutusunda, istediğiniz işlev adı türü için aşağıdaki sözdizimini kullanın. aracı:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::**`FunctionName`. Birden çok işlevleri ayırmak için noktalı virgül kullanın. Bir yıldız işareti kullanın (\*) bir veya daha fazla karakter için joker karakter belirtmek için. Örneğin, **/ include: MyNS::\\*** MyNS ad alanındaki tüm işlevleri belirtir.  
  
   > [!NOTE]
   >  Bir ikili işlevlerde listelemek için profil oluşturma araçları yükleme dizininde bir komut istemi penceresi açın (genellikle tools\performance Araçlar dizini altında [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] yükleme dizini) ve ardından yazın **vsınstr / DumpFuncs**  
  
### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>Bir ikili dosyada belirli işlevler için izlemeyi sınırlama  
  
1. İçinde **performans Gezgini**, ikili adı bulun **hedefleri** performans oturumu düğümünün.  
  
2. İkili adına sağ tıklayın ve ardından **özellikleri**.  
  
    **Özellik sayfaları** iletişim kutusu görüntülenir.  
  
3. Üzerinde **özellik sayfaları** iletişim kutusu, tıklayın **Gelişmiş**.  
  
4. İçinde **ek izleme seçeneklerini** metin kutusunda, istediğiniz işlev adı türü için aşağıdaki sözdizimini kullanın. aracı:  
  
    **/ include:** `FuncSpec` **[;** `FuncSpec` **]** `...`  
  
    `FuncSpec` ad alanı ve işlev adıdır. Şu biçimdedir `Namespace` **::**`FunctionName`. Birden çok işlevleri ayırmak için noktalı virgül kullanın. Bir yıldız işareti kullanın (\*) bir veya daha fazla karakter için joker karakter belirtmek için. Örneğin, **/ include: MyNS::\\*** MyNS ad alanındaki tüm işlevleri belirtir.  
  
   > [!NOTE]
   >  Bir ikili işlevlerde listelemek için profil oluşturma araçları yükleme dizininde bir komut istemi penceresi açın (genellikle tools\performance Araçlar dizini altında [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] yükleme dizini) ve ardından yazın **vsınstr / DumpFuncs**  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri toplama denetimi](../profiling/controlling-data-collection.md)   
 [Nasıl yapılır: belirli DLL'ler için izleme sınırlama](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Nasıl Yapılır: Ek İzleme Seçeneklerini Belirtme](../profiling/how-to-specify-additional-instrumentation-options.md)



