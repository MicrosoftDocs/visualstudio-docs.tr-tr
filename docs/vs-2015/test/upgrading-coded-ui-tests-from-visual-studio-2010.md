---
title: Kodlanmış UI testlerini yükseltme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-devops-test
ms.topic: conceptual
ms.assetid: 11232a83-73ea-46bd-bc0c-46f74f6e3a42
caps.latest.revision: 35
ms.author: gewarren
manager: douge
ms.openlocfilehash: 664eeb618b92b7d3181a223a531aac02e046ab0f
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53055056"
---
# <a name="upgrading-coded-ui-tests-from-visual-studio-2010"></a>Visual Studio 2010'dan Kodlanmış UI Testlerini Yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Test projeleri oluşturulan kodlanmış UI testleri içeren [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 sessizce Visual Studio 2012'de açıldığında onarıldı. Test projeleri kaynak denetimine iade edildiğinden, bu onarım için proje dosyaları kullanıma. Onardıktan sonra bu test kodlanmış UI testleri can içeren projeleri sonra her ikisinde de kullanılması [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 ve [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

 **Gereksinimler**

-   Visual Studio Enterprise

> [!NOTE]
>  Visual Studio, birden fazla test proje türü içerir. Yeni kodlanmış UI testi oluşturursanız, bir kodlanmış UI testi proje türü oluşturulur. Daha fazla bilgi için [Visual Studio'nun önceki sürümleri yükseltme testlerden](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52).

> [!WARNING]
>  [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] Kodlanmış UI testleri içeren test projelerini gerekir yeniden test projesini açtığınızda [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] veya [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yan yana ile [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!WARNING]
>  İçinde oluşturulan bir test projesi [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ve yalnızca birim testleri içeren açılır [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodlanmış UI testleri için eklenemez. Benzer şekilde, oluşturulan birim test projesi kodlanmış UI test ekleyemezsiniz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

## <a name="compatibility-issues-between-visual-studio-2010-and-visual-studio-2012"></a>Visual Studio 2010 ve Visual Studio 2012 arasındaki uyumluluk sorunları
 Aşağıdaki tabloda, geçiş kodlanmış UI testleri arasında dikkat etmeniz sorunlarını listeler [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] ve [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].

> [!CAUTION]
>  Kodlanmış UI test projeleri Çözüm Gezgini'nde görünmeyen başvuruları ile ilgili bilinen bir sorun yoktur. Daha fazla bilgi için dahil Benioku dosyasına bakın [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] yükleme medyası.

|Kodlanmış kullanıcı Arabirimi işlevleri|Sorun|Çözüm|
|----------------------------|-----------|--------------|
|Silverlight UI testi desteklenmiyor. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Yapı başarısız olur**<br /><br /> Varsa [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] özellik paketi 2 ve sahip Silverlight uygulamaları için kodlanmış UI Test projeleri oluşturulan bu projeleri de açılamaz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Bu projeler yönettiğiniz öneririz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yalnızca özellik paketi 2.|
|Firefox UI testi desteklenmiyor. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Derleme başarılı olur, test çalıştırması başarısız olur**<br /><br /> Varsa [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] özellik paketi 2 ve sahip Firefox'ta web uygulamaları için kodlanmış UI Test projeleri oluşturulan bu projeleri de açılamaz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Bu projeler yönettiğiniz öneririz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] yalnızca özellik paketi 2.|
|Yeni kullanıcı Arabirimi kodu test API'leri eklenmiş [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]|**Yapı başarısız olur**<br /><br /> Kodlanmış UI testleri, kullanıcı Arabirimi testi yeni API'yi kullandığınızda oluşturursanız [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], bu proje açılamıyor [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].|Yeni API'yi kullanarak projeleri yönetilmesi gereken [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] yalnızca.|
|İçinde [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], başvuruları csproj dosyasının bir 'Seç' deyiminde içine eklendi. İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodlanmış UI Test bütünleştirilmiş kod başvuruları eklemek için bir geri bildirim hedefler dosyası kullanıyoruz.|İçinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], bir kodlanmış UI testi içinde oluşturulan bir Test projesine eklenemez [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] (veya SP1) bir kodlanmış UI testi içermiyordu.<br /><br /> Onarım işlemini hedefler dosyası ve Seç ifadesi ekler. Kodlanmış UI testi ve Test projesinde değil sonra projeyi onarıldı olarak işaretlenir ve uygun başvuruları eklenmeyecek, kodlanmış UI testi eklerken [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|Kullanarak aynı çözüm içinde yeni bir Test projesi oluşturmanız gerekecektir [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ve yeni kodlanmış UI testi ekleyin. Alternatif olarak, Test projesine kodlanmış UI testleri ekleyebilirsiniz [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1 ve açın, proje içinde [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)].|

##  <a name="UpgradingCodedUIFromVS2010_Update"></a> Visual Studio 2010 SP1 Güncelleştirmesi
 Bir güncelleştirme [!INCLUDE[vs2010](../includes/vs2010-md.md)] adresten SP1 uyumluluk desteği için Visual Studio 2012 ve Windows 8 ile kullanılabilir [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=34677) ve ayrıca Visual Studio olarak güncelleştirin.

 Aşağıdaki güncelleştirme uygulandıktan sonra [!INCLUDE[vs2010](../includes/vs2010-md.md)] kodlanmış UI test aracı özellikleri, Windows 8 için geliştirilir SP1:

- Windows 8 çalıştıran bir bilgisayarda Microsoft .NET Framework 4.5 tabanlı Windows Presentation Foundation (WPF) denetimleri, bir kodlanmış UI testi çalıştırabilirsiniz.

- 64-bit (x 64) Internet Explorer 10 için Windows 8 çalıştıran bir bilgisayarda bir kodlanmış UI testi çalıştırabilirsiniz.

  Güncelleştirme, ayrıca aşağıdaki sorunlar için düzeltmeler içerir:

- **Kod kapsamı:** Visual Studio 2012'de tarafından oluşturulan bir kod kapsamı dosyası (.coverage) açmak için bağlanamama [!INCLUDE[vs2010](../includes/vs2010-md.md)] SP1.

- **Test yapıtlarını stranded:** ekibinizin Team Foundation Server (TFS) 2010 geçersiz bir kullanıcıya atanmış bir test yapıtı sahip. Örneğin, bir kullanıcı şirketten, ancak hala kendisine atanan bir test çalışması içeriyor. TFS 2010 için TFS 2012 yükseltme. Kullandığınız [!INCLUDE[TCMext](../includes/tcmext-md.md)] yükseltilen TFS sunucusuna bağlanmak için 2010. Test yapıtı kullanarak herhangi bir TFS kullanıcıya atamak mümkün değildir [!INCLUDE[TCMext](../includes/tcmext-md.md)] 2010.

- **Yük testi:** bir bilgisayarda yerel alan ağı (LAN) profili dışındaki bir ağ türü ile birlikte bir yük testi çalıştırdığınızda, Windows 8 çalıştıran, ağ öykünücüsü sürücüsü işletim sistemi kilitlenmesine neden olur. Daha fazla ayrıntı için [KB makalesi 2736182](http://support.microsoft.com/kb/2736182).

## <a name="see-also"></a>Ayrıca Bkz.
 [Taşıma, geçirme ve Visual Studio projelerini yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Visual Studio'nun önceki sürümlerinden testleri yükseltme](http://msdn.microsoft.com/en-us/e9c8b7f6-bd72-448e-8edb-d090dcc5cf52) [kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md) [oluşturma bir Kodlanmış UI testi var olan bir eylem kaydından](http://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497) [desteklenen yapılandırmalar ve platformlar için kodlanmış UI testleri ve eylem kayıtları](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
