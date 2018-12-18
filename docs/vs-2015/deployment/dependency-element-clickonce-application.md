---
title: '&lt;bağımlılık&gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
caps.latest.revision: 36
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: e76d517af1e0bd93507a47facd63bd50ae98e635
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49233863"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;bağımlılık&gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulama için gerekli olan bir platform veya derleme bağımlılık tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
  
      <dependency>  
   <dependentOS  
      supportURL  
      description  
   >  
      <osVersionInfo>  
         <os  
            majorVersion  
            minorVersion  
            buildNumber  
            servicePackMajor  
            servicePackMinor  
            productType  
            suiteType  
         />   
      </osVersionInfo>  
   </dependentOS>  
   <dependentAssembly  
      dependencyType  
      allowDelayedBinding  
      group  
      codeBase  
      size  
   >  
      <assemblyIdentity  
         name  
         version  
         processorArchitecture  
         language  
      >  
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
  
      </assemblyIdentity>  
   </dependentAssembly>  
</dependency>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `dependency` Öğesi gereklidir. Birden çok örneğini olabilir `dependency` aynı uygulama bildiriminde.  
  
 `dependency` Öğesi özniteliklere sahip ve aşağıdaki alt öğeleri içerir.  
  
### <a name="dependentos"></a>dependentOS  
 İsteğe bağlı. İçeren `osVersionInfo` öğesi. `dependentOS` Ve `dependentAssembly` öğeleri karşılıklı olarak birbirini dışlar: birini veya diğerini için bulunmalıdır bir `dependency` öğesi, ancak ikisine birden değil.  
  
 `dependentOS` Aşağıdaki öznitelikler destekler.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`supportUrl`|İsteğe bağlı. Bağımlı bir platform için destek URL'sini belirtir. Bu URL, gerekli platformda bulunursa kullanıcıya gösterilir.|  
|`description`|İsteğe bağlı. Açıklar, insan tarafından okunabilir formda tarafından tanımlanan işletim sistemini `dependentOS` öğesi.|  
  
### <a name="osversioninfo"></a>OSVERSIONINFO  
 Gerekli. Bu öğenin alt öğesi olan `dependentOS` öğesi ve içeren `os` öğesi. Bu öğenin öznitelikleri yok.  
  
### <a name="os"></a>işletim sistemi  
 Gerekli. Bu öğenin alt öğesi olan `osVersionInfo` öğesi. Bu öğe aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`majorVersion`|Gerekli. İşletim sistemi ana sürüm numarasını belirtir.|  
|`minorVersion`|Gerekli. İşletim sistemi alt sürümü sayısını belirtir.|  
|`buildNumber`|Gerekli. İşletim sistemi yapı sayısını belirtir.|  
|`servicePackMajor`|Gerekli. İşletim sistemi hizmet paketi ana sayısını belirtir.|  
|`servicePackMinor`|İsteğe bağlı. İşletim sistemi hizmet paketi alt sayısını belirtir.|  
|`productType`|İsteğe bağlı. Ürün türü değeri tanımlar. Geçerli değerler `server`, `workstation`, ve `domainController`. Örneğin, Windows 2000 Professional için bu öznitelik değeri olan `workstation`.|  
|`suiteType`|İsteğe bağlı. Sistem veya sistem yapılandırma türü mevcut bir ürün paketi tanımlar. Geçerli değerler `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted`, ve `terminal`. Örneğin, Windows 2000 Professional için bu öznitelik değeri olan `professional`.|  
  
