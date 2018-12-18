---
title: '&lt;fileAssociation&gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <fileAssociation> element [ClickOnce application manifest]
- manifests [ClickOnce], fileAssociation element
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 62e099f949af3cc3ea336663224c1dd92726ac53
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080031"
---
# <a name="ltfileassociationgt-element-clickonce-application"></a>&lt;fileAssociation&gt; öğesi (ClickOnce uygulaması)
Uygulamayla ilişkilendirilecek bir dosya uzantısı tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `fileAssociation` Öğesi, isteğe bağlıdır. Öğe, aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`extension`|Gerekli. Uygulamayla ilişkilendirilecek dosya uzantısı.|  
|`description`|Gerekli. Kabuk tarafından kullanım için dosya türünün açıklaması.|  
|`progid`|Gerekli. Dosya türü benzersiz olarak tanımlayan ad.|  
|`defaultIcon`|Gerekli. Bu uzantılı dosyalar için kullanılacak simgeyi belirtir. Simge dosyası kullanılarak belirtilmelidir [ \<Dosya > öğesi](../deployment/file-element-clickonce-application.md) içinde [ \<derleme > öğesi](../deployment/assembly-element-clickonce-application.md) bu öğeyi içeren.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu öğe için bir XML ad alanı başvurusu içermelidir "urn: schemas-microsoft-com:clickonce.v1". Varsa `<fileAssociation>` öğesi kullanılırsa, sonra gelmelidir `<application>` üst öğesinde [ \<derleme > öğesi](../deployment/assembly-element-clickonce-application.md).  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosya ilişkilendirmeleri üzerine yazmaz. Bununla birlikte, ClickOnce uygulaması dosya uzantısı yalnızca geçerli kullanıcı için geçersiz kılabilirsiniz. Bu ClickOnce Uygulama kaldırıldıktan sonra kullanıcı için dosya ilişkilendirmesi ClickOnce siler ve makine başına ilişkisini yeniden etkindir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde gösterilmiştir `fileAssociation` bildiriminde bir uygulamada kullanılarak dağıtılan bir metin düzenleyicisi uygulaması için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Ayrıca bu kod örneği içerir [ \<Dosya > öğesi](../deployment/file-element-clickonce-application.md) gerektirdiği `defaultIcon` özniteliği.  
  
```xml  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)