---
title: "Nasıl yapılır: birim testlerini .NET Framework'ün önceki sürümünü hedefleyecek şekilde yapılandırma | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adb6c011-5abd-41d2-8ead-08cd7579bf37
caps.latest.revision: 14
ms.author: gewarren
manager: douge
ms.openlocfilehash: 978f4e3edeb83d5980d793d74cf209e8e8f7205e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892798"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Nasıl yapılır: Birim Testlerini .NET Framework'ün Önceki Sürümünü Hedefleyecek Şekilde Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Visual Studio ile bir test projesi oluşturduğunuzda, .NET Framework'ün en son sürümü ve hedef olarak varsayılan olarak ayarlanır. Test projeleri Visual Studio'nun önceki sürümlerinden yükseltiyorsanız, ayrıca, bunlar .NET Framework'ün en son sürümünü hedefleyecek şekilde yükseltilir. Proje özelliklerini düzenleyerek, açıkça projenin .NET Framework'ün önceki sürümleri için yeniden hedefleyebilirsiniz.  
  
 .NET Framework'ün belirli sürümlerini hedefleyen bir test projeleri birim oluşturabilirsiniz. Hedeflenen sürüm 3.5 veya sonraki sürümler olmalıdır ve bir istemci sürümü olamaz. Visual Studio, belirli sürümlerini hedefleyen birim testleri için aşağıdaki temel destek sağlar:  
  
- Birim test projesi oluşturmak ve bunları belirli bir .NET Framework sürümünü hedef.  
  
- Birim testleri belirli bir .NET Framework sürümünü hedefleyen yerel makinenizde Visual Studio'dan çalıştırabilirsiniz.  
  
- Komut satırından MSTest.exe kullanarak, belirli bir .NET Framework sürümünü hedefleyen birim testleri çalıştırabilirsiniz.  
  
