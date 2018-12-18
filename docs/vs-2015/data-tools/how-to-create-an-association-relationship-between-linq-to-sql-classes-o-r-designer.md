---
title: 'Nasıl yapılır: LINQ to SQL sınıfları (O R Designer) arasında bir ilişkilendirme (ilişki) oluşturma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c739fcf11cec7eb841b99e58b01ada32cfdfd49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209371"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Nasıl yapılır: LINQ to SQL sınıfları (O/R Tasarımcısı) arasında bir ilişki (ilişki) oluşturun
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Varlık sınıfları arasındaki ilişkilendirmeleri [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] veritabanındaki tablolar arasında ilişki benzer. Kullanarak varlık sınıfları arasında ilişkiler oluşturabilirsiniz **ilişkilendirme Düzenleyicisi** iletişim kutusu.  
  
 Kullandığınızda, bir üst ve alt sınıfı seçmelisiniz **ilişkilendirme Düzenleyicisi** ilişkilendirme oluşturmak için iletişim kutusu. Birincil anahtarı içeren varlık sınıfı üst sınıftır; yabancı anahtar içeren varlık sınıfı alt sınıfıdır. Örneğin, Northwind Customers ve Orders tablolarını eşleştiren bir varlık sınıfları oluşturulduysa, müşteri sınıfı üst sınıfın olacaktır ve sipariş sınıfı alt sınıf olur.  
  
> [!NOTE]
>  Tablodan sürüklediğinizde **Sunucu Gezgini**/**veritabanı Gezgini** üzerine [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), ilişkileri otomatik olarak var olan alınarak oluşturulur veritabanında yabancı anahtar ilişkileri.  
  
 O/R Tasarımcısı'nda ilişkilendirme seçtiğinizde bir ilişkilendirme oluşturduktan sonra bazı yapılandırılabilir özellik vardır **özellikleri** penceresi. (Satır ilgili sınıflar arasında bir ilişkilendirmedir.) Aşağıdaki tabloda bir ilişkilendirmenin özellikleri için açıklamalar sağlar.  
  
|Özellik|Açıklama|  
|--------------|-----------------|  
|**önem düzeyi**|Bire çok veya birebir ilişki olup olmadığını denetler.|  
|**Alt özellik**|Bir koleksiyon veya ilişkilendirme yabancı anahtar tarafındaki alt kayıtlara bir başvuru olan üst bir özellik oluşturulup oluşturulmayacağını belirtir. Örneğin, müşteri ve sipariş arasındaki ilişki içinde varsa **alt özellik** ayarlanır **True**, Siparişler adlı bir özellik üst sınıf üzerinde oluşturulur.|  
|**Üst özellik**|İlişkilendirilen üst sınıfa başvuran alt sınıftaki özellik. Örneğin, müşteri ile sipariş arasındaki ilişkide sipariş sınıfını ilişkili müşterinin sipariş başvuran müşteri adlı bir özellik oluşturulur.|  
|**Katılım özellikleri**|İlişki özellikleri görüntüler ve sağlayan bir **üç nokta** yeniden açılır düğmesini (…) **ilişkilendirme Düzenleyicisi** iletişim kutusu.|  
|**benzersiz**|Yabancı hedef sütunların benzersiz bir kısıtlaması olup olmadığını belirtir.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Varlık sınıfları arasında ilişkilendirme oluşturma  
  
1.  İlişkideki üst sınıfın temsil ettiği varlık sınıfı sağ tıklatın, **Ekle**ve ardından **ilişkilendirme**.  
  
2.  Doğrulayın doğru **üst sınıf** seçili **ilişkilendirme Düzenleyicisi** iletişim kutusu.  
  
3.  Seçin **alt sınıf** birleşik giriş kutusundaki.  
  
4.  Seçin **ilişkilendirme özellikleri** sınıfları ilgilidir. Genellikle, bu veritabanında tanımlanan yabancı anahtar ilişkisi eşlenir. Örneğin, müşteriler ve siparişler ilişkilendirme olarak **ilişkilendirme özellikleri** CustomerID her sınıf için olan.  
  
5.  Tıklayın **Tamam** bir ilişki oluşturmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [DataContext yöntemi (O/R Tasarımcısı)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Nasıl yapılır: Birincil Anahtarları Temsil Etme](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

