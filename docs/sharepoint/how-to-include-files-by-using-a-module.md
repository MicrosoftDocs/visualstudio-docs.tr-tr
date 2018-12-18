---
title: 'Nasıl yapılır: bir modül kullanarak dosyaları dahil etme | Microsoft Docs'
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
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5c5152221e5e58504ba84e0ad0f31511b4d93aa0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120416"
---
# <a name="how-to-include-files-by-using-a-module"></a>Nasıl yapılır: bir modül kullanarak dosyaları dahil etme
  *Modülleri* (ile karıştırılmamalıdır [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modülleri) ASPX ana sayfalar gibi dosyaları, metin dosyaları ya da görüntüleri SharePoint'e dağıtmanıza olanak sağlayan kapsayıcılardır.  
  
 Belge kitaplığına veya normal bir dosya (örneğin, default.aspx) gibi bir dosya dağıtmak belge kitaplığı dışında seçebilirsiniz. Belge kitaplığına bir dosya eklemek için belirtin `Type="GhostableInLibrary"` bir öznitelik olarak **dosya** öğesi. Bu ayar kitaplığa eklendiğinde dosyanızla gitmek için bir liste öğesi oluşturmak için SharePoint bildirir. Belge kitaplığı dışında bir dosyayla dağıtılması için ya da belirttiğiniz `Type="Ghostable"` veya yalnızca çıkarın **türü** özniteliği.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Bir SharePoint çözüm bir modül Ekle  
  
#### <a name="to-add-a-module"></a>Bir modül eklemek için  
  
1.  İçinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bir SharePoint projesi oluşturun veya açın.  
  
     Daha fazla bilgi için bkz: [SharePoint projesi ve proje öğesi şablonları](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  İçinde **Çözüm Gezgini**, proje düğümünü seçin ve ardından, menü çubuğunda, **proje** > **Yeni Öğe Ekle**.  
  
     **Yeni Öğe Ekle** iletişim kutusu açılır.  
  
3.  SharePoint şablonları listesinden seçip **Modülü** şablonu ve ardından **Ekle** düğmesi.  
  
     Bu adım, bir düğümü Module1 adlı projeye oluşturur.  
  
4.  Module1 altında silmek *örnek.txt* dosya.  
  
     Örnek.txt tüm yeni modüllerdeki örneğin amaçları dahil edilir ve gerekli değildir. (Dosya silme de girdisini modülün kaldırır, Not *Elements.xml* dosyası.)  
  
5.  SharePoint belirli klasör yapısını dağıtmak için dosyalarınızı istiyorsanız, bu klasörleri Module1 altında oluşturun [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Module1 düğümü seçerek ve ardından, menü çubuğu seçme **proje**, **yeni Klasör**.  
  
6.  İstediğiniz dosyayı ekleyin ve ardından, menü çubuğunda klasörü seçin **proje**, **varolan öğeyi Ekle**.  
  
7.  SharePoint'e dağıtın ve ardından istediğiniz bir veya daha fazla dosya seçin **Ekle** düğmesi.  
  
     Projeye bir dosya eklediğinizde, bunun için bir giriş modülün Elements.xml dosyasına otomatik olarak eklenir. Proje dağıtıldığında, dosyalar tarafından belirtilen projenin kök dizine göreli SharePoint sunucusuna kopyalanır **dosya** öğenin **Url** gibi öznitelik `Url="Module1/New Folder/SomeFile.doc`. Bir dosya için dağıtım konumu değiştirmek istiyorsanız, ya da başka bir klasöre taşıyın **Çözüm Gezgini** veya değiştirmek kendi **Url** ayarı.  
  
8.  Bir Belge Kitaplığı'nda görünmesini istediğiniz tüm dosyaları ekleme `Type="GhostableInLibrary"` özniteliği kendi girişi *Elements.xml*. Örneğin,  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Projeyi dağıtın.  
  
     SharePoint içinde belirtilen konumlara dosyaları kopyalayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [SharePoint Çözümleri Geliştirme](../sharepoint/developing-sharepoint-solutions.md)  
  
