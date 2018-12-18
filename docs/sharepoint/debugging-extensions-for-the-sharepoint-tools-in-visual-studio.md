---
title: Visual Studio'da SharePoint araçları için hata ayıklama uzantıları | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f878284c6e181956cbd3e708334301963aa25cf
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326101"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Uzantıları Visual Studio'da SharePoint araçları için hata ayıklama
  SharePoint araç uzantıları deneysel örneği ya da Visual Studio normal örneğini ayıklayabilirsiniz. Uzantı davranışını gidermek gerekiyorsa, ek hata bilgileri görüntülemek için ve Visual Studio SharePoint komutları nasıl yürütür yapılandırmak için kayıt defteri değerlerini de değiştirebilirsiniz.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Visual Studio'nun deneysel örneği uzantılarında hata ayıklama
 Visual Studio geliştirme ortamınızı yanlışlıkla bozulmaya sınanmamış uzantıları tarafından korunması için Visual Studio SDK'sı olarak adlandırılan bir alternatif Visual Studio örneği sağlar *deneysel örneği*, kullanabileceğiniz Yükleme ve uzantılarını test etmek için. Visual Studio normal örneğini kullanarak yeni uzantılar geliştirmek, ancak hata ayıklama ve deneysel örneğinde çalıştırın. Daha fazla bilgi için bkz: [deneysel örneği](../extensibility/the-experimental-instance.md).

 Uzantınızı dağıtmak için VSIX proje kullanın ve başlangıç projesi çözümünüzdeki VSIX proje ise, Visual Studio, otomatik olarak yükler ve çözümünüzü hata ayıklarken uzantısı deneysel örneğinde çalışır. Başlangıç projesi olarak birden çok proje içeren bir çözüm ayıklarken başlayan projesidir. Uzantınızı dağıtmak üzere bir VSIX proje kullanma hakkında daha fazla bilgi için bkz: [Visual Studio'da SharePoint araçları için Uzantılar dağıtmak](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Visual Studio'nun deneysel örneği uzantılarında çeşitli türlerde hata ayıklamak nasıl gösteren örnekler için aşağıdaki izlenecek bakın:

-   [İzlenecek yol: bir SharePoint proje öğesi türünü genişletme](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [İzlenecek yol: SharePoint projeleri için bir özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [İzlenecek yol: Web bölümlerini görüntülemek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [İzlenecek yol: bir sunucu Gezgini uzantısında SharePoint istemcisi nesne modelini çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Visual Studio normal örneğini uzantılarında hata ayıklama
 Uzantı projeniz Visual Studio normal örneğindeki hata ayıklamak istediğiniz ilk uzantısı normal örneğinde yükleyin. Ardından, hata ayıklayıcı ikinci bir Visual Studio işlemini ekleyin. İşlemi tamamladığınızda, böylece artık geliştirme bilgisayarınızda yükler uzantısı kaldırabilirsiniz.

#### <a name="to-install-the-extension"></a>Uzantıyı yüklemek için

1.  Visual Studio tüm örneklerini kapatın.

2.  Uzantı projesi derleme çıktı klasöründe açın *.vsix* dosyasını çift tıklatarak veya kısayol menüsünü açarak ve ardından seçme **açmak**:

3.  İçinde **Visual Studio Uzantı Yükleyicisi** iletişim kutusunda, Visual Studio uzantısını yükleyin ve ardından istediğiniz sürümü seçin **yükleme** düğmesi.

     Visual Studio için %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions uzantısı dosyalarını yükler\\*yazar adı*\\*uzantı adı* \\ *sürüm*. Bu yolun son üç klasörlerde gelen oluşturulan `Author`, `Name`, ve `Version` öğelerinde *extension.vsixmanifest* dosya uzantısı.

4.  Visual Studio uzantı yüklemelerinden sonra seçin **Kapat** düğmesi.

#### <a name="to-debug-the-extension"></a>Dahili hata ayıklamak için

1.  Yönetici ayrıcalıklarıyla Visual Studio'yu başlatın ve uzantı projesini açın. Bu örneği Visual Studio aşağıdaki adımları başvurmak *ilk örneği*.

2.  Başka bir örnek Visual Studio'nun yönetici ayrıcalıklarıyla başlatın. Bu örneği Visual Studio aşağıdaki adımları başvurmak *ikinci örneği*.

3.  Visual Studio ilk örneğine geçin.

4.  Menü çubuğunda seçin **hata ayıklama**, **ekleme işlemi için**.

5.  İçinde **kullanılabilir işlemler** listesinde, seçin *devenv.exe*. Bu giriş, Visual Studio ikinci örneğine başvurur; Bu proje uzantısı'nda hata ayıklamak istediğiniz örneğidir.

6.  Seçin **Attach** düğmesi.

     Visual Studio uzantı projesi hata ayıklama modunda çalışır.

7.  Visual Studio ikinci örneğe geçin.

8.  Uzantınızı yükler yeni bir SharePoint projesi oluşturun. Örneğin, bir uzantı listesi tanımı proje öğeleri için hata ayıklama, oluşturma bir **listesi tanımını** projesi.

9. Hangi adımları uzantısı kodunuzu test etmek için gerekli olan gerçekleştirin.

10. Hata ayıklama uzantısı işiniz bittiğinde, Visual Studio ikinci bir örneğini kapatın.

#### <a name="to-remove-the-extension"></a>Uzantıyı kaldırmak için

1.  Menü çubuğunda, Visual Studio'da seçin **Araçları**, **Uzantılar ve güncelleştirmeler**.

     **Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.

2.  Uzantılar listesinde uzantısının adını seçin ve ardından **kaldırma** düğmesi.

3.  Görüntülenen iletişim kutusunda seçin **Evet** düğmesi uzantıyı kaldırmak istediğinizi onaylayın.

4.  Seçin **şimdi yeniden Başlat** kaldırma işleminin tamamlanması için düğmesi.

## <a name="debug-sharepoint-commands"></a>SharePoint komutları hata ayıklama
 Bir SharePoint araçları uzantısı parçası olan bir SharePoint komutu hata ayıklamak istiyorsanız, hata ayıklayıcısını gerekir *vssphost4.exe* işlemi. SharePoint komutları yürütür 64-bit ana bilgisayar işlemi budur. SharePoint komutları hakkında daha fazla bilgi ve *vssphost4.exe*, bkz: [SharePoint nesne modellerini çağırma](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Hata ayıklayıcı vssphost4.exe işleme iliştirilemiyor

1.  Yukarıdaki yönergeleri izleyerek Visual Studio'nun deneysel örneği veya Visual Studio normal örneği uzantı hata ayıklamayı Başlat.

2.  Visual Studio içinde çalışırken hata ayıklayıcı menü çubuğunda örneğinde seçin **hata ayıklama**, **ekleme işlemi için**.

3.  İçinde **kullanılabilir işlemler** listesinde, seçin *vssphost.exe*.

    > [!NOTE]
    >  Vssphost.exe listede görünmüyorsa, başlamalıdır *vssphost4.exe* Visual Studio uzantısı, çalıştırdığınız örneğindeki işlem. Genellikle, geliştirme bilgisayarındaki SharePoint sitesine bağlanmak Visual Studio neden olan bir eylem uygulayarak yaparsınız. Örneğin, Visual Studio başlatır *vssphost4.exe* altında bir site bağlantısı düğümünü (bir site URL'si görüntüler düğüm) genişlettiğinizde **SharePoint bağlantıları** düğümünde **Sunucu Gezgini**  penceresinde veya eklediğinizde, belirli bir SharePoint Proje öğeleri gibi **listesi örneği** veya **olay alıcı** bir SharePoint Proje öğeleri.

4.  Seçin **Attach** düğmesi.

5.  Ayıklanacak Visual Studio örneğinde komutu yürütmek için gerekli adımları uygulayın.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>SharePoint araç uzantıları hata ayıklama yardımcı olmak için kayıt defteri değerlerini değiştirme
 Visual Studio'da SharePoint araçları uzantısı hata ayıklarken uzantısı gidermenize yardımcı olması için kayıt defteri değerlerini değiştirebilirsiniz. Altında değerleri mevcut **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** anahtarı. Bu değerler varsayılan olarak yok.

 Uzantıyı SharePoint Araçları'nın gidermenize yardımcı olması için oluşturabilir ve EnableDiagnostics değerini ayarlayın. Aşağıdaki tabloda, bu değer açıklanmaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|EnableDiagnostics|Tanılama iletileri içinde görüntülenip görüntülenmeyeceğini belirtir REG_DWORD **çıkış** penceresi.<br /><br /> Tanılama iletileri görüntülemek için bu değer 1 olarak ayarlayın. İletilerin görüntüleme durdurmak için bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> İletileri yazmak için **çıkış** bir SharePoint penceresinden araçları uzantısı, SharePoint Proje hizmeti kullanın. Daha fazla bilgi için bkz: [SharePoint Proje hizmetini kullanma](../sharepoint/using-the-sharepoint-project-service.md).|

 Dahili bir SharePoint komutu içeriyorsa, oluşturun ve komut gidermenize yardımcı olması için ek değerleri ayarlayın. Aşağıdaki tabloda, bu değerleri açıklanmaktadır.

|Değer|Açıklama|
|-----------|-----------------|
|AttachDebuggerToHostProcess|Hata ayıklayıcısını olanak tanıyan bir iletişim kutusu görüntülenip görüntülenmeyeceğini belirtir REG_DWORD *vssphost4.exe* onu başlar başlamaz. Bu işlem başlatıldıktan hemen sonra tarafından vssphost.exe hata ayıklamak istediğiniz komut yürütülürse faydalı olur ve hata ayıklayıcı komut yürütülmeden önce el ile eklemek için yeterli bir süre değil. İletişim kutusunu görüntülemek için *vssphost4.exe* çağrıları <xref:System.Diagnostics.Debugger.Break%2A> başlatıldığında yöntemi.<br /><br /> Bu davranışı etkinleştirmek için bu değer 1 olarak ayarlayın. Bu davranışı devre dışı bırakmak için bu değeri 0 olarak ayarlayın veya bu değeri silin.<br /><br /> Bu değer 1 olarak ayarlarsanız, ayrıca kendiniz Visual Studio bekliyor önce hata ayıklayıcısı eklemek için yeterli süre sağlamak için HostProcessStartupTimeout değerini artırmak isteyebilirsiniz *vssphost4.exe* sinyal başarıyla başlatıldı.|
|ChannelOperationTimeout|Visual Studio bir SharePoint komutu yürütmek bekleyeceği saniye cinsinden süreyi belirten REG_DWORD. Komutu, zaman içindeki yürütün değil, bir <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> oluşturulur.<br /><br /> Varsayılan değer 120 saniyedir.|
|HostProcessStartupTimeout|Bu Visual Studio süreyi saniye cinsinden belirten REG_DWORD, bekleyen *vssphost4.exe* sinyal başarıyla başlatıldı. Varsa *vssphost4.exe* başarılı bir başlangıç, zaman içindeki işaret etmiyor bir <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> oluşturulur.<br /><br /> Varsayılan değer 60 saniyedir.|
|MaxReceivedMessageSize|Visual Studio arasında geçirilen WCF iletilerinin bayt cinsinden boyutu, izin verilen maksimum belirten REG_DWORD ve *vssphost4.exe*.<br /><br /> 1.048.576 bayt (1 MB) varsayılandır.|
|MaxStringContentLength|Visual Studio arasında geçirilen dizeleri bayt cinsinden boyutu, izin verilen maksimum belirten REG_DWORD ve *vssphost4.exe*.<br /><br /> 1.048.576 bayt (1 MB) varsayılandır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da SharePoint araçları genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
