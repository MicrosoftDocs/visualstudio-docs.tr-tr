---
title: 'Nasıl yapılır: ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25d8d12b8ad49b40309845def60964c13a3da708
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919401"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturma
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] böylece kullanıcı o türden bir dosyayı açtığında uygulamayı otomatik olarak başlatılacak bir veya daha fazla dosya adı uzantılarına sahip uygulamalar ilişkilendirilebilir. Dosya adı uzantısı desteği için ekleme bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamasıdır basit.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturma  
  
1. Oluşturma bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama normal olarak veya mevcut [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  
  
2. Uygulama bildirimi, bir metin veya Not Defteri gibi bir XML Düzenleyicisi ile açın.  
  
3. Bulma `assembly` öğesi. Daha fazla bilgi için [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md).  
  
4. Bir alt öğesi olarak `assembly` öğe, Ekle bir `fileAssociation` öğesi. `fileAssociation` Öğesinde dört öznitelikler bulunur:  
  
   - `extension`: Uygulamayla ilişkilendirmek istediğiniz dosya adı uzantısı.  
  
   - `description`: Windows Kabuğu'nda görünür dosya türünün açıklaması.  
  
   - `progid`: Kayıt defterinde işaretlemek için dosya türü benzersiz olarak tanımlayan bir dize.  
  
   - `defaultIcon`: Bu dosya türü için kullanılacak bir simge. Simge dosyası kaynak uygulama bildirimi olarak eklenmesi gerekir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Bir örneği `file` ve `fileAssociation` öğeler, bkz [ \<fileAssociation > öğesi](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Birden fazla dosya türü uygulamayla ilişkilendirmek istiyorsanız, ek Ekle `fileAssociation` öğeleri. Unutmayın `progid` özniteliği, her biri için farklı olmalıdır.  
  
6. Uygulama bildirimini tamamladıktan sonra bildirimi yeniden imzalayın. Komut satırından kullanarak bunu yapabilirsiniz *Mage.exe*.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [\<fileAssociation > öğesi](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)