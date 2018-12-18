---
title: '&lt;Dosya&gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b516a8e63d29f91b3404e8e62d910ca18ca69c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933540"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;Dosya&gt; öğesi (ClickOnce uygulaması)
İndirilen ve uygulama tarafından kullanılan tüm nonassembly dosyaları tanımlar.  

## <a name="syntax"></a>Sözdizimi  

```xml  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `file` Öğesi, isteğe bağlıdır. Öğe, aşağıdaki özniteliklere sahiptir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Gerekli. Dosya adını tanımlar.|  
|`size`|Gerekli. Dosyanın bayt cinsinden boyutunu belirtir.|  
|`group`|İsteğe bağlı `optional` özniteliği belirtilmemişse veya kümesine `false`; kullanılmıyorsa gereklidir `optional` olduğu `true`. Bu dosyanın ait olduğu grubu adı. Adı herhangi bir Unicode dize değeri geliştirici tarafından seçmiş olabilir ve dosya ile isteğe bağlı yükleme için kullanılan <xref:System.Deployment.Application.ApplicationDeployment> sınıfı.|  
|`optional`|İsteğe bağlı. Bu dosya gerekip gerekmediğini uygulamanın ilk çalıştırıldığında veya isteğe bağlı olarak uygulama isteğe bağlı olarak edene kadar dosya yalnızca sunucuda olup bulunmalıdır belirtir. Varsa `false` ya da tanımlanmamışsa, uygulamayı ilk kez çalıştırdığınızda veya dosyası indirilir. Varsa `true`, `group` uygulama bildirimi geçerli olması belirtilmelidir. `optional` TRUE olamaz, `writeableType` değeriyle belirtilen `applicationData`.|  
|`writeableType`|İsteğe bağlı. Bu dosyanın bir veri dosyası olduğunu belirtir. Şu anda geçerli olan `applicationData`.|  

## <a name="typelib"></a>tür kitaplığı  
 `typelib` Dosya öğesi için isteğe bağlı bir alt öğesidir. COM bileşenine ait tür kitaplığını açıklar. Öğe, aşağıdaki özniteliklere sahiptir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`tlbid`|Gerekli. Tür Kitaplığı'na atanan GUID.|  
|`version`|Gerekli. Tür kitaplığı sürüm sayısı.|  
|`helpdir`|Gerekli. Bileşen için Yardım dosyalarını içeren dizin. Sıfır uzunluğunda olabilir.|  
|`resourceid`|İsteğe bağlı. Yerel ayar tanıtıcısı (LCID) onaltılık dize gösterimi. Bu, bir ile dört onaltılık basamak 0 x öneki ve önünde sıfır olmadan olur. LCID nötr alt dili tanımlayıcı sahip olabilir.|  
|`flags`|İsteğe bağlı. Bu tür kitaplığı için tür kitaplığı bayrakları dize gösterimi. Özellikle, "RESTRICTED", "CONTROL", "Gizli" ve "HASDISKIMAGE" biri olmalıdır.|  

## <a name="comclass"></a>comClass  
 `comClass` İsteğe bağlı bir alt öğedir `file` öğesi, ancak gereklidir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düşünüyor kayıt gerektirmeyen com kullanarak dağıtmak için bir COM bileşeni, uygulama içerir Öğe, aşağıdaki özniteliklere sahiptir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`clsid`|Gerekli. Sınıf kimliği bir GUID olarak ifade edilen COM bileşeni.|  
|`description`|İsteğe bağlı. Sınıf adı.|  
|`threadingModel`|İsteğe bağlı. İşlemde COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılır. Bileşen istemci ana iş parçacığı üzerinde oluşturulur ve diğer iş parçacıklarını çağrılarından bu iş parçacığı için hazırlanırlar. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `Apartment`, `Free`, `Both`, ve `Neutral`.|  
|`tlbid`|İsteğe bağlı. Bu COM bileşeni için tür kitaplığı için GUID.|  
|`progid`|İsteğe bağlı. Sürüme bağımlı programlı tanımlayıcısı COM bileşeni ile ilişkili. Biçimi bir `ProgID` olduğu `<vendor>.<component>.<version>`.|  
|`miscStatus`|İsteğe bağlı. Derlemedeki çoğaltır tarafından sağlanan bilgileri `MiscStatus` kayıt defteri anahtarı. Değilse değerleri `miscStatusIcon`, `miscStatusContent`, `miscStatusDocprint`, veya `miscStatusThumbnail` öznitelikler bulunamadı, listelenen karşılık gelen varsayılan değerin `miscStatus` eksik öznitelikleri için kullanılır. Değer, öznitelik değerleri aşağıdaki tabloda, virgülle ayrılmış listesini olabilir. COM sınıfı gerektiren bir OCX sınıfı ise bu özniteliği kullanabilirsiniz `MiscStatus` kayıt defteri anahtarı değerleri.|  
|`miscStatusIcon`|İsteğe bağlı. Derlemedeki DVASPECT_ICON tarafından sağlanan bilgileri çoğaltır. Bu, bir nesnenin bir simge sağlayabilir. Değer, öznitelik değerleri aşağıdaki tabloda, virgülle ayrılmış listesini olabilir. COM sınıfı gerektiren bir OCX sınıfı ise bu özniteliği kullanabilirsiniz `Miscstatus` kayıt defteri anahtarı değerleri.|  
|`miscStatusContent`|İsteğe bağlı. Derlemedeki DVASPECT_ICON tarafından sağlanan bilgileri çoğaltır. Bunu bir ekran veya yazıcı için görüntülenebilir bir bileşik belge sağlayabilirsiniz. Değer, öznitelik değerleri aşağıdaki tabloda, virgülle ayrılmış listesini olabilir. COM sınıfı gerektiren bir OCX sınıfı ise bu özniteliği kullanabilirsiniz `MiscStatus` kayıt defteri anahtarı değerleri.|  
|`miscStatusDocPrint`|İsteğe bağlı. Derlemedeki DVASPECT_ICON tarafından sağlanan bilgileri çoğaltır. Bir yazıcıya yokmuş gibi bir nesne temsili görüntülenebilir ekranda sağlayabilir. Değer, öznitelik değerleri aşağıdaki tabloda, virgülle ayrılmış listesini olabilir. COM sınıfı gerektiren bir OCX sınıfı ise bu özniteliği kullanabilirsiniz `MiscStatus` kayıt defteri anahtarı değerleri.|  
|`miscStatusThumbnail`|İsteğe bağlı. Bir derlemede desteklemek istiyorsanız tarafından sağlanan bilgileri çoğaltır. Bu tarama aracı içinde görüntülenebilen bir nesnenin bir küçük resim sağlayabilir. Değer, öznitelik değerleri aşağıdaki tabloda, virgülle ayrılmış listesini olabilir. COM sınıfı gerektiren bir OCX sınıfı ise bu özniteliği kullanabilirsiniz `MiscStatus` kayıt defteri anahtarı değerleri.|  

## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 `comInterfaceExternalProxyStub` İsteğe bağlı bir alt öğedir `file` öğesinde, gerekli olabilir ancak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düşünüyor kayıt gerektirmeyen com kullanarak dağıtmak için bir COM bileşeni içeren uygulama Öğe, aşağıdaki öznitelikleri içerir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`iid`|Gerekli. Bu proxy tarafından hizmet Kimliğini (IID) arabirim. IID çevreleyen küme ayraçları olmalıdır.|  
|`baseInterface`|İsteğe bağlı. Arabirim başvuruyor arabirimi Laboratuvardaki `iid` türetilir.|  
|`numMethods`|İsteğe bağlı. Arabirimi tarafından uygulanan yöntemlerin sayısı.|  
|`name`|İsteğe bağlı. Bu arabirim adını kodda görünür.|  
|`tlbid`|İsteğe bağlı. Tarafından belirtilen arabirim açıklamasını içeren bir tür kitaplığı `iid` özniteliği.|  
|`proxyStubClass32`|İsteğe bağlı. CLSID 32-bit proxy'sinde DLL'ler için bir IID eşler.|  

## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 `comInterfaceProxyStub` İsteğe bağlı bir alt öğedir `file` öğesinde, gerekli olabilir ancak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düşünüyor kayıt gerektirmeyen com kullanarak dağıtmak için bir COM bileşeni içeren uygulama Öğe, aşağıdaki öznitelikleri içerir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`iid`|Gerekli. Bu proxy tarafından hizmet Kimliğini (IID) arabirim. IID çevreleyen küme ayraçları olmalıdır.|  
|`baseInterface`|İsteğe bağlı. Arabirim başvuruyor arabirimi Laboratuvardaki `iid` türetilir.|  
|`numMethods`|İsteğe bağlı. Arabirimi tarafından uygulanan yöntemlerin sayısı.|  
|`Name`|İsteğe bağlı. Bu arabirim adını kodda görünür.|  
|`Tlbid`|İsteğe bağlı. Tarafından belirtilen arabirim açıklamasını içeren bir tür kitaplığı `iid` özniteliği.|  
|`proxyStubClass32`|İsteğe bağlı. CLSID 32-bit proxy'sinde DLL'ler için bir IID eşler.|  
|`threadingModel`|İsteğe bağlı. İsteğe bağlı. İşlemde COM sınıfları tarafından kullanılan iş parçacığı modeli. Bu özellik null ise, iş parçacığı modeli kullanılır. Bileşen istemci ana iş parçacığı üzerinde oluşturulur ve diğer iş parçacıklarını çağrılarından bu iş parçacığı için hazırlanırlar. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `Apartment`, `Free`, `Both`, ve `Neutral`.|  

## <a name="windowclass"></a>windowClass  
 `windowClass` İsteğe bağlı bir alt öğedir `file` öğesinde, gerekli olabilir ancak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] düşünüyor kayıt gerektirmeyen com kullanarak dağıtmak için bir COM bileşeni içeren uygulama Öğe uygulanmış bir sürüme sahip bir COM bileşeni tarafından tanımlanan bir pencere sınıfını gösterir. Öğe, aşağıdaki öznitelikleri içerir.  

|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`versioned`|İsteğe bağlı. Pencere sınıfını içeren derleme sürümünü içeren iç pencere sınıf kaydında kullanılan adı olup olmadığını denetler. Bu özniteliğin değeri olabilir `yes` veya `no`. Varsayılan, `yes` değeridir. Değer `no` yalnızca aynı pencere sınıfı bir yan yana bileşeni ve bir eşdeğer-yana olmayan bileşeni tarafından tanımlanır ve aynı pencere sınıfı olarak değerlendirilecek istiyorsanız kullanılmalıdır. Pencere sınıfı kaydı hakkında genel kurallar uygulamak not — yalnızca kendisine uygulanan bir sürüm olmadığı için pencere sınıfını kaydeder ilk bileşen, kaydetmek mümkün olacaktır.|  

## <a name="hash"></a>hash  
 `hash` İsteğe bağlı bir alt öğedir `file` öğesi. `hash` Öğesi özniteliklere sahip değildir.  

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir uygulamadaki tüm dosyaların algoritmik bir karma güvenlik denetimi, dosyaların hiçbiri dağıtımdan sonra değişmediğinden emin olmak için kullanır. Varsa `hash` öğesi dahil değildir, bu denetimi gerçekleştirilmeyecek. Bu nedenle, atlama `hash` öğesi önerilmez.  

 Bir bildirim değil karma bir dosya içeriyorsa, bu bildirimi dijital olarak olamaz kullanıcılar bütün bir dosyanın içeriğini doğrulayamadığı için imzalanmış.  

## <a name="dsigtransforms"></a>dsig:TRANSFORMS  
 `dsig:Transforms` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:Transforms` Öğesi özniteliklere sahip değildir.  

