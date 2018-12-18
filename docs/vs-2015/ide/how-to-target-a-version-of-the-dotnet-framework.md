---
title: 'Nasıl yapılır: .NET Framework sürümü hedefleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370c62535f2bb915115533ea79f4b913c3ac347
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182370"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Nasıl Yapılır: .NET Framework Sürümü Hedefleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu belge, proje oluştururken bir .NET Framework sürümünü hedefleyen bir projenin nasıl oluşturulacağını ve varolan bir Visual Basic, Visual C# veya Visual F# projesinde hedeflenen sürümün nasıl değiştirileceğini belirtir.  
  
> [!IMPORTANT]
>  C++ projeleri için hedef sürümü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: hedef Framework ve Platform araç kümesini değiştirme](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **Bu konudaki**  
  
-   [Bir proje oluştururken bir sürümü hedefleme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Hedef sürümü değiştirme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Bir proje oluştururken bir sürümü hedefleme  
 Bir proje oluştururken, hedeflediğiniz .NET Framework sürümü hangi şablonları kullanabileceğinizi belirler.  
  
> [!NOTE]
>  Visual Studio'nun Express sürümlerinde, önce projeyi oluşturmalısınız ve hedef olarak daha sonra değiştirebilirsiniz [hedef sürümü değiştirme](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) bu konunun ilerleyen bölümlerinde açıklanmıştır.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Projenizi oluştururken bir sürümü hedeflemek için  
  
1.  Menü çubuğunda, **dosya**, **yeni**, **proje**.  
  
2.  Üst kısmındaki listede **yeni proje** iletişim kutusunda, projenizin hedeflemesini istediğiniz .NET Framework sürümünü seçin.  
  
    > [!NOTE]
    >  Normalde, yalnızca bir .NET Framework sürümü Visual Studio ile birlikte yüklenir. Başka bir sürümü hedeflemek istiyorsanız, önce bu sürümün yüklü olduğundan emin olmalısınız. Bkz: [Visual Studio çoklu sürüm desteğine genel bakış](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  Yüklü Şablonlar listesinde, oluşturmak, projeyi adlandırın ve ardından istediğiniz proje türünü seçin **Tamam** düğmesi.  
  
     Şablon listesi yalnızca seçtiğiniz .NET Framework sürümünün desteklediği projeleri gösterir.  
  
##  <a name="bkmk_existing"></a> Hedef sürümü değiştirme  
 Visual Basic, Visual C# veya Visual F # projesinde .NET Framework'ün hedeflenen sürümünü bu yordamı izleyerek değiştirebilirsiniz.  
  
#### <a name="to-change-the-targeted-version"></a>Hedeflenen sürümü değiştirmek için  
  
1.  İçinde **Çözüm Gezgini**, değiştirin ve ardından istediğiniz projenin kısayol menüsünü **özellikleri**.  
  
     ![Visual Studio Çözüm Gezgini özellikleri](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  C++ projeleri için hedef sürümü değiştirme hakkında daha fazla bilgi için bkz: [nasıl yapılır: hedef Framework ve Platform araç kümesini değiştirme](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  Özellikler penceresinin sol sütununda seçin **uygulama** sekmesi.  
  
     ![Visual Studio uygulama özellikleri uygulama sekmesi](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Bir Windows Store uygulaması oluşturduktan sonra hedeflenen Windows ya da .NET Framework sürümü değiştirilemiyor.  
  
3.  İçinde **hedef Framework'ü** listesinde, istediğiniz sürümü seçin.  
  
4.  Görüntülenen doğrulama iletişim kutusunda seçin **Evet** düğmesi.  
  
     Projenin yüklemesi kaldırılır. Yeniden yüklediğinde, seçtiğiniz .NET Framework sürümünü hedefler.  
  
    > [!NOTE]
    >  Kodunuz hedeflediğinizden farklı bir .NET Framework sürümüne başvurular içeriyorsa, kodu derlediğinizde veya çalıştırdığınızda hata iletileri görülebilir. Bu hataları gidermek için başvuruları değiştirmeniz gerekir. Bkz: [.NET Framework hedefleme hatalarının sorunlarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio çoklu sürüm desteğine genel bakış](../ide/visual-studio-multi-targeting-overview.md)   
 [.NET framework çoklu sürüm desteği için ASP.NET Web projeleri](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [.NET Framework hedefleme hatalarının sorunlarını giderme](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Projeleri yapılandırma](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Nasıl Yapılır: Hedef Framework ve Platform Araç Kümesini Değiştirme](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)