- Birim Testleri yapının bir parçası olarak bir yapı aracısında çalıştırabilirsiniz.  
  
  **SharePoint uygulamalarını test etme**  
  
  Yukarıda listelenen özellikleri de birim testleri yazma ve Visual Studio kullanarak SharePoint uygulamaları için tümleştirme testleri sağlar. [!INCLUDE[crabout](../includes/crabout-md.md)] Visual Studio kullanarak SharePoint uygulamaları geliştirmenize nasıl [SharePoint çözümleri oluşturma](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631), [oluşturma ve hata ayıklama SharePoint çözümleri](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae) ve [doğrulama ve hata ayıklama SharePoint Kod](http://msdn.microsoft.com/library/b5f3bce2-6a51-41b1-a292-9e384bae420c).  
  
  **Sınırlamalar**  
  
  .NET Framework'ün önceki sürümlerini kullanmak için test projelerinizi yeniden hedeflediğinizde aşağıdaki sınırlamalar geçerlidir:  
  
- .NET Framework 3.5, çoklu sürüm desteği yalnızca birim testleri içeren test projeleri için desteklenir. .NET Framework 3.5, kodlanmış kullanıcı Arabirimi veya yük testi gibi diğer test türlerini desteklemez. Yeniden hedefleme, birim testleri dışında test türleri için engellenir.  
  
- .NET Framework'ün önceki bir sürümde hedeflenen Test yürütme, yalnızca varsayılan ana bilgisayar bağdaştırıcısında desteklenir. ASP.NET ana bilgisayar bağdaştırıcısında desteklenmiyor. ASP.NET Geliştirme Sunucusu bağlamında çalışacak şekilde ASP.NET uygulamaları .NET Framework'ün geçerli sürümüyle uyumlu olması gerekir.  
  
- .NET Framework 3.5 çoklu hedefleme desteği testleri çalıştırırken veri koleksiyonu desteği devre dışı bırakıldı. Visual Studio komut satırı araçlarını kullanarak kod kapsamı çalıştırabilirsiniz.  
  
- Uzak makinede .NET Framework 3.5 kullanan birim testleri çalıştıramazsınız.  
  
- Birim testleri için framework'ün önceki istemci sürümlerini hedefleyemez.  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Visual Basic birim testi projeleri için tekrar belirli bir .NET Framework sürümünü hedefleme  
  
1.  Yeni bir Visual Basic birim testi projesi oluşturun. Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Altında **yüklü şablonlar**, genişletme **Visual Basic**. Seçin **Test** seçip **Test projesi** şablonu.  
  
3.  İçinde **adı** metin kutusunda, Visual Basic için bir ad test projesi ve ardından **Tamam**.  
  
4.  Çözüm Gezgini'nde **özellikleri** yeni Visual Basic test projesinin kısayol menüsünden.  
  
     Visual Basic test projeniz için özellikleri görüntülenir.  
  
5.  Üzerinde **derleme** sekmesini seçin **Gelişmiş derleme seçenekleri** aşağıdaki çizimde gösterildiği gibi.  
  
     ![Gelişmiş derleme seçenekleri](../test/media/howtoconfigureunittest35frameworka.png "HowToConfigureUnitTest35FrameworkA")  
  
6.  Kullanım **hedef Framework'ü (tüm yapılandırmaları)** için hedef Framework'ü değiştirmek için açılır listede **.NET Framework 3.5** veya sonraki bir sürümünü belirtme çizgisi B aşağıdaki resimde gösterildiği gibi. Bir istemci sürümü belirtilmemelidir.  
  
     ![Hedef framework bırakma&#45;açılan listesinde](../test/media/howtoconfigureunitest35frameworkstepb.png "HowToConfigureUniTest35FrameworkStepB")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Visual C# birim testi projeleri için tekrar belirli bir .NET Framework sürümünü hedefleme  
  
1.  Yeni bir Visual C# birim testi projesi oluşturun. Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
2.  Altında **yüklü şablonlar**, genişletme **Visual C#**. Seçin **Test** seçip **Test projesi** şablonu.  
  
3.  İçinde **adı** metin kutusunda, bir ad için Visual C# test projesi ve ardından **Tamam**.  
  
4.  Çözüm Gezgini'nde **özellikleri** yeni Visual C# test projenizin kısayol menüsünden.  
  
     Visual C# test projeniz için özellikleri görüntülenir.  
  
5.  Üzerinde **uygulama** sekmesini seçin **hedef Framework'ü** seçip **.NET Framework 3.5** veya gösterilen hedef framework.as değiştirmek için aşağı açılan listeden sonraki bir sürümü Aşağıdaki çizimde. Bir istemci sürümü belirtilmemelidir.  
  
     ![Hedef framework bırakma&#45;açılan listesinde](../test/media/howtoconfigureunittest35frameworkcsharp.png "HowToConfigureUnitTest35FrameworkCSharp")  
  
### <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Belirli bir .NET Framework sürümünü hedefleyen C + için yeniden +/ CLI birim testi projeleri  
  
1.  Yeni bir C++ birim testi projesi oluşturun. Üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.  
  
     **Yeni proje** iletişim kutusu görüntülenir.  
  
    > [!WARNING]
    >  İçin derleme C + +/ CLI birim testlerini .NET framework'ün önceki bir sürümü için Visual C++ için ilgili Visual Studio sürümünü kullanmanız gerekir. Örneğin, .NET Framework 3.5 hedeflemek için yüklemelisiniz [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] ve [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] Service Pack 1.  
  
2.  Altında **yüklü şablonlar**, genişletme **Visual C ++**. Seçin **Test** seçip **Test projesi** şablonu.  
  
3.  İçinde **adı** metin kutusunda, Visual C++ için bir ad test projesi ve ardından **Tamam**.  
  
4.  Çözüm Gezgini'nde **projeyi** yeni Visual C++ test projenizden.  
  
5.  Çözüm Gezgini'nde kaldırılan Visual C++ test projesini seçin ve ardından **Düzenle \<proje adı > .vcxproj**.  
  
     .Vcxproj dosyası düzenleyicide açılır.  
  
6.  Ayarlama `TargetFrameworkVersion` sürüm 3.5 veya sonraki bir sürümde `PropertyGroup` etiketli `"Globals"`. Bir istemci sürümü belirtilmemelidir:  
  
    ```  
    <PropertyGroup Label="Globals">  
        <TargetName>DefaultTest</TargetName>  
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>  
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>  
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>  
        <Keyword>ManagedCProj</Keyword>  
        <RootNamespace>CPP_Test</RootNamespace>  
      </PropertyGroup>  
  
    ```  
  
7.  .vcxproj dosyasını kaydedip kapatın.  
  
8.  Çözüm Gezgini'nde Seç **projeyi** yeni Visual C++ test projenizin kısayol menüsünden.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma ve varolan kod için birim testleri çalıştırma](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)   
 [SharePoint çözümleri oluşturma](http://msdn.microsoft.com/library/4bfb1e59-97c9-4594-93f8-3068b4eb9631)   
 [Oluşturma ve SharePoint çözümlerinde hata ayıklama](http://msdn.microsoft.com/library/c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae)   
 [Gelişmiş Derleme Ayarları İletişim Kutusu (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)



