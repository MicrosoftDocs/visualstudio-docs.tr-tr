---
title: 'İzlenecek yol: Bir ClickOnce uygulamasını el ile dağıtma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e9f25c0e0b60a3b0f52df534db8f3593a26a435a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902892"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>İzlenecek yol: ClickOnce uygulamasını el ile dağıtma
Dağıtmak için Visual Studio kullanamıyorsanız, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama veya gelişmiş dağıtım özelliklerini kullanması gereken güvenilen uygulama dağıtımı gibi kullanmalısınız *Mage.exe* , oluşturmakiçinkomutsatırıaracı[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bildirimleri. Bu izlenecek yolda nasıl oluşturulacağını açıklar bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] komut satırı sürümünü kullanarak dağıtımı (*Mage.exe*) veya grafik sürümünü (*MageUI.exe*) bildirim oluşturma ve Düzenleme aracı.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuzda, bazı önkoşulları ve dağıtım oluşturulmadan önce seçmek için gereken seçenekler vardır.  
  
- Yükleme *Mage.exe* ve *MageUI.exe*.  
  
   *Mage.exe* ve *MageUI.exe* parçası olan [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Ya da olmalıdır [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] yüklü sürümünü veya [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Visual Studio'ya dahil edildi. Daha fazla bilgi için [Windows SDK'sı](http://go.microsoft.com/fwlink/?LinkId=158044) MSDN'de.  
  
- Dağıtmak üzere bir uygulama sağlar.  
  
   Bu izlenecek yol, dağıtım için hazır olan bir Windows uygulaması sahibi olduğunuzu varsayar. Bu uygulama AppToDeploy olarak anılacaktır.  
  
- Dağıtımın nasıl dağıtılacağı belirleyin.  
  
   Dağıtım seçenekleri şunları içerir: Web, dosya paylaşımı veya CD. Daha fazla bilgi için [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md).  
  
- Uygulama yükseltilmiş bir güven düzeyi isteyip istemediğini belirler.  
  
   Uygulamanız gerekiyorsa tam güven — Örneğin, tam erişim kullanıcının sistem — kullanabilirsiniz `-TrustLevel` seçeneği *Mage.exe* bunu ayarlamak için. Uygulamanız için özel bir izin tanımlamak istiyorsanız, Internet veya intranet izni bölümü başka bir bildirimden kopyalayabilir, gereksinimlerinize uyacak şekilde değiştirin ve bir metin düzenleyicisi kullanarak uygulama bildirimine ekleyin veya  *MageUI.exe*. Daha fazla bilgi için [güvenilir uygulama dağıtımına genel bakış](../deployment/trusted-application-deployment-overview.md).  
  
- Authenticode sertifikası alın.  
  
   Dağıtımınızı Authenticode sertifikası ile imzalaması gerekir. Visual Studio kullanarak bir test sertifika oluşturabileceğiniz gibi *MageUI.exe*, veya *MakeCert.exe* ve *Pvk2Pfx.exe* araçları veya elde edebilirsiniz bir sertifika bir sertifika Yetkilisi (CA). Güvenilir uygulama dağıtımını kullanmayı tercih ederseniz, tek seferlik bir sertifikayı tüm istemci bilgisayarlara yüklenmesini de gerçekleştirmeniz gerekir. Daha fazla bilgi için [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
  > [!NOTE]
  >  Ayrıca, dağıtımınızı bir sertifika yetkilisinden elde edebilirsiniz bir CNG sertifikasıyla oturum açabilirsiniz.  
  
- Uygulama UAC bilgilerini içeren bir bildirimi yok emin olun.  
  
   Uygulamanızı bir bildirim, kullanıcı hesabı denetimi (UAC) bilgilerle gibi içerip içermediğini belirlemek gereken bir `<dependentAssembly>` öğesi. Bir uygulama bildirimi incelemek için Windows Sysinternals'dan kullanabilirsiniz [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) yardımcı programı.  
  
   Uygulamanız bir bildirim UAC ayrıntıları içeriyorsa UAC bilgisi olmadan yeniden oluşturmalısınız. Bir C# projesi için Visual Studio'da proje özelliklerini açın ve uygulama sekmesini seçin. İçinde **bildirim** aşağı açılan listesinden **bildirim olmadan uygulama oluşturma**. Visual Studio'da Visual Basic projesi için proje özelliklerini açın, uygulama sekmesini seçin ve tıklayın **UAC ayarları görüntüle**. Açık bildirim dosyasında tüm öğeleri tek kaldırın `<asmv1:assembly>` öğesi.  
  
- Uygulamanın istemci bilgisayarda önkoşullar gerekli olup olmadığını belirler.  
  
   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Visual Studio'dan dağıtılan uygulamaları, bir önkoşul önyükleyicisi içerebilir (*setup.exe*) dağıtımınız ile. Bu izlenecek yol için gerekli iki bildirim oluşturur bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım. Bir önkoşul önyükleyici kullanarak oluşturabileceğiniz [GenerateBootstrapper görevi](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Komut satırı aracı Mage.exe ile bir uygulamayı dağıtmak için  
  
1. Depolayacağınız bir dizin oluşturun, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım dosyaları.  
  
2. Yeni oluşturduğunuz dağıtım dizininde bir sürüm dizin oluşturun. Bu uygulamayı ilk kez ise, sürüm alt ad **1.0.0.0**.  
  
   > [!NOTE]
   >  Sürüm dağıtımınızın, uygulamanızın sürümünden farklı olabilir.  
  
3. Tüm uygulama dosyalarını, yürütülebilir dosyalar, derlemeleri, kaynakları ve veri dosyaları dahil olmak üzere sürüm alt dizinine kopyalayın. Gerekirse, ek dosyaları içeren ek alt dizinleri oluşturabilirsiniz.  
  
4. Açık [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] veya Visual Studio komut istemi ve sürüm alt dizinine geçin.  
  
5. Bir çağrı ile bir uygulama bildirimi oluşturun *Mage.exe*. Aşağıdaki deyim x86 Intel işlemci üzerinde çalıştırmak için derlenen kod için bir uygulama bildirimi oluşturur.  
  
   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
   ```  
  
   > [!NOTE]
   >  Nokta (.) eklediğinizden emin olun `-FromDirectory` seçeneğinden geçerli dizinini gösterir. Nokta eklemezseniz uygulama dosyalarınızı yolunu belirtmeniz gerekir.  
  
6. Uygulama bildirimini Authenticode sertifikanızla imzalayın. Değiştirin *mycert.pfx* ile sertifika dosyanızın yolu. Değiştirin *parola* , sertifika dosyası parolası ile.  
  
   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
   ```  
  
   Visual Studio ve Windows SDK'sı ile dağıtılır, .NET Framework 4.6.2 SDK ile başlayarak *mage.exe* bildirimleri CNG ile yanı sıra Authenticode sertifikalar ile imzalar. Authenticode sertifikalarla gibi aynı komut satırı parametrelerini kullanın.
    
7. Dağıtım dizini kök dizinine değiştirin.  
  
8. Bir çağrıyla dağıtım bildirimi oluşturmak *Mage.exe*. Varsayılan olarak, *Mage.exe* işaretler, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım yüklü bir uygulama, BT'nin hem çevrimiçi çalıştırabilmeniz için ve çevrimdışı olarak. Kullanıcının çevrimiçi olduğunda uygulama kullanılabilir yapmak için `-Install` değerini seçeneğiyle `false`. Varsayılan değer kullandığınız ve kullanıcıların bir Web sitesi veya dosya paylaşımından uygulamanızı yükleme, emin olun değerini `-ProviderUrl` seçeneği noktaları uygulamanın konumuna bildirimi Web sunucusu veya paylaşımı.  
  
   ```cmd  
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
   ```  
  
9. Dağıtım bildirimini Authenticode veya CNG sertifikanızla imzalayın.  
  
    ```cmd  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Dağıtım hedefi veya medya dosyalarının tümünü dağıtım dizininde kopyalayın. Bu, bir Web sitesi veya FTP sitesi, bir dosya paylaşımı veya CD-ROM klasör ya da olabilir.  
  
11. Kullanıcılarınızın, URL, UNC veya uygulamanızı yüklemek için gereken fiziksel ortam sağlar. Bir URL veya UNC sağlarsanız, dağıtım bildirimine tam yolu, kullanıcılarınızın vermeniz gerekir. Örneğin, AppToDeploy dağıtılır http://webserver01/ AppToDeploy dizininde tam bir URL yolu olacaktır http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>MageUI.exe grafik aracını kullanarak bir uygulamayı dağıtmak için  
  
1. Depolayacağınız bir dizin oluşturun, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım dosyaları.  
  
2. Yeni oluşturduğunuz dağıtım dizininde bir sürüm dizin oluşturun. Bu uygulamayı ilk kez ise, sürüm alt ad **1.0.0.0**.  
  
   > [!NOTE]
   >  Dağıtımınızın sürümünden büyük olasılıkla uygulamanızı sürümünden farklıdır.  
  
3. Tüm uygulama dosyalarını, yürütülebilir dosyalar, derlemeleri, kaynakları ve veri dosyaları dahil olmak üzere sürüm alt dizinine kopyalayın. Gerekirse, ek dosyaları içeren ek alt dizinleri oluşturabilirsiniz.  
  
4. Başlangıç *MageUI.exe* grafik aracıdır.  
  
   ```cmd  
   MageUI.exe  
   ```  
  
5. Seçerek yeni bir uygulama bildirimi oluşturmak **dosya**, **yeni**, **uygulama bildirimi** menüsünde.  
  
6. Varsayılan **adı** sekmesinde, bu dağıtımın adını ve sürüm numarasını yazın. Ayrıca belirtin **İşlemci** , uygulamanız için x86 gibi oluşturulmuştur.  
  
7. Seçin **dosyaları** sekmesine ve üç nokta simgesine tıklayın (**...** ) düğmesinin yanındaki **uygulama dizini** metin kutusu. A **klasöre Gözat** iletişim kutusu görüntülenir.  
  
8. Uygulama dosyalarınızı içeren sürüm alt seçin ve ardından **Tamam**.  
  
9. Internet Information Services (IIS) dağıtacaksınız, seçin **doldurma eklediğinizde .deploy uzantısını yok herhangi bir dosyaya** onay kutusu.  
  
10. Tıklayın **Doldur** düğmesini tüm uygulama dosyalarını dosya listesine ekleyin. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, bu dağıtım için bir başlangıç uygulaması olarak ana yürütülebilir dosyayı seçerek işaretlemek **giriş noktası** gelen **dosya türü** aşağı açılan listesi. (Uygulamanızın tek bir yürütülebilir dosya içeriyorsa *MageUI.exe* sizin için işaretler.)  
  
11. Seçin **gerekli izinler** sekmesini ve onay için uygulamanız gereken güven düzeyini seçin. Varsayılan değer **FullTrust**, çoğu uygulama için uygun olacak.  
  
12. Seçin **dosya**, **Kaydet** menüsünde. Uygulama bildirimi imzalamak için imzalama Seçenekleri iletişim kutusu görüntülenir.  
  
13. Dosya sisteminizdeki bir dosya olarak depolanan bir sertifika varsa **sertifika dosyası işaretiyle** seçeneğini ve üç nokta simgesini kullanarak dosya sisteminden sertifikayı seçin (**...** ) düğmesi. Ardından, sertifika parolasını yazın.  
  
     veya  
  
     Sertifikanızı bilgisayarınızdan erişilebilir bir sertifika deposunda tutuluyorsa seçin **depolanan bir sertifika ile oturum** seçenek ve sağlanan listeden bir sertifika seçin.  
  
14. Tıklayın **Tamam** uygulama bildiriminizi imzalamak için. **Kaydet** iletişim kutusu görüntülenir.  
  
15. İçinde **Kaydet** iletişim kutusunda, sürüm dizini belirtin ve ardından **Kaydet**.  
  
16. Seçin **dosya**, **yeni**, **dağıtım bildirimi** menüsünden, dağıtım bildirimi oluşturmak için.  
  
17. Üzerinde **adı** sekmesinde, bu dağıtım için bir ad ve sürüm numarası belirtin (**1.0.0.0** Bu örnekte). Ayrıca belirtin **İşlemci** , uygulamanız için x86 gibi oluşturulmuştur.  
  
18. Seçin **açıklama** sekmesini tıklatın ve değerlerini belirtin **yayımcı** ve **ürün**. (**Ürün** uygulamanız çevrimdışı kullanım için bir istemci bilgisayara yüklendiğinde, uygulamanıza Windows Başlat menüsündeki verilen addır.)  
  
19. Seçin **dağıtım seçenekleri** sekmesinde ve **Başlat konumu** metin kutusunda, Web sunucusu veya paylaşımı uygulama bildiriminin konumu belirtin. Örneğin,  *\\\myServer\myShare\AppToDeploy.application*.  
  
20. Eklediyseniz *.deploy* uzantısı bir önceki adımda da seçin **.deploy dosya adı uzantısını kullandığınızdan** burada.  
  
21. Seçin **Güncelleştirme Seçenekleri** sekmesini tıklatın ve güncelleştirmek için bu uygulamanın ne sıklıkta istediğinizi belirtin. Uygulamanız kullanıyorsa <xref:System.Deployment.Application.UpdateCheckInfo> kendisini güncelleştirmeleri denetlemek için temizleyin **bu uygulama güncelleştirmeleri denetlesin** onay kutusu.  
  
22. Seçin **uygulama başvurusu** sekmesine ve ardından **seçin** düğmesi. Açık bir iletişim kutusu görünür.  
  
23. Daha önce oluşturduğunuz uygulama bildirimini seçin ve ardından **açık**.  
  
24. Seçin **dosya**, **Kaydet** menüsünde. A **imzalama seçenekleri** iletişim kutusu dağıtım bildirimi imzalamanızı isteyen görüntülenir.  
  
25. Dosya sisteminizdeki bir dosya olarak depolanan bir sertifika varsa **sertifika dosyası işaretiyle** seçeneğini ve üç nokta simgesini kullanarak dosya sisteminden sertifikayı seçin (**...** ) düğmesi. Ardından, sertifika parolasını yazın.  
  
     veya  
  
     Sertifikanızı bilgisayarınızdan erişilebilir bir sertifika deposunda tutuluyorsa seçin **depolanan bir sertifika ile oturum** seçenek ve sağlanan listeden bir sertifika seçin.  
  
26. Tıklayın **Tamam** Dağıtım bildiriminizi imzalamak için. **Kaydet** iletişim kutusu görüntülenir.  
  
27. İçinde **Kaydet** iletişim kutusu, bir dizin Yukarı Taşı, dağıtım ve ardından kök **Kaydet**.  
  
28. Dağıtım hedefi veya medya dosyalarının tümünü dağıtım dizininde kopyalayın. Bu, bir Web sitesi veya FTP sitesi, bir dosya paylaşımı veya CD-ROM klasör ya da olabilir.  
  
29. Kullanıcılarınızın, URL, UNC veya uygulamanızı yüklemek için gereken fiziksel ortam sağlar. Bir URL veya UNC sağlarsanız, dağıtım bildiriminin tam yolu, kullanıcılarınızın vermeniz gerekir. Örneğin, AppToDeploy dağıtılır http://webserver01/ AppToDeploy dizininde tam bir URL yolu olacaktır http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Sonraki adımlar  
 Uygulamanın yeni bir sürümünü dağıtmanız gerekebilir, sonra yeni sürümü adlı yeni bir dizin oluşturun — Örneğin, 1.0.0.1 yeni uygulama dosyaları kopyalama yeni dizine. Ardından, oluşturmak ve yeni bir uygulama bildirimini imzalayın ve güncelleştirme ve dağıtım bildirimi imzalamak için önceki adımları izlemeniz gerekir. Her ikisinde de aynı daha yüksek bir sürüme belirtilmesi konusunda dikkatli olun *Mage.exe* `-New` ve `-Update` çağrıları olarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yalnızca daha yüksek sürümlerinde, en önemli en soldaki tamsayı ile güncelleştirir. Kullandıysanız *MageUI.exe*, dağıtım bildirimini açarak, seçerek güncelleştirebilirsiniz **uygulama başvurusu** sekmesine tıklayarak **seçin** düğmesi ve Daha sonra güncelleştirilmiş uygulama bildirimini seçme.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Mage.exe (bildirim üretme ve düzenleme aracı)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Uygulama bildirimi](../deployment/clickonce-application-manifest.md)