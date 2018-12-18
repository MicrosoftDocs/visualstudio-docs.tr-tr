---
title: '&lt;bağımlılık&gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33e210b0787c3325a009bc54505812f22c44da84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916900"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;bağımlılık&gt; öğesi (ClickOnce dağıtımı)
Sürümü yüklemek için uygulama ve uygulama bildiriminin konumunu tanımlar.  

## <a name="syntax"></a>Sözdizimi  

```xml  

      <dependency>   
   <dependentAssembly  
      preRequisite  
      visible  
      dependencyType  
      codeBase  
      size  
   >   
      <assemblyIdentity   
         name   
         version   
         publicKeyToken   
         processorArchitecture   
         language  
         type  
      />   
      <hash>  
         <dsig:Transforms>  
            <dsig:Transform  
                Algorithm  
            />  
         </dsig:Transforms>  
         <dsig:DigestMethod />  
         <dsig:DigestValue>  
         </dsig:DigestValue>  
      </hash>  

   </dependentAssembly>   
</dependency>  
```  

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `dependency` Öğesi gereklidir. Bu öznitelikleri yok. Bir dağıtım bildirimi birden çok olabilir `dependency` öğeleri.  

 `dependency` Öğesi genellikle ifade ana uygulama için bağımlılıklar içinde bulunan derlemeler üzerinde bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. Main.exe uygulamanız DotNetAssembly.dll olarak adlandırılan bir derleme kullanırsa, bu derleme bağımlılık bölümünde listelenmesi gerekir. Bağımlılık, ancak aynı zamanda diğer türleri gibi belirli bir ortak dil çalışma zamanı sürümünü bağımlılıkları bağımlılık bir derlemeyi genel derleme önbelleğinde (GAC) veya bir COM nesnesi ifade edebilir. Bir dokunmadan dağıtım teknolojisi olduğundan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olamaz başlatma indirme ve yükleme bağımlılıkları, ancak bu tür engellemez uygulamanın çalışmasını bir veya daha fazla belirtilen bağımlılık yoksa.  

## <a name="dependentassembly"></a>dependentAssembly  
 Gerekli. Bu öğeyi içeren `assemblyIdentity` öğesi. Aşağıdaki tabloda öznitelikleri gösterir `dependentAssembly` destekler.  


| Öznitelik | Açıklama |
|------------------| - |
| `preRequisite` | İsteğe bağlı. Bu derlemenin GAC'de zaten olmaması gerektiğini belirtir. Geçerli değerler `true` ve `false`. Varsa `true`ve belirtilen derlemeyi GAC içinde yok, uygulamayı çalıştırmak başarısız olur. |
| `visible` | İsteğe bağlı. Bağımlılıkları da dahil olmak üzere, en üst düzey uygulama kimliği tanımlar. Tarafından dahili olarak kullanılan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama depolama ve etkinleştirme yönetmek için. |
| `dependencyType` | Gerekli. Bu bağımlılık ve uygulama arasındaki ilişki. Geçerli değerler şunlardır:<br /><br /> -   `install`. Bileşenini, geçerli uygulamadan ayrı bir yükleme temsil eder.<br />-   `preRequisite`. Bileşen geçerli uygulama tarafından gereklidir. |
| `codebase` | İsteğe bağlı. Uygulama bildiriminin tam yolu. |
| `size` | İsteğe bağlı. Uygulama bildirimini bayt cinsinden boyutu. |

## <a name="assemblyidentity"></a>assemblyIdentity  
 Gerekli. Bu öğenin alt öğesi olan `dependentAssembly` öğesi. İçeriği `assemblyIdentity` aynı açıklandığı olmalıdır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi. Aşağıdaki tabloda gösterilmektedir dosyanın öznitelikleri `assemblyIdentity` öğesi.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Name`|Gerekli. Uygulamanın adını tanımlar.|  
|`Version`|Gerekli. Uygulamanın sürüm sayısını şu biçimde belirtir: `major.minor.build.revision`|  
|`publicKeyToken`|Gerekli. Son 8 bayt altında derleme veya uygulama imzalanan ortak anahtarı SHA-1 karmasını temsil eden 16 karakterlik bir onaltılık dize belirtir. İmzalamak için kullanılan ortak anahtar, 2048 bit olmalıdır veya büyük.|  
|`processorArchitecture`|Gerekli. Mikro işlemciyi belirtir. Geçerli değerler `x86` 32-bit Windows için ve `IA64` 64 bit Windows için.|  
|`Language`|İsteğe bağlı. Derlemenin iki bölümü dil kodlarını tanımlar. Örneğin, EN-US, İngilizce (ABD) anlamına gelir. Varsayılan, `neutral` değeridir. Bu öğe `asmv2` ad alanı.|  
|`type`|İsteğe bağlı. Geriye dönük uyumluluk Windows yan yana ile yüklemek için teknoloji. Yalnızca izin verilen değer `win32`.|  

## <a name="hash"></a>hash  
 `hash` İsteğe bağlı bir alt öğedir `file` öğesi. `hash` Öğesi özniteliklere sahip değildir.  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulamadaki tüm dosyaların algoritmik bir karma dosyaların hiçbiri dağıtımdan sonra değişmediğinden emin olmak için güvenlik denetimi olarak kullanır. Varsa `hash` öğesi dahil değildir, bu denetimi gerçekleştirilmeyecek. Bu nedenle, atlama `hash` öğesi önerilmez.  

## <a name="dsigtransforms"></a>dsig:TRANSFORMS  
 `dsig:Transforms` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:Transforms` Öğesi özniteliklere sahip değildir.  

## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform` Öğesi gerekli alt öğesi olan `dsig:Transforms` öğesi. Aşağıdaki tabloda gösterilmektedir dosyanın öznitelikleri `dsig:Transform` öğesi.  


| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğu `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig  
 `dsig:DigestMethod` Öğesi gerekli alt öğesi olan `hash` öğesi. Aşağıdaki tabloda gösterilmektedir dosyanın öznitelikleri `dsig:DigestMethod` öğesi.  


| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğu `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>DigestValue  
 `dsig:DigestValue` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:DigestValue` Öğesi özniteliklere sahip değildir. Metin değeri, belirtilen dosya için hesaplanan karmasıdır.  

## <a name="remarks"></a>Açıklamalar  
 Dağıtım bildirimleri genellikle sahip tek bir `assemblyIdentity` adı ve sürümü uygulama bildiriminin tanımlayan öğesi.  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örnekte gösterildiği bir `dependency` öğesinde bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimi.  

```xml  
<!-- Identify the assembly dependencies -->  
<dependency>  
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">  
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, zaten GAC'de kurulu bir derleme üzerinde bir bağımlılık belirtir.  

```xml  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />  
  </dependentAssembly>  
</dependency>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir bağımlılık belirli bir ortak dil çalışma zamanı sürümünü belirtir.  

```xml  
<dependency>  
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />  
  </dependentAssembly>  
</dependency>  
```  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir işletim sistemi bağımlılık belirtir.  

```xml  
<dependency>  
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">  
      <osVersionInfo>  
         <os majorVersion="4" minorVersion="10" />  
      </osVersionInfo>  
   </dependentOS>  
</dependency>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [\<bağımlılık > öğesi](../deployment/dependency-element-clickonce-application.md)