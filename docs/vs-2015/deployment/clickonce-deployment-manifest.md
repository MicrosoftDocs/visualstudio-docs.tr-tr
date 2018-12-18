---
title: ClickOnce dağıtım bildirimi | Microsoft Docs
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
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 96ce7d873c20b8c29e5586a54c577a5d744b0caa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306793"
---
# <a name="clickonce-deployment-manifest"></a>ClickOnce Dağıtım Bildirimi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir dağıtım bildirimi açıklayan bir XML dosyasıdır bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] geçerli tanımlaması dahil olmak üzere, dağıtım [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtmak için uygulama sürümü.  
  
 Dağıtım bildirimleri, aşağıdaki öğeleri ve öznitelikleri vardır.  
  
|Öğe|Açıklama|Öznitelikler|  
|-------------|-----------------|----------------|  
|[\<derleme > öğesi](../deployment/assembly-element-clickonce-deployment.md)|Gerekli. En üst düzey öğe.|`manifestVersion`|  
|[\<assemblyIdentity > öğesi](../deployment/assemblyidentity-element-clickonce-deployment.md)|Gerekli. Uygulama bildirimi için tanımlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<Açıklama > öğesi](../deployment/description-element-clickonce-deployment.md)|Gerekli. Bir kabuk varlığı oluşturmak için kullanılan uygulama bilgilerini tanımlar ve **Program Ekle veya Kaldır** Denetim Masası'ndaki öğesi.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<Dağıtım > öğesi](../deployment/deployment-element-clickonce-deployment.md)|İsteğe bağlı. Güncelleştirmeler ve sistem maruz kalma riskinizi dağıtımı için kullanılan öznitelikleri tanımlar.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks > öğesi](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Gerekli. Burada bu uygulamayı yükleyip çalıştırabileceği bir .NET Framework sürümlerini tanımlar.|`SupportUrl`|  
|[\<bağımlılık > öğesi](../deployment/dependency-element-clickonce-deployment.md)|Gerekli. Dağıtım için yüklemek için uygulama sürümü ve uygulama bildiriminin konumunu tanımlar.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity > öğesi](../deployment/publisheridentity-element-clickonce-deployment.md)|İmzalı bildirimler için gereklidir. Bu dağıtım bildirimi imzalayan yayımcı hakkında bilgi içerir.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<İmza > öğesi](../deployment/signature-element-clickonce-deployment.md)|İsteğe bağlı. Bu dağıtım bildirimi dijital olarak imzalamak için gereken bilgileri içerir.|Yok.|  
|[\<customErrorReporting > öğesi](../deployment/customerrorreporting-element-clickonce-deployment.md)|İsteğe bağlı. Bir hata oluştuğunda göstermek için bir URI belirtir.|URI|  
  
## <a name="remarks"></a>Açıklamalar  
 Dağıtım bildirimi dosyasını tanımlayan bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] geçerli sürümü ve diğer dağıtım ayarları dahil olmak üzere, uygulama dağıtımı. Bu uygulama ve dağıtım içinde yer alan dosyalar geçerli sürümünü açıklar uygulama bildirimini başvuruyor.  
  
 Daha fazla bilgi için [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Dosya konumu  
 Dağıtım bildirimi dosyasının doğru uygulama bildirimi geçerli uygulama sürümü için başvuruda bulunuyor. Bir uygulama dağıtımının yeni bir sürüm kullanılabilir duruma getirdiğinizde, yeni bir uygulama bildirimi başvurmak için dağıtım bildirimi güncelleştirmeniz gerekir.  
  
 Dağıtım dosyası bildiriminin kesin adlandırılmış olmalıdır ve sertifikalar için yayımcı doğrulama de içerebilir.  
  
## <a name="file-name-syntax"></a>Dosya adı sözdizimi  
 Bir dağıtım bildirimi dosyasının adı .application uzantısıyla bitmelidir.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kod örneği, bir dağıtım bildirimi gösterir.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
  manifestVersion="1.0"  
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"  
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#  
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"  
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"  
  xmlns="urn:schemas-microsoft-com:asm.v2"  
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"  
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"  
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)



