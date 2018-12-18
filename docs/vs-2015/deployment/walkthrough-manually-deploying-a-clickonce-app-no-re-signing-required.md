---
title: İzlenecek yol:, Yeniden imzalama gerektirmeyen ve marka bilgisini koruyan bir ClickOnce uygulamasını el ile dağıtma | Microsoft Docs
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
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2d6531a94a99e2a1c24d80e9f326d23fcc6c4ec3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252999"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>İzlenecek yol: Yeniden İmzalama Gerektirmeyen ve Marka Bilgisini Koruyan bir ClickOnce Uygulamasını El ile Dağıtma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oluştururken bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama ve ardından bu yayımlamak için bir müşteri verin ve dağıtmak, müşteri geleneksel dağıtım bildirimini güncelleştir ve yeniden oturum oluşturdu. Çoğu durumda tercih edilen yöntem, hala olmakla birlikte, .NET Framework 3.5 oluşturmanızı sağlayan [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] yeni bir dağıtım bildirimi yeniden oluşturmak zorunda kalmadan, müşteriler tarafından dağıtılabilir dağıtımlar. Daha fazla bilgi için [dağıtma ClickOnce uygulamaları test etme ve üretim sunucularına Resigning olmadan](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Oluştururken bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama ve ardından bu yayımlamak için bir müşteri verin ve dağıtmak, uygulama müşterinin marka kullanabilirsiniz veya marka bilgilerinizi koruyabilirsiniz. Örneğin, uygulamanın tek bir özel uygulama ise, markanızı isteyebilirsiniz. Uygulamanın her müşteri için yüksek oranda özelleştirilmiş ise, müşterinin marka kullanmak isteyebilirsiniz. Dağıtmak üzere bir uygulama için bir kuruluş verdiğinizde .NET Framework 3.5, markanızı, yayımcı bilgileri ve güvenlik imza sağlar. Daha fazla bilgi için [oluşturma başkalarının ClickOnce uygulamaları dağıtma](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  Bu izlenecek yolda, dağıtımları el ile veya komut satırı aracı Mage.exe, hem de MageUI.exe grafik aracını kullanarak oluşturun. Dağıtımlar hakkında daha fazla bilgi için bkz. [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolda adımları gerçekleştirmek için aşağıdakiler gerekir:  
  
-   Dağıtmaya hazır bir Windows Forms uygulaması. Bu uygulama WindowsFormsApp1 olarak anılacaktır.  
  
-   Visual Studio veya Windows SDK'sı.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Birden çok dağıtım ve Mage.exe kullanarak marka desteği ile ClickOnce uygulamasında dağıtmak için  
  
1.  Visual Studio komut istemi açın veya [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] komut istemi ve depolama dizinine, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dosyaları.  
  
2.  Geçerli dağıtım sürümünün adını bir dizin oluşturun. Bu uygulamayı ilk kez ise, büyük olasılıkla seçeceğiniz **1.0.0.0**.  
  
    > [!NOTE]
    >  Dağıtımınızın sürümünden uygulama dosyalarınızı sürümünden farklı olabilir.  
  
3.  Adlı bir alt dizin oluşturma **bin** ve yürütülebilir dosyalar, derlemeleri, kaynakları ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı buraya kopyalayın.  
  
4.  Mage.exe çağrısı ile bir uygulama bildirimi oluşturur.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Uygulama bildirimi dijital sertifikanızla imzalayın.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Mage.exe bir çağrıyla dağıtım bildirimi oluşturur. Varsayılan olarak, Mage.exe işaretler, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım yüklü bir uygulama, BT'nin hem çevrimiçi çalıştırabilmeniz için ve çevrimdışı olarak. Kullanıcının çevrimiçi olduğunda uygulama kullanılabilir yapmak için `-i` bağımsız değişken değerini `f`. Bu uygulama birden çok dağıtım özelliğinden yararlanın dışlayın `-providerUrl` Mage.exe bağımsız değişkeni. (Dışlama .NET Framework sürüm 3.5, önceki sürümlerinde `-providerUrl` için çevrimdışı bir uygulama bir hataya neden olur.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Dağıtım bildirimi oturum yok.  
  
8.  Uygulama, ağ üzerinde dağıtan müşteriye, tüm dosyaları sağlar.  
  
9. Bu noktada, müşteri, dağıtım bildirimini kendi kendinden oluşturulmuş bir sertifika ile oturum açmanız gerekir. Örneğin, müşteri Adventure Works adlı bir şirketin çalışırsa, kendisinin MakeCert.exe aracı kullanarak otomatik olarak imzalanan bir sertifika oluşturabilirsiniz. Ardından, Mage.exe için geçirilen bir PFX dosyasına MakeCert.exe tarafından oluşturulan dosyaları birleştirmek için Pvk2pfx.exe Aracı'nı kullanın.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Müşteri, sonra dağıtım bildirimi imzalamak için bu sertifikayı kullanır.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Müşteri, kullanıcılar uygulamayı dağıtır.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Birden çok dağıtım ve MageUI.exe kullanarak marka desteği ile ClickOnce uygulamasında dağıtmak için  
  
1.  Visual Studio komut istemi açın veya [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] komut istemi ve depolama dizinine gidin, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dosyaları.  
  
2.  Adlı bir alt dizin oluşturma **bin** ve yürütülebilir dosyalar, derlemeleri, kaynakları ve veri dosyaları dahil olmak üzere tüm uygulama dosyalarınızı buraya kopyalayın.  
  
