---
title: UML modelleri için standart stereotipler | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1fcc876a847429c0de9600a5a727b19334819119
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51763237"
---
# <a name="standard-stereotypes-for-uml-models"></a>UML modelleri için standart stereotipler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okuyucu veya makine işlemek için ek bilgi sağlamak için UML model öğelerine stereotipler ekleyebilirsiniz. Stereotipler profillerinde tanımlanır ve her bir profil stereotipler sunmaktadır. Birkaç profil, Visual Studio ile sağlanır. Ayrıca, kendi stereotipler içerebilir kendi profilinizi tanımlayabilirsiniz. Daha fazla bilgi için [UML genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md).  
  
 Bu özellik, Visual Studio'nun hangi sürümlerinin desteklediğini görmek için bkz: [mimari ve Modelleme Araçları sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="the-standard-profiles"></a>Standart profilleri  
 Bunu yükledikten hemen sonra aşağıdaki profiller Visual Studio'nun desteklenen bir sürümü kullanılabilir.  
  
|Profil|Amaç|  
|-------------|-------------|  
|[UML profili standart L2](#L2)|Bir öğe veya ilişki hakkında ek bilgi eklemek için kullanılan stereotipler standart bir dizi.|  
|[UML profili standart L3](#L3)|Bir öğe veya ilişki hakkında ek bilgi eklemek için kullanılan stereotipler standart bir dizi.|  
|[C# profili](#NetProfile)|Program kodunu temsil eden bir UML modeli bir sınıfı veya diğer öğe düşünüyorsanız, bu C# profilini uygulayarak stereotiplerden bir tanesi gösterebilir.<br /><br /> Bu stereotip özellikleri model öğelere de ekleyin.|  
  
 Yeni bir UML modeli oluşturduğunuzda, L3 ve UML Standart profilleri L2 bağlantıları kaldırmadıysanız modeline bağlıdır.  
  
 Stereotiplerin bu profillerin içinde kullanmak için öncelikle bir paket veya onlara uygulamak istediğiniz öğeleri içeren bir model profili bağlamanız gerekir.  
  
#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Bir profili bir model veya paket bağlamak için  
  
1.  Açık **UML Model Gezgini**. Üzerinde **mimarisi** menüsünde **Windows**ve ardından **UML Model Gezgini**.  
  
2.  Bir paket veya profildeki stereotiplerin isteyeceksiniz tüm öğelerini içeren model bulun.  
  
3.  Paket veya model sağ tıklayın ve ardından **özellikleri**.  
  
4.  İçinde **özellikleri** penceresinde **profilleri** istediğiniz profillerine özelliği.  
  
#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Bir profili ve bir modeli arasındaki bağlantıyı kaldırın veya paket için  
  
1.  UML Model Gezgini'nde, model veya paket sağ tıklayın ve ardından **özellikleri**.  
  
2.  Özellikler penceresinde ayarlayın **profilleri** özelliğine boş.  
  
    > [!NOTE]
    >  Model veya paketin içinde öğelerin hiçbiri bu profilin stereotiplerini kullanıyorsanız yalnızca bir profili kesebilir.  
  
#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Bir model öğesine bir stereotip uygulamak için  
  
1.  Diyagram üzerinde veya buna model öğesine sağ tıklayın **UML Model Gezgini**ve ardından **özellikleri**.  
  
2.  Tıklayın **stereotipler** özelliği ve uygulamak istediğiniz stereotipler seçin.  
  
     «Ayraç» içinde model öğesi çoğu öğe türleri için Seçili stereotipler görünür.  
  
    > [!NOTE]
    >  Göremiyorsanız **stereotipler** özelliği veya istediğiniz stereotip görünmüyorsa, model öğesi bir paket veya model için uygun profili bağlandı içinde olduğundan emin olun.  
  
3.  Bazı stereotipler model öğesi için ek özelliklerin değerlerini ayarlamanıza olanak sağlar. Bu özellikleri görmek için genişletin **stereotipler** özelliği.  
  
###  <a name="L2"></a> UML profili standart L2  
 Profil bağlantısını modelden kaldırılmadığı sürece aşağıdaki stereotipler anlamı, UML model öğelerini özelleştirmek için kullanılabilir.  
  
 Bu stereotipler tam anlamı, modeli işlemek için kullanıyor olabileceğiniz herhangi bir aracı ve kendi yerel kuralları tarafından belirlenir.  
  
|Stereotip|Uygulandığı öğe:|Açıklama|  
|----------------|----------------|-------------|  
|yardımcı|örneği|İlave bir mantık uygulayan başka bir sınıf genellikle destekleyen bir sınıf. Başka bir sınıfın «odak» stereotipi olabilir.|  
|çağrısı|Bağımlılık|Sağlayıcı işlemlerini istemci sınıfı çağırır.|  
|oluşturma|Bağımlılık|İstemci sınıfı, tedarikçi örneklerini oluşturur.|  
|oluşturma|İleti|Gönderen, alıcı oluşturur.|  
|oluşturma|Çalışma|Bu işlem bir oluşturucudur.|  
|türetilen|Bağımlılık|İstemci öğesi tedarikçiden tamamen veya kısmen hesaplanır.|  
|yok|Çalışma|İşlemi kendi örneğini yok eder.|  
|belge|Yapıt|A «file» bir kaynak veya yürütülebilir bir dosya değil.|  
|varlık|Bileşen|Bileşenin iş kavramını temsil eder.|  
|yürütülebilir|Yapıt|«Dosya» yürütülebilir.|  
|dosyası|Yapıt|Fiziksel bir dosya.|  
|odak|örneği|Çekirdek iş mantığını tanımlayan bir sınıf, birkaç «yardımcı» sınıfları tarafından desteklenir.|  
|çerçeve|Paket|Bu paket, yeniden kullanılabilir tasarım desenini tanımlar.|  
|Uygulama|Bileşen|«Belirtimi» uygulanması.|  
|implementationClass|örneği|Sınıfının bir uygulamasını açıklar ve her bir çalışma zamanı örneği bir sabit uygulama sınıfı vardır. «Türüyle» karşılaştırın.|  
|örneği|Bağımlılık|İstemci, tedarikçi örneklerini oluşturur.|  
|kitaplık|Yapıt|«Dosya» bir kitaplık.|  
|metaclass|örneği|Bu sınıfın örnekleri de sınıflardır.|  
|modelLibrary|Paket|İçeri aktarılan paketler tarafından kullanılabilmeleri için amaçlanan model öğelerini içerir. Genellikle bir profilinin bir parçası tanımlanan ve profilinin bir uygulama tarafından otomatik olarak içeri aktarıldı.|  
|process|Bileşen|İşlem tabanlı bir bileşen veya bir iş parçacığı taşır.|  
|gerçekleştirme|Sınıf, arayüz, bileşeni|Bir uygulamayı açıklar.|  
|İyileştir|Bağımlılık|İstemci sınıfı, bileşen veya paket daha tedarikçi belirtiminin ya da tasarımı hakkında daha fazla bilgi sağlar.|  
|Sorumluluk|Bağımlılık|Bağımlılık tedarikçi sonundaki açıklama istemcisi sınıfı ya da bileşene ait Sorumlulukları tanımlar.|  
|betik|Yapıt|Bir yorumlanabilirinde «dosyası».|  
|Gönder|Bağımlılık|Kaynak işlemi ' % s'hedef sinyali gönderir.|  
|hizmet|Bileşen|Durum bilgisi olmayan bir bileşen.|  
|kaynak|Yapıt|Bir derlenebilir «dosyası».|  
|belirtim|Sınıf, arayüz, bileşeni|Dahili olarak şekli tanımlamadan bir bileşen ya da nesne davranışını tanımlar.|  
|Alt sistem|Bileşen|Büyük bir sistemin parçası. Bir alt sisteminde bir kullanım durumu diyagramı, alt stereotip ile bir bileşenidir.|  
|izleme|Bağımlılık|İstemci öğesi tedarikçiyi tasarımının bir parçasıdır. Bu bağımlılık iki ucunu genellikle farklı modeller içindedir. Bu modeller diğer gerçekleştirme biridir.|  
|türü|örneği|Nesnenin davranışını nasıl uygulandığını bildirmeden belirtir. Bir nesne belirtimine uygun bir tür üyesi ise.|  
|yardımcı program|örneği|Statik işlevler koleksiyonu. Sınıfının hiçbir örneği yok.|  
  
###  <a name="L3"></a> UML profili standart L3  
 Modelden profili bağlantılıysa aşağıdaki stereotipler anlamı, UML model öğelerini özelleştirmek için kullanılabilir.  
  
 Bu stereotipler tam anlamı, modeli işlemek için kullanıyor olabileceğiniz herhangi bir aracı ve kendi yerel kuralları tarafından belirlenir.  
  
|Stereotip|Uygulandığı öğe:|Açıklama|  
|----------------|----------------|-----------------|  
|buildComponent|Bileşen|Bir yapı tanımlamak için kullanılan öğeleri koleksiyonu.|  
|metaModel|Model|UML bir değişken gibi bir modelleme dili veya bir etki alanına özgü dil tanımlar.|  
|systemModel|Model|Aynı sistemde, örneğin, bir belirtim, gerçekleştirme ve onlar arasındaki ilişkileri izleme geçerli modellerin bir koleksiyonu bir modeli.|  
  
##  <a name="NetProfile"></a> C# profili  
 Stereotiplerin bu profilde tanımlanan çeviri program kodu için bir model öğesini düşünüldüğünü belirtmenize olanak tanır. Her stereotip ayarlayabileceğiniz model öğesi üzerinde ek özellikleri tanımlar.  
  
 Bu stereotipler kullanılabilir hale getirmek için bir model veya paket için C# profilini bağlayın. Model veya paket model öğelerine stereotipler ardından uygulayabilirsiniz.  
  
 Kullanılabilir stereotipler, öğeler, bunlar geçerlidir ve bunlar kullanılabilir hale getirdiğiniz ek özellikler aşağıdaki tabloda özetlenmiştir.  
  
|Stereotip|Uygulandığı öğe:|Özellikler|  
|----------------|----------------|----------------|  
|**C# sınıfı**|UML sınıfı<br /><br /> Bileşen|**CLR öznitelikleri**<br /><br /> **Kısmen içerir**<br /><br /> **Korumalı**<br /><br /> **Statik**<br /><br /> **Güvenli değildir**<br /><br /> **Paket görünürlüğü**|  
|**C# yapısı**|UML sınıfı<br /><br /> Bileşen|**CLR öznitelikleri**<br /><br /> **Kısmen içerir**<br /><br /> **Güvenli değildir**<br /><br /> **Paket görünürlüğü**|  
|**C# Genel üyeler**|UML sınıfı<br /><br /> Bileşen|**CLR öznitelikleri**|  
|**C# arabirimi**|UML arabirimi|**CLR öznitelikleri**<br /><br /> **Kısmen içerir**<br /><br /> **Paket görünürlüğü**|  
|**C# sabit listesi**|UML numaralandırması|**ClrAttributes**<br /><br /> **Temel tür**|  
|**C# ad alanı**|UML Paket|**CLR öznitelikleri**<br /><br /> **Taban adı**<br /><br /> **Ad alanlarını kullanma**|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md)   
 [Modelinizi profiller ve stereotipler aracılığıyla özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [UML’yi genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)



