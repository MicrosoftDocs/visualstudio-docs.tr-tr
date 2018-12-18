---
title: DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: ccfb4fa9de6513ecc36cad7156117d70879fca2e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814934"
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>DSL Kitaplığı Kullanarak DSL'ler Arasında Sınıfları Paylaşma
Visual Studio Görselleştirme ve modelleme SDK'si, başka bir DSL alabilir tamamlanmamış bir DSL tanımını oluşturabilirsiniz. Bu, benzer modeller ortak bölümlerini faktörü sağlar.

## <a name="creating-and-using-dsl-libraries"></a>DSL kitaplığı kullanarak ve oluşturma

#### <a name="to-create-a-dsl-library"></a>DSL kitaplığı oluşturmak için

1.  Yeni bir DSL projesi oluşturun ve DSL kitaplığı çözüm şablonu seçin.

     Tek bir DSL projesi ile boş bir model oluşturulur.

2.  Etki alanı sınıfları, ilişkilerini, Şekil vb. ekleyebilirsiniz.

     Kitaplık öğelerinde, tek bir gömme ağacı oluşturmak sahip değilsiniz.

     Importers kullanabileceğiniz bir ilişki tanımlamak için iki alan sınıfı oluşturun ve bunlar arasında ilişki oluşturun.

     Ayarlamayı düşünün **devralma değiştiricisi** için etki alanı sınıflarının `Abstract`.

3.  DSL Gezgini bağlantı oluşturucular gibi tanımlayan öğeler ekleyebilirsiniz.

4.  Doğrulama kısıtlamaları gibi ek kod gerektiren özelleştirmeler ekleyebilirsiniz.

5.  Tıklayın **tüm şablonları dönüştürme**.

6.  Projeyi oluşturun.

7.  DSL kullanılacak diğer kişiler için dağıttığınızda, hem derlemede (DLL) hem de dosyanın sağlamalıdır `DslDefinition.dsl`. Derlenmiş bütünleştirilmiş kod klasörü altında bulabilirsiniz `Dsl\bin\*`

#### <a name="to-import-a-dsl-library"></a>DSL kitaplığı içeri aktarmak için

1. Başka bir DSL tanımındaki içinde **DSL Gezgini**DSL kök sınıfının sağ tıklayın ve ardından **ekleme yeni DslLibrary alma**.

2. Özellikler penceresinde ayarlayın **dosya yolu** kitaplığı. Bir göreli veya mutlak bir yol kullanabilirsiniz.

    İçeri aktarılan kitaplık salt okunur modda DSL Gezgini'nde görünür.

3. İçeri aktarılan sınıflar temel sınıf olarak kullanabilirsiniz. İçeri aktarma DSL içinde alan sınıfı oluşturun ve Özellikler penceresinde ayarlayın **temel sınıf** içeri aktarılan bir sınıf.

4. Tüm Şablonları Dönüştür tıklayın.

5. DSL kitaplığı proje tarafından oluşturulan derleme (DLL) başvuru DSL projeye ekleyin.

6. Çözümü oluşturun.

   DSL kitaplığı diğer tür kitaplıklarını içeri aktarabilirsiniz. Bir kitaplığı içeri aktardığınızda, içeri aktarmalarından DSL Gezgini'nde da otomatik olarak görünür.

## <a name="see-also"></a>Ayrıca Bkz.

- [Nasıl yapılır: Etki Alanına Özgü bir Dili Tanımlama](../modeling/how-to-define-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
