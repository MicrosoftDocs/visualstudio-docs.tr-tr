---
title: Birim testlerini .NET Framework'ün önceki sürümünü hedefleyecek
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 7b9032e8a1b6ee796bbea6ce7f7e3f5db7bcd205
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064737"
---
# <a name="how-to-configure-unit-tests-to-target-an-earlier-version-of-the-net-framework"></a>Nasıl yapılır: birim testlerini .NET Framework'ün önceki sürümünü hedefleyecek şekilde yapılandırma

Microsoft Visual Studio ile bir test projesi oluşturduğunuzda, .NET Framework'ün en son sürümü ve hedef olarak varsayılan olarak ayarlanır. Test projeleri Visual Studio'nun önceki sürümlerinden yükseltiyorsanız, ayrıca, bunlar .NET Framework'ün en son sürümünü hedefleyecek şekilde yükseltilir. Proje özelliklerini düzenleyerek, açıkça projenin .NET Framework'ün önceki sürümleri için yeniden hedefleyebilirsiniz.

.NET Framework'ün belirli sürümlerini hedefleyen bir test projeleri birim oluşturabilirsiniz. Hedeflenen sürüm 3.5 veya sonraki sürümler olmalıdır ve bir istemci sürümü olamaz. Visual Studio, belirli sürümlerini hedefleyen birim testleri için aşağıdaki temel destek sağlar:

- Birim test projesi oluşturmak ve bunları belirli bir .NET Framework sürümünü hedef.

- Birim testleri belirli bir .NET Framework sürümünü hedefleyen yerel makinenizde Visual Studio'dan çalıştırabilirsiniz.

- Hedef .NET Framework'ün belirli bir sürümü kullanarak birim testlerini çalıştırabilirsiniz *MSTest.exe* komut isteminden.

- Birim Testleri yapının bir parçası olarak bir yapı aracısında çalıştırabilirsiniz.

**SharePoint uygulamalarını test etme**

Yukarıda listelenen özellikleri de birim testleri yazma ve Visual Studio kullanarak SharePoint uygulamaları için tümleştirme testleri sağlar. Visual Studio kullanarak SharePoint uygulamaları geliştirme hakkında daha fazla bilgi için bkz. [oluşturma SharePoint çözümleri](../sharepoint/create-sharepoint-solutions.md), [oluşturun ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md) ve [doğrulayın ve hata ayıklama SharePoint kodunu](../sharepoint/verifying-and-debugging-sharepoint-code.md).

**Sınırlamalar**

.NET Framework'ün önceki sürümlerini kullanmak için test projelerinizi yeniden hedeflediğinizde aşağıdaki sınırlamalar geçerlidir:

- .NET Framework 3.5, çoklu sürüm desteği yalnızca birim testleri içeren test projeleri için desteklenir. .NET Framework 3.5, kodlanmış kullanıcı Arabirimi veya yük testi gibi diğer test türlerini desteklemez. Yeniden hedefleme, birim testleri dışında test türleri için engellenir.

- .NET Framework'ün önceki bir sürümde hedeflenen Test yürütme, yalnızca varsayılan ana bilgisayar bağdaştırıcısında desteklenir. ASP.NET ana bilgisayar bağdaştırıcısında desteklenmiyor. ASP.NET Geliştirme Sunucusu bağlamında çalışacak şekilde ASP.NET uygulamaları .NET Framework'ün geçerli sürümüyle uyumlu olması gerekir.

- .NET Framework 3.5 çoklu hedefleme desteği testleri çalıştırırken veri koleksiyonu desteği devre dışı bırakıldı. Visual Studio komut satırı araçlarını kullanarak kod kapsamı çalıştırabilirsiniz.

- Uzak makinede .NET Framework 3.5 kullanan birim testleri çalıştıramazsınız.

- Birim testleri için framework'ün önceki istemci sürümlerini hedefleyemez.

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-basic-unit-test-projects"></a>Visual Basic birim testi projeleri için .NET Framework'ün belirli bir sürüme yeniden hedefleme

1.  Yeni bir Visual Basic birim testi projesi oluşturun. Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

2.  Altında **yüklü şablonlar**, genişletme **Visual Basic**. Seçin **Test** seçip **Test projesi** şablonu.

3.  İçinde **adı** metin kutusunda, Visual Basic için bir ad test projesi ve ardından **Tamam**.

4.  İçinde **Çözüm Gezgini**, seçin **özellikleri** yeni Visual Basic test projesinin kısayol menüsünden.

     Visual Basic test projeniz için özellikleri görüntülenir.

