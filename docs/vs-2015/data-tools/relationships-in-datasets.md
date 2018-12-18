---
title: Veri kümelerindeki ilişkiler | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DesignRelation
- vbdata.Microsoft.VSDesigner.DataSource.DesignRelation
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- relationships, about relationships
- datasets [Visual Basic], relationships
- relationships, datasets
ms.assetid: cfe274f0-71fe-40f6-994e-7c7f6273c9ba
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0b138b9ad49a0fd1a406e698aafd121478e95f4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935412"
---
# <a name="relationships-in-datasets"></a>Veri kümelerindeki ilişkiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
İlgili verileri içeren veri kümeleri tablolar kullanım <xref:System.Data.DataRelation> nesneleri tablolar arasında bir üst/alt ilişkilerini temsil eden ve birbirlerinden ilgili kayıtları döndürmek için. İlişkili tabloları kullanarak veri kümelerine ekleme **veri kaynağı Yapılandırma Sihirbazı**, veya **veri kümesi Tasarımcısı**oluşturur ve yapılandırır <xref:System.Data.DataRelation> nesnesi.  
  
 <xref:System.Data.DataRelation> Nesne iki işlevleri gerçekleştirir:  
  
- Kullanılabilir çalıştığınız bir kayıtla ilgili kayıtların yapabilirsiniz. Bir üst kayıt varsa alt kayıtları sağlar. (<xref:System.Data.DataRow.GetChildRows%2A>) ve bir alt kaydı ile çalışıyorsanız üst kaydı (<xref:System.Data.DataRow.GetParentRow%2A>).  
  
- Bu, üst kaydını sildiğinizde ilgili alt kayıtları silme gibi başvurusal bütünlük kısıtlamaları zorunlu kılabilir.  
  
  Doğru bir birleştirme ve işlevi arasındaki farkı anlamak önemlidir bir <xref:System.Data.DataRelation> nesne. Doğru bir birleştirme işleminde kayıtlarını üst ve alt tablolarından alınan ve tek, düz bir kayıt yerleştirin. Kullandığınızda, bir <xref:System.Data.DataRelation> nesne hiçbir yeni bir kayıt oluşturulur. Bunun yerine, DataRelation tablolar arasında ilişki izler ve üst ve alt kayıtları uyumlu kalmasını sağlar.  
  
## <a name="datarelation-objects-and-constraints"></a>DataRelation nesneleri ve kısıtlamalar  
 A <xref:System.Data.DataRelation> nesnesi oluşturun ve aşağıdaki kısıtlamalar uygulamak için de kullanılır:  
  
- Bir tablo sütununda yinelenen değer yok içerdiğini garanti eder, benzersiz kısıtlama.  
  
