---
title: '&lt;trustInfo&gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
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
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 77915ddfe59361623aa5aee3048c6411c6c0c02c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175571"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo&gt; öğesi (ClickOnce uygulaması)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uygulamanın istemci bilgisayarda çalışması gereken en düşük güvenlik izinleri açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
  
      <trustInfo>  
   <security>  
      <applicationRequestMinimum>  
         <PermissionSet  
            ID  
            Unrestricted>  
            <IPermission  
               class  
               version  
               Unrestricted  
            />  
         </PermissionSet>  
         <defaultAssemblyRequest  
            permissionSetReference  
         />  
         <assemblyRequest  
            name  
            permissionSetReference  
         />  
      </applicationRequestMinimum>  
      <requestedPrivileges>  
         <requestedExecutionLevel  
            level  
            uiAccess  
         />  
      </requestedPrivileges>  
   </security>  
</trustInfo>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `trustInfo` Öğesi gereklidir ve içinde `asm.v2` ad alanı. Bu özniteliklere sahip ve aşağıdaki öğeleri içerir.  
  
## <a name="security"></a>güvenlik  
 Gerekli. Bu öğenin alt öğesi olan `trustInfo` öğesi. İçerdiği `applicationRequestMinimum` öğesi ve öznitelikleri yok.  
  
## <a name="applicationrequestminimum"></a>applicationRequestMinimum  
 Gerekli. Bu öğenin alt öğesi olan `security` öğesi ve içeren `PermissionSet`, `assemblyRequest`, ve `defaultAssemblyRequest`öğeleri. Bu öğenin öznitelikleri yok.  
  
## <a name="permissionset"></a>PermissionSet  
 Gerekli. Bu öğenin alt öğesi olan `applicationRequestMinimum` öğesi ve içeren `IPermission` öğesi. Bu öğe aşağıdaki özniteliklere sahiptir.  
  
-   `ID`  
  
     Gerekli. İzin kümesi tanımlar. Bu öznitelik herhangi bir değer olabilir. Kimliği başvurulduğundan `defaultAssemblyRequest` ve `assemblyRequest` öznitelikleri.  
  
-   `version`  
  
     Gerekli. İzni sürümünü tanımlar. Normalde bu değer, `1`.  
  
## <a name="ipermission"></a>IPermission  
 İsteğe bağlı. Bu öğenin alt öğesi olan `PermissionSet` öğesi. `IPermission` Öğesi tam olarak içinde izin sınıfını tanımlar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. `IPermission` Öğesi izin sınıfını özelliklere karşılık gelen ek öznitelikler şu öznitelikler bulunur, ancak. Belirli bir izni sözdizimi öğrenmek için Security.config dosyasında listelenen örneklere bakın.  
  
-   `class`  
  
     Gerekli. Tanımlayıcı adla izin sınıfını tanımlar. Örneğin, aşağıdaki kodu tanımlayan `FileDialogPermission` türü.  
  
     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
-   `version`  
  
     Gerekli. İzni sürümünü tanımlar. Genellikle bu değer, `1`.  
  
-   `Unrestricted`  
  
     Gerekli. Uygulamanın bir sınırsız kullanım hakkı bu izne ihtiyacı olup olmadığını tanımlar. Varsa `true`, izin verme koşulsuz olur. Varsa `false`, veya bu öznitelik tanımlanmamışsa, üzerinde tanımlanan izin özgü özniteliklere göre kısıtlı `IPermission` etiketi. Şu izinleri alın:  
  
    ```  
    <IPermission  
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Read="USERNAME" />  
    <IPermission  
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
      version="1"   
      Unrestricted="true" />  
    ```  
  
     Bu örnekte, bildirimi <xref:System.Security.Permissions.EnvironmentPermission> ise kullanıcı adı, yalnızca ortam değişkenini okumak için uygulamayı sınırlar bildirimi <xref:System.Security.Permissions.FileDialogPermission> tüm sınırsız uygulama kullanımı sağlar <xref:System.Windows.Forms.FileDialog> sınıfları.  
  
## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest  
 İsteğe bağlı. Tüm derlemeler için verilen izinler kümesini tanımlar. Bu öğenin alt öğesi olan `applicationRequestMinimum` öğesi ve aşağıdaki özniteliklere sahiptir.  
  
-   `permissionSetReference`  
  
     Gerekli. Varsayılan izin izin kümesi kimliği tanımlar. İzin kümesi içinde bildirildiği `PermissionSet` öğesi.  
  
## <a name="assemblyrequest"></a>assemblyRequest  
 İsteğe bağlı. Belirli bir derlemenin izinlerini tanımlar. Bu öğenin alt öğesi olan `applicationRequestMinimum` öğesi ve aşağıdaki özniteliklere sahiptir.  
  
