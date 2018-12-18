---
title: 'Nasıl yapılır: kod yerelleştirme | Microsoft Docs'
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
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d170906a66ffaaa0e73d4d7d236c8f41290abe55
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120561"
---
# <a name="how-to-localize-code"></a>Nasıl yapılır: kod yerelleştirme
  Yerelleştirilmemiş kod, sabit kodlanmış dize değerlerini kullanır. Kod dizeleri yerelleştirme için bunları çağrıları yerine <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, hangi yerelleştirilmiş kaynaklar başvuruda bulunan bir yöntemdir.  
  
## <a name="localize-code"></a>Kod yerelleştirme  
  
#### <a name="to-localize-code"></a>Kod yerelleştirme için  
  
1.  İçinde **Çözüm Gezgini**bir proje öğesi için kısayol menüsünü açın ve ardından **Ekle** > **Modülü**.  
  
     Seçin **kaynakları dosya** şablonu.  
  
    > [!NOTE]  
    >  Dağıtım türü özelliği kullanılabilir olmasını sağlamak için bir SharePoint proje öğesi kaynak dosyası eklediğinizden emin olun. Bu yordamda daha sonra bu özellik gereklidir.  
  
2.  Varsayılan dil kaynak dosyasına eklenen tercih ettiğiniz bir ad verin bir *.resx* uzantısı gibi *MyAppResources.resx*.  
  
3.  SharePoint proje öğesi için ayrı kaynak dosyaları eklemek için 1 ve 2 adımları yineleyin: her yerelleştirilmiş dili.  
  
     Her bir yerelleştirilmiş kaynak dosya için aynı temel adı kullanın, ancak kültür kimliği Ekle Örneğin, kaynak adı bir Almanca yerelleştirilmiş *MyAppResources.de DE.resx*.  
  
4.  Her kaynak dosyasını açın ve yerelleştirilmiş dizeleri ekleyin. Aynı dize kimlikleri her dosyasını kullanın.  
  
5.  Değerini değiştirme **dağıtım türü** için her kaynak dosyasının özelliği **AppGlobalResource** sunucunun App_GlobalResources klasöre dağıtmak için her bir dosyaya neden olacak.  
  
6.  Değerini bırakın **yapı eylemi** özelliği her bir dosyanın **katıştırılmış kaynak**.  
  
     Katıştırılmış kaynakları projenin DLL'e derlenir.  
  
7.  Uydu DLL'leri kaynak oluşturmak için projeyi oluşturun.  
  
8.  İçinde **paket tasarımcısını**, seçin **Gelişmiş** sekmesini tıklatın ve ardından uydu derleme ekleyin.  
  
9. İçinde **konumu** kutusunda, konumu yolu bir kültür kimliği klasörü gibi başına *de-DE\\\<proje öğesi adı >. resources.dll*.  
  
10. Çözümünüzü System.Web derleme zaten başvurmaması durumunda bir başvuru ekleyin ve kodunuzu bir yönerge eklentisi <xref:System.Web>.  
  
11. UI metin, hataları ve ileti metni gibi kullanıcılara görünür kodunuzdaki tüm sabit kodlanmış dizeleri bulun. Çağrı yerine <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> yöntemi aşağıdaki sözdizimini kullanarak:  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Seçin **F5** anahtarı oluşturun ve uygulamayı çalıştırın.  
  
13. SharePoint'te varsayılandan görüntüleme dilini değiştirin.  
  
     Yerelleştirilmiş dizeleri uygulamada görüntülenir. Yerelleştirilmiş kaynakları görüntülemek için SharePoint sunucusu kaynak dosyanın kültür eşleşen bir dil paketi olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint Çözümlerini Yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md)   
 [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)   
 [Nasıl yapılır: ASPX biçimlendirmesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)   
 [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)  

