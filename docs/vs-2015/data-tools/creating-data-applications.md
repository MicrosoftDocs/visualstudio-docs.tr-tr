---
title: Veri uygulamaları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291323"
---
# <a name="creating-data-applications"></a>Veri Uygulamaları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio, veri erişim uygulamalarını oluşturmanıza yardımcı olması için birçok tasarım zamanı aracı sağlar. Bu giriş, verilerle çalışan uygulamalar oluşturmak için gerekli olan temel işlemlere dair genel bir bakış sunar. Burada yer alan bilgiler kasıtlı olarak birçok ayrıntıyı atlar ve kaynağı genel bilgiler ve bir veri uygulaması oluşturma ile ilgili birçok diğer Yardım sayfalarına sıçrama noktası olarak tasarlanmıştır.  
  
 İçindeki verilere erişen uygulamalar geliştirirken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], farklı gereksinimleriniz olacaktır. Bazı durumlarda, yalnızca formdaki verileri görüntülemek isteyebilirsiniz. Diğer durumlarda, diğer uygulamalar ve süreçler ile bilgi paylaşımı için bir yol oluşturmanız gerekebilir.  
  
 Verilerle ne olursa olsun, anlamanız gereken bazı temel kavramları vardır. Hiç veri işleme ayrıntılarının bazılarını bilmeniz gerekmeyebilir; Örneğin, hiçbir zaman programlı olarak veritabanı oluşturmak ihtiyacınız olabilecek — ancak temel veri kavramlarının yanı sıra veri araçlarını (sihirbazlar ve tasarımcılar) içinde kullanılabiliranlamakçokkullanışlıdır[!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Normal bir veri uygulaması şu şemada gösterilen işlemlerin çoğunu kullanır:  
  
 ![Veri döngüsü grafiği](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
Veri döngüsü  
  
 Uygulamanızı oluştururken etmeye çalıştığınız görevi düşünün. Bulmaya yardımcı olması için aşağıdaki bölümlere [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araçları ve sizin için kullanılabilir olan nesneler.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Önceki Diyagramda gösterilen işlemlerin bazıları basitleştirecek sihirbazlar sağlar. Örneğin, çalışan **veri kaynağı Yapılandırma Sihirbazı** uygulamanızla verilere bağlanmak, verileri almak için türü belirtilmiş veri kümesi oluşturma ve veriyi uygulamanıza getirmek için yeterli bilgi sağlar.  
  
 Hızlı bir şekilde görmek için nasıl [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veri uygulamaları geliştirmenize yardımcı olan bkz [izlenecek yol: Basit veri uygulaması oluşturma](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Verilere Bağlanma  
 Uygulamanıza veri getirmek (ve değişiklikleri veri kaynağına geri göndermek için), bazı tür iki taraflı iletişim kurulması gerekir. Bu iki yönlü iletişim, genellikle veri modelinizdeki nesneler tarafından işlenir.  
  
 Örneğin, bir `TableAdapter` bir veritabanına veri kümelerini kullanan uygulamaları bağlanır ve <xref:System.Data.Objects.ObjectContext> varlık çerçevesindeki varlıkları bir veritabanına bağlanır. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamanız tarafından kullanılan bağlantı oluşturmada yardımcı olacak çeşitli araçlar sağlar. Uygulamanızı verilere bağlanma ile ilgili daha fazla bilgi için bkz: [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Uygulamanızı bir veritabanındaki verilere bağlamak için veri kümelerini kullanan öğrenmek için bkz. [izlenecek yol: (Windows Forms) bir veritabanındaki verilere bağlanma](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Uygulamanızı Veri Almaya Hazırlama  
 Uygulamanız bağlantısız veri modeli kullanıyorsa ile çalışırken, uygulamanızda geçici verileri depolamak gerekir. Visual Studio, uygulamanızın kullandığı geçici depolama veri nesnelerini oluşturma yardımcı olacak araçlar sağlar: veri kümeleri, varlıkları ve [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] nesneleri.  
  
> [!NOTE]
>  Bağlantısız veri modeli kullanan bir uygulama genellikle bir veritabanına bağlanmak, uygulamaya verileri getirmek üzere sorgu çalıştıran, veritabanı bağlantısını kesmek ve yeniden bağlanma ve veritabanını güncelleştirmeden önce veriyi çevrimdışı işlemek.  
  
 Türü belirtilmiş datasets oluşturma ile ilgili daha fazla bilgi için bkz: [uygulamanızı hazırlama veri almak için](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). N katmanlı uygulamalarda veri kümeleri kullanma hakkında ek bilgi için bkz: [ayrı veri kümeleri ve TableAdapters öğelerini farklı projelere ayırma](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Bir veri kümesi oluşturma hakkında bilgi edinmek için konusundaki yordamları tamamlayın [izlenecek yol: bir veri kümesi Tasarımcısı ile oluşturma](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Nasıl oluşturulacağını öğrenmek için [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] nesneleri konusundaki yordamları tamamlayın [izlenecek yol: oluşturma LINQ to SQL sınıfları (O R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Uygulamanıza Veri Getirme  
 Uygulamanız bağlantısız veri modeli veya kullanmasın, verileri uygulamanıza getirebilmeniz gerekir. Sorguları veya saklı yordamları veritabanında yürüterek uygulamanıza veri getirmek. Veri kümelerine verileri depolayan uygulamalar yürütme sorguları ve depolanan yordamları kullanarak `TableAdapter`s, verileri varlıklara depolayan uygulamalar kullanarak sorgular yürütün ise [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) veya varlıkları bağlanarak saklı yordamlar için doğrudan. TableAdapters kullanan sorguları oluşturma ve düzenleme hakkında daha fazla bilgi için bkz. [nasıl yapılır: TableAdapter sorguları oluşturma](../data-tools/how-to-create-tableadapter-queries.md) ve [nasıl yapılır: Edit TableAdapter Queries](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Verinin veri kümelerine yüklenmesi ve sorguların ve saklanan yordamların yürütülmesi hakkında daha fazla bilgi için bkz: [uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md).  
  
 Bir veri kümesine veri yüklemek hakkında bilgi edinmek için konusundaki yordamları tamamlayın [izlenecek yol: bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) ve form-load olay işleyicisinde kodu inceleyin.  
  
 Veri yükleme konusunda bilgi almak için [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] nesneleri konusundaki yordamları tamamlayın [izlenecek yol: oluşturma LINQ to SQL sınıfları (O R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Bir SQL sorgusu oluşturma ve yürütme konusunda bilgi almak için bkz: [nasıl yapılır: oluşturma ve satırları döndürür bir SQL deyimi yürütme](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Bir saklı yordam çalıştırma hakkında bilgi edinmek için bkz: [nasıl yapılır: bir saklı yordam yürütme satırları döndürür](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Formlarda verileri görüntüleme  
 Uygulamanıza veri getirme sonra genellikle bir formda görüntülemek veya değiştirmek kullanıcıları görüntüler. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sağlar [veri kaynakları penceresi](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), burada formlara otomatik olarak verileri görüntüleyen verilere bağlı denetimler oluşturmak için öğeleri sürükleyebilirsiniz. Veri bağlama ve veriyi kullanıcılara gösterme hakkında daha fazla bilgi için bkz. [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Kullanıcılar veri sunma hakkında bilgi için aşağıdaki izlenecek yollardaki yordamları tamamlayın. (işlemin sürüklemeye özellikle dikkat ederek ödeme **veri kaynakları** pencere):  
  
-   [İzlenecek yol: Bir Windows formunda veri görüntüleme](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Bir WCF veri hizmetine WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [İzlenecek yol: Bir WCF veri hizmetine Silverlight denetimleri bağlama](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Uygulamanızdaki Verileri Düzenleme  
 Kullanıcılarınıza veri ile sunulduktan sonra bunlar büyük olasılıkla, yeni kayıtlar ekleyerek değiştirir ve veritabanına düzenleme ve veri göndermeden önce kayıtları silme.  
  
 Kümenize yüklendikten sonra veri ile çalışma hakkında daha fazla bilgi için bkz. [uygulamanız verileri düzenleme](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Verileri Doğrulama  
 Veri değişiklikleri yaparken, genellikle dataset nesnesine kabul veya veritabanına yazılan değerleri izin vermeden önce değişiklikleri doğrulamak isteyeceksiniz. *Doğrulama* bu yeni değerleri, uygulamanızın gereksinimleri için kabul edilebilir olduğunu doğrulamak için işlem adıdır. Değiştiklerinde, uygulamanızdaki değerleri denetlemek için mantık ekleyebilirsiniz. Visual Studio, sütun ve satır değişiklikleri sırasında veri doğrulama kodu eklemeye yardımcı araçlar sağlar. Daha fazla bilgi için [veri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Uygulamanıza veri doğrulaması ekleme konusunda bilgi almak için bkz: [izlenecek yol: bir veri kümesine doğrulama ekleme](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 N katmanlı bir uygulamaya ayrılmış bir veri kümesine doğrulama ekleme konusunda bilgi edinmek için [bir n katmanlı bir veri kümesine doğrulama ekleme](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Verileri Kaydetme  
 Değişiklik yapmadan uygulamanızı (ve bu değişiklikleri doğruladıktan) sonra genellikle değişiklikleri veritabanına geri göndermek istersiniz. Veri kümelerinde genellikle veri deposu uygulamaları, verileri kaydetmek için bir TableAdapterManager kullanın. Daha fazla bilgi için [TableAdapterManager genel bakışı](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Varlık çerçevesi uygulamaları kullanın <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> verileri kaydetmek için yöntemi.  
  
 Güncelleştirilmiş verileri bir veritabanına geri gönderme hakkında daha fazla bilgi için bkz. [verileri kaydetme](../data-tools/saving-data.md).  
  
 Bir veri kümesinden bir veritabanına güncelleştirilmiş veriler göndermek öğrenmek için konusundaki yordamları tamamlayın [izlenecek yol: ilgili veri tabloları (hiyerarşik güncelleştirme) veri kaydetmeyi](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>İlgili Konular  
 [Veri uygulamaları Visual Studio'da genel bakış](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Verilerle çalışan uygulamalarının nasıl oluşturulacağını açıklayan konulara bağlantılar sağlar.  
  
 [Visual Studio'da verilere bağlanma](../data-tools/connecting-to-data-in-visual-studio.md)  
 Nasıl kullanılacağı hakkındaki konulara bağlantılar sağlar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uygulamanızı verilere bağlamak ve uygulamalarınız için veri kaynakları oluşturmak için.  
  
 [Uygulamanızı veri almaya hazırlama](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Veri kümeleri ve varlık veri modelleri de dahil olmak üzere, uygulamanızdaki veri modelleri ile nasıl çalışılacağını açıklayan konulara bağlantılar sağlar.  
  
 [Uygulamanıza veri getirme](../data-tools/fetching-data-into-your-application.md)  
 Veriler uygulamanıza yükleme açıklayan konulara bağlantılar sağlar.  
  
 [Visual Studio'da verilere denetimler bağlama](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Bağlama denetimleri nasıl Windows Forms açıklayan konulara, WPF denetimlerinin ve Silverlight denetimlerinin veri kaynaklarına bağlantılar sağlar.  
  
 [Uygulamanızdaki verileri düzenleme](../data-tools/editing-data-in-your-application.md)  
 Uygulamanızdaki verilerin nasıl değiştirilebileceğini açıklayan konulara bağlantılar sağlar.  
  
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Veri değişikliklerine doğrulamanın nasıl açıklayan konulara bağlantılar sağlar.  
  
 [Verileri Kaydetme](../data-tools/saving-data.md)  
 XML gibi diğer biçimlerde kaydetme veya uygulamanızdan veritabanına güncelleştirilmiş veriler göndermek nasıl açıklayan konulara bağlantılar sağlar.  
  
 [Visual Studio'da veri kaynaklarıyla çalışma araçları](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Gibi Visual Studio'da veri kaynaklarıyla çalışmak için kullanabileceğiniz araçlar hakkındaki konulara bağlantılar sağlar **veri kaynakları** penceresi ve ADO.NET varlık veri modeli Tasarımcısı.