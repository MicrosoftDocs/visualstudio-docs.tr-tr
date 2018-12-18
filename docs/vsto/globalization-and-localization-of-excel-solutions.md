---
title: Genelleştirme ve yerelleştirme Excel çözümleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], configuring
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ade59e757778ac7858732f5bf9880b9f88eacd69
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39567472"
---
# <a name="globalization-and-localization-of-excel-solutions"></a>Genelleştirme ve yerelleştirme Excel çözümleri
  Bu bölüm Windows ayarları İngilizce dışındaki bilgisayarlarda çalışan Microsoft Office Excel çözümleri ilgili özel konular hakkında bilgi içerir. Diğer Visual Studio kullanarak çözüm türlerini oluşturduğunuzda karşılaşabileceğinizi birçok yönden Genelleştirme ve yerelleştirme Microsoft Office çözümleri aynı değildir. Genel bilgi için bkz. [Globalize ve uygulamalarını yerelleştirme](/visualstudio/ide/globalizing-and-localizing-applications).  
  
 Varsayılan olarak, Microsoft Office Excel çalışma konak denetimleri düzgün Windows bölgesel ayarda herhangi geçirilen veya kullanılarak tüm verileri yönetilen kod sürece biçimlendirme İngilizce (Amerika Birleşik Devletleri) kullanılarak biçimlendirildiğinde. ' İ hedefleyen projelerde [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] veya [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], bu davranış, ortak dil çalışma zamanı tarafından (CLR) denetlenir.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="format-data-in-excel-with-various-regional-settings"></a>Excel verileri biçimlendirme çeşitli bölgesel ayarları  
 Yerel ayar duyarlı, tarihleri ve İngilizce (Amerika Birleşik Devletleri) veri biçimi (yerel ayar kimliği 1033), önce kullanarak para birimi gibi Microsoft Office Excel için geçti veya kod Office projenizdeki verileri okuyabilir biçimlendirme olan tüm verileri biçimlendirmeniz gerekir.  
  
 Office çözümünü Visual Studio'da geliştirirken, varsayılan olarak, Excel nesne modeli (Bu da yerel ayar kimliği1033 nesne modelinde kilitleme adlandırılır) yerel kimliği1033 veri biçimlendirme bekliyor. Bu davranış, Visual Basic uygulamalar için uygun yolu eşleşir. Ancak, Office çözümlerinde bu davranışı değiştirebilirsiniz.  
  
### <a name="understand-how-the-excel-object-model-always-expects-locale-id-1033"></a>Excel nesne modeline her zaman yerel kimliği1033 bekliyor nasıl anlama  
 Varsayılan olarak, Visual Studio kullanılarak oluşturulan Office çözümlerini son kullanıcının yerel ayarları tarafından etkilenmez ve her zaman yerel ayarı İngilizce (Amerika Birleşik Devletleri) olsa gibi davranır. Örneğin, get veya set <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> özelliğindeki, verileri yerel ayar kimliği 1033 bekliyor şekilde biçimlendirilmelidir. Farklı veri biçimi kullanırsanız, beklenmeyen sonuçlar alabilirsiniz.  
  
 Geçirilen veya yönetilen kod tarafından yönetilen veri için İngilizce (Amerika Birleşik Devletleri) biçimini kullanıyor olsanız da Excel yorumlar ve verileri doğru şekilde son kullanıcının yerel ayarına göre görüntüler. Yönetilen kodun yerel ayar kimliği1033 verileri İngilizce (ABD) olduğunu gösterir verileriyle birlikte biçimi geçirir ve kullanıcının yerel ayarı eşleştirilecek biçimlendirilmeli çünkü Excel verileri doğru şekilde biçimlendirebilirsiniz.  
  
 Örneğin, son kullanıcıların kendi Bölgesel Seçenekler Almanca (Almanya) yerel ayarını varsa, bu şekilde Biçimlendirilecek tarih 29 Haziran 2005 beklediği: 29.06.2005. Ancak, çözümünüzü Excel dize olarak tarihi geçerse, tarihe göre İngilizce (Amerika Birleşik Devletleri) biçimi biçimlendirmeniz gerekir: 6/29/2005. Hücrenin tarih hücresi olarak biçimlendirilmişse Excel tarihini Almanca (Almanya) biçiminde görüntüler.  
  
### <a name="pass-other-locale-ids-to-the-excel-object-model"></a>Excel nesne modeline diğer yerel ayar kimlikleri geçirme  
 Ortak dil çalışma zamanı (CLR), tüm yöntemler ve yerel ayar duyarlı verileri kabul eden özellikleri Excel nesne modelinde 1033 yerel ayar Kimliğini otomatik olarak geçirir. Nesne modelini tüm çağrıları için otomatik olarak bu davranışı değiştirmek için hiçbir yolu yoktur. Belirli bir yöntem kullanarak farklı bir yerel ayar kimliği ancak geçirebilirsiniz <xref:System.Type.InvokeMember%2A> yöntemini çağırmak için ve yerel ayar kimliği için geçirerek *kültür* yönteminin parametresi.  
  
