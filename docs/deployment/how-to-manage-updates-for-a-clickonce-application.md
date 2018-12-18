---
title: 'Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5bd9d8d7e88bc9ee8c8b041571ddaa258067c300
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283658"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Uygulama güncelleştirmeleri otomatik olarak veya programlama yoluyla denetleyebilirsiniz. Bir geliştirici olarak ne zaman ve nasıl güncelleme kontrolleri gerçekleştirilir, güncelleştirmeleri zorunlu olan ve burada uygulama güncelleştirmeleri denetlemeli belirtme esneklik kullanabileceğiniz birçok seçenek mevcuttur.  
  
 Uygulama güncelleştirmeleri otomatik olarak uygulama başlamadan önce ya da belirlenen aralıklarda uygulama başladıktan sonra denetlemek için yapılandırabilirsiniz. Buna ek olarak, gerekli en düşük sürüm belirtebilirsiniz; diğer bir deyişle, kullanıcının sürüm gereken sürümden düşükse bir güncelleştirmenin yüklü olduğu.  
  
 Program aracılığıyla bir kullanıcı isteği gibi bir olay tabanlı güncelleştirmeleri denetlemek için uygulamanın yapılandırabilirsiniz. "Güncelleştirmeleri programlı olarak denetlemek için" yordamında bu konuda kullanan kodu nasıl yazacağınızı gösterir <xref:System.Deployment.Application.ApplicationDeployment> güncelleştirmeleri denetlemek için sınıf tabanlı bir olayı.  
  
 Ayrıca, uygulamanızı bir konumdan dağıtabilir ve başka bir yerden güncelleştirebilirsiniz. "Farklı bir güncelleştirme konumu belirtin." yordamına bakın.  
  
 Daha fazla bilgi için [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Güncelleştirme davranışını yönetilir **uygulama güncelleştirmeleri** iletişim kutusu, kullanılabilir **Yayımla** sayfasının **Proje Tasarımcısı.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Uygulama başlamadan önce güncelleştirmeleri denetlemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **güncelleştirmeleri** açmak için düğmeyi **uygulama güncelleştirmeleri** iletişim kutusu.  
  
4.  İçinde **uygulama güncelleştirmeleri** iletişim kutusunda, emin olun **uygulama güncelleştirmeleri denetlesin** onay kutusu seçilidir.  
  
5.  İçinde **uygulamanın güncelleştirmeleri denetleyeceği zamanı seçin** bölümünden **Uygulama başlatılmadan önce**. Bu, kullanıcıların ağa her zaman bağlı uygulama yapılan son güncelleştirmelerle birlikte çalışmasını sağlar.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Uygulama başlatıldıktan sonra arka planda güncelleştirmeleri denetlemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **güncelleştirmeleri** açmak için düğmeyi **uygulama güncelleştirmeleri** iletişim kutusu.  
  
4.  İçinde **uygulama güncelleştirmeleri** iletişim kutusunda, emin onay kutusunu **uygulama güncelleştirmeleri denetlesin** seçilir.  
  
5.  İçinde **uygulama için güncelleştirmeleri bölümüne denetleyeceği zamanı seçin**seçin **uygulama başladıktan sonra**. Uygulama, böylece daha hızlı başlatılır ve ardından, arka planda güncelleştirmeleri denetler ve bir güncelleştirme kullanılabilir olduğunda yalnızca kullanıcıya bildir. Uygulama yeniden başlatılana kadar yüklendikten sonra güncelleştirmeleri etkili olmaz.  
  
6.  İçinde **uygulamanın güncelleştirmeleri ne sıklıkla denetleyeceğini belirtin** bölümünde, ya da seçin **uygulama her çalıştırıldığında denetle** (varsayılan) veya **denetleyin her** ve bir sayı ve zaman aralığı girin.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Uygulama için gerekli en düşük sürüm olarak belirtmek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **güncelleştirmeleri** açmak için düğmeyi **uygulama güncelleştirmeleri** iletişim kutusu.  
  
4.  İçinde **uygulama güncelleştirmeleri** iletişim kutusunda, emin olun **uygulama güncelleştirmeleri denetlesin** onay kutusu seçilidir.  
  
5.  Seçin **bu uygulama için gerekli en düşük sürüm belirtin** onay kutusunu işaretleyin ve ardından girin **ana**, **küçük**, **derleme**ve  **Düzeltme** uygulama için sayı.  
  
### <a name="to-specify-a-different-update-location"></a>Farklı güncelleştirme konumunu belirtmek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **güncelleştirmeleri** açmak için düğmeyi **uygulama güncelleştirmeleri** iletişim kutusu.  
  
4.  İçinde **uygulama güncelleştirmeleri** iletişim kutusunda, emin olun **uygulama güncelleştirmeleri denetlesin** onay kutusu seçilidir.  
  
5.  İçinde **güncelleştirme konumu** alanına, aşağıdaki biçimi kullanarak tam bir URL ile güncelleştirme konumu *http://Hostname/ApplicationName*, ya da UNC yolu biçiminde  *\\\Server\ ApplicationName*, veya **Gözat** güncelleştirme konumu için Gözat düğmesini.  
  
### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri programlı olarak denetlemek için  
  
1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**.  
  
2.  Tıklayın **Yayımla** sekmesi.  
  
3.  Tıklayın **güncelleştirmeleri** açmak için düğmeyi **uygulama güncelleştirmeleri** iletişim kutusu.  
  
4.  İçinde **uygulama güncelleştirmeleri** iletişim kutusunda, emin **uygulama güncelleştirmeleri denetlesin** onay kutusu işaretli değilse. (İsteğe bağlı olarak, güncelleştirmeleri programlama yoluyla ve aynı zamanda güncelleştirmeleri otomatik olarak denetle ClickOnce çalışma zamanı denetlemesine izin vermek için bu onay kutusunu seçebilirsiniz.)  
  
5.  İçinde **güncelleştirme konumu** alanına, aşağıdaki biçimi kullanarak tam bir URL ile güncelleştirme konumu *http://Hostname/ApplicationName*, ya da UNC yolu biçiminde  *\\\Server\ ApplicationName*, veya **Gözat** güncelleştirme konumu için Gözat düğmesini. Uygulamanın güncelleştirilmiş bir sürümünü kendisi için nerede görüneceğini güncelleştirme konumdur.  
  
6.  Güncelleştirmeleri denetlemek için kullanıcıları seçip bir Windows formunda bir düğme, menü öğesi veya diğer kullanıcı arabirimi öğesi oluşturun. Bu öğenin olay işleyicisinden denetlemek ve güncelleştirmeleri yüklemek için bir yöntemini çağırın. Bu tür bir yöntem için Visual Basic ve Visual C# koduna ilişkin bir örnek bulabilirsiniz [nasıl yapılır: ClickOnce dağıtım API'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Uygulamanızı oluşturun.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Uygulama güncelleştirmeleri iletişim kutusu](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))   
 [ClickOnce güncelleştirme stratejisini seçin](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce uygulamalara yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Nasıl yapılır: ClickOnce dağıtım API'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)