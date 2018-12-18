---
title: MSBuild proje dosyasında kalıcı veri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 059ddc7b9b8fe0de06530af704bb5f7e271f6744
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749645"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild Proje Dosyasında Verileri Kalıcı Hale Getirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Daha sonra kullanmak için proje dosyası içine alt özgü verileri kalıcı hale getirmek bir proje alt gerekebilir. Proje alt türü, aşağıdaki gereksinimleri karşılaması için proje dosya kalıcılığına kullanır:  
  
1.  Proje oluşturmanın bir parçası olarak kullanılan verileri kalıcı hale getirin. (Microsoft Build Engine hakkında daha fazla bilgi için bkz. [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b).) Derlemeyle ilgili bilgileri şunlardan birini yapabilirsiniz:  
  
    1.  Bağımsız yapılandırma verileri. Diğer bir deyişle, MSBuild öğeleri boş veya eksik koşullarla depolanan veriler.  
  
    2.  Bağımlı yapılandırma verileri. Diğer bir deyişle, belirli bir proje yapılandırması için koşuluna MSBuild öğeleri depolanan veriler. Örneğin:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Derlemek ilgili olmayan verileri kalıcı hale getirin. Bu veriler, bir XML şemasına göre doğrulanmadı serbest biçimli XML olarak ifade edilebilir.  
  
    1.  Bağımsız yapılandırma verileri.  
  
    2.  Bağımlı yapılandırma verileri.  
  
## <a name="persisting-build-related-information"></a>Derlemeyle ilgili bilgileri kalıcı hale getirme  
 Bir proje oluşturmak için faydalı veri kalıcılığı MSBuild işlenir. MSBuild sistemi bir ana tablo derlemeyle ilgili bilgileri tutar. Proje alt türleri almak ve özellik değerlerini ayarlamak için bu verilere erişmek için sorumlu olursunuz. Proje alt türleri kalıcı için ek özellikler ekleyerek ve kalıcı olmayan şekilde özellikleri kaldırarak ayrıca derlemeyle ilgili veri tablosu genişletebilirsiniz.  
  
 MSBuild verileri değiştirmek için bir proje alt türü temel proje sistemi MSBuild property nesnesini almak için sorumlu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Temel Proje sistemi ve toplama proje alt sorgular için çalıştırarak uygulanan bir arabirim `QueryInterface`.  
  
 Aşağıdaki yordamı kullanarak bir özelliği kaldırmak için gereken adımları özetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Bir MSBuild proje dosyasından bir özelliği kaldırmak için  
  
1.  Çağrı `QueryInterface` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> , proje alt türü.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> ile `pszPropName` kaldırmak istediğiniz özelliğini ayarlayın.  
  
### <a name="persisting-non-build-related-information"></a>Derleme olmayan ilgili bilgileri kalıcı hale getirme  
 Proje dosyaları oluşturmak için önemli değildir veri kalıcılığı aracılığıyla işlenir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Uygulayabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> ana `project subtype aggregator` nesnesi `project subtype project configuration` nesne veya her ikisini de.  
  
 Aşağıdaki noktaları kavramlarla ilgili derleme dışı ilgili bilgilerin Kalıcılık özetler.  
  
-   Yükleme ve yapılandırma bağımsız veri kaydetmek için ana proje alt türü (diğer bir deyişle, en dıştaki proje alt) toplayıcısı nesne üzerinde temel projenin çağırır ve yüklemek veya bağımlı yapılandırmasını kaydetmek için proje alt proje yapılandırma nesneler üzerinde çağrılır veriler.  
  
-   Temel projenin yöntemlerini çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> birden çok kez her proje alt toplama düzeyi için ve her düzeyi bir GUID geçirir.  
  
-   Temel projenin geçer veya belirli proje alt türü için ayrılmış ve kalıcı hale getirme durumu toplama düzeyleri arasındaki bir yol olarak bu mekanizma kullanan bir XML parçası alır.  
  
-   Temel projenin en dıştaki proje alt'ın çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>GUID geçirme uygulaması. GUID için en dıştaki proje alt aitse, çağrı işler; Aksi takdirde GUID karşılık gelen proje alt bulunana kadar çağrısı bir iç proje alt türü ve benzeri atar.  
  
-   Önce veya sonra çağrısı bir iç proje alt temsilcilerin bir proje alt XML parçası de değiştirebilirsiniz. Aşağıdaki örnek, burada bir proje alt türü için belirli özellikleri içeren dosyanın adını geçirilir, proje alt türü için bir proje dosyası kitabından gösterir.  
  
    ```  
    <ProjectExtensions>  
        <VisualStudio>  
          <FlavorProperties GUID="{<FlavorGUID>}">  
            <FlavorProject TestFileFolder="TestFile" />  
          </FlavorProperties>  
        </VisualStudio>  
      </ProjectExtensions>  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Proje Alt Türleri](../../extensibility/internals/project-subtypes.md)

