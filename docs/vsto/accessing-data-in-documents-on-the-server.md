---
title: Sunucudaki belgelerde verilere
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], accessing on server
- data access [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 70c00a9c0de4afd9f54062e1c2ffabcc2911a538
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305578"
---
# <a name="access-data-in-documents-on-the-server"></a>Sunucudaki belgelerde verilere
  Microsoft Office Word veya Microsoft Office Excel nesne modelini kullanmak zorunda kalmadan belge düzeyinde özelleştirme veriye karşı programlama yapabilirsiniz. Bu belgede sözcük olmayan bir sunucuda bulunan verilere erişebilir veya Excel yüklü anlamına gelir. Örneğin, bir sunucu üzerinde kod (örneğin, bir [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] sayfası) bir belgedeki verileri özelleştirebilir ve özelleştirilmiş belgeyi bir son kullanıcıya gönderin. Son kullanıcıya belgeyi açtığında, çözüm derlemesine veri bağlama kodunu belgeye özelleştirilmiş veri bağlar. Belgedeki verileri kullanıcı arabiriminden ayrıldığı için bu olasıdır. Daha fazla bilgi için [veri belge düzeyi özelleştirmelerdeki önbelleğe alınmış](../vsto/cached-data-in-document-level-customizations.md).  

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  

## <a name="cache-data-for-use-on-a-server"></a>Sunucuda kullanmak için verileri önbelleğe alma  
 Bir belge veri nesnesinde önbelleğe almak için kendisiyle işaretlemek <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliği tasarım zamanında ya da kullanmak `StartCaching` çalışma zamanında konak öğesinin yöntemi. Bir veri nesnesini bir belgede önbelleğe aldığınızda [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] belge içinde depolanan XML dizesine nesnesini serileştirir. Nesneleri önbelleğe almak için uygun olması için belirli gereksinimleri karşılaması gerekir. Daha fazla bilgi için [veriyi önbelleğe alma](../vsto/caching-data.md).  

 Sunucu tarafı kod, tüm veri nesnelerini veri önbelleğindeki işleyebilirsiniz. Önbelleğe alınmış verileri örneklerine bağlı denetimler, istemcide belge açıldığında verilerde yapılan tüm sunucu tarafı değişiklikler otomatik olarak görünür, böylece kullanıcı arabirimi ile eşitlenir.  

## <a name="access-data-in-the-cache"></a>Önbellekteki verileri erişimi  
 Önbellekteki verileri, uygulamalardan, ofis dışından örnek bir konsol uygulaması, bir Windows Forms uygulaması veya bir Web sayfası erişebilirsiniz. Önbelleğe alınan verilere erişen uygulama tam güven olmalıdır; kısmi güven ilişkisi olan bir Web uygulaması eklemek, alma veya bir Office belgesini önbelleğe alınmış verileri değiştirme.  

 Veri önbelleği tarafından sunulan bir koleksiyon hiyerarşisi aracılığıyla erişilebilir <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> özelliği <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı:  

- <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> Özelliği döndürür bir <xref:Microsoft.VisualStudio.Tools.Applications.CachedData>, tüm belge düzeyi özelleştirmesinde önbelleğe alınmış verileri içerir.  

- Her <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> birini veya daha fazlasını içeren <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> nesneleri. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> tek bir sınıf içinde tanımlanan tüm önbelleğe alınan verilerin nesneler içerir.  

- Her <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> birini veya daha fazlasını içeren <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> nesneleri. A <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> tek önbelleğe alınmış veri nesnesini temsil eder.  

  Aşağıdaki kod örneği, önbelleğe alınmış bir dizede nasıl erişileceğini gösteren `Sheet1` bir Excel çalışma kitabı projesi sınıfı. Bu örnek için sağlanan daha büyük bir örneğin parçasıdır <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> yöntemi.  

  [!code-csharp[Trin_ServerDocument#12](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#12)]
  [!code-vb[Trin_ServerDocument#12](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#12)]  

## <a name="modify-data-in-the-cache"></a>Önbellekteki verileri değiştirme  
 Önbelleğe alınmış verileri nesneyi değiştirmek için genellikle aşağıdaki adımları gerçekleştirin:  

1.  Nesnesinin yeni bir örneğini XML gösterimine önbelleğe alınmış nesnenin seri durumdan çıkarır. XML kullanarak erişebileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> özelliği <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> önbelleğe alınmış veri nesnesini temsil eden.  

2.  Bu kopyada değişiklik.  

3.  Değiştirilen nesne, aşağıdaki seçeneklerden birini kullanarak verileri önbelleğe geri sıralayın:  

    -   Otomatik olarak değişiklikleri seri hale getirmek istiyorsanız, kullanın <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> yöntemi. Bu yöntemde **DiffGram** serileştirmek için biçim <xref:System.Data.DataSet>, <xref:System.Data.DataTable>ve yazılan veri kümesi nesnelerini veri önbelleğindeki. **DiffGram** biçimi, çevrimdışı bir belgedeki veri önbelleğini değişiklikler sunucuya doğru olarak gönderilmesini sağlar.  

    -   Önbelleğe alınan verilerde yapılan değişiklikleri için kendi serileştirme gerçekleştirmek istiyorsanız, doğrudan yazabileceğiniz <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> özelliği. Belirtin **DiffGram** kullanırsanız, biçimlendirme bir <xref:System.Data.Common.DataAdapter> verilerde yapılan değişikliklerle bir veritabanını güncelleştirmek için bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya yazılan veri kümesi. Aksi takdirde, <xref:System.Data.Common.DataAdapter> varolan satırları değiştirmek yerine yeni satır ekleyerek veritabanını güncelleştirir.  

### <a name="modify-data-without-deserializing-the-current-value"></a>Geçerli değer seri durumdan çıkarılırken verileri değiştirme  
 Bazı durumlarda, ilk geçerli değeri seri durumdan çıkarılırken olmadan önbelleğe alınmış nesnenin değerini değiştirmek isteyebilirsiniz. Örneğin, bir tamsayı veya dize gibi basit bir türe sahip bir nesne değeri değiştiriyorsanız veya bir önbelleğe alınan başlatma bunu yapabilirsiniz <xref:System.Data.DataSet> bir sunucuda bir belgedeki. Bu durumlarda, kullandığınız <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> önbelleğe alınmış nesnenin geçerli değerini ilk seri durumdan çıkarılırken olmadan yöntemi.  

 Aşağıdaki kod örneği, önbelleğe alınmış bir dize değerini değiştirmek gösterilmiştir `Sheet1` bir Excel çalışma kitabı projesi sınıfı. Bu örnek için sağlanan daha büyük bir örneğin parçasıdır <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A> yöntemi.  

 [!code-csharp[Trin_ServerDocument#11](../vsto/codesnippet/CSharp/Trin_ServerDocument/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../vsto/codesnippet/VisualBasic/Trin_ServerDocument/Form1.vb#11)]  

### <a name="modify-null-values-in-the-data-cache"></a>Veri önbelleğini null değerleri değiştirme  
 Veri önbelleğini değerine sahip nesneleri depolamaz **null** zaman Belge kaydedildiğinde ve kapatıldı. Önbelleğe alınmış verileri değiştirdiğinizde, bu sınırlama bazı sonuçları vardır:  

-   Değer veri önbelleğindeki herhangi bir nesne ayarlarsanız **null**, tüm veri önbelleğindeki nesneler otomatik olarak ayarlanacak **null** zaman belge açılır ve tüm veri önbelleği zaman temizlenir Belge kaydedildi ve kapatıldı. Diğer bir deyişle, veri önbelleği'ndeki tüm önbelleğe alınan nesneleri kaldırılacak ve <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> koleksiyonu boş olacak.  

-   Bir çözüm oluşturuyorsanız **null** nesnelerindeki veri önbelleği ve bu nesneleri kullanarak başlatmak istediğiniz <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı belge önce ilk kez açıldığında, tüm nesneleri başlattığınızdan emin olun Veri karmasındaki. Yalnızca bazı nesneler başlatmak, tüm nesneleri ayarlanacak **null** zaman belge açılır ve Belge kaydedildi ve tüm veri önbelleği temizlendi.  

## <a name="access-typed-datasets-in-the-cache"></a>Türü belirtilmiş veri kümeleri önbelleğe erişim  
 Office çözümünü ve ofis dışında bir uygulama bir Windows Forms uygulaması gibi bir türü belirtilmiş veri kümesi verilere erişmek istiyorsanız veya [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] projesini hem de başvuruda bulunulan ayrı bir derlemede yazılmış veri kümesi tanımlamalıdır projeleri. Kullanarak türü belirtilmiş veri kümesi için her bir proje eklediğinizde **veri kaynağı yapılandırması** Sihirbazı veya **veri kümesi Tasarımcısı**, .NET Framework türü belirtilmiş datasets içinde iki proje farklı olarak değerlendir . Türü belirtilmiş datasets oluşturma hakkında daha fazla bilgi için bkz. [oluşturun ve Visual Studio'da veri kümeleri yapılandırma](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).  

## <a name="see-also"></a>Ayrıca bkz.  
 [Sunucudaki belgelerde verilere](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Belge düzeyi özelleştirmelerdeki önbelleğe alınmış veriler](../vsto/cached-data-in-document-level-customizations.md)  
