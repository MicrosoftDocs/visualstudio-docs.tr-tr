---
title: Bir simgenin veya Dekoratörün görünürlüğünü denetleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4befc49fab1d1b53d70f1b79ee1a2bbe96be11f1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913416"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir Simgenin veya Dekoratörün Görünürlüğünü Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *dekoratör* bir simge ya da bir etki alanına özgü dil (DSL) şeklinde görünen metin satırı. Dekoratör görünmesi ve modelinde özelliklerini durumuna bağlı olarak kaybolur. Örneğin, bir kişiyi temsil eden bir şekli üzerinde alt sayıda kişinin cinsiyet bağlı olarak görünür ve benzeri farklı simgeler olabilir.  
  
## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Bir simgenin veya dekoratörün görünürlüğünü denetleme  
 Aşağıdaki yordam, zaten bir şekli ve kendi eşleme için bir alan sınıfına tanımladığınız varsayar. Daha fazla bilgi için [etki alanına özgü bir dili tanımlama nasıl](../modeling/how-to-define-a-domain-specific-language.md).  
  
#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Bir simge veya metin dekoratörün görünürlüğünü denetleme için  
  
1. DSL tanım diyagramı simgeler veya görünmesini istediğiniz metin dekoratörleri şekli sınıfına ekleyin.  
  
   1.  Şekil sınıfı sağ tıklatın, **Ekle**ve ardından dekoratör gerekli türüne tıklayın.  
  
   2.  Dekoratörün ait ayarlamak **konumu** özelliği. Aynı konumda birden fazla dekoratöre sahip olabilir. Örneğin erkek aynı konum paylaşımı kadın için simgeler olabilir.  
  
   3.  Ayarlama **varsayılan simge** bir simge dekoratörünün özelliği.  
  
2. Şekil sınıfı DSL tanım diyagramı üzerinde alan sınıfı arasındaki gri çizgidir diyagram öğesi eşlemesi'ni seçin.  
  
3. DSL Ayrıntıları penceresinde de **Dekoratör eşlemeleri** sekmesinde, bir dekoratör seçin. Örneğin, MaleDecorator.  
  
4. Denetleme **görünürlük filtresini** kutusu.  
  
5. Hemen etki alanı sınıfı üzerinde görünürlük kontrol domain özelliği ise bırakın **filtre özelliğinin yolu** boş.  
  
    Aksi takdirde, açılan menüsüne tıklayın ve ilişki veya özelliği olduğu sınıf gidin.  
  
   -   Bir hata raporu önlemek için ile işaretlenmiş bir ilişki gezinmek değil "*" Gezinti aracında.  
  
6. Ayarlama **filtre özelliği** bir alan özelliği için. Örneğin, cinsiyeti.  
  
7. İçinde **görünürlük girdileri** listesinde, bu etki alanı özelliğinin dekoratörün görünür olacağı değerleri ekleyin. Örneğin, erkek.  
  
8. Her simge için adımları yineleyin.  
  
9. **Tüm Şablonları dönüştürme**, derleme ve çalıştırma ve test diyagramı açın.  
  
10. Denetleme özellik değeri değiştiğinde dekoratörler kaybolur ve görünür.  
  
    Sık, daha karmaşık bir formül daha basit bir değerler kümesi tarafından denetlenmesi için görünürlük istersiniz. Örneğin, belirli türde bir bağlantı sayısına bağlı olarak bir simgesi vardır ya da bir olup olmadığına göre bağlı sağlamak için belirli bir aralıkta bir sayı olabilir. Bu durumda, aşağıdaki yordamı kullanın.  
  
#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Bir formüle göre bir dekoratörün görünürlüğünü denetleme için  
  
1.  Hesaplanan alan özelliği için etki alanı sınıfı ekleyin. İçinde **özellikleri** penceresinde aşağıdaki değerleri ayarlayın:  
  
     **IsBrowsable =**`False`**-bu özellik kullanıcıdan gizler**  
  
     **Tür =**`Calculated`**-bu değeri hesaplar kod sağlayacak anlamına gelir.**  
  
     **Adı** örneğin **DecoratorControl**  
  
     **Türü** = `Boolean`  
  
     Daha fazla bilgi için [hesaplanan ve özel depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).  
  
2.  Yeni özellik dekoratör görünürlüğünü denetleme yapın.  
  
    1.  Etki alanı sınıfı gri satırından şeklin olduğu diyagram öğesi eşlemesi'ni seçin. İçinde **DSL ayrıntıları** penceresini açık **DecoratorMap** sekmesi.  
  
    2.  Denetleme **görünürlük filtresini** kutusu.  
  
    3.  İçinde **filtre özelliği**, denetim özelliği seçin **DecoratorControl**.  
  
    4.  Altında **görünürlük girdileri**, girin `True`.  
  
3.  Tıklayın **tüm Şablonları Dönüştür** Çözüm Gezgini araç.  
  
4.  Tıklayın **Çözümü Derle** üzerinde **derleme** menüsü.  
  
5.  Göründü hata raporuna çift tıklayın: "*YourClass* bir için GetDecoratorControlValue neobsahuje platnou definici...".  
  
     Metin Düzenleyici üzerinde Dsl\GeneratedCode\DomainClasses.cs açılır. Vurgulanan hata bir yöntem eklemek için istek bir açıklamadır.  
  
6.  Ad alanı, sınıf ve metod eksik olan unutmayın.  Örneğin, Company.FamilyTree.Person.GetDecoratorControlValue().  
  
7.  Ayrı kod dosyasında, eksik yöntemi içeren kısmi sınıf tanımını yazın. Örneğin:  
  
    ```  
    namespace Company.FamilyTree  
    { partial class Person  
      { bool GetDecoratorControlValue()  
        {  
          return this.Children.Count > 0;  
    } } }  
    ```  
  
     Program kodunda modeli özelleştirme hakkında daha fazla bilgi için bkz. [gezinme ve güncelleştirme Program kodundaki modeli](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
8.  Yeniden oluşturun ve çözümü çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekiller ve bağlayıcıları tanımlama](../modeling/defining-shapes-and-connectors.md)   
 [Diyagram üzerinde arka plan görüntüsü ayarlama](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Gezinme ve Program kodundaki modeli güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Etki Alanına Özgü Dili Özelleştirmek için Kod Yazma](../modeling/writing-code-to-customise-a-domain-specific-language.md)



