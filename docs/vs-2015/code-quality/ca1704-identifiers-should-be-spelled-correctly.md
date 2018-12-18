---
title: 'CA1704: Tanımlayıcılar doğru yazılmalıdır | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c1e31917356e3d55a7db38ba7aabc9258af1deb0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49827551"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Tanımlayıcılar doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategori|Microsoft.Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir tanımlayıcı ad Microsoft Yazım kitaplığı tarafından tanınmayan bir veya birkaç sözcük içerir. Bu kural olmayan oluşturucular veya özel adlı üye alma gibi denetleyin ve özellik erişimcileri ayarlayın.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural tanımlayıcısı belirteçlere ayrıştırmak ve her belirtecin yazımını denetler. Ayrıştırma algoritma şu dönüşümleri gerçekleştirir:

- Yeni bir belirteç harfle başlatın. Örneğin, MyNameIsJoe "My", "Name", "Is", "Joe" tokenizes.

- Birden çok büyük harf, yeni bir belirteç son büyük harfle başlar. Örneğin, "GUI", "Düzenleyicisi" GUIEditor tokenizes.

- Baştaki ve sondaki kesme kaldırılır. Örneğin, "sender" için 'sender' tokenizes.

- Alt çizgi, bir belirteç sonunu belirtmek ve kaldırılır. Örneğin, "Hello" Hello_world tokenizes "world".

- Katıştırılmış kodlarına kaldırılır. Örneğin, & mat tokenizes "biçimlendirmek için".

  Varsayılan olarak, yazım denetimcisi (TR) İngilizce sürümü kullanılır. Diğer bir dil sözlükleri şu anda kullanılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için sözcük yazımını düzeltin veya word CustomDictionary.xml adlı bir özel sözlüğüne ekleyin. Sözlük proje dizinine aracının yükleme dizininde veya kullanıcı profili altındaki aracı ile ilişkili dizine yerleştirin (%USERPROFILE%\Application veri\\...). Bir projeye özel sözlük ekleme hakkında bilgi edinmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bkz: [nasıl yapılır: kod çözümleme dizinini özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Sözlük/sözcükleri/Recognized yolunda bir ihlali oluşmamalıdır sözcükler ekleyin.

- Sözlük/sözcükleri/tanınmayan yolunda bir ihlali neden olmamalıdır sözcükler ekleyin.

- Sözlük/sözcükleri/kullanım dışı yolunda geçersiz olarak işaretlenmiş sözcükler ekleyin. İlişkili kural konusuna [CA1726: tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)daha fazla bilgi için.

- Sözlük/kısaltmalar/CasingExceptions yoluna kısaltma büyük/küçük harf kuralları için özel durumlar ekleyin.

  Aşağıdaki özel sözlük dosyası yapısının bir örneğidir.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı yalnızca bilerek yanlış yazılmış bir sözcüktür ve sınırlı bir kitaplık kümesi için Word'ün uyguladığı gösterme. Doğru bir şekilde yazılmış kelimeler yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır.

## <a name="related-rules"></a>İlgili kuralları
 [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)



