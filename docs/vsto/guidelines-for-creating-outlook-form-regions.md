---
title: Outlook form bölgeleri oluşturma yönergeleri
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 535ab0329412b261b06fb2d04daefe817299dbe9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892018"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Outlook form bölgeleri oluşturma yönergeleri
  Aşağıdaki bilgiler, form bölgeleri en iyi duruma getirmek ve olası sorunları önlemenize yardımcı olabilir:  
  
- [Form bölgesi adlarını kullanın](#UsingFormRegions).  
  
- [Form bölgesi devralmayı devre dışı bırak](#DisablingInheritance).  
  
- [İleti sınıf adları ve türlerini anlamanız](#ClassNames).  
  
- [Form bölgeleri okuma bölmesi için bitişik tasarım](#ReadingPane).  
  
- [En iyi simgesi boyutlarını kullanın](#UsingOptimal).  
  
  Form bölgeleri hakkında daha fazla bilgi için bkz. [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
##  <a name="UsingFormRegions"></a> Form bölgesi adlarını kullanın  
 Form bölgesini tanımlamak için kullanılan birkaç ad vardır. Bu adlar ve form bölgesini nasıl etkilediklerini arasındaki farkı anlamak önemlidir. Aşağıdaki tabloda, her ad açıklanmaktadır.  
  
|Form bölgesi adı|Açıklama|  
|----------------------|-----------------|  
|Form bölgesi öğesi adı|İçin belirttiğiniz ad **Outlook Form bölgesi** öğesi **Yeni Öğe Ekle** iletişim kutusu. Görüntülenen form bölgesi kod dosyası adıdır **Çözüm Gezgini**.|  
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> Özelliği|Bu adla belirlediğiniz **açıklayıcı metni sağlayın ve görüntüleme tercihlerinizi seçin** sayfasının **yeni Outlook Form bölgesi** Sihirbazı. Bu ad olarak görünür **FormRegionName** özelliğinde **özellikleri** penceresi.<br /><br /> Kullanım <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> özelliğini form bölgesinin Outlook kullanıcı arabiriminde (UI) tanımlayan etiketi belirtin. Ayrı form bölgeleri için Outlook öğesinin şeridinde düğme olarak bu ad görünür.<br /><br /> Bitişik form bölgeleri için bu ad, yukarıdaki form bölgesinin üst bilgi metni olarak görünür.|  
|`Microsoft.Office.Tools.Outlook.FormRegionName` Özniteliği|Eklediğinizde bir **Outlook Form bölgesi** öğesi projeye, Visual Studio bu özelliğe form bölgesinin tam olarak nitelenmiş adını ayarlar. Varsayılan tam adı, VSTO Eklentisi adı noktayla form bölgesinin adına bağlı. — Örneğin, `OutlookAddIn1.FormRegion1`.<br /><br /> Bu tam adı da form bölgesi fabrikası sınıfının üst özniteliği olarak görünür.<br /><br /> Kullanım `Microsoft.Office.Tools.Outlook.FormRegionName` form bölgesinin tüm Outlook VSTO eklentileri arasında benzersiz olarak tanımlamak için öznitelik. Değerini değiştiremezsiniz `Microsoft.Office.Tools.Outlook.FormRegionName` öznitelik form bölgesi öğesinin yeniden adlandırılması veya değiştirerek <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> özelliği. Bu adını değiştirmek için değiştirmelisiniz `Microsoft.Office.Tools.Outlook.FormRegionName` form bölgesi kod dosyasında özniteliği.|  
  
##  <a name="DisablingInheritance"></a> Form bölgesi devralmayı devre dışı bırak  
 Varsayılan olarak, bir özel ileti sınıf temel ileti sınıfının tüm form bölgesi ilişkilendirmelerini devralır. Örneğin, bir ileti sınıfı adı `IPM.Task.Contoso` türetildiği `IPM.Task`. Bu nedenle, `IPM.Task.Contoso` form bölgesi ilişkilendirmelerini devralan `IPM.Task`.  
  
 Türetilen ileti sınıflarından ile ilişkilendirilecek form bölgesinin istemiyorsanız ayarlamak <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> özelliği için form bölgesinin **true**. Örneğin, bitişik bir form bölgesi ile ilişkilendirirseniz `IPM.Task` ve <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> özelliğini **true**, form bölgesi yalnızca standart görev formun altına eklenir. Form bölgesini standart görev formuna özelleştirilmiş tüm sürümlerini altına eklenmemiş.  
  
##  <a name="ClassNames"></a> Türleri ve ileti sınıf adları anlama  
 Bir Outlook öğesinin tür adı, bir Outlook öğesinin ileti sınıf adından farklıdır. Örneğin, bir RSS öğesinin tür adı olan `Microsoft.Office.Interop.Outlook.PostItem`. Bir RSS öğesinin ileti sınıfı adı `IPM.Post.RSS`.  
  
 Kod bir Outlook öğesindeki başvurmak için tür adı kullanın. Tür adları listesi için bkz. [form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
 Outlook öğelerinde ileti sınıfı adını kullanın **yeni Outlook Form bölgesi** öğesi form bölgesi ile ilişkilendirmek için Sihirbazı. Geçerli ileti sınıf adları listesi için bkz. [form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
##  <a name="ReadingPane"></a> Bitişik form bölgeleri okuma bölmesi için Tasarım  
 Outlook öğesine öğesi açmadan önizlemek için Outlook Okuma Bölmesi'ni kullanabilirsiniz. Okuma bölmesi, yalnızca okumak için tasarlanmıştır. Bu nedenle, bir metin kutusu gibi bitişik bir form bölgesi ekleme giriş denetimlerinin ne zaman beklendiği gibi çalışmayabilir öğesi ve form bölgesi Okuma Bölmesi'nde açın.  
  
 Örneğin, bitişik bir form bölgesi olan bir öğe Okuma Bölmesi'nde açık ise, aşağıdaki durum mümkündür:  
  
1. Form bölgesi üzerinde olan textbox içindeki metin seçin.  
  
2. Tuşuna **Sil**.  
  
3. Tüm posta öğesini metin yerine silinir.  
  
   Giriş denetimlerinin bitişik bir form bölgesi tasarlıyorsanız, denetimleri düzgün çalıştığından emin olmak için Okuma Bölmesi'nde test edin. Beklendiği gibi davranmaya olmayan denetimleri devre dışı bırakan özel kod eklemeyi düşünün.  
  
   Alternatif olarak, ayarlayabileceğiniz <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> özelliği için form bölgesinin **False**. Böylece form bölgesinin Okuma Bölmesi'nde kullanılamaz.  
  
##  <a name="UsingOptimal"></a> En iyi simgesi boyutlarını kullanın  
 Hangi simgelerin simge özellik ayarlayarak görüntülemek için form bölgesinin istediğiniz belirtebilirsiniz **simgeler** özellik grubu **özellikleri** penceresi. En iyi görsel kaliteyi elde etmek için aşağıdaki yönergeleri kullanın:  
  
- İçin **sayfa** simgesi, Taşınabilir Ağ Grafikleri (PNG) dosyasını kullanın.  
  
- **Pencere** simgeler 32 x 32 piksel olmalıdır.  
  
- Diğer tüm simgeleri 16 x 16 piksel olmalıdır.  
  
  **Sayfa** Inspector ayrı, değiştirme ve tümünü değiştirme form bölgesi olan öğeler için Şeritteki simgesi görünür.  
  
  **Penceresi** simgesi görünür bildirim alanında hem de **Alt**+**sekmesini** Aç iletişim kutusu, görüntü değiştirme veya tümünü değiştirme form öğeleri bölgeleri.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  