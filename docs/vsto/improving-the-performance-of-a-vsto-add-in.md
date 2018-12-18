---
title: Bir VSTO eklentisinin performansını
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 918ff0ac0a0b7f4e16c779516c015d7b74cec415
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672658"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Bir VSTO eklentisinin performansını iyileştirme
  Office uygulamaları kapatın ve böylece bunlar, hızlı başlangıç için oluşturduğunuz VSTO Add-Ins iyileştirerek kullanıcılarınıza daha iyi bir deneyim sunmak, öğeleri ve diğer görevleri gerçekleştirebilirsiniz. Ayrıca, VSTO eklentisi için Outlook ise, VSTO eklenti olacak olasılığını azaltabilirsiniz kötü performans nedeniyle devre dışı. Aşağıdaki stratejileri uygulayarak, VSTO eklentisinin performansını artırabilirsiniz:  
  
- [VSTO eklentilerinde isteğe bağlı yükleme](#Load).  
  
- [Windows Installer kullanarak Office çözümleri yayımlama](#Publish).  
  
- [Şerit yansıma atlama](#Bypass).  
  
- [Pahalı işlemler bir ayrı yürütme iş parçacığı üzerinde gerçekleştirebilir](#Perform).  
  
  Bir Outlook VSTO eklentisi en iyi duruma getirme hakkında daha fazla bilgi için bkz. [etkin VSTO eklentileri tutmak performans ölçütleri](http://go.microsoft.com/fwlink/?LinkID=266503).  
  
##  <a name="Load"></a> VSTO eklentilerinde isteğe bağlı yükleme  
 Bir VSTO yalnızca aşağıdaki durumlarda yüklenecek eklenti yapılandırabilirsiniz:  
  
- VSTO eklentisi yüklendikten sonra kullanıcı uygulamayı başlatır ilk kez.  
  
- Kullanıcı bir sonraki zaman uygulama başlatıldıktan sonra VSTO eklentisi ile etkileşime giren ilk kez.  
  
  Kullanıcı olarak etiketlenmiş özel bir düğme seçtiğinde, VSTO eklenti verilerle çalışma doldurmak **My Veri Al**. Uygulama VSTO eklenti en az bir kez yüklemeniz gerekir böylece **My Veri Al** düğmesi, şeritte görünebilir. Ancak, VSTO eklentisi yeniden kullanıcı, sonraki açışınızda uygulama başladığında yüklenmiyor. VSTO eklentisi yükler yalnızca zaman kullanıcının seçtiği **My Veri Al** düğmesi.  
  
### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>VSTO eklentilerinde isteğe bağlı olarak yüklemek için ClickOnce çözümü yapılandırmak için  
  
1.  İçinde **Çözüm Gezgini**, proje düğümünü seçin.  
  
2.  Menü çubuğunda, **görünümü** > **özellik sayfaları**.  
  
3.  Üzerinde **Yayımla** sekmesini, **seçenekleri** düğmesi.  
  
4.  İçinde **yayımlama seçeneği** iletişim kutusunda **Office ayarları** liste öğesini **isteğe bağlı yük** seçeneğini ve ardından **Tamam**düğmesi.  
  
### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>VSTO eklentilerinde isteğe bağlı olarak yüklemek için Windows Installer çözümü yapılandırmak için  
  
1.  Kayıt defterinde, ayarlanan `LoadBehavior` girişi **_kök_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Eklenti kimliği_** anahtarını **0x10**.  
  
     Daha fazla bilgi için [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  
  
### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>VSTO eklentilerinde isteğe bağlı bir çözüme hata ayıklaması sırasında yüklemek için bir çözümü yapılandırmak için  
  
1.  Ayarlar bir betik oluşturma `LoadBehavior` girişi **_kök_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Eklenti kimliği_** anahtarını **0x10**.  
  
     Aşağıdaki kod örneği bu betiğin gösterir.  
  
    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]  
    "Description"="MyAddIn"  
    "FriendlyName"="MyAddIn"  
    "LoadBehavior"=dword:00000010  
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"  
  
    ```  
  
2.  Kayıt defteri komut dosyasını kullanarak güncelleştirmeleri bir derleme sonrası olay oluşturun.  
  
     Aşağıdaki kod örneği için bir derleme sonrası olay eklemiş olabileceğiniz bir komut dizesi gösterir.  
  
    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"  
  
    ```  
  
     Derleme sonrası olayı oluşturma hakkında daha fazla bilgi için bir C# projesine [nasıl yapılır: belirtin derleme olayları &#40;C&#35;&#41;](/visualstudio/ide/how-to-specify-build-events-csharp).  
  
     Visual Basic projesinde bir derleme sonrası olay oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirtin derleme olayları &#40;Visual Basic&#41;](/visualstudio/ide/how-to-specify-build-events-visual-basic).  
  
##  <a name="Publish"></a> Windows Installer kullanarak Office çözümleri yayımlama  
 Windows Installer kullanarak çözümünüzü yayımlayın, VSTO eklentisi yüklediğinde, Office çalışma zamanı için Visual Studio 2010 Araçları aşağıdaki adımları atlar.  
  
- Bildirim şeması doğrulanıyor.  
  
- Otomatik Güncelleştirmeler denetleniyor.  
  
- Dağıtım bildirimleri dijital imzalarını doğrulama.  
  
  > [!NOTE]  
  >  Bu yaklaşım, kullanıcıların bilgisayarlarında güvenli bir konuma VSTO eklenti dağıtırsanız, gerekli değildir.  
  
  Daha fazla bilgi için [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
##  <a name="Bypass"></a> Şerit yansıma atlama  
 Bir çözüm kullanarak derleme yaparsanız [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], çözümü dağıttığınızda, kullanıcılar Office çalışma zamanı için Visual Studio 2010 Araçları en son sürümünü yüklediğinizden emin olun. Bu çalışma zamanı daha eski sürümleri, Şerit özelleştirmeleri bulmak için çözüm derlemeye yansıtılır. Bu işlem, VSTO eklenti daha yavaş yüklemek, neden olabilir.  
  
 Alternatif olarak, Şerit özelleştirmeleri tanımlamak için yansıma kullanarak herhangi bir sürümünü Office çalışma zamanı için Visual Studio 2010 Araçları engelleyebilirsiniz. Bu stratejiyi izlemek için geçersiz kılma `CreateRibbonExtensibility` yöntemi ve açıkça dönüş Şerit nesneleri. Şerit özelleştirmeler, VSTO eklentisi içermiyorsa, dönüş `null` yöntemi içinde.  
  
 Aşağıdaki örnek, bir alanın değerine göre bir Şerit nesnesi döndürür.  
  
 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]  
  
##  <a name="Perform"></a> Pahalı işlemler bir ayrı yürütme iş parçacığı üzerinde gerçekleştirebilir  
 Ayrı bir iş parçacığı (örneğin, uzun süre çalışan görevleri, veritabanı bağlantıları veya diğer ağ çağrıları tür) uzun süren görevler gerçekleştirmeyi düşünün. Daha fazla bilgi için [Office'te iş parçacığı desteği](../vsto/threading-support-in-office.md).  
  
> [!NOTE]  
>  Office nesne modelini çağıran tüm kod ana iş parçacığında yürütmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Talep üzerine yükleniyor VSTO eklentileri](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)   
 [Office eklentileri CLR'de gecikme yükleme](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)   
 [VSTO eklentilerinde Office için Visual Studio kullanarak oluşturma](create-vsto-add-ins-for-office-by-using-visual-studio.md)   