## <a name="localize-document-text"></a>Belge metninin yerelleştirme  
 Belge, şablonu veya projenizdeki çalışma kitabı büyük olasılıkla derlemeden ayrı olarak yerelleştirilmiş ve yönetilen kaynakları olması gereken statik metin içerir. Bunu yapmak için basit bir yol, belgenin bir kopyasını alın ve Microsoft Office Word veya Microsoft Office Excel kullanarak metni Çevir sağlamaktır. Kod, hiçbir değişiklik olsa bile herhangi bir sayıda belgeleri aynı derlemeye bağlanabilir olduğundan bu işlem çalışır.  
  
 Yine de herhangi bir bölümünü belge metninin ile etkileşime giren kodunuzun metin ve adlandırılmış aralıklar, bu yer işaretleri diliyle eşleşiyor devam eder ve tüm gerekli Office belgesinin biçimlendirme diğer görünen alanları uyum emin olmanız gerekir farklı dil bilgisi ve metin uzunluğu için ayarlayın. Görece küçük metin içeren belge şablonları için kaynak dosyalarında metin depolamak ve ardından metni çalışma zamanında yükleme düşünmek isteyebilirsiniz.  
  
### <a name="text-direction"></a>Metin yönü  
 Excel'de, sağdan sola metin işlemek için çalışma özelliği ayarlayabilirsiniz. Konak denetimleri veya sahip herhangi bir denetime bir `RightToLeft` tasarımcıda otomatik olarak yerleştirilen özelliği, bu ayarlar çalışma zamanında eşleşmesi. Word belge ayarı (yalnızca değiştirmeniz, metin hizalamasını), iki yönlü metin yok denetimler için bu ayarı eşlenemez bu nedenle. Bunun yerine, her denetim için metin hizalamasını ayarlamanız gerekir. Tüm denetimleri yol ve bunları sağdan sola metin işlemek için zorlamak için kod yazmak mümkündür.  
  
### <a name="change-culture"></a>Kültürü değiştirme  
 İçin her şey bu iş parçacığı üzerinde çalışan iş parçacığı kültürü için yaptığınız tüm değişiklikler etkiler, belge düzeyinde özelleştirme kodunuzun ana UI iş parçacığı Excel, genellikle paylaşır; değişiklik özelleştirmeniz için sınırlı değildir.  
  
 Windows Forms denetimleri, uygulama düzeyinde VSTO eklentileri konak uygulama tarafından başlatılan önce başlatılır. Bu gibi durumlarda, kullanıcı Arabirimi denetimleri ayarlamadan önce kültürü değiştirilmelidir.  
  