5.  Üzerinde **derleme** sekmesini, **Gelişmiş derleme seçenekleri** aşağıdaki çizimde gösterildiği gibi.

     ![Gelişmiş derleme seçenekleri](../test/media/howtoconfigureunittest35frameworka.png)

6.  Kullanım **hedef Framework'ü (tüm yapılandırmaları)** için hedef Framework'ü değiştirmek için açılır listede **.NET Framework 3.5** veya sonraki bir sürümünü belirtme çizgisi B aşağıdaki resimde gösterildiği gibi. Bir istemci sürümü belirtilmemelidir.

     ![Hedef framework bırakma&#45;açılan listesinde](../test/media/howtoconfigureunitest35frameworkstepb.png)

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-visual-c-unit-test-projects"></a>Belirli bir .NET Framework sürümünü hedefleyen Visual C# için yeniden birim testi projeleri

1.  Yeni bir Visual C# birim testi projesi oluşturun. Üzerinde **dosya** menüsünde seçin **yeni** seçip **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

2.  Altında **yüklü şablonlar**, genişletme **Visual C#**. Seçin **Test** seçip **Test projesi** şablonu.

3.  İçinde **adı** metin kutusunda, bir ad için Visual C# test projesi ve ardından **Tamam**.

4.  İçinde **Çözüm Gezgini**, seçin **özellikleri** yeni Visual C# test projenizin kısayol menüsünden.

     Visual C# test projeniz için özellikleri görüntülenir.

5.  Üzerinde **uygulama** sekmesini, **hedef Framework'ü**. Aşağı açılan listeden seçin **.NET Framework 3.5** veya aşağıdaki çizimde gösterildiği gibi sonraki bir sürümü. Bir istemci sürümü belirtilmemelidir.

     ![Hedef framework bırakma&#45;açılan listesinde](../test/media/howtoconfigureunittest35frameworkcsharp.png)

## <a name="re-targeting-to-a-specific-version-of-the-net-framework-for-ccli-unit-test-projects"></a>Belirli bir .NET Framework sürümünü hedefleyen C + için yeniden +/ CLI birim testi projeleri

1.  Yeni bir C++ birim testi projesi oluşturun. Üzerinde **dosya** menüsünde **yeni** ve ardından **proje**.

     **Yeni proje** iletişim kutusu görüntülenir.

    > [!WARNING]
    > İçin derleme C + +/ CLI birim testlerini .NET framework'ün önceki bir sürümü için Visual C++ için ilgili Visual Studio sürümünü kullanmanız gerekir. Örneğin, .NET Framework 3.5 hedeflemek için Visual Studio 2008 ve Visual Studio 2008 Service Pack 1 yüklemeniz gerekir.

2.  Altında **yüklü şablonlar**, genişletme **Visual C ++**. Seçin **Test** seçip **Test projesi** şablonu.

3.  İçinde **adı** metin kutusunda, Visual C++ için bir ad test projesi ve ardından **Tamam**.

4.  İçinde **Çözüm Gezgini**, seçin **projeyi** yeni Visual C++ test projenizden.

5.  İçinde **Çözüm Gezgini**, kaldırılan Visual C++ test projesi seçin ve ardından **Düzenle \<proje adı > .vcxproj**.

     *.Vcxproj* dosyası düzenleyicide açılır.

6.  Ayarlama `TargetFrameworkVersion` sürüm 3.5 veya sonraki bir sürümde `PropertyGroup` etiketli `"Globals"`. Bir istemci sürümü belirtilmemelidir:

    ```xml
    <PropertyGroup Label="Globals">
        <TargetName>DefaultTest</TargetName>
        <ProjectTypes>{3AC096D0-A1C2-E12C-1390-A8335801FDAB};{8BC9CEB8-8B4A-11D0-8D11-00A0C91BC942}</ProjectTypes>
        <ProjectGUID>{CE16D77A-E364-4ACD-948B-1EB6218B0EA3}</ProjectGUID>
        <TargetFrameworkVersion>3.5</TargetFrameworkVersion>
        <Keyword>ManagedCProj</Keyword>
        <RootNamespace>CPP_Test</RootNamespace>
      </PropertyGroup>
    ```

7.  Kaydet ve Kapat *.vcxproj* dosya.

8.  İçinde **Çözüm Gezgini**, Seç **projeyi** yeni Visual C++ test projenizin kısayol menüsünden.

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint çözümleri oluşturma](../sharepoint/create-sharepoint-solutions.md)
- [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Gelişmiş derleme Ayarları iletişim kutusu (Visual Basic)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)
