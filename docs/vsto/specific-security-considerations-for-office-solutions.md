---
title: Office çözümleriyle ilgili belirli güvenlik konuları
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: dcb2e0a3c381b1dd07c7724c3a64c53307856014
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49951398"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office çözümleriyle ilgili belirli güvenlik konuları
  Microsoft Office ve Microsoft .NET Framework tarafından sağlanan güvenlik özelliklerine Office çözümünüzü olası güvenlik tehditlerine karşı korunmasına yardımcı olabilir. Bu konu, bu tehditleri bazıları açıklanmıştır ve bunlara karşı koruma sağlamak için öneriler sağlar. Ayrıca, Microsoft Office güvenlik ayarları Office çözümlerini nasıl etkilediği hakkında bilgi içerir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Yeni, kötü amaçlı bir belge güvenilen kod tasarlanır  
 Bir saldırgan, belirli bir amaç için örneğin, çalışan uygulamanın kişisel bilgiler indiriliyor yöneliktir güvenilen kod alın ve yeniden çalışma gibi başka bir belgede. Kod, özgün belgenin çalışmıyor ve kişisel bilgilerini elde etmek veya farklı bir kullanıcı tarafından açıldığında artan ayrıcalıkları ile kod yürüten gibi tehditlere'kurmak açılabilir bilmez. Alternatif olarak, saldırgan için victim gönderildiğinde, beklenmedik bir şekilde davranır Öyle ki çalışma sayfasındaki verileri değiştirebilirsiniz. Değerleri, formüller ve sunu kodla bağlantılı bir çalışma sayfası özelliklerini değiştirerek, kötü niyetli bir kullanıcı başka bir kullanıcı tarafından değiştirilmiş dosya gönderme saldırmak mümkündür. Ayrıca kullanıcılar, çalışma değerleri değiştirerek görmek için görmemesi bilgilere erişmek için mümkün olabilir.  
  
 Bütünleştirilmiş kod konumu hem belge konumu yürütmek için yeterli kanıt olmalıdır olduğundan, Bu saldırının bağlamak kolay değildir. Örneğin, e-posta eklerindeki veya güvenilmeyen intranet sunucuları belgeleri çalıştırmak için yeterli izinlere sahip değil.  
  
 Bu saldırı mümkün kılmak için kod koruyabilmeleri verilere dayalı kararları kolaylaştırır biçimde yazılmış olması gerekir. Bir veritabanı sunucusu adını içeren bir gizli hücre içeren bir çalışma sayfası örneği oluşturmaktır. Kullanıcının çalışma sayfasına SQL kimlik doğrulaması ve sabit kodlanmış bir SA parolasını kullanarak bu sunucuya bağlanma girişiminde bir ASPX sayfa gönderir. Bir saldırgan, farklı bir bilgisayar adı ile gizli hücrenin içeriğini değiştirin ve SA parolasını alın. İçin bu sorun, hiçbir sabit kodlu parolalar önlemek ve her zaman sunucu kimliklerini iç sunucuya erişmeden önce iyi olduğu bilinen sunucular listesine karşı denetleyin.  
  
### <a name="recommendations"></a>Önerileri  
  
-   Kullanıcı, belge, bir veritabanı, bir web hizmeti veya diğer kaynaklardan gelmediğini giriş ve verileri her zaman doğrulayın.  
  
-   Kullanıcı adına ayrıcalıklı veri alma ve korumasız bir çalışma sayfasına koyarak gibi işlevselliği, belirli türde oluştururken dikkatli olun.  
  
-   Uygulamanın türüne bağlı olarak, özgün belgenin herhangi bir kod yürütülmeden önce çalıştığını doğrulamak için mantıklı olabilir. Örneğin, bilinen ve güvenli bir konumda depolanan bir belgeden çalıştığından emin olun.  
  
-   Uygulamanızın tüm ayrıcalıklı Eylemler gerçekleştiriyorsa belgeyi açtığında bir uyarı görüntülemek için iyi bir fikir olabilir. Örneğin, giriş ekranı veya uygulama kişisel bilgilere erişebilir ve devam etmek İptal'i seçin kullanıcının olduğunu belirten bir başlatma iletişim kutusu oluşturabilirsiniz. Son kullanıcı, bu tür bir uyarı görünüşte zararsız bir belgeden alırsa, isterse herhangi bir şey güvenliği ihlal edilmeden önce bu uygulamadan çıkmak mümkün olacaktır.  
  
## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod Outlook nesne modeli Koruması tarafından engellendi  
 Microsoft Office, belirli özellikleri, yöntemleri ve nesneler içinde nesne modeli kullanarak kodu kısıtlayabilirsiniz. Bu nesnelere erişimi kısıtlayarak Outlook e-posta solucanlar ve virüs kötü amaçlar için nesne modeli kullanarak önlemeye yardımcı olur. Bu güvenlik özelliğini Outlook nesne modeli koruması bilinir. Bir VSTO eklentisi nesne modeli koruması etkin durumdayken sınırlı bir özellik veya yöntem kullanmayı denerse, Outlook, işlemi durdurmak kullanıcının sağlar ya da kullanıcının t sınırlı bir süre için özellik veya yöntem erişim izni sağlar bir güvenlik uyarısı görüntüler. IME. Kullanıcının işlemi durdurur, Visual Studio'da Office çözümleri kullanılarak oluşturulan Outlook VSTO eklentileri oluşturur bir <xref:System.Runtime.InteropServices.COMException>.  
  
 Nesne modeli koruması, VSTO eklentileri, Outlook Microsoft Exchange Server ile kullanılıp bağlı olarak farklı şekillerde etkileyebilir:  
  
- Outlook ile Exchange kullanılmıyorsa yönetici etkinleştirebilir veya tüm VSTO eklentileri bilgisayarda için nesne modeli koruması devre dışı bırakın.  
  
- Outlook ile Exchange kullanılırsa, yönetici etkinleştirebilir veya devre dışı tüm VSTO eklentileri bilgisayarda için nesne modeli koruması veya yönetici belirli VSTO eklentileri nesne modeli koruması karşılaşılmadan çalıştırabilirsiniz belirleyebilirsiniz. Yöneticiler, nesne modelinin belirli alanlar için nesne modeli koruması davranışını değiştirebilirsiniz. Örneğin, Yöneticiler otomatik olarak nesne modeli koruması etkinleştirilmiş olsa dahi VSTO Add-Ins programlı olarak e-posta göndermek izin verebilir.  
  
  Outlook 2007'de başlayarak, nesne modeli koruması davranışını Outlook güvenli kalmasına yardımcı olun sırasında Geliştirici ve kullanıcı deneyimini iyileştirmek üzere değiştirildi. Daha fazla bilgi için [kod Outlook 2007'de güvenlik değişikliklerini](http://go.microsoft.com/fwlink/?LinkId=73429).  
  
### <a name="minimize-object-model-guard-warnings"></a>Nesne modeli koruma uyarıları simge durumuna küçült  
 Sınırlı özelliklere ve yöntemlere kullandığınızda güvenlik uyarılarını önlemek için VSTO eklenti Outlook nesnelerden aldığına emin olun `Application` alanını `ThisAddIn` projenizdeki sınıfı. Bu alan hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).  
  
 Yalnızca bu nesneden elde edilen Outlook nesneler tarafından nesne modeli koruması güvenebilir. Buna karşılık, elde edilen bir yeni nesneleri `Microsoft.Office.Interop.Outlook.Application` nesne güvenilir değildir ve kısıtlı özellikleri ve yöntemleri nesne modeli koruması etkinleştirilirse güvenlik uyarıları verir.  
  
 Nesne modeli koruması etkinleştirilirse aşağıdaki kod örneğinde bir güvenlik uyarısı görüntüler. `To` Özelliği `Microsoft.Office.Interop.Outlook.MailItem` sınıfı nesne modeli Koruması tarafından kısıtlanmış. `Microsoft.Office.Interop.Outlook.MailItem` Kodunu alır çünkü nesne güvenilmeyen bir `Microsoft.Office.Interop.Outlook.Application` kullanılarak oluşturulan **yeni** eşitlenmemesine yerine işleci `Application` alan.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]  
  
 Aşağıdaki kod örneğinde nasıl özelliğine kısıtlı kullanılacağını gösterir. bir `Microsoft.Office.Interop.Outlook.MailItem` nesne modeli Koruması tarafından güvenilen bir nesne. Güvenilen kodda `Application` almak için alan `Microsoft.Office.Interop.Outlook.MailItem`.  
  
 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]  
  
> [!NOTE]  
>  Outlook ile Exchange kullanılırsa, tüm Outlook nesnelerden elde etme `ThisAddIn.Application` VSTO eklenti tüm Outlook nesne modeline erişme olanağına olacağını garanti etmez. Exchange yönetici Outlook otomatik olarak ayarlar, Outlook için özelliğe erişmek bir önceki kod örneğinde vermez, bu kod örneği kullansa bile, tüm Outlook nesne modeli kullanarak adres bilgilerine erişme girişimi Reddet Güvenilen `ThisAddIn.Application` alan.  
  
### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Exchange kullanıldığında güvenmek için hangi eklentileri belirtin  
 Outlook ile Exchange kullanıldığında, yöneticilerin belirli VSTO eklentileri nesne modeli koruması karşılaşılmadan çalıştırabilirsiniz belirtebilirsiniz. Outlook VSTO Add-Ins Visual Studio'da Office çözümleri kullanılarak oluşturulan tek tek güvenilir olamaz; Bunlar yalnızca bir grup olarak güvenilir olabilir.  
  
 Bir VSTO bir VSTO eklentisinin giriş noktası DLL'nin karma koduna göre eklentisi Outlook güvenir. Tüm Outlook VSTO hedefleyen eklentiler [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı giriş noktası DLL'ine (*VSTOLoader.dll*). Bunun anlamı tüm VSTO hedefleyen eklentisi yönetici güveniyorsa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nesne modeli koruması ve diğer tüm VSTO eklentileri hedefleyen karşılaşılmadan çalıştırmak için [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ayrıca güvenilirdir. Belirli VSTO nesne modeli koruması karşılaşılmadan çalıştırmak için eklentileri güvenen hakkında daha fazla bilgi için bkz. [Outlook kullandığı virüs önleme özelliklerini yönetmek için bir yöntem belirtmek](http://go.microsoft.com/fwlink/?LinkId=128773).  
  
## <a name="permission-changes-do-not-take-effect-immediately"></a>İzin değişiklikleri hemen etkili olmaz  
 Yöneticinin bir belgeyi veya derleme için izinleri ayarlar, kullanıcıların çıkın ve yürütülebilmesi söz konusu değişiklikler için tüm Office uygulamalarını yeniden gerekir.  
  
 Microsoft Office uygulamaları barındıran diğer uygulamalar yeni izinler zorlanmasını de engelleyebilirsiniz. Kullanıcılar, Office, barındırılan veya tek başına, güvenlik ilkeleri değiştirildiğinde kullanan tüm uygulamaları çıkın.  
  
## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Güven Merkezi Ayarları Microsoft Office sistemindeki eklentileri veya belge düzeyi özelleştirmeleri etkilemez  
 Kullanıcıları engelleyebilir VSTO eklentileri yüklenmesini bir seçenek ayarlayarak **Güven Merkezi**. Ancak, VSTO eklentileri ve belge düzeyi özelleştirmeleri Visual Studio'da Office çözümleri kullanılarak oluşturulan bu güven ayarları tarafından etkilenmez.  
  
 Kullanıcı VSTO eklentileri kullanarak yüklenmesini engeller, **Güven Merkezi**, VSTO eklentileri aşağıdaki türde yüklenmez:  
  
- Yönetilen ve yönetilmeyen COM, VSTO eklentileri.  
  
- Yönetilen ve yönetilmeyen belgeler.  
  
- Yönetilen ve yönetilmeyen Otomasyon VSTO eklentileri.  
  
- Yönetilen ve yönetilmeyen gerçek zamanlı veri bileşenleri.  
  
  Aşağıdaki yordamlar, kullanıcıların nasıl kullanabileceğinizi açıklar **Güven Merkezi** VSTO eklentileri yüklenirken Microsoft gelen kısıtlamak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve Microsoft Office 2010. Bu yordamlar, VSTO eklentileri veya Visual Studio'da Office geliştirme araçlarını kullanarak oluşturulan özelleştirmeleri etkilemez.  
  
#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice15shortvstoincludesoffice-15-short-mdmd-applications"></a>VSTO eklentilerinde Microsoft Office 2010 ve Microsoft devre dışı bırakmak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uygulamaları  
  
1.  Seçin **dosya** sekmesi.  
  
2.  Seçin *ApplicationName* **seçenekleri** düğmesi.  
  
3.  Kategorileri bölmesinde **Güven Merkezi**.  
  
4.  Ayrıntılar bölmesinde **Güven Merkezi Ayarları**.  
  
5.  Kategorileri bölmesinde **eklentileri**.  
  
6.  Ayrıntılar bölmesinde seçin **gerektiren uygulama güvenilen bir yayımcı tarafından imzalanmalıdır eklentileri** veya **tüm uygulama eklentileri devre dışı**.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümleri güvenliğini sağlama](../vsto/securing-office-solutions.md)  
  
  