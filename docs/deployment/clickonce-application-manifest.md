---
title: ClickOnce Uygulama bildirimi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- application manifests [ClickOnce]
- ClickOnce, application manifests
ms.assetid: 29570cec-4e53-4660-a850-abc4fa150243
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5326f71ba7a075cc6ca3e321318de89624c56894
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872896"
---
# <a name="clickonce-application-manifest"></a>ClickOnce Uygulama bildirimi
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi kullanılarak dağıtılan bir uygulamayı tanımlayan bir XML dosyası olduğunu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimleri, aşağıdaki öğeleri ve öznitelikleri vardır.  


| Öğe | Açıklama | Öznitelikler |
| - | - | - |
| [\<derleme > öğesi](../deployment/assembly-element-clickonce-application.md) | Gerekli. En üst düzey öğe. | `manifestVersion` |
| [\<assemblyIdentity > öğesi](../deployment/assemblyidentity-element-clickonce-application.md) | Gerekli. Birincil derlemenin tanımlayan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. | `name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `language` |
| [\<trustInfo > öğesi](../deployment/trustinfo-element-clickonce-application.md) | Uygulama güvenlik gereksinimlerini tanımlar. | Yok. |
| [\<entryPoint > öğesi](../deployment/entrypoint-element-clickonce-application.md) | Gerekli. Uygulama kodu giriş noktasını tanımlar. | `name` |
| [\<bağımlılık > öğesi](../deployment/dependency-element-clickonce-application.md) | Gerekli. Uygulamayı çalıştırmak için gereken her bir bağımlılığın tanımlar. İsteğe bağlı olarak önceden yüklenmiş gereken bütünleştirilmiş kodları tanımlar. | Yok. |
| [\<Dosya > öğesi](../deployment/file-element-clickonce-application.md) | İsteğe bağlı. Uygulama tarafından kullanılan her nonassembly dosyayı tanımlar. Dosya ile ilgili Bileşen Nesne Modeli (COM) yalıtım veriler içerebilir. | `name`<br /><br /> `size`<br /><br /> `group`<br /><br /> `optional`<br /><br /> `writeableType` |
| [\<fileAssociation > öğesi](../deployment/fileassociation-element-clickonce-application.md) | İsteğe bağlı. Uygulamayla ilişkilendirilecek bir dosya uzantısı tanımlar. | `extension`<br /><br /> `description`<br /><br /> `progid`<br /><br /> `defaultIcon` |

## <a name="remarks"></a>Açıklamalar  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Kullanarak dağıtılmış bir uygulamada uygulama bildirim dosyasını tanımlayan [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).  

## <a name="file-location"></a>Dosya konumu  
 A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirimi dağıtımı tek bir sürümüne özeldir. Bu nedenle, bunlar ayrı olarak dağıtım bildirimlerinden depolanması gerekir. Genel kural bunları ilişkili sürümü adlı bir alt dizinde yerleştirmektir.  

 Uygulama bildirimini her zaman dağıtımdan önce oturum açmanız gerekir. Bir uygulama bildirimi el ile değiştirirseniz, kullanmalısınız *mage.exe* uygulama bildirimini yeniden imzalamanız için dağıtım bildirimini güncelleştirin ve sonra dağıtım bildirimi yeniden imzalayın. Daha fazla bilgi için [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  

## <a name="file-name-syntax"></a>Dosya adı sözdizimi  
 Adı bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama bildirim dosyası olmalıdır tam adını ve uzantısını uygulamanın tanımlandığı gibi `assemblyIdentity` uzantısı tarafından izlenen öğesini *.manifest*. Örneğin, başvuran bir uygulama bildirimi *Example.exe* uygulama aşağıdaki dosya adı sözdizimi kullanmanız.  

 `example.exe.manifest`  

## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için bir uygulama bildirimi gösterir bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama.  

```xml
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd" manifestVersion="1.0" xmlns:asmv3="urn:schemas-microsoft-com:asm.v3" xmlns:dsig="http://www.w3.org/2000/09/xmldsig#" xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2" xmlns="urn:schemas-microsoft-com:asm.v2" xmlns:asmv1="urn:schemas-microsoft-com:asm.v1" xmlns:asmv2="urn:schemas-microsoft-com:asm.v2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">  
  <asmv1:assemblyIdentity name="My Application Deployment.exe" version="1.0.0.0" publicKeyToken="43cb1e8e7a352766" language="neutral" processorArchitecture="x86" type="win32" />  
  <application />  
  <entryPoint>  
    <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
    <commandLine file="MyApplication.exe" parameters="" />  
  </entryPoint>  
  <trustInfo>  
    <security>  
      <applicationRequestMinimum>  
        <PermissionSet Unrestricted="true" ID="Custom" SameSite="site" />  
        <defaultAssemblyRequest permissionSetReference="Custom" />  
      </applicationRequestMinimum>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <!--  
          UAC Manifest Options  
          If you want to change the Windows User Account Control level replace the   
          requestedExecutionLevel node with one of the following.  

        <requestedExecutionLevel  level="asInvoker" uiAccess="false" />  
        <requestedExecutionLevel  level="requireAdministrator" uiAccess="false" />  
        <requestedExecutionLevel  level="highestAvailable" uiAccess="false" />  

         If you want to utilize File and Registry Virtualization for backward   
         compatibility then delete the requestedExecutionLevel node.  
    -->  
        <requestedExecutionLevel level="asInvoker" uiAccess="false" />  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
  <dependency>  
    <dependentOS>  
      <osVersionInfo>  
        <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
      </osVersionInfo>  
    </dependentOS>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">  
      <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.20506.0" />  
    </dependentAssembly>  
  </dependency>  
  <dependency>  
    <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="4096">  
      <assemblyIdentity name="MyApplication" version="1.0.0.0" language="neutral" processorArchitecture="x86" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAINCONTROLLER\UserMe" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
...  
</Signature></r:issuer></r:license></msrel:RelData></KeyInfo></Signature></asmv1:assembly>  
```  

## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)