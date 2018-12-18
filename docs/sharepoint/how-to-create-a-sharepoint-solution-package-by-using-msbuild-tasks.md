---
title: 'Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120414"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Nasıl yapılır: MSBuild görevlerini kullanarak bir SharePoint çözüm paketi oluşturma
  Yapı, temizleme ve SharePoint paketi doğrulama (*.wsp*) geliştirme bilgisayarındaki komut satırı MSBuild görevlerini kullanarak. Bu komutlar, yapı işlemi bir yapı bilgisayarında Team Foundation Server kullanarak otomatik hale getirmek için de kullanabilirsiniz.  
  
## <a name="build-a-sharepoint-package"></a>Bir SharePoint paketi oluşturma  
  
#### <a name="to-build-a-sharepoint-package"></a>Bir SharePoint paketi oluşturmak için  
  
1.  Windows **Başlat** menüsünde seçin **tüm programlar** > **Donatılar** > **komut istemi**.  
  
2.  SharePoint Proje bulunduğu dizine geçin.  
  
3.  Proje için bir paket oluşturmak için aşağıdaki komutu girin. Değiştir *ProjectFileName* proje adı.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Örneğin, ListDefinition1 adlı bir SharePoint Proje paketlemek için aşağıdaki komutlardan birini çalıştırabilirsiniz.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Bir SharePoint paketi Temizle  
  
#### <a name="to-clean-a-sharepoint-package"></a>Bir SharePoint paketi temizlemek için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  SharePoint Proje bulunduğu dizine geçin.  
  
3.  Proje için bir paket temizlemek için aşağıdaki komutu girin. Değiştir *ProjectFileName* proje adı.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Örneğin, ListDefinition1 adlı bir SharePoint Proje temizlemek için aşağıdaki komutlardan birini çalıştırabilirsiniz.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Bir SharePoint paketi doğrulama  
  
#### <a name="to-validate-a-sharepoint-package"></a>Bir SharePoint paketi doğrulamak için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  SharePoint Proje bulunduğu dizine geçin.  
  
3.  Proje için bir paket doğrulamak için aşağıdaki komutu girin. Değiştir *ProjectFileName* proje adı.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Örneğin, ListDefinition1 adlı bir SharePoint Proje doğrulamak için aşağıdaki komutlardan birini çalıştırabilirsiniz.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Bir SharePoint paket özelliklerini ayarlama  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Bir SharePoint pakette bir özelliği ayarlamak için  
  
1.  Bir komut istemi penceresi açın.  
  
2.  SharePoint Proje bulunduğu dizine geçin.  
  
3.  Proje için bir paketteki bir özelliği ayarlamak için aşağıdaki komutu girin. Değiştir *PropertyName* ayarlamak istediğiniz özelliğine sahip.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Örneğin, uyarı düzeyini ayarlamak için aşağıdaki komutu çalıştırabilirsiniz.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint özellikleri oluşturma](../sharepoint/creating-sharepoint-features.md)   
 [Nasıl yapılır: bir SharePoint özelliğini özelleştirme](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Nasıl yapılır: SharePoint özelliklerine öğe ekleyip](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