### <a name="dependentassembly"></a>dependentAssembly  
 İsteğe bağlı. İçeren `assemblyIdentity` öğesi. `dependentOS` Ve `dependentAssembly` öğeleri karşılıklı olarak birbirini dışlar: birini veya diğerini için bulunmalıdır bir `dependency` öğesi, ancak ikisine birden değil.  
  
 `dependentAssembly` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`dependencyType`|Gerekli. Bağımlılık türünü belirtir. Geçerli değerler `preprequisite` ve `install`. Bir `install` derlemenin bir parçası olarak yüklü [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. A `prerequisite` derleme genel derleme önbelleğinde (GAC) önce mevcut olmalıdır [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama yükleyebilirsiniz.|  
|`allowDelayedBinding`|Gerekli. Derleme programlı olarak çalışma zamanında yüklenebilir olup olmadığını belirtir.|  
|`group`|İsteğe bağlı. Varsa `dependencyType` özniteliği `install`, isteğe bağlı olarak yalnızca yükleme derlemelerin adlandırılmış bir grubu belirtir. Daha fazla bilgi için [izlenecek yol: ClickOnce dağıtım API'sini kullanarak tasarımcı ile isteğe bağlı derlemeleri indirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Varsa kümesine `framework` ve `dependencyType` özniteliği `prerequisite`, .NET Framework'ün bir parçası olarak derlemeyi belirtir. Genel Derleme Önbelleği (GAC) Bu derleme için yüklerken işaretlenmediği [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] ve sonraki sürümler.|  
|`codeBase`|Ne zaman gerekli `dependencyType` özniteliği `install`. Bağımlı derleme yolu. Mutlak bir yol veya bildirim kodunun göreli bir yol, temel olabilir. Bu yol, geçerli olması için bütünleştirilmiş kod bildirimi sırada geçerli bir URI olmalıdır.|  
|`size`|Ne zaman gerekli `dependencyType` özniteliği `install`. Bağımlı derlemenin bayt cinsinden boyutu.|  
  
### <a name="assemblyidentity"></a>assemblyIdentity  
 Gerekli. Bu öğenin alt öğesi olan `dependentAssembly` öğesi ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli. Uygulamanın adını tanımlar.|  
|`version`|Gerekli. Uygulamanın sürüm numarası şu biçimde belirtir: `major.minor.build.revision`|  
|`publicKeyToken`|İsteğe bağlı. Son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir `SHA-1` altında derleme veya uygulama imzalanan ortak anahtarı değerini karma. Katalog imzalamak için kullanılan ortak anahtar, 2048 bit veya daha fazla olmalıdır.|  
|`processorArchitecture`|İsteğe bağlı. İşlemciyi belirtir. Geçerli değerler `x86` 32-bit Windows için ve `I64` 64 bit Windows için.|  
|`language`|İsteğe bağlı. İki bölümlü dil kodları EN-US, derlemenin gibi tanımlar.|  
  
### <a name="hash"></a>hash  
 `hash` İsteğe bağlı bir alt öğedir `assemblyIdentity` öğesi. `hash` Öğesi özniteliklere sahip değildir.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] bir uygulamadaki tüm dosyaların algoritmik bir karma güvenlik denetimi, dosyaların hiçbiri dağıtımdan sonra değişmediğinden emin olmak için kullanır. Varsa `hash` öğesi dahil değildir, bu denetimi gerçekleştirilmeyecek. Bu nedenle, atlama `hash` öğesi önerilmez.  
  
### <a name="dsigtransforms"></a>dsig:TRANSFORMS  
 `dsig:Transforms` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:Transforms` Öğesi özniteliklere sahip değildir.  
  
### <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform` Öğesi gerekli alt öğesi olan `dsig:Transforms` öğesi. `dsig:Transform` Öğesinde şu öznitelikler bulunur.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] olduğu `urn:schemas-microsoft-com:HashTransforms.Identity`.|  
  
### <a name="dsigdigestmethod"></a>dsig  
 `dsig:DigestMethod` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:DigestMethod` Öğesinde şu öznitelikler bulunur.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Algorithm`|Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] olduğu `http://www.w3.org/2000/09/xmldsig#sha1`.|  
  
### <a name="dsigdigestvalue"></a>DigestValue  
 `dsig:DigestValue` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:DigestValue` Öğesi özniteliklere sahip değildir. Metin değeri, belirtilen dosya için hesaplanan karmasıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanız tarafından kullanılan tüm derlemelerin karşılık gelen olmalıdır `dependency` öğesi. Bağımlı derlemeleri genel derleme önbelleğinde platformu derlemeleri ' önceden yüklenmiş derlemeleri içermez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde gösterilmiştir `dependency` öğelerinde bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama bildirimi. Bu kod örneği için sağlanan daha büyük bir örneğin parçasıdır [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md) konu.  
  
```  
<dependency>  
  <dependentOS>  
    <osVersionInfo>  
      <os   
        majorVersion="4"   
        minorVersion="10"   
        buildNumber="0"   
        servicePackMajor="0" />  
    </osVersionInfo>  
  </dependentOS>  
</dependency>  
<dependency>  
  <dependentAssembly  
    dependencyType="preRequisite"  
    allowDelayedBinding="true">  
    <assemblyIdentity  
      name="Microsoft.Windows.CommonLanguageRuntime"  
      version="4.0.20506.0" />  
  </dependentAssembly>  
</dependency>  
  
<dependency>  
  <dependentAssembly  
    dependencyType="install"  
    allowDelayedBinding="true"  
    codebase="MyApplication.exe"  
    size="4096">  
    <assemblyIdentity  
      name="MyApplication"  
      version="1.0.0.0"  
      language="neutral"  
      processorArchitecture="x86" />  
    <hash>  
      <dsig:Transforms>  
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
      </dsig:Transforms>  
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
    </hash>  
  </dependentAssembly>  
</dependency>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)   
 [\<bağımlılık > öğesi](../deployment/dependency-element-clickonce-deployment.md)