## <a name="dsigtransform"></a>dsig:Transform  
 `dsig:Transform` Öğesi gerekli alt öğesi olan `dsig:Transforms` öğesi. `dsig:Transform` Öğesinde şu öznitelikler bulunur.  


| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğu `urn:schemas-microsoft-com:HashTransforms.Identity`. |

## <a name="dsigdigestmethod"></a>dsig  
 `dsig:DigestMethod` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:DigestMethod` Öğesinde şu öznitelikler bulunur.  


| Öznitelik | Açıklama |
|-------------| - |
| `Algorithm` | Bu dosya için Özet hesaplamak için kullanılan algoritma. Şu anda kullanılan tek değer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] olduğu `http://www.w3.org/2000/09/xmldsig#sha1`. |

## <a name="dsigdigestvalue"></a>DigestValue  
 `dsig:DigestValue` Öğesi gerekli alt öğesi olan `hash` öğesi. `dsig:DigestValue` Öğesi özniteliklere sahip değildir. Metin değeri, belirtilen dosya için hesaplanan karmasıdır.  

## <a name="remarks"></a>Açıklamalar  
 Bu öğe, uygulamayı oluşturan tüm nonassembly dosyaları tanımlar ve özellikle karma değerlerini dosya doğrulama. Bu öğe, dosya ile ilgili Bileşen Nesne Modeli (COM) yalıtım verileri de içerebilir. Bir dosya değiştiğinde değişimi yansıtmak için uygulama bildirim dosyasına da güncelleştirilmesi gerekir.  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde gösterilmiştir `file` bildiriminde bir uygulamada kullanılarak dağıtılan bir uygulama için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

```xml  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)