---
title: 'Nasıl yapılır: ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: fd1bd7965f0277ce1d3d900be6ee10db097eeb3f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49909113"
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için Dosya İlişkilendirmeleri Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] böylece kullanıcı o türden bir dosyayı açtığında uygulamayı otomatik olarak başlatılacak bir veya daha fazla dosya adı uzantılarına sahip uygulamalar ilişkilendirilebilir. Dosya adı uzantısı desteği için ekleme bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamasıdır basit.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>ClickOnce uygulaması için dosya ilişkilendirmeleri oluşturma  
  
1. Oluşturma bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama normal olarak veya mevcut [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.  
  
2. Uygulama bildirimi, bir metin veya Not Defteri gibi bir XML Düzenleyicisi ile açın.  
  
3. Bulma `assembly` öğesi. Daha fazla bilgi için [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md).  
  
4. Bir alt öğesi olarak `assembly` öğe, Ekle bir `fileAssociation` öğesi. `fileAssociation` Öğesinde dört öznitelikler bulunur:  
  
   - `extension`: Uygulamayla ilişkilendirmek istediğiniz dosya adı uzantısı.  
  
   - `description`: Windows Kabuğu'nda görünür dosya türünün açıklaması.  
  
   - `progid`: Kayıt defterinde işaretlemek için dosya türü benzersiz olarak tanımlayan bir dize.  
  
   - `defaultIcon`: Bu dosya türü için kullanılacak bir simge. Simge dosyası kaynak uygulama bildirimi olarak eklenmesi gerekir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Bir örneği `file` ve `fileAssociation` öğeler, bkz [ \<fileAssociation > öğesi](../deployment/fileassociation-element-clickonce-application.md).  
  
5. Birden fazla dosya türü uygulamayla ilişkilendirmek istiyorsanız, ek Ekle `fileAssociation` öğeleri. Unutmayın `progid` özniteliği, her biri için farklı olmalıdır.  
  
6. Uygulama bildirimini tamamladıktan sonra bildirimi yeniden imzalayın. Komut satırından Mage.exe kullanarak bunu yapabilirsiniz.  
  
    `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
    Daha fazla bilgi için [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<fileAssociation > öğesi](../deployment/fileassociation-element-clickonce-application.md)   
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)



