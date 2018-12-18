---
title: İş verileri bağlantı modeli oluşturma | Microsoft Docs
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
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 68940d6e48f1f3a3e51017e1cc838976735de104
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49930212"
---
# <a name="create-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli oluşturma
  Bir iş verileri bağlantısı (BDC) modeli oluşturabilir veya Visual Studio kullanarak mevcut bir BDC modelini özelleştirin. Her SharePoint projesi, yalnızca bir modeli içerebilir. Daha fazla bilgi için [iş verilerini SharePoint ile tümleştirmeyi](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Yeni model oluştur
 Yeni bir modeli oluşturmak için bir **iş verileri bağlantı modeli** ekleyin veya proje bir **iş verileri bağlantı modeli** öğesinin bir **boş SharePoint projesi**.  
  
> [!NOTE]  
>  Olmalıdır [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] bilgisayarınızda yüklü.  
  
 Visual Studio, projeye bir klasör ekler. Bu klasör için belirttiğiniz ada sahip **iş verileri bağlantı modeli** öğesi **Yeni Öğe Ekle** iletişim kutusu. Yeni bir oluşturursanız **iş verileri bağlantı modeli** proje, Visual Studio klasör adları **BdcModel1**.  
  
 Visual Studio aşağıdaki dosyalarını yeni klasöre ekler:  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|Model tanımı dosyası|Varlıklar, yöntemleri, çizgi, iş kolu (LOB) sistem nesneleri ve modeli açıklayan diğer meta verileri tanımlayan XML içeriyor.<br /><br /> İVB Tasarımcısı kullanarak bu dosya meta verilerde değişiklik **BDC Gezgini**, **BDC yöntem ayrıntıları** penceresinde ve **özellikleri** penceresi.|  
|Varlık hizmeti kodu dosyası|Alma, güncelleştirme ve varsayılan varlık örneklerini silme yöntemlerini içerir.|  
  
 Bir varlığın özelliklerini tanımlamak için varlık kod dosyasını düzenleyin. Daha fazla bilgi için [nasıl yapılır: modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Varlık örneklerini silme almak ve güncelleştirmek için varlık hizmet kodu dosyası için kodu ekleyin. Daha fazla bilgi için [iş verileri bağlantı modeli tasarlama](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Visual Studio, Projeyi derlediğinizde, bir derleme oluşturur. Proje bütünleştirilmiş kodu için kod ekleme proje diğer öğeleri eklemediğinizden emin olun (örneğin: bir **sıralı iş akışı** öğesi veya bir **Web Bölümü** öğesi). Çözüm paketi derlemeyi genel bütünleştirilmiş kod önbelleğine kopyalamaz çünkü çözümünü dağıttığınızda, bu öğe için kod çalışmaz.  Çözüm paketi İVB veritabanına SharePoint yalnızca derleme dağıtır.  
  
> [!NOTE]  
>  Projede hata ayıklaması yaparken visual Studio derleme konumlarının her ikisinde de yerel bilgisayarınıza kopyalar.  
  
## <a name="add-an-existing-model"></a>Mevcut bir model ekleme
 SharePoint Designer gibi diğer araçları kullanılarak oluşturulmuş bir modeli içeri aktarabilirsiniz. Projenize aşağıdaki durumlarda var olan bir model almayı da tercih edebilirsiniz:  
  
- Zaten bir SharePoint sunucu grubu için Dağıtılmış bir modelinin özelleştirmek için.  
  
- Paketleme ve birden çok SharePoint sunucu grupları için mevcut bir model dağıtma için.  
  
  Her iki durumda da, içeri aktardığınız modelde tanımlı LOB sistemlerini etkilenmez ve beklendiği gibi çalışmayı sürdürecektir. Bir SharePoint projesine mevcut bir model eklemek için Visual Studio kullanan **varolan öğeyi Ekle** iletişim kutusu. Daha fazla bilgi için [nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
  Bir seçenek belirleyerek, içeri aktarılan modele türü .NET Framework derlemesinin bir LOB sistemine ekleyebilirsiniz **LobSystem ekleme .NET bütünleştirilmiş kodu**. Bu, özel kod yazmanıza ve alınan model meta verilerini tanımlamak için bir tasarımcı kullanmanıza olanak sağlar.  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: BDC modeli oluşturma](../sharepoint/how-to-create-a-bdc-model.md)|Yeni bir BDC modeli oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: bir SharePoint projesine mevcut bir BDC modeli dosyası ekleme](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Bir SharePoint projesine mevcut bir model alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: yerelleştirilmiş adlar, özellikler ve izinleri belirtmek için bir kaynak dosyası kullanma](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Modeli bir Web Bölümü veya Web sayfası tarafından kullanıldığında birleştirilir dizeleri ile model meta verilerini sağlamak açıklar.|  
|[Nasıl yapılır: özel bir derlemeyi bir BDC özelliğine dahil etme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Özel bir derlemeyi özelliği etme işlemi gösterilmektedir.|  
  
 
