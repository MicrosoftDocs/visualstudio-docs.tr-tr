---
title: Çözümde dosyaları eklemeyi modüllerini kullanma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deployment modules
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f0773d9c167a0a799b7d9bc8ddd2b52afc9bc6f2
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120431"
---
# <a name="use-modules-to-include-files-in-the-solution"></a>Çözüme dosyaları dahil etmek için modülleri kullanın
  SharePoint server gibi yeni ana sayfalar kendi dosya türü ne olursa olsun dosyaları dağıtmak istediğinizde zamanlar olabilir. Bunu yapmak için kullanabileceğiniz *modülleri* (ile karıştırılmamalıdır [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] kod modülleri). Modüller, bir SharePoint çözüm dosyalarında kapsayıcılardır. Çözüm dağıtıldığında, modül dosyalarında SharePoint sunucusunda belirtilen klasörlerine kopyalanır.  
  
## <a name="module-items-and-elements"></a>Modül öğeleri ve öğeleri
 Bir modül oluşturmak için bu projeye içinde seçerek eklemek **Yeni Öğe Ekle** iletişim kutusu. Ardından, değiştirme, *Elements.xml* dosyasını, sistemde nerede ve SharePoint sunucusu üzerine kopyalanmalıdır dağıtmak istediğiniz dosyaların adını içerecek şekilde.  
  
 Bir örneği burada verilmiştir *Elements.xml* bir modül için dosya:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Elements xmlns="http://schemas.microsoft.com/sharepoint/">  
    <Module Name="Module1">  
        <File Path="Module1\Sample.txt" Url="Module1/Sample.txt" />  
    </Module>  
</Elements>  
  
```  
  
 Yeni oluşturulan modüller aşağıdaki varsayılan dosyaları içerir:  
  
|Dosya Adı|Açıklama|  
|---------------|-----------------|  
|*Elements.XML*|Modül tanımı dosyası.|  
|*Örnek.txt*|Modül dosyasında bir örnek olarak hizmet veren bir yer tutucu dosyası.|  
  
 *Elements.xml* dosyası aşağıdaki öğeleri içerir:  
  
|Öğe adı|Açıklama|  
|------------------|-----------------|  
|Öğeleri|Modülde tanımlanan tüm öğeleri içerir.|  
|Modül|Modül öğesi tek bir özniteliği var *adı*, modül adı biçiminde belirtir `<Module Name="Module1">`.<br /><br /> Modülün adını değiştirirseniz unutmayın (veya kendi *klasör adı* özelliği), modül öğesindeki adla el ile güncelleştirmeniz gerekir.<br /><br /> Dosya veya dosyalar için bir alt modülü öğesinde belirtirseniz, [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) otomatik olarak oluşturacak eşleşen bir dizin yapısına kendileri için.|  
|Dosya|Dosya öğesi iki parametreye sahip *yolu* ve *Url*.<br /><br /> -Path: Adını ve konumunu SharePoint çözüm dosyasında. Biçimidir, `Path="Module1\Sample.txt"`.<br /><br /> -Url: SharePoint sunucusu üzerinde dosya dağıtılacağı konumu. Biçimidir, `Url="Module1/Sample.txt"`.<br /><br /> -Type: iki ayarlara sahip bir isteğe bağlı öznitelik: *GhostableInLibrary* ve *Ghostable*. Biçimidir, `Type="GhostableInLibrary"`. Belirtme *GhostableInLibrary* dosya, SharePoint belge kitaplığında kitaplığa eklendiğinde dosya eşlik için bir liste öğesi ile birlikte eklenir anlamına gelir. Belirtme *Ghostable* belge kitaplığı dışında SharePoint'e eklenecek dosyanın neden olur.|  
  
 Dağıtmak istediğiniz her dosya için ayrı bir gerekli `<File>` öğe girişi *Elements.xml*.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [Nasıl yapılır: bir modül kullanarak dosyaları dahil etme](../sharepoint/how-to-include-files-by-using-a-module.md)   
 [nasıl yapılır: bir dosya sağlama](http://go.microsoft.com/fwlink/?LinkID=144271)   
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Paket ve SharePoint çözümlerini dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