- Bir veri kümesindeki bir üst ve alt tablo arasında bilgi tutarlılığını korumak için kullanılan bir yabancı anahtar kısıtlaması.  
  
  Belirttiğiniz kısıtlamaları bir <xref:System.Data.DataRelation> nesne otomatik olarak uygun nesneleri oluşturma veya özelliklerini ayarlama uygulanır. Bir yabancı anahtar kısıtlaması kullanarak oluşturursanız <xref:System.Data.DataRelation> nesnesi, örneklerini <xref:System.Data.ForeignKeyConstraint> sınıfı eklenir <xref:System.Data.DataRelation> nesnenin <xref:System.Data.DataRelation.ChildKeyConstraint%2A> özelliği.  
  
  Benzersiz kısıtlama uygulanan yalnızca ayarlayarak ya da <xref:System.Data.DataColumn.Unique%2A> bir veri sütununun özellik `true` veya örneği ekleyerek <xref:System.Data.UniqueConstraint> sınıfının <xref:System.Data.DataRelation> nesnenin <xref:System.Data.DataRelation.ParentKeyConstraint%2A> özelliği. Bir veri kümesinde kısıtlamaları askıya alma hakkında daha fazla bilgi için bkz. [bir veri kümesini doldururken kısıtlamaları kapatma kapatma](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
### <a name="referential-integrity-rules"></a>Bilgi tutarlılığı kuralları  
 Yabancı anahtar kısıtlamasının bir parçası olarak üç noktalarda uygulanan tutarlılığını kuralları belirtebilirsiniz:  
  
- Üst kayıt güncelleştirildiğinde  
  
- Bir üst kaydı silindiğinde  
  
- Bir değişiklik olduğunda kabul veya reddedildi  
  
  Yapabileceğiniz kuralları belirtilen <xref:System.Data.Rule> sabit listesi ve bu aşağıdaki tabloda listelenen.  
  
|Yabancı anahtar kısıtlaması kuralı|Eylem|  
|----------------------------------|------------|  
|<xref:System.Data.Rule>|Üst kayıtta yapılan değişiklik (güncelleştirme veya silme) alt tablosundaki ilgili kayıtlar da gerçekleştirilir.|  
|<xref:System.Data.Rule>|Alt kayıtları silinmez, ancak alt kayıtlardaki yabancı anahtarı kümesine <xref:System.DBNull>. Bu ayar, "artık" alt kayıtları bırakılabilir — diğer bir deyişle, bunlar hiç üst kayıtlar ilişkisi. **Not:** bu kullanarak alt tablosunda geçersiz veri sonuçlanabilir.|  
|<xref:System.Data.Rule>|İlgili alt kayıtları yabancı anahtarının varsayılan değerine ayarlanır (sütun tarafından belirlenen <xref:System.Data.DataColumn.DefaultValue%2A> özelliği).|  
|<xref:System.Data.Rule>|İlgili alt kayıtları değişiklik yapılmaz. Bu ayar, başvuruları geçersiz üst kayıtlar için alt kayıtları içerebilir.|  
  
 Veri kümesi tablolarını güncelleştirmeleri hakkında daha fazla bilgi için bkz: [verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md).  
  
### <a name="constraint-only-relations"></a>Yalnızca kısıtlaması ilişkileri  
 Oluştururken bir <xref:System.Data.DataRelation> nesnesi, ilişki yalnızca kısıtlamaları uygulamak için kullanılan belirtme seçeneğiniz vardır — diğer bir deyişle, bu da ilgili kayıtların erişmek için kullanılmaz. Biraz daha verimlidir ve ilgili kayıtları özelliğiyle olandan daha az yöntemleri içeren bir veri kümesi oluşturmak için bu seçeneği kullanabilirsiniz. Ancak, ilgili kayıtlarına erişmek mümkün olmayacaktır. Örneğin, yalnızca kısıtlaması ilişkisi alt kayıtlarına olan üst kaydını silmesini engeller ve üst alt kayıtları erişemez.  
  
## <a name="manually-creating-a-data-relation-in-the-dataset-designer"></a>El ile veri kümesi Tasarımcısı'nda veri ilişkisi oluşturma  
 Visual Studio'da veri tasarım araçlarını kullanarak veri tabloları oluşturduğunuzda, veri kaynağından bilgileri toplanabilir, ilişkileri otomatik olarak oluşturulur. Veri tablolarından el ile eklerseniz **veri kümesi** sekmesinde **araç kutusu**, ilişki el ile oluşturmanız gerekebilir. Oluşturma hakkında bilgi için <xref:System.Data.DataRelation> programlı olarak bkz [DataRelations ekleme](http://msdn.microsoft.com/library/a4a564fb-c1c4-4135-b6c2-b030e51195e4).  
  
 Veri tabloları arasında ilişki görünen satırlar halinde **veri kümesi Tasarımcısı**, ilişki tek-çok yönüyle gösteren bir anahtar ve sonsuzluk karakteri ile. Varsayılan olarak, adı ' % s'relationshipCommentEnd Kimliği = '1c8c78e19b7fa441' tasarım yüzeyinde görünmez.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-a-relationship-between-two-data-tables"></a>İki veri tabloları arasında bir ilişki oluşturmak için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Sürükleme bir **ilişkisi** nesnesinden **veri kümesi** ilişki alt veri tablosunda toolbox.  
  
     **İlişkisi** iletişim kutusu açılır ve doldurma **alt tablo** sürüklediğiniz tablonun kutusuyla **ilişkisi** oturum nesnesi.  
  
3.  Üst tablosundan bilgi seçme **üst tablo** kutusu. Üst tablo "bir" bir-çok ilişkisi tarafındaki kayıtları içerir.  
  
4.  Doğru alt tablo görüntülendiğini doğrulayın **alt tablo** kutusu. Alt tablo "many" bir-çok ilişkisi tarafındaki kayıtları içerir.  
  
5.  İlişkide'için bir ad yazın **adı** kutusunu veya seçilen tabloları varsayılan adı bırakın. Bu gerçek adıdır <xref:System.Data.DataRelation> kod nesnesi.  
  
6.  Tabloları birleştirme içinde sütunları seçin **anahtar sütunları** ve **yabancı anahtar sütunları** listeler.  
  
7.  Bir ilişki, kısıtlama veya her ikisi de oluşturulup oluşturulmayacağını seçin. Bilgi için [DataRelation nesnelerine giriş](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
8.  Seçin veya temizleyin **iç içe ilişkisi** kutusu. Bu seçeneği ayarlar seçerek <xref:System.Data.DataRelation.Nested%2A> özelliğini `true`, ve bu satır XML verileri olarak yazılan veya eşitlenmiş üst sütun içinde iç içe ilişkisinin satır alt neden <xref:System.Xml.XmlDataDocument>. Daha fazla bilgi için [iç içe DataRelations](http://msdn.microsoft.com/library/9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab).  
  
9. Bu tablolarındaki kayıtlara değişiklik zaman uygulanacak kuralları ayarlayın. Daha fazla bilgi için bkz. <xref:System.Data.Rule>.  
  
10. Tıklayın **Tamam** ilişki oluşturmak için. Tasarımcı iki tablo arasında bir ilişki satırı görünür.  
  
#### <a name="to-display-a-relation-name-in-the-dataset-designer"></a>Veri kümesi Tasarımcısı'nda bir ilişki adı görüntülemek için  
  
1.  Kümenizde açın **veri kümesi Tasarımcısı**. Daha fazla bilgi için [nasıl yapılır: bir veri kümesini veri kümesi Tasarımcısı'nda açma](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Gelen **veri** menüsünde **ilişki etiketlerini göster** ilişki adı görüntülenecek komutu. İlişki adı gizlemek için bu komutu temizleyin.

