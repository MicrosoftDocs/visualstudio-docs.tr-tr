---
title: MSBuild proje dosyası içinde kalıcı veri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 324f9dfd4e381e9580e4940f06f652ef64d9d3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132087"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>MSBuild proje dosyası içinde kalıcı veri
Proje alt alt özgü veriler daha sonra kullanmak için proje dosyasına kalıcı olması gerekebilir. Proje alt proje dosyası Kalıcılık aşağıdaki gereksinimleri karşılaması için kullanır:  
  
1.  Proje derleme bir parçası olarak kullanılan veri kalıcı olmasını sağlar. (Microsoft Build Engine hakkında daha fazla bilgi için bkz: [MSBuild](../../msbuild/msbuild.md).) Yapı ilgili bilgiler şunlardan birini yapabilirsiniz:  
  
    1.  Bağımsız yapılandırma verileri. Diğer bir deyişle, boş veya eksik koşullarla MSBuild öğeleri depolanan verileri.  
  
    2.  Yapılandırmaya bağlı verileri. Diğer bir deyişle, belirli bir projede yapılandırmayı söylediğinizde MSBuild öğeleri depolanan verileri. Örneğin:  
  
        ```  
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
        ```  
  
2.  Yapı ilgili olmayan veriler kalıcı olmasını sağlar. Bu veriler, bir XML şemasına göre doğrulanmaz serbest biçimli XML belirtilebilir.  
  
    1.  Bağımsız yapılandırma verileri.  
  
    2.  Yapılandırmaya bağlı verileri.  
  
## <a name="persisting-build-related-information"></a>Kalıcı yapı ilgili bilgiler  
 Proje derleme için yararlı verilerinin kalıcılığı MSBuild gerçekleştirilir. MSBuild sistem bir ana tablo yapı ile ilgili bilgileri tutar. Proje alt türleri, özellik değerlerini almak ve ayarlamak için bu veri erişimi için sorumludur. Kalıcı için ek özellikler ekleyerek ve kalıcı değildir şekilde özellikleri kaldırarak proje alt yapı ile ilgili veri tablosu da genişletebilirsiniz.  
  
 MSBuild verileri değiştirmek için bir proje alt temel proje sisteminden MSBuild özelliği nesnesini almak için sorumlu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Çekirdek proje sistemi ve aggregating proje alt sorgular için çalıştırarak uygulanan bir arabirimi `QueryInterface`.  
  
 Aşağıdaki yordamı kullanarak bir özelliği kaldırmak için gereken adımları özetler <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  
  
#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>MSBuild proje dosyasından bir özelliği kaldırmak için  
  
1.  Çağrı `QueryInterface` üzerinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> proje alt.  
  
2.  Çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> ile `pszPropName` kaldırmak istediğiniz özelliğini ayarlayın.  
  
### <a name="persisting-non-build-related-information"></a>Kalıcı olmayan yapı ilgili bilgiler  
 Proje dosyaları oluşturmak için önemli değildir veri kalıcılığı aracılığıyla gerçekleştirilir <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.  
  
 Uygulayabileceğiniz <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> ana `project subtype aggregator` nesnesi `project subtype project configuration` nesne ya da her ikisini de.  
  
 Aşağıdaki noktaları kavramlarla ilgili derleme dışı ilgili bilgiler kalıcılığı ana hatlarını vermektedir.  
  
-   Yükleme ve yapılandırma bağımsız verileri kaydetmek için ana proje alt (diğer bir deyişle, en dıştaki proje alt) toplayıcısı nesnede temel projesini çağıran ve yüklemek veya bağımlı yapılandırmasını kaydetmek için proje alt proje yapılandırma nesnelerde çağırır veriler.  
  
-   Temel Proje yöntemlerini çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> birden çok kez her proje alt toplama düzeyi için ve her düzeyi için GUID geçirir.  
  
-   Temel Proje geçirmeden veya belirli bir projede alt için ayrılmış ve toplama düzeyleri arasında kalıcı durumunun bir yolu olarak bu mekanizma kullanan bir XML parçası alır.  
  
-   Dıştaki proje alt ait temel projesini çağıran <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>bir GUID geçirme uygulama. GUID en dıştaki proje alt aitse, çağrı işler; Aksi takdirde GUID karşılık gelen proje alt bulunana kadar çağrısı bir iç proje alt vb. atar.  
  
-   Proje alt XML parçası çalıştırmadan önce veya bir iç proje alt çağrısı temsilciler sonra değiştirebilirsiniz. Aşağıdaki örnek, bir proje alt özgü özellikleri içeren bir dosya adı bu proje alt geçirilen burada bir proje dosyasından bir alıntı gösterir.  
  
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