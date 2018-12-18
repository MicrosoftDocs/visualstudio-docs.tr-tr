---
title: '&lt;entryPoint&gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56996f83f0ac8d9e7b2bce81ab7e2c8e13faee52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49934632"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt; öğesi (ClickOnce uygulaması)
Gereken derleme tanımlayan yürütülmesi bu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı bir istemci bilgisayarda çalıştırın.  

## <a name="syntax"></a>Sözdizimi  

```xml  
<entryPoint  
   name  
>  
   <assemblyIdentity  
      name  
      version  
      processorArchitecture  
      language  
   />  
   <commandLine  
      file  
      parameters  
   />  
   <customHostRequired />  
   <customUX />  
</entryPoint>  
```  

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `entryPoint` Öğesi gereklidir ve içinde `urn:schemas-microsoft-com:asm.v2` ad alanı. Yalnızca olabilir bir `entryPoint` uygulama bildiriminde tanımlanan öğe.  

 `entryPoint` Öğesi aşağıdaki özniteliklere sahiptir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|İsteğe bağlı. Bu değer, .NET Framework tarafından kullanılmaz.|  

 `entryPoint` Aşağıdaki öğelere sahiptir.  

## <a name="assemblyidentity"></a>assemblyIdentity  
 Gerekli. Rolü `assemblyIdentity` ve özniteliklerini tanımlanmış [ \<assemblyIdentity > öğesi](../deployment/assemblyidentity-element-clickonce-application.md).  

 `processorArchitecture` Özniteliği bu öğenin ve `processorArchitecture` tanımlanan öznitelik `assemblyIdentity` uygulama bildirimi başka bir yerde eşleşmelidir.  

## <a name="commandline"></a>komut satırı  
 Gerekli. Bir alt öğesi olmalıdır `entryPoint` öğesi. Alt öğe yok ve aşağıdaki özniteliklere sahiptir.  


| Öznitelik | Açıklama |
|--------------| - |
| `file` | Gerekli. Yerel başvuru için başlangıç derlemesine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. Bu değer, eğik çizgi (/) veya ters eğik çizgi içeremez (\\) yol ayırıcı. |
| `parameters` | Gerekli. Giriş noktası ile gerçekleştirilecek eylemi açıklar. Yalnızca geçerli değer `run`; boş bir dize sağlanmazsa `run` varsayılır. |

## <a name="customhostrequired"></a>customHostRequired  
 İsteğe bağlı. Bu onay kutusu eklediyseniz, bu dağıtım için özel bir ana bilgisayar içinde dağıtılan bir bileşen içerdiğini belirtir ve tek başına bir uygulama değildir.  

 Bu öğe varsa `assemblyIdentity` ve `commandLine` öğeleri de mevcut olmamalıdır. Böyle bir durumda [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yükleme sırasında bir doğrulama hatası verir.  

 Bu öğenin öznitelikleri ve alt öğe var.  

## <a name="customux"></a>customUX  
 İsteğe bağlı. Uygulama yüklenir ve özel bir yükleyici tarafından korunur ve oluşturmaz Başlat menüsü girişi, kısayol veya Ekle veya programlar girdisini kaldırmak olduğunu belirtir.  

```xml  
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />  
```  

 CustomUX öğesi içeren bir uygulama kullanan özel bir yükleyici sağlamalısınız <xref:System.Deployment.Application.InPlaceHostingManager> yükleme işlemlerini gerçekleştirmek için. Bu öğe ile bir uygulama bildirimi ya da setup.exe, önkoşul önyükleyici çift tıklayarak yüklenemez. Başlangıç menüsünde girişleri, kısayolları ve Program Ekle veya Kaldır girişleri özel yükleyici oluşturabilirsiniz. Özel yükleyici Program Ekle veya Kaldır bir giriş oluşturmaz, tarafından sağlanan abonelik tanımlayıcısı depolamalısınız <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> özelliği ve etkinleştirme çağırarak daha sonra uygulamayı kaldırmak için kullanıcı <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> yöntemi. Daha fazla bilgi için [izlenecek yol: ClickOnce uygulaması için özel bir yükleyici oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).  

## <a name="remarks"></a>Açıklamalar  
 Bu öğe için derleme ve giriş noktasını tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  

 Kullanamazsınız `commandLine` uygulamanıza çalışma zamanında parametreleri geçirmek için. Sorgu dizesi parametreleri için erişebileceğiniz bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın dağıtımından <xref:System.AppDomain>. Daha fazla bilgi için [nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde gösterilmiştir bir `entryPoint` öğesi için bir uygulama bildiriminde bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md) konu.  

```xml  
<!-- Identify the main code entrypoint. -->  
<!-- This code runs the main method in an executable assembly. -->  
  <entryPoint>  
    <assemblyIdentity   
      name="MyApplication"   
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)
