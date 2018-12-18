---
title: 'Nasıl yapılır: kod çözümleme dizinini özelleştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8dcc182664832775f2aa3878fb3320e01d3901dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49840109"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi yazım ve dilbilgisi çalışması diğer adlandırma kurallarına göre hataları kodunuzda tanımlayıcıları denetlemek için yerleşik bir sözlük kullanan [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] yönergeleri. Eklemek, kaldırmak veya hüküm ve kısaltmalar yerleşik sözlüğüne kısaltmalar değiştirmek için bir özel sözlük Xml dosyası oluşturabilirsiniz.  
  
 Örneğin, kodunuzu bulunan adlı bir sınıf varsayalım **DoorKnokker**. Kod Analizi adı iki bir kelimelerin bileşik tanımlamak: **kapı** ve **knokker**. Ardından bir uyarı oluşturacak, **knokker** doğru yazıldığından değil. Kod Analizi yazım tanımak için zorlamak için terimi ekleyebilirsiniz **knokker** için özel sözlük.  
  
## <a name="to-create-a-custom-dictionary"></a>Özel bir sözlüğü oluşturmak için  
 Adlı bir dosya oluşturun **CustomDictionary.xml**.  
  
 Aşağıdaki XML yapısını kullanarak özel kelimeleriniz tanımlayın:  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>knokker</Word>  
         </Unrecognized>  
         <Recognized>  
            <Word></Word>  
         </Recognized>  
         <Deprecated>  
            <Term PreferredAlternate=""></Term>  
         </Deprecated>  
         <Compound>  
            <Term CompoundAlternate=""></Term>  
         </Compound>  
         <DiscreteExceptions>  
            <Term></Term>  
         </DiscreteExceptions>  
      </Words>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym></Acronym>  
         </CasingExceptions>  
      </Acronyms>  
   </Dictionary>  
```  
  
## <a name="custom-dictionary-elements"></a>Özel sözlük öğeleri  
 Özel sözlük aşağıdaki öğeleri iç metni olarak koşulları ekleyerek kod çözümleme dizinini davranışını değiştirebilirsiniz:  
  
- [/ Sözcükleri/tanınan/sözcüğü](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)  
  
- [/ Sözcükleri/tanınmayan/sözcüğü](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)  
  
- [Sözlük/sözcükleri/kullanım dışı/terimi [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)  
  
- [Sözlük/sözcükleri/bileşik/terimi [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)  
  
- [Sözlük/sözcükleri/DiscreteExceptions/terimi](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)  
  
- [Sözlük/kısaltmalar/CasingExceptions/kısaltma](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)  
  
###  <a name="BKMK_DictionaryWordsRecognizedWord"></a> / Sözcükleri/tanınan/sözcüğü  
 Bir terim olarak doğru yazıldığından, Kod Analizi tanımlayan koşulları listesinde dahil etmek için bir sözlük/sözcükleri/Recognized/Word öğesinin iç metni terim ekleyin. Koşulları/sözcükleri/Recognized/sözcüğü öğelerinin büyük küçük harfe duyarlı değildir.  
  
 **Örnek**  
  
```  
<Dictionary>  
      <Words>  
         <Recognized>  
            <Word>knokker</Word>  
            ...  
         </Recognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Aşağıdaki kod analizi kuralları için Sözlük/sözcükleri/Recognized düğüm bağlamında uygulanır:  
  
