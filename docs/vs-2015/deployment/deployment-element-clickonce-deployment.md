---
title: '&lt;Dağıtım&gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
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
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d6d4472502315a12529c6c7ea59007c5502cfd5d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49231551"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;Dağıtım&gt; öğesi (ClickOnce dağıtımı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Güncelleştirmeler ve sistem maruz kalma riskinizi dağıtımı için kullanılan öznitelikleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `deployment` Öğesi gereklidir ve içinde `urn:schemas-microsoft-com:asm.v1` ad alanı. Öğe, aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`install`|Gerekli. Bu uygulamayı Windows üzerinde bir varlığı tanımlar olup olmadığını belirtir **Başlat** menü ve Denetim Masası'nda **Program Ekle veya Kaldır** uygulama. Geçerli değerler `true` ve `false`. Varsa `false`, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ağdan bu uygulamanın en son sürümü her zaman çalışır ve algılamayacak `subscription` öğesi.|  
|`minimumRequiredVersion`|İsteğe bağlı. İstemci üzerinde çalışabilen bu uygulamanın en düşük sürümü belirtir. Sürüm numarası uygulamanın dağıtım bildiriminde sağlanan sürüm numarasından daha küçükse, uygulama çalışmaz. Sürüm numaraları biçiminde belirtilmelidir `N.N.N.N`burada `N` işaretsiz bir tamsayıdır. Varsa `install` özniteliği `false`, `minimumRequiredVersion` ayarlanmamalıdır.|  
|`mapFileExtensions`|İsteğe bağlı. Varsayılan olarak `false`. Varsa `true`, Dağıtımdaki tüm dosyaları .deploy uzantısını olmalıdır. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bu Web sunucusundan indirir hemen sonra bu uzantı bu dosyalardan çıkarır. Uygulamanızı kullanarak yayımlarsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bu uzantıyı tüm dosyalar için otomatik olarak ekler. İçindeki tüm dosyalar bu parametreyi sağlar bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] "güvenli" uzantılar .exe gibi sonlanan dosyaların aktarımını engelleyen bir Web sunucusundan yüklenecek dağıtım.|  
|`disallowUrlActivation`|İsteğe bağlı. Varsayılan olarak `false`. Varsa `true`, yüklü bir uygulama URL'si tıklayarak ya da Internet Explorer'a URL girilerek başlatılmasını önler. Varsa `install` öznitelik yoksa, bu öznitelik yoksayılır.|  
|`trustURLParameters`|İsteğe bağlı. Varsayılan olarak `false`. Varsa `true`URL'nin uygulamanın içine geçirilen sorgu dizesi parametreleri içermesine izin verir, çok benzer bir komut satırı bağımsız değişkenlerini komut satırı uygulamaya geçirilir. Daha fazla bilgi için [nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Varsa `disallowUrlActivation` özniteliği `true`, `trustUrlParameters` bildirimden hariç, veya açıkça `false`.|  
  
 `deployment` Öğesi şu alt öğelerden de içerir.  
  
## <a name="subscription"></a>Abonelik  
 İsteğe bağlı. İçeren `update` öğesi. `subscription` Öğesi özniteliklere sahip değildir. Varsa `subscription` öğesi mevcut değil, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama hiçbir zaman güncelleştirmeleri için tarama. Varsa `install` özniteliği `deployment` öğesi `false`, `subscription` öğesi göz ardı edilir, çünkü bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ağdan başlatılan her zaman uygulamanın en son sürümünü kullanır.  
  
## <a name="update"></a>Güncelleştirme  
 Gerekli. Bu öğenin alt öğesi olan `subscription` öğesi ve ya da içeren `beforeApplicationStartup` veya `expiration` öğesi. `beforeApplicationStartup` ve `expiration` hem de aynı dağıtım bildiriminde belirtilemez.  
  
 `update` Öğesi özniteliklere sahip değildir.  
  
## <a name="beforeapplicationstartup"></a>beforeApplicationStartup  
 İsteğe bağlı. Bu öğenin alt öğesi olan `update` öğesi ve öznitelikleri yok. Zaman `beforeApplicationStartup` öğe varsa, uygulama zaman engellenen [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] güncelleştirmeleri, istemcinin çevrimiçi olup olmadığını denetler. Bu öğe yoksa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ilk için belirtilen değerlere göre güncelleştirmeleri için tarama yapmadan `expiration` öğesi. `beforeApplicationStartup` ve `expiration` hem de aynı dağıtım bildiriminde belirtilemez.  
  
## <a name="expiration"></a>süre sonu  
 İsteğe bağlı. Bu öğenin alt öğesi olan `update` öğesi ve alt öğesi yok. `beforeApplicationStartup` ve `expiration` hem de aynı dağıtım bildiriminde belirtilemez. Var olan sürüm çalışırken güncelleştirme denetimi oluşur ve güncelleştirilmiş bir sürümü algılandı, yeni sürüm önbelleğe alır. Yeni sürüm daha sonra sonraki başlatmada yükledikten [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.  
  
 `expiration` Öğesi aşağıdaki öznitelikler destekler.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maximumAge`|Gerekli. Güncelleştirme denetimi uygulamanın gerçekleştirdiği önce geçerli güncelleştirme kaç yaşında olması gerektiğini tanımlar. Zaman birimi tarafından belirlenen `unit` özniteliği.|  
|`unit`|Gerekli. İçin zaman birimi tanımlar `maximumAge`. Geçerli birimleri `hours`, `days`, ve `weeks`.|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 .NET Framework 2.0 için dağıtım bildirimi içeriyorsa, bu öğe gereklidir bir `subscription` bölümü. .NET Framework 3.5 ve daha sonra bu öğe isteğe bağlıdır ve sunucu ve dosya yolu, dağıtım bildiriminde bulunan varsayılan olur.  
  
 Bu öğenin alt öğesi olan `deployment` öğesi ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`codebase`|Gerekli. Tekdüzen Kaynak Tanımlayıcısı (URI) olarak güncelleştirmek için kullanılan dağıtım bildiriminin konumunu tanımlayan [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama. Bu öğe, CD tabanlı yüklemeler için güncelleştirme konumları iletmek için de sağlar. Geçerli bir URI olmalıdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yapılandırabileceğiniz, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] başlangıçta güncelleştirmeleri taramak için uygulama başlangıcından sonra güncelleştirmeleri için tarama ya da asla güncelleştirmeleri denetleme. Başlangıçta güncelleştirmeleri taramak için emin olun `beforeApplicationStartup` öğesi var. altında `update` öğesi. Başlangıcından sonra güncelleştirmeleri taramak için emin olun `expiration` öğesi var. altında `update` öğesi ve güncelleştirme aralıkları sağlanır.  
  
 Güncelleştirmeleri denetlemeyi devre dışı bırakmak için kaldırmanız `subscription` öğesi. Hiçbir zaman güncelleştirmeleri taramak için dağıtım bildirimi içinde belirttiğinizde, yine de el ile güncelleştirmeleri kullanarak denetleyebilirsiniz <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> yöntemi.  
  
 DeploymentProvider'ın güncelleştirmeleri nasıl olduğu ile ilgili daha fazla bilgi için bkz: [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneğinde gösterilmiştir bir `deployment` öğesinde bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım bildirimi. Örnekte bir `deploymentProvider` tercih edilen güncelleştirme konumunu göstermek için öğesi.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Dağıtım Bildirimi](../deployment/clickonce-deployment-manifest.md)