-   `Name`  
  
     Gerekli. Derleme adını tanımlar.  
  
-   `permissionSetReference`  
  
     Gerekli. Bu derlemeyi izin kümesi kimliği tanımlar. İzin kümesi içinde bildirildiği `PermissionSet` öğesi.  
  
## <a name="requestedprivileges"></a>requestedPrivileges  
 İsteğe bağlı. Bu öğenin alt öğesi olan `security` öğesi ve içeren `requestedExecutionLevel` öğesi. Bu öğenin öznitelikleri yok.  
  
## <a name="requestedexecutionlevel"></a>requestedExecutionLevel  
 İsteğe bağlı. Yürütülecek uygulamanın istekleri güvenlik düzeyini tanımlar. Bu öğenin alt öğesi yok ve aşağıdaki özniteliklere sahiptir.  
  
-   `Level`  
  
     Gerekli. Uygulama güvenlik düzeyini isteyen gösterir. Olası değerler şunlardır:  
  
     `asInvoker`, ek izinler istenmez. Bu düzey, hiçbir ek güven istemi gerektirir.  
  
     `highestAvailable`, üst işleme kullanılabilir olan en yüksek izinler isteyen.  
  
     `requireAdministrator`, tam yönetici izinleri istiyor.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamaları yalnızca bir değeri ile yükleme `asInvoker`. Başka bir değer ile yükleme başarısız olur.  
  
-   `uiAccess`  
  
     İsteğe bağlı. Uygulama erişim korumalı kullanıcı arabirimi öğeleri için gerekli olup olmadığını gösterir. Değerleri `true` veya `false`, ve varsayılan değer false'dur. Yalnızca imzalı uygulamaları true değeri olması gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama, istemci bilgisayarda varsayılan olarak, ortak dil çalışma zamanının güven yöneticisi, kullanıcı kendisi uygulamanın yükseltilmiş düzey güven vermek istemediğini sorar vereceğinden daha fazla izin sorar. Kullanıcı hayır derse, uygulama çalışmaz; Aksi takdirde istenen izinlerle çalışacaktır.  
  
 Tüm izinleri kullanarak istenen `defaultAssemblyRequest` ve `assemblyRequest` dağıtım bildirimi geçerli bir güven lisansı varsa, kullanıcıya sormadan verilecektir.  
  
 İzin yükseltilmesi hakkında daha fazla bilgi için bkz: [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md). İlke dağıtma hakkında daha fazla bilgi için bkz. [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki üç kod örnekleri göstermek `trustInfo` varsayılan olarak adlandırılan güvenlik bölgeleri için öğeleri — Internet ve LocalIntranet FullTrust — kullanılmak üzere bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtımın uygulama bildirimi.  
  
 İlk örnekte `trustInfo` Internet güvenlik bölgesi varsayılan izinleri için öğesi.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="Internet">  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Access="Open" />  
          <IPermission  
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"  
            Allowed="DomainIsolationByUser"  
            UserQuota="10240" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Flags="Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Window="SafeTopLevelWindows"  
            Clipboard="OwnClipboard" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"   
            Level="SafePrinting" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="Internet" />  
      </applicationRequestMinimum>  
    </security>  
  </trustInfo>  
```  
  
 İkinci örnekte `trustInfo` LocalIntranet güvenlik bölgesinde varsayılan izinler için öğesi.  
  
```  
<trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet ID="LocalIntranet">  
          <IPermission  
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Read="USERNAME" />  
          <IPermission  
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Allowed="AssemblyIsolationByUser"  
            UserQuota="9223372036854775807"  
            Expiry="9223372036854775807"  
            Permanent="True" />  
          <IPermission  
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="ReflectionEmit" />  
          <IPermission  
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"   
            version="1"   
            Flags="Assertion, Execution" />  
          <IPermission   
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1"   
            Unrestricted="true" />  
          <IPermission  
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"  
            version="1"  
            Level="DefaultPrinting" />  
          <IPermission  
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
            version="1" />  
        </PermissionSet>  
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />  
      </applicationRequestMinimum>  
    </security>  
</trustInfo>  
```  
  
 Üçüncü örnek gösterilmektedir `trustInfo` FullTrust güvenlik bölgesinde varsayılan izinler için öğesi.  
  
```  
<trustInfo>  
  <security>  
    <applicationRequestMinimum>  
      <PermissionSet ID="FullTrust" Unrestricted="true" />  
      <defaultAssemblyRequest permissionSetReference="FullTrust" />  
    </applicationRequestMinimum>  
  </security>  
</trustInfo>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenilir Uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md)   
 [ClickOnce Uygulama Bildirimi](../deployment/clickonce-application-manifest.md)