3.  Geçerli dağıtım sürümünün adını bir dizin oluşturun. Bu uygulamayı ilk kez ise, büyük olasılıkla seçeceğiniz **1.0.0.0**.  
  
    > [!NOTE]
    >  Dağıtımınızın sürümünden uygulama dosyalarınızı sürümünden farklı olabilir.  
  
4.  Taşıma \\ **bin** 2. adımda oluşturduğunuz dizine dizin.  
  
5.  Grafik araç MageUI.exe başlatın.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Seçerek yeni bir uygulama bildirimi oluşturmak **dosya**, **yeni**, **uygulama bildirimi** menüsünde.  
  
7.  Varsayılan **adı** sekmesinde, bu dağıtımın adını ve sürüm numarasını girin. Ayrıca, bir değer sağlamak **yayımcı**, doğrulayacak uygulamanın kısayol bağlantısı öğesinin Başlangıç menüsündeki klasör adı olarak dağıtıldığında.  
  
8.  Seçin **uygulama seçenekleri** sekmesine **kullanmak, uygulama bildirimi güven bilgi**. Bu üçüncü taraf markayı olanak tanıyacak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama.  
  
9. Seçin **dosyaları** sekmesine **Gözat** uygulama dizini metin kutusunun yanındaki düğmeyi.  
  
10. 2. adımda oluşturduğunuz uygulama dosyalarınızı içeren dizine seçip tıklayın **Tamam** klasör seçimi iletişim kutusunda.  
  
11. Tıklayın **Doldur** düğmesini tüm uygulama dosyalarını dosya listesine ekleyin. Uygulamanız birden fazla yürütülebilir dosya içeriyorsa, bu dağıtım için bir başlangıç uygulaması olarak ana yürütülebilir dosyayı seçerek işaretlemek **giriş noktası** gelen **dosya türü** aşağı açılan listesi. (Uygulamanız yalnızca bir çalıştırılabilir dosya içeriyorsa, MageUI.exe bunu sizin için işaretler.)  
  
12. Seçin **gerekli izinler** sekmesini ve onay için uygulamanız gereken güven düzeyini seçin. Varsayılan değer **tam güven**, çoğu uygulama için uygun olacak.  
  
13. Seçin **dosya**, **Kaydet** menüsünde ve uygulama bildirimini kaydedin. Kaydettiğinizde uygulama bildirimini imzalayın istenir.  
  
14. Dosya sisteminizdeki bir dosya olarak depolanan bir sertifika varsa, **sertifika dosyası olarak oturum** seçeneğini ve üç nokta simgesini kullanarak dosya sisteminden sertifikası seçin (**...** ) düğmesi.  
  
     veya  
  
     Sertifikanızı bilgisayarınızdan erişilebilen bir sertifika deposunda kaldığı seçin **depolanan bir sertifika seçeneği ile oturum**, sağlanan listeden bir sertifika seçin.  
  
15. Seçin **dosya**, **yeni**, **dağıtım bildirimi** menüden Dağıtım bildiriminizi oluşturmak ve ardından **adı** sekmesinde, tedarik bir ad ve sürüm numarası (**1.0.0.0** Bu örnekte).  
  
16. Geçiş **güncelleştirme** sekmesini tıklatın ve güncelleştirmek için bu uygulamanın istediğiniz sıklığı belirtin. Uygulamanız kullanıyorsa [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım kendisi, güncelleştirmeleri denetlemek için API etiketli onay kutusunu temizleyin **bu uygulama güncelleştirmeleri denetlesin**.  
  
17. Geçiş **uygulama başvurusu** sekmesi. Tüm değerleri bu sekmedeki tıklayarak önceden doldurabilirsiniz **seçin** , düğmesine tıklayıp uygulama bildirimini önceki adımlarda oluşturduğunuz.  
  
18. Seçin **Kaydet** ve dağıtım bildirimini diske kaydedin. Kaydettiğinizde uygulama bildirimini imzalayın istenir. Tıklayın **iptal** imzalamadan bildirimi kaydetmek için.  
  
19. Tüm uygulama dosyalarını müşteriye sağlayın.  
  
20. Bu noktada, müşteri, dağıtım bildirimini kendi kendinden oluşturulmuş bir sertifika ile oturum açmanız gerekir. Örneğin, müşteri Adventure Works adlı bir şirketin çalışırsa, kendisinin MakeCert.exe aracı kullanarak otomatik olarak imzalanan bir sertifika oluşturabilirsiniz. Ardından, bir PFX dosyasına MageUI.exe geçirilebilir MakeCert.exe tarafından oluşturulan dosyaları birleştirmek için Pvk2pfx.exe Aracı'nı kullanın.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Oluşturulan sertifika ile müşteri artık MageUI.exe dağıtım bildirimini açarak ve ardından kaydederek bir dağıtım bildirimini imzalar. İmza iletişim kutusu göründüğünde, müşterinin seçtiği **sertifika dosyası işarete** seçenek ve he diskte kaydetti PFX dosyasını seçer.  
  
22. Müşteri, kullanıcılar uygulamayı dağıtır.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Mage.exe (bildirim üretme ve düzenleme aracı)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (bildirim üretme ve düzenleme aracı, grafik istemci)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [MakeCert.exe (sertifika oluşturma aracı)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)



