---
title: "Nasıl yapılır: bir ClickOnce dağıtımı'nda bağımsız Önkoşullar için destek URL'sini belirtme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e93e8ab84a751c447488e1b4dc6e3e6779b86b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913288"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Nasıl yapılır: bir ClickOnce dağıtımı ' bağımsız Önkoşullar için destek URL'sini belirtme
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım için istemci bilgisayardaki kullanılabilir olması gereken önkoşulları test [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] çalıştırmak için uygulama. Gerekli en düşük sürümü bu bağımlılıkları içerecek [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], işletim sistemi ve genel derleme önbelleğinde (GAC) yüklenmiş herhangi bir derleme sürümü. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], bu önkoşulları hiçbirini kendisini; ancak, yükleyemezsiniz bir önkoşul bulunamadı, yalnızca yükleme durdurur ve yükleme neden başarısız olduğunu açıklayan bir iletişim kutusu görüntüler.  
  
 Önkoşulları yüklemek için iki yöntem vardır. Bir önyükleyici uygulaması kullanarak bunları yükleyebilirsiniz. Alternatif olarak, önkoşul bulunmazsa, kullanıcılara iletişim kutusunda görüntülenir bağımsız Önkoşullar için destek URL'sini belirtebilirsiniz. Bu URL tarafından başvurulan sayfa için gereken önkoşulları yükleme yönergeleri için bağlantıları içerebilir. Bir uygulama için ayrı bir önkoşulu destek URL'si belirtmezse [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tanımlıysa, bir bütün olarak uygulamadan dağıtım bildiriminde belirtilen destek URL'sini görüntüler.  
  
 Sırada [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], *Mage.exe*, ve *MageUI.exe* tüm oluşturmak için kullanılabilir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımlar, bu araçlar hiçbiri doğrudan destek kişi için destek URL'sini belirtme Önkoşullar. Bu belge, dağıtımınızın değiştirilecek açıklar uygulama bildirimi ve bunlar için dağıtım bildirimi URL'leri destekler.  
  
### <a name="specify-a-support-url-for-an-individual-prerequisite"></a>Tek bir önkoşulu için destek URL'sini belirtme  
  
1. Uygulama bildirimini açın ( *.manifest* dosyası) için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir metin düzenleyicisinde uygulama.  
  
2. Bir işletim sistemi önkoşulları ekleme `supportUrl` özniteliğini `dependentOS` öğesi:  
  
   ```xml  
    <dependency>  
       <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
         <osVersionInfo>  
           <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
         </osVersionInfo>  
       </dependentOS>  
     </dependency>  
   ```  
  
3. Belirli bir ortak dil çalışma zamanı sürümü için bir önkoşul ekleme `supportUrl` özniteliğini `dependentAssembly` ortak dil çalışma zamanı bağımlılık belirten girişi:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
         <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
4. Genel derleme önbelleğinde önceden bir derleme için önkoşulları ayarlamak `supportUrl` için `dependentAssembly` gerekli derleme belirten öğe:  
  
   ```xml  
     <dependency>  
       <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
         <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
       </dependentAssembly>  
     </dependency>  
   ```  
  
5. İsteğe bağlı. Açık .NET Framework 4'ü hedefleyen uygulamalar için dağıtım bildirimi ( *.application* dosyası) için [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bir metin düzenleyicisinde uygulama.  
  
6. Bir .NET Framework 4 önkoşulları ekleme `supportUrl` özniteliğini `compatibleFrameworks` öğesi:  
  
   ```xml  
   <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
     <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
     <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
   </compatibleFrameworks>  
   ```  
  
7. El ile uygulama bildirimini değiştirmiş sonra gerekir, dijital sertifikayı kullanarak uygulama bildirimini yeniden imzalamanız sonra güncelleştirme ve de dağıtım bildirimini yeniden imzalamanız. Kullanım *Mage.exe* veya *MageUI.exe* kullanarak bu dosyaları yeniden olarak bağlı olarak, bu görevi gerçekleştirmek için SDK araçlarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] el ile yaptığınız değişiklikleri siler. Bildirimleri yeniden imzalamak için Mage.exe kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: yeniden imzalama uygulama ve dağıtım bildirimlerini](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>.NET Framework güvenliği  
 Uygulama kısmi güvende çalıştırmak için işaretlendiyse, destek URL'sini iletişim kutusunda görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > öğesi](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce ve Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Uygulama dağıtımının önkoşulları](../deployment/application-deployment-prerequisites.md)