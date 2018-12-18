---
title: Bir etki alanına özgü dilden kod oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5edc6e267957f08837399ae5c2e56bce3cc26cce
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232004"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Etki Alanına Özgü Dilden Kod Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../includes/dsl-md.md)] modellerinde temsil verilerden kod, belgeler, yapılandırma dosyalarını ve diğer yapıları üretmek için güçlü bir yol sağlar. Kullanarak [!INCLUDE[dsl](../includes/dsl-md.md)], verilerinizi temsil eden sınıf kümesi oluşturabileceğiniz ve adları sınıflarda metin şablonlarınızı yazabilirsiniz ve özellikleri, bu verileri yansıtır.  
  
 Örneğin, Fabrikam, müşteri adları ve e-posta adreslerini bir XML dosyası vardır. Geliştiricileri, müşteri özellikleri adı ve e-posta ile bir sınıf olan bir modeli oluşturun. Bunlar, bir HTML sayfasının parçası tüm müşteriler tablosunu oluşturan bu parça içeren verileri işlemek için çeşitli metin şablonlarını yazma:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Müşteri veritabanı işlendiğinde, XML dosyasını modeli deposuna okunur. A *yönerge işlemcisi*, kullanılarak oluşturulan [!INCLUDE[dsl](../includes/dsl-md.md)], müşteri sınıfı metin şablonunun kod için kullanılabilir hale getirir. Birçok metin şablonları aynı deponun karşı çalıştırabilirsiniz.  
  
 Metin şablonları için temel [!INCLUDE[dsl](../includes/dsl-md.md)]. VSPackage'ı ve araçlarla tümleştirme gerçekleştirmek için kullanılan denetimler de etki alanı model öğeleri için kaynak kodunu oluşturmak için kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Bu bölümde oluşturmak, değiştirmek ve metin şablonları kullanılan hata ayıklama için yollardan bazılarını ele alınmaktadır [!INCLUDE[dsl](../includes/dsl-md.md)].  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Metin Şablonlarından Modellere Erişme](../modeling/accessing-models-from-text-templates.md)  
  
 Metin şablonlarında etki alanına özgü dil başvurma hakkında temel bilgiler sağlar.  
  
 [İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Bir etki alanına özgü dil başvuran bir metin şablonunda hata ayıklama ve sorun giderme yapılacağını açıklar.  
  
 [İzlenecek yol: Üretilen bir Yönerge İşlemcisine Ana Bilgisayar Bağlama](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Özel bir ana bilgisayar üretilen bir yönerge işlemcisine bağlama açıklar.  
  
 [DslTextTransform Komutu](../modeling/the-dsltexttransform-command.md)  
  
 Etki alanına özgü diller başvuru metin şablonları için komut satırında TextTransform yürütülebilir dosyayı çalıştırır komut dosyası açıklanmaktadır.  
  
## <a name="reference"></a>Başvuru  
 [T4 Metin Şablonu Yazma](../modeling/writing-a-t4-text-template.md)  
  
 Metin şablonu yönergeleri ve denetim blokları söz dizimi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [T4 Metin Şablonları Kullanarak Tasarım Zamanı Kodu Oluşturma](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Metin şablonu dönüştürme süreci açıklanmaktadır.  
  
 [Derleme Sürecinde Kod Oluşturma](../modeling/code-generation-in-a-build-process.md)  
  
 Bir DSL bir yapı sunucusunda gelen dosyaları oluşturuyorsanız bu konuyu okuyun.