-   [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsUnrecognizedWord"></a> / Sözcükleri/tanınmayan/sözcüğü  
 Bir terim olarak doğru yazıldığından, Kod Analizi tanımlayan koşulları listesinden dışlamak için bir sözlük/sözcükleri/tanınmayan/Word öğesinin iç metni hariç tutmak için terimi ekleyin. Koşulları/sözcükleri/tanınmayan/sözcüğü öğelerinin büyük küçük harfe duyarlı değildir.  
  
 **Örnek**  
  
```  
<Dictionary>  
      <Words>  
         <Unrecognized>  
            <Word>meth</Word>  
            ...  
         </Unrecognized>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Terimleri sözlüğü/sözcükleri/tanınmayan düğümünde, aşağıdaki kod analizi kuralları uygulanır:  
  
-   [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
-   [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)  
  
-   [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Sözlük/sözcükleri/kullanım dışı/terimi [@PreferredAlternate]  
 Kod Analizi, kullanım dışı olarak tanımlayan koşulları listesinde bir terimi eklemek için bir sözlük/sözcükleri/kullanım dışı/terimi öğesinin iç metni terim ekleyin. Kullanım dışı bir terim doğru yazıldığından, ancak kullanılmaması gereken bir word dosyasıdır.  
  
 Uyarıda önerilen alternatif bir terimi eklemek için diğer terimi öğe PreferredAlternate özniteliklerini belirtin. Alternatif önermek istemiyorsanız, öznitelik değeri boş bırakabilirsiniz.  
  
- Sözlük/sözcükleri kullanım dışı terimini/kullanım dışı/terimi öğe büyük küçük harfe duyarlı değildir.  
  
- PreferredAlternate öznitelik değeri büyük/küçük harf duyarlıdır. Baş harfleri büyük bileşik alternatifleri için kullanın.  
  
  **Örnek**  
  
```  
<Dictionary>  
      <Words>  
         <Deprecated>  
            <Term PreferredAlternate="LogOn">login</Term>  
            ...  
         </Deprecated>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Terimleri sözlüğü/sözcükleri/kullanım dışı düğümünde, aşağıdaki kod analizi kuralları uygulanır:  
  
-   [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
-   [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)  
  
###  <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Sözlük/sözcükleri/bileşik/terimi [@CompoundAlternate]  
 Yerleşik sözlük bazı terimi bir bileşik terimi yerine tek ve ayrık terimler olarak tanımlar. Bir terimi bir bileşik sözcük Kod Analizi tanımlayan koşulları listesini dahil etmek ve terimi doğru büyük küçük harfleri belirtmek için terim sözlüğü/sözcükleri/bileşik/terimi öğesinin iç metni ekleyin. Terim öğesinin CompoundAlternate özniteliği bileşik terimi (Pascal harf) kelimeler ilk harfi büyük harf yaparak oluşturan kelimeler belirtin. İç metni belirtilen dönem sözcükleri/sözlük/DiscreteExceptions listesine otomatik olarak eklendiğini unutmayın.  
  
- Sözlük/sözcükleri kullanım dışı terimini/kullanım dışı/terimi öğe büyük küçük harfe duyarlı değildir.  
  
- PreferredAlternate öznitelik değeri büyük/küçük harf duyarlıdır. Baş harfleri büyük bileşik alternatifleri için kullanın.  
  
  **Örnek**  
  
```  
<Dictionary>  
      <Words>  
         <Compound>  
            <Term CompoundAlternate="CheckBox">checkbox</Term>  
            ...  
         </Compound>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Terimleri sözlüğü/sözcükleri/bileşik düğümünde, aşağıdaki kod analizi kuralları uygulanır:  
  
-   [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
-   [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
-   [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
###  <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Sözlük/sözcükleri/DiscreteExceptions/terimi  
 Terimi bileşik sözcüklerin büyük/küçük harf kuralları tarafından iade edildiğinde ayrı word bir terim tek bir kod analizi tanımlayan koşulları listesinden dışlamak için bir sözlük/sözcükleri/DiscreteExceptions/terimi öğesinin iç metni terim ekleyin. Terim sözlüğü/sözcükleri/DiscreteExceptions/dönem öğesinde büyük küçük harfe duyarlı değil.  
  
 **Örnek**  
  
```  
<Dictionary>  
      <Words>  
         <DiscreteExceptions>  
            <Term>checkbox</Term>  
            ...  
         </DiscreteExceptions>  
         ...  
      </Words>  
      ...  
</Dictionary>  
  
```  
  
 Terimleri sözlüğü/sözcükleri/DiscreteExceptions düğümünde, aşağıdaki kod analizi kuralları uygulanır:  
  
-   [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
-   [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
###  <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Sözlük/kısaltmalar/CasingExceptions/kısaltma  
 Bir kısaltma olarak doğru yazılmış kod analizi tanımlayan koşulları listesini dahil etmek ve terimi büyük/küçük harf olarak işaretlendiğinde kısaltması için bileşik sözcüklerin nasıl kuralları belirtmek için terim sözlüğü/kısaltmalar/CasingExceptions iç metni ekleyin. / Öğesini harflendirme. Sözlük/kısaltmalar/CasingExceptions/kısaltması öğesinde kısaltma büyük/küçük harf duyarlıdır.  
  
 **Örnek**  
  
```  
<Dictionary>  
      <Acronyms>  
         <CasingExceptions>  
            <Acronym>NESW</Acronym>   <!-- North East South West -->  
            ...  
         </CasingExceptions>  
         ...  
      </Acronyms>  
      ...  
</Dictionary>  
  
```  
  
 Terimleri sözlüğü/kısaltmalar/CasingExceptions düğümünde, aşağıdaki kod analizi kuralları uygulanır:  
  
-   [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
##  <a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Bir projeye özel sözlük uygulamak için  
  
1.  İçinde **Çözüm Gezgini**, aşağıdaki yordamlardan birini kullanın:  
  
2.  Tek bir projeye bir sözlük eklemek, proje adına sağ tıklayın ve ardından **varolan öğeyi Ekle**. Dosyasında belirtirsiniz **varolan öğeyi Ekle** iletişim kutusu.  
  
3.  İki veya daha fazla projeler arasında paylaşılan bir sözlük eklemek için içinde paylaşmak için dosyayı bulun **varolan öğeyi Ekle** iletişim kutusunda, aşağı oka tıklayın **Ekle** düğmesine ve ardından **bağlantı olarak Ekle** .  
  
4.  İçinde **Çözüm Gezgini**, sağ **CustomDictionary.xml** dosya adı ve tıklatın **özellikleri**.  
  
5.  Gelen **derleme eylemi** listesinden **CodeAnalysisDictionary**.  
  
6.  Gelen **çıkış dizinine Kopyala** listesinden **kopyalamayın**.



