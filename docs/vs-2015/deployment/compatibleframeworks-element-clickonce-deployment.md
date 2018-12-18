---
title: '&lt;compatibleFrameworks&gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
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
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 051fd3eea0ffab2a7c5f088538d7208c8286d1d6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176600"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Burada bu uygulamayı yükleyip çalıştırabileceği bir .NET Framework sürümlerini tanımlar.  
  
> [!NOTE]
>  [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14) desteklemediği `compatibleFrameworks` bir uygulama bildirimi kaydedilirken öğesi zaten açtığı kullanarak bir sertifika [MageUI.exe](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Bunun yerine, kullanmalısınız [Mage.exe](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<compatibleFrameworks  
      SupportUrl>   
   <framework  
      targetVersion  
      profile  
      supportedRuntime  
   />   
</ compatibleFrameworks>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `compatibleFrameworks` Hedefleyen dağıtım bildirimleri için öğesi gereklidir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] çalışma zamanı tarafından sağlanan [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] veya üzeri. `compatibleFrameworks` Öğesi içeren bir veya daha fazla `framework` belirten .NET Framework sürümleri bu uygulamayı çalıştırabilirsiniz. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Çalışma zamanı, ilk uygulama çalışacak kullanılabilir `framework` bu listede.  
  
 Aşağıdaki tabloda öznitelikleri listeler, `compatibleFrameworks` öğeyi destekler.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`S``upportUrl`|İsteğe bağlı. Tercih edilen uyumlu .NET Framework sürümünü nereden indirilebileceğini bir URL'yi belirtir.|  
  
## <a name="framework"></a>çerçeve  
 Gerekli. Aşağıdaki tabloda öznitelikleri listeler, `framework` öğeyi destekler.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`targetVersion`|Gerekli. Hedef .NET Framework'ün sürüm numarasını belirtir.|  
|`profile`|Gerekli. Hedef .NET Framework'ü profilini belirtir.|  
|`supportedRuntime`|Gerekli. Hedef .NET Framework ile ilişkili çalışma zamanı sürüm numarasını belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekte gösterildiği bir `compatibleFrameworks` öğesinde bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi. Bu dağıtım üzerinde çalışabilen [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]. Ayrıca çalıştırılabileceği [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] çünkü bu bir üst [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)].  
  
```  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Bildirimi](../deployment/clickonce-deployment-manifest.md)



