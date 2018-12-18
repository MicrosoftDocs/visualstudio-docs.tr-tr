---
title: '&lt;compatibleFrameworks&gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 44329fc4c2ec5e9f2f8352d69ea487f23cbe3c5a
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077691"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks&gt; öğesi (ClickOnce dağıtımı)
Burada bu uygulamayı yükleyip çalıştırabileceği bir .NET Framework sürümlerini tanımlar.  
  
> [!NOTE]
>  [*MageUI.exe* ](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) desteklemediği `compatibleFrameworks` bir uygulama bildirimi kaydedilirken öğesi zaten açtığı kullanarak bir sertifika [ *MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Bunun yerine, kullanmalısınız [ *Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
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
 `compatibleFrameworks` Hedefleyen dağıtım bildirimleri için öğesi gereklidir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalışma zamanı tarafından sağlanan [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] veya üzeri. `compatibleFrameworks` Öğesi içeren bir veya daha fazla `framework` belirten .NET Framework sürümleri bu uygulamayı çalıştırabilirsiniz. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Çalışma zamanı, ilk uygulama çalışacak kullanılabilir `framework` bu listede.  
  
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
 Aşağıdaki kod örnekte gösterildiği bir `compatibleFrameworks` öğesinde bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi. Bu dağıtım üzerinde çalışabilen [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)]. Ayrıca çalıştırılabileceği [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] çünkü bu bir üst [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].  
  
```xml  
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
  <framework   
      targetVersion="4.0"   
      profile="Client"   
      supportedRuntime="4.0.30319" />  
</compatibleFrameworks>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)