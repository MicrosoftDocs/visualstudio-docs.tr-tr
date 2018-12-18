---
title: VSTO eklentileri için kayıt defteri girişleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 14d35e8d6aa6209f628e38be65c9be5fbc614561
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50673022"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO eklentileri için kayıt defteri girişleri
  Visual Studio kullanılarak oluşturulan VSTO Add-Ins dağıttığınızda, belirli bir kayıt defteri girdileri oluşturmanız gerekir. Bu kayıt defteri girdileri bulmak ve VSTO eklentisi yükleme Microsoft Office uygulamasını sağlayan bilgiler sağlar.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Projenizi oluşturduğunuzda, Visual Studio geliştirme bilgisayarında bu kayıt defteri girdileri kolayca çalışmasını ve VSTO eklentisi hata ayıklama oluşturur. VSTO eklenti dağıtmak için ClickOnce'ı kullanma, kayıt defteri girdilerini son kullanıcı bilgisayarda otomatik olarak oluşturulur. VSTO eklenti dağıtmak için Windows Installer kullanırsanız, son kullanıcı bilgisayarda kayıt defteri girişleri oluşturmak için InstallShield Limited Edition projesi yapılandırmanız gerekir.  
  
 Kayıt defteri girdilerini VSTO eklentileri için yükleme işlemi sırasında nasıl kullanıldığı hakkında daha fazla bilgi için bkz. [mimarisi, VSTO eklentileri](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Bu konuda, metin *eklenti kimliği* VSTO eklenti için benzersiz bir kimliği temsil eder. Varsayılan olarak VSTO eklentisi derlemenizin adını kimliğidir.  
  
## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>VSTO eklentileri için tüm kullanıcılar ve geçerli kullanıcının kayıt  
 Bir VSTO Eklenti yüklendiğinde, iki yolla kaydedilebilir:  
  
- Yalnızca geçerli kullanıcı için (diğer bir deyişle, VSTO eklentisi yüklü olan bilgisayarda oturum açan kullanıcıya kullanılabilir). Bu durumda, kayıt defteri girişleri altında oluşturulan **HKEY_CURRENT_USER**.  
  
- Tüm kullanıcılar için (diğer bir deyişle, bilgisayarda oturum açan her kullanıcı için VSTO eklentisi kullanabilirsiniz). Bu durumda, kayıt defteri girişleri altında oluşturulan **HKEY_LOCAL_MACHINE**.  
  
  Geçerli kullanıcı için tüm VSTO Visual Studio kullanarak oluşturduğunuz eklentileri kaydedilebilir. Ancak, yalnızca belirli senaryolarda tüm kullanıcılar için VSTO eklentileri kaydedilebilir. Bu senaryolar sürümüne bilgisayarda Microsoft Office ve VSTO eklentisi nasıl dağıtıldığına bağlıdır.  
  
### <a name="microsoft-office-version"></a>Microsoft Office sürümü  
 Office uygulamaları, VSTO altında kayıtlı eklentileri yükleyebilir **HKEY_LOCAL_MACHINE** veya **HKEY_CURRENT_USER**.  
  
 VSTO altında kayıtlı eklentileri yüklemeye **HKEY_LOCAL_MACHINE**, bilgisayarları, güncelleştirme paketini 976477 yüklü olması gerekir. Daha fazla bilgi için bkz. [http://go.microsoft.com/fwlink/?LinkId=184923](http://go.microsoft.com/fwlink/?LinkId=184923).  
  
### <a name="deployment-type"></a>Dağıtım türü  
 Bir VSTO eklentisi dağıtmak için ClickOnce'ı kullanma, VSTO eklentisi yalnızca geçerli kullanıcı için kaydedilebilir. ClickOnce yalnızca altında oluşturma anahtarları desteklediğinden budur **HKEY_CURRENT_USER**. VSTO eklentisi bir bilgisayardaki tüm kullanıcılar için kaydetmek istiyorsanız, VSTO eklentisi dağıtmak için Windows Installer kullanmanız gerekir. Bu dağıtım türleri hakkında daha fazla bilgi için bkz. [ClickOnce kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-clickonce.md) ve [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md).  
  
## <a name="registry-entries"></a>Kayıt defteri girdileri  
 Gerekli VSTO eklenti kayıt defteri girdilerini, Visio dışındaki tüm uygulamalar için aşağıdaki kayıt defteri anahtarı altında bulunan burada *kök* olduğu **HKEY_CURRENT_USER** veya **HKEY_LOCAL_MACHINE** .  
  
 **Visio dışında tüm uygulamalar**  
  
|Office sürümü|Yapılandırma yolu|  
|--------------------|------------------------|  
|32 bit:|*Kök*\Software\Microsoft\Office\\*uygulama adı*\Addins\\*eklenti kimliği*|  
|64 bit|*Kök*\Software\Wow6432Node\Microsoft\Office\\*uygulama adı*\Addins\\*eklenti kimliği*|  
  
 **Visio**  
  
|Office sürümü|Yapılandırma yolu|  
|--------------------|------------------------|  
|32 bit:|*Kök*\Software\Microsoft\Visio\Addins\\*eklenti kimliği*|  
|64 bit|*Kök*\Software\Wow6432Node\Visio\Addins\\*eklenti kimliği*|  
  
 Aşağıdaki tabloda, bu kayıt defteri anahtarı altındaki girişleri listeler.  
  
|Giriş|Tür|Değer|  
|-----------|----------|-----------|  
|**Açıklama**|REG_SZ|Gerekli. Kısa bir açıklaması için VSTO eklentisi.<br /><br /> Bu açıklama kullanıcı VSTO eklenti seçtiğinde görüntülenir **eklentileri** bölmesinde **seçenekleri** iletişim kutusunda, Microsoft Office uygulaması.|  
|**FriendlyName**|REG_SZ|Gerekli. VSTO görüntülenen eklentisi, açıklayıcı bir ad **COM eklentileri** iletişim kutusunda, Microsoft Office uygulaması. Varsayılan değer eklentisi VSTO kimliğidir.|  
|**LoadBehavior**|REG_DWORD|Gerekli. Uygulama için VSTO eklentisi ve VSTO eklenti (yüklü veya kaldırılmış), geçerli durumunu yüklemeye çalıştığında belirten bir değeri.<br /><br /> Varsayılan olarak, bu girdi, VSTO eklentisi başlangıçta yüklendiğini belirten 3'e ayarlanır. Daha fazla bilgi için [LoadBehavior değerleri](#LoadBehavior). **Not:** bir kullanıcı için VSTO eklentisi devre dışı bırakırsa bu eylemi değiştirir **LoadBehavior** değerini **HKEY_CURRENT_USER** kayıt defteri kovanı. Her kullanıcının, değerini **LoadBehavior** HKEY_CURRENT_USER hive değerini geçersiz kılar, varsayılan **LoadBehavior** tanımlanan **HKEY_LOCAL_MACHINE** hive.|  
|**Bildirimi**|REG_SZ|Gerekli. Dağıtım bildirimi için VSTO eklentisi tam yolu. Yerel bilgisayardaki bir konuma yol olabilir bir ağ paylaşımına (UNC) veya bir Web sunucusu (HTTP).<br /><br /> Çözümü dağıtmak için Windows Installer kullanırsanız, ön eki eklemelisiniz **file:///** için **bildirim** yolu. Ayrıca dize eklemeniz gerekir  **&#124;vstolocal** (diğer bir deyişle, dikey çizgi karakterinden **&#124;** ardından **vstolocal**) sonuna kadar bu yolu. Bu, çözümünüzün ClickOnce önbelleğinden yerine yükleme klasörünü yüklenmesini sağlar. Daha fazla bilgi için [Windows Installer kullanarak Office çözümü dağıtma](../vsto/deploying-an-office-solution-by-using-windows-installer.md). **Not:** geliştirme bilgisayarında bir VSTO eklentisi oluşturma sırasında Visual Studio otomatik olarak ekler  **&#124;vstolocal** bu kayıt defteri girdisi için dize.|  
  
###  <a name="OutlookEntries"></a> Outlook form bölgeleri için kayıt defteri girişleri  
 VSTO eklentisi için Outlook içinde bir özel form bölgesi oluşturursanız, ek kayıt defteri girdileri form bölgesinin Outlook ile kaydetmek için kullanılır. Bu girişler, bir form bölgesinin desteklediği her bir ileti sınıfı için farklı bir kayıt defteri anahtarı altında oluşturulur. Bu kayıt defteri anahtarlarını aşağıdaki konumda bulunan burada *kök* olduğu **HKEY_CURRENT_USER** veya **HKEY_LOCAL_MACHINE**.  
  
 *Kök*\Software\Microsoft\Office\Outlook\FormRegions\\*ileti sınıfı*  
  
 Projenizi yapılandırdığınızda tüm VSTO eklentileri tarafından paylaşılan diğer kayıt defteri girdilerini gibi Visual Studio form bölgesi kayıt defteri girdilerini geliştirme bilgisayarında oluşturur. VSTO eklenti dağıtmak için ClickOnce'ı kullanma, kayıt defteri girdilerini son kullanıcı bilgisayarda otomatik olarak oluşturulur. VSTO eklenti dağıtmak için Windows Installer kullanırsanız, son kullanıcı bilgisayarda kayıt defteri girişleri oluşturmak için InstallShield Limited Edition projesi yapılandırmanız gerekir.  
  
 Form bölgesi kayıt defteri girdileri hakkında daha fazla bilgi için bkz. [özel bir formu bir form bölgesinin konumunu belirtin](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form). Outlook form bölgeleri hakkında daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
##  <a name="LoadBehavior"></a> LoadBehavior değerleri  
 **LoadBehavior** altında girdisi *kök*\Software\Microsoft\Office\\*uygulama adı*\Addins\\*eklentisi Kimliği* anahtar VSTO eklentisi çalışma zamanı davranışını belirten değerlerinin Bitsel bir birleşimi içerir. En düşük sıralı bitten (değerler 0 ile 1) VSTO eklentisi şu anda kaldırıldı yüklenen mı olduğunu gösterir. Uygulama için VSTO eklentisi yüklemeye çalıştığında diğer bitler gösterir.  
  
 Genellikle, **LoadBehavior** girişi, 0, 3 ya da 16 (ondalık)'için ayarlanmış olması amaçlanmıştır VSTO eklentisi yüklü olduğunda son kullanıcı bilgisayarlarında. Varsayılan olarak, Visual Studio ayarlar **LoadBehavior** VSTO eklenti oluşturun veya yayımladığınızda 3 girişi.  
  
 Tüm olası değerleri aşağıdaki tabloda **LoadBehavior** girişi. Bu tabloda bazı açıklamalar el ile veya programlama yoluyla yüklemek için VSTO eklentisi bakın. Bir VSTO eklentisi el ile yüklemek için VSTO eklentisi içinde yanındaki onay kutusunu seçin. **COM eklentileri** iletişim kutusunda uygulama. Bir VSTO eklenti programlama yoluyla yüklemek için <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> özelliği <xref:Microsoft.Office.Core.COMAddIn> için VSTO eklentisi temsil eden nesne **true**.  
  
|(Ondalık) değeri|VSTO eklenti durumu|VSTO eklenti yükleme davranışı|Açıklama|  
|--------------------------|-------------------------|--------------------------------|-----------------|  
|0|Kaldırıldı|Otomatik olarak yüklenmiyor|Uygulama, VSTO eklentisi otomatik olarak yüklemek hiçbir zaman çalışır. VSTO eklentisi el ile yüklemek kullanıcı deneyebilir veya VSTO eklentisi programlı olarak yüklenebilir.<br /><br /> VSTO eklentisi başarıyla yüklendi, **LoadBehavior** değeri 0 olarak kalır, ancak VSTO eklenti durumu **COM eklentileri** iletişim kutusu, VSTO eklentisi yüklü olduğunu belirtmek için güncelleştirilir.|  
|1.|Yüklü|Otomatik olarak yüklenmiyor|Uygulama, VSTO eklentisi otomatik olarak yüklemek hiçbir zaman çalışır. VSTO eklentisi el ile yüklemek kullanıcı deneyebilir veya VSTO eklentisi programlı olarak yüklenebilir.<br /><br /> Ancak **COM eklentileri** uygulama başladıktan sonra VSTO eklentisi yüklendi, el ile veya programlama yoluyla yüklenene kadar VSTO eklentisi yüklü değil iletişim kutusu gösterir.<br /><br /> Uygulama başarıyla VSTO eklentisi, yüklerse **LoadBehavior** değeri 0 olarak değiştirir ve uygulama kapatıldıktan sonra 0 olarak kalır.|  
|2|Kaldırıldı|Başlangıçta yükle|Uygulama, VSTO eklentisi otomatik olarak yüklemek denemez. VSTO eklentisi el ile yüklemek kullanıcı deneyebilir veya VSTO eklentisi programlı olarak yüklenebilir.<br /><br /> Uygulama başarıyla VSTO eklentisi, yüklerse **LoadBehavior** değeri 3 olarak değiştirir ve uygulama kapatıldıktan sonra 3 kalır.|  
|3|Yüklü|Başlangıçta yükle|Uygulama, uygulama başlatıldığında, VSTO eklenti yüklemek çalışır. Bu, yapı ya da bir VSTO eklentisi Visual Studio'da yayımlama varsayılan değerdir.<br /><br /> Uygulama başarıyla VSTO eklentisi, yüklerse **LoadBehavior** değeri 3 olarak kalır. VSTO Eklenti yüklenirken bir hata meydana gelirse **LoadBehavior** değeri 2'ye değişir ve uygulama kapatıldıktan sonra 2'de kalır.|  
|8|Kaldırıldı|İsteğe bağlı olarak yükleme|Uygulama, VSTO eklentisi otomatik olarak yüklemek denemez. VSTO eklentisi el ile yüklemek kullanıcı deneyebilir veya VSTO eklentisi programlı olarak yüklenebilir.<br /><br /> Uygulama başarıyla VSTO eklentisi, yüklerse **LoadBehavior** 9 değerini değiştirir.|  
|9|Yüklü|İsteğe bağlı olarak yükleme|Uygulama, gerektirdiğinde gibi bir kullanıcı bir kullanıcı Arabirimi öğesi tıkladığında işlevselliği, VSTO Eklentisi (örneğin, Şeritteki özel düğme) kullanan VSTO eklentisi yüklenir.<br /><br /> Uygulama başarıyla VSTO eklentisi, yüklerse **LoadBehavior** değer 9 olarak kalır, ancak VSTO eklenti durumu **COM eklentileri** iletişim kutusu, VSTO eklentisi olduğunu göstermek için güncelleştirilir şu anda yüklü. VSTO Eklenti yüklenirken bir hata meydana gelirse **LoadBehavior** değeri 8 olarak değişir.|  
|16|Yüklü|İlk kez yükleyin ve sonra isteğe bağlı|VSTO isteğe bağlı olarak yüklenmesi için eklenti istiyorsanız bu değeri ayarlayın. Kullanıcı uygulamayı ilk kez çalıştırdığında uygulama için VSTO eklentisi yükler. Kullanıcı uygulamayı çalıştırdığında VSTO eklentisi tarafından tanımlanan herhangi bir kullanıcı Arabirimi öğeleri uygulama yükler, ancak kullanıcı VSTO eklentisi ile ilişkili olan bir kullanıcı Arabirimi öğesi tıklayana kadar VSTO eklentisi yüklenmedi.<br /><br /> Uygulama başarıyla VSTO eklentisi ilk kez yüklendiğinde **LoadBehavior** VSTO Eklenti yüklenirken değeri 16 olarak kalır. Uygulama kapatıldıktan sonra **LoadBehavior** 9 değerini değiştirir.|  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Visual Studio'da Office çözümleri mimarisi](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [VSTO eklentileri mimarisi](../vsto/architecture-of-vsto-add-ins.md)   
 [Office çözümleri oluşturun](../vsto/building-office-solutions.md)   
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)  
  
  