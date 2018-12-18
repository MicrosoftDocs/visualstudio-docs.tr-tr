---
title: 'Nasıl yapılır: O R Tasarımcısı kullanarak devralmayı yapılandırma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7a6c8e4b2da87185c41157b8d03bd59b37188a43
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222697"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Nasıl yapılır: O/R Tasarımcısı kullanarak devralmayı yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) İlişkisel sistemlerde sık uygulandığı şekilde tek tablolu devralma kavramını destekler. Tek tablo devralma işleminde üst bilgi hem de alt bilgi için alanları içeren bir tek veritabanı tablosu yok. İlişkisel verilerle bir ayrıştırıcı sütunu her kaydın ait olduğu sınıfı belirleyen bir değer içerir.  
  
 Örneğin, herkesin şirket tarafından kullanılan içeren bir kişi tabloya göz önünde bulundurun. Bazı kişiler çalışanlar ve bazı kişiler yöneticileri. Kişiler tablo adlı bir sütun içeren `EmployeeType` 1 değeri, yöneticileri ve 2 değerini çalışanlar için sahip; bu ayrıştırıcı sütunu. Bu senaryoda, çalışanların öğesinin oluşturabilir ve sınıf olan kayıtlar ile doldurmak bir `EmployeeType` değeri 2'dir. Ayrıca her sınıfların geçerli olmayan sütunları kaldırabilirsiniz.  
  
 Devralma kullanır (ve ilişkisel verilere karşılık gelir) nesne modeli oluşturma biraz kafa karıştırıcı olabilir. Aşağıdaki yordam devralma O/R Tasarımcısı ile yapılandırmak için gereken adımlar açıklanmaktadır. Sağlanan verileri kullanan bir kılavuz için var olan bir tablo ve sütunlara başvuruda bulunmadan aşağıdaki genel adımları zor olabilir. Devralma kullanarak yapılandırmaya yönelik ayrıntılı adım adım yönergeler için [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], bkz: [izlenecek yol: oluşturma LINQ to SQL sınıfları kullanarak tek tablolu devralma (O/R Tasarımcısı) tarafından](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### <a name="to-create-inherited-data-classes"></a>Devralınan veri sınıfları oluşturmak için  
  
1.  Açık [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ekleyerek bir **LINQ to SQL sınıfları** varolan bir Visual Basic veya C# projesine öğesi.  
  
2.  Temel sınıf olarak kullanmak istediğiniz tabloyu sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
3.  İkinci bir kopyası tablosunu sürükleyin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ve yeniden adlandırın. Türetilmiş bir sınıf ya da alt budur.  
  
4.  Tıklayın **devralma** içinde **Object Relational Designer** sekmesinde **araç kutusu**, alt (adlandırdığınız tablosu) tıklayın ve ardından temel sınıfa bağlanın.  
  
    > [!NOTE]
    >  Tıklayın **devralma** öğesi **araç kutusu** ve fare düğmesini bırakın, 3. adımda oluşturulan sınıf ikinci bir kopyası tıklatın ve 2. adımda oluşturduğunuz ilk sınıf'ye tıklayın. Devralım çizgisi üzerindeki oku ilk sınıfa işaret etmesini sağlayacaksınız.  
  
5.  Her sınıfta görünmesini istemiyorsanız ve ilişkileri için kullanılmayan tüm nesne özellikleri silin. Nesne özellikleri ilişkilendirmeler için kullanılan silmeye çalışıyorsanız, bir hata alırsınız: [özelliği \<özellik adı > ilişkilendirmesine katıldığından silinemiyor \<ilişkilendirme adı >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Türetilmiş bir sınıf kendi temel sınıfta tanımlanan özellikleri devraldığından, aynı sütunlara her sınıfında tanımlanamaz. (Sütunları özellikleri olarak uygulanır.) Temel sınıf özelliğini temel alan ait devralma değiştiricisinin ayarlayarak türetilmiş sınıftaki sütunları oluşturulmasını etkinleştirebilirsiniz. Daha fazla bilgi için [NOT ın derleme: geçersiz kılma özellikleri ve yöntemleri](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  İçinde devralım çizgisini seçin [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
7.  İçinde **özellikleri** penceresinde **ayrıştırıcı özelliği** sınıflarınızı kayıtları ayırmak için kullanılan sütun adı.  
  
8.  Ayarlama **türetilen sınıf ayrıştırıcısı değerinin** kaydı devralınan türü olarak atar veritabanındaki değerle özelliği. (Bu, ayrıştırıcı sütunu depolanır ve devralınan sınıf belirlemek için kullanılan değerdir.)  
  
9. Ayarlama **temel sınıf ayrıştırıcı değeri** özelliğini kaydı temel tür olarak belirten değer. (Bu, ayrıştırıcı sütunu depolanır ve temel sınıf belirlemek için kullanılan değerdir.)  
  
10. İsteğe bağlı olarak da ayarlayabilirsiniz **devralma varsayılan** devralma kod tanımlanan eşleşmeyen satırlar yüklenirken kullanılan bir devralma hiyerarşisi içindeki bir tür belirtmek için özellik. Kayıt, kendi ayrıştırıcı sütunu bir değere sahipse, diğer bir deyişle, ya da değer eşleşmiyor **türetilen sınıf ayrıştırıcısı değerinin** veya **temel sınıf ayrıştırıcı değeri** özellikleri, kayıt olarak atanan türü yükleyecek **devralma varsayılan**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [İzlenecek yol: LINQ to SQL sınıfları (O R Designer) oluşturma](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [PAVE veri uygulaması geliştirme Visual Studio 2012'deki yenilikler](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Visual Studio'da verilere erişme](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [İzlenecek yol: Tek tablolu devralma (O/R Tasarımcısı) kullanarak LINQ to SQL sınıfları oluşturma](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [DEĞİL IN derleme: Visual Basic'te devralma](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Devralma](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