## <a name="install-the-language-packs"></a>Dil paketlerini yükleme  
 Windows için İngilizce olmayan ayarları varsa, yükleyebileceğiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] görmek için dil paketlerini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Windows ile aynı dilde iletileri. Tüm son kullanıcılar, Windows için İngilizce olmayan ayarlarla çözümlerinizi çalıştırırsanız, bunlar Windows aynı dilde çalışma zamanı mesajlarını görmek için doğru dil paketi yüklü olmalıdır. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Dil paketlerini web'da [Microsoft İndirme Merkezi](http://www.microsoft.com/downloads).  
  
 Ayrıca, .NET Framework yeniden dağıtılabilir dil paketleri için ClickOnce iletileri gereklidir. .NET Framework dil paketleri kullanılabilir [Microsoft İndirme Merkezi](http://www.microsoft.com/downloads).  
  
## <a name="regional-settings-and-excel-com-calls"></a>Bölgesel ayarlar ve Excel COM çağrıları  
 Yönetilen bir istemci bir COM nesnesi üzerinde bir yöntemi çağırır ve kültüre özgü bilgileri geçirmek ihtiyacı olduğunda, bunu kullanarak yaptığı <xref:System.Globalization.CultureInfo.CurrentCulture%2A> (yerel), geçerli iş parçacığı yerel ayarı eşleşir. Geçerli iş parçacığı yerel ayarı varsayılan olarak kullanıcının bölgesel ayarları devralınır. Ancak, Excel nesne modeline çağrı Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan bir Excel çözümünden yapmak, İngilizce (Amerika Birleşik Devletleri) veri biçimi (yerel ayar kimliği 1033) Excel nesne modeline otomatik olarak geçirilir. Microsoft Office Excel geçirin veya proje kodunuzdan verileri okumak için önce İngilizce (Amerika Birleşik Devletleri) veri biçimi kullanarak tarihleri ve para birimi gibi yerel ayar duyarlı biçimlendirme olan tüm verileri biçimlendirmeniz gerekir.  
  
## <a name="considerations-for-storing-data"></a>Veri depolamak için dikkat edilmesi gerekenler  
 Verilerinizi doğru olarak yorumlanır ve görüntülenen, bir uygulama içinde dize değişmez değerleri Excel çalışma sayfası formülleri gibi verileri depolarken sorunlar oluşabilir düşünmelisiniz emin olmak için (yerine kesin olarak belirlenmiş nesneler kodlanmış). Bir kültür sabit veya İngilizce (Amerika Birleşik Devletleri) (LCID değer 1033) stili varsayılarak biçimlendirilmiş veri kullanmanız gerekir.  
  
### <a name="applications-that-use-string-literals"></a>Dize değişmez değerleri kullanan uygulamalar  
 Sabit kodlanmış olabilir olası değerler, İngilizce (Amerika Birleşik Devletleri) biçimi ve yerelleştirilmiş işlev adlarını içeren Excel çalışma sayfası formüller yazılan tarih sabit değerleri içerir. Diğer bir olasılık "1,000" gibi bir sayı içeren bir sabit kodlanmış bir dize olabilir Bazı kültürlerin Bu bin yorumlanır, ancak diğer kültürde bu bir noktası sıfır temsil eder. Hesaplamaları ve yanlış biçim yapılan karşılaştırmalar yanlış veri kaybına neden.  
  
 Excel dizesiyle dizeleri geçirilen LCID uygun olarak yorumlar. Dize biçimi geçirilen LCID karşılık gelmiyorsa bu bir sorun olabilir. Excel çözümlerini Visual Studio'da Office geliştirme araçları kullanılarak oluşturulan tüm veri geçirirken LCID 1033'tür (en-US) kullanın. Excel verileri Excel kullanıcı arabirimi dili ve bölgesel ayarlarına göre görüntüler. Visual Basic for Applications (VBA) de bu şekilde çalışır; dizeleri en-US biçimlendirilir ve VBA, neredeyse her zaman 0 (dil belirsiz) LCID geçirir. Örneğin, aşağıdaki VBA kodu, doğru biçimlendirilmiş bir değer Mayıs 12, 2004 için geçerli kullanıcı yerel ayarı uygun olarak görüntüler:  
  
```vb
'VBA  
Application.ActiveCell.Value2 = "05/12/04"  
```  
  
 Tarihi en-US stilinde biçimlendirildiğinde aynı sonuçları Excel'e COM birlikte çalışması yoluyla geçirilen ve Visual Studio'da Office geliştirme araçları kullanılarak oluşturulmuş bir çözümü kullanıldığında aynı kodu üretir.  
  
 Örneğin:  
  
 [!code-vb[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#6)]
 [!code-csharp[Trin_VstcoreCreatingExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#6)]  
  
 Kesin türü belirtilmiş veri dize değişmez değerleri mümkün olduğunda yerine ile çalışması gerekir. Örneğin, bir dize sabit değeri bir tarih depolamak yerine olarak depolamak bir <xref:System.Double>, onu şöyle dönüştürün bir <xref:System.DateTime> işleme için nesne.  
  
 Aşağıdaki kod örneği, bir kullanıcı A5 hücreye girer, olarak depolayan bir tarihi alır bir <xref:System.Double>, kendisine dönüştürür bir <xref:System.DateTime> hücresinde A7 görüntülemek için nesne. Tarih görüntüleme için hücre A7 biçimlendirilmiş olması gerekir.  
  
 [!code-vb[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#7)]
 [!code-csharp[Trin_VstcoreCreatingExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#7)]  
  
### <a name="excel-worksheet-functions"></a>Excel çalışma sayfası işlevleri  
 Çalışma sayfası işlev adlarını Excel çoğu dil sürümleri için dahili olarak çevrilir. Ancak, olası dil ve COM birlikte çalışma sorunları nedeniyle, kodunuzda yalnızca İngilizce işlev adlarını kullanmanız önerilir.  
  
### <a name="applications-that-use-external-data"></a>Dış veriler kullanan uygulamalar  
 En-US yanı sıra herhangi bir biçimde kullanarak bu tür dosyaları dışarı aktardıysanız açar veya aksi takdirde eski bir sistemden dışarı virgülle ayrılmış değerler (CSV dosyaları) dosyaları gibi dış veri kullanan herhangi bir kod da etkilenebilir. Veritabanı dize olarak tarihleri depolar ya da ikili biçimi kullanmayan işlemleri gerçekleştirir sürece tüm değerleri ikili biçimde olmalıdır çünkü veritabanı erişimi etkilenmeyebilir. Ayrıca, Excel verilerini kullanarak SQL sorguları oluşturmak, en-US biçiminde kullanmanızı işlevi bağlı olarak olduklarından emin olmak gerekebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: Office Çok Dilde Kullanıcı arabirimini hedefleme](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)   
 [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md)  
  
  