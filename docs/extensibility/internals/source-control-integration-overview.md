---
title: Kaynak denetimini tümleştirmeye genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], about source control
ms.assetid: 3a46e4eb-e677-49c3-8647-d927d035a19a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: edd2e04f4e1102d66cc04cd1365dc7abd1488c9c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931852"
---
# <a name="source-control-integration-overview"></a>Kaynak Denetimini Tümleştirmeye Genel Bakış
Bu bölümde, Visual Studio kaynak denetimine tümleştirmek için iki şekilde karşılaştırır; Kaynak denetimi eklentisi ve bir kaynak denetimi çözümü sağlar ve yeni kaynak denetimi özellikleri vurgular VSPackage'ı. Visual Studio el ile kaynak denetimi eklentileri ve kaynak denetimi VSPackage'ları arasında geçiş yapma ek olarak çözüm tabanlı otomatik geçiş sağlar.  
  
## <a name="source-control-integration"></a>Kaynak denetimi tümleştirmesi  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iki tür kaynak denetimi tümleştirmesi seçeneği destekler. Tüm sürümlerinde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], yine de bir eklenti kaynak denetimi Eklentisi (daha önce de MSSCCI API olarak adlandırılır), Visual Studio kaynak denetimi kullanıcı arabirimi (kullanırken temel kaynak denetimi işlevlerini sağlar. API göre tümleştirebilirsiniz UI). Kaynak denetimi VSPackage'ı, diğer yandan, bir yeni, derin tümleştirme sağlar [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] açıdan çok yönlülük ve özerkliği, kaynak denetimi modelindeki üst düzey talepleri kaynak denetimi tümleştirmesi için uygun yolu.  
  
 ![Kaynak denetimine genel bakış](../../extensibility/internals/media/sourcectnrloverview.gif "SourceCtnrlOverview")  
  
## <a name="source-control-plug-in"></a>Kaynak Denetimi Eklentisi  
 Visual Studio'nun tüm sürümleri, kaynak denetimi eklentisi API Belirtimi sürüm 1.2 bir tümleştirme yolu olarak destekler. Kaynak Denetimi Eklentisi uygulayan açıklandığı gibi kaynak denetimi tümleştirmesi ve kayıt için kaynak denetimi eklentisi API işlevleri uygulayan bir DLL Yazar [kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md). Bu yaklaşımda, tümleşik geliştirme ortamı (IDE) kullanan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] iade, kullanıma alma, Araçlar/Seçenekler özellik sayfaları, araç çubukları ve kaynak denetim karakterleri gibi iletişim kutuları için kullanıcı Arabirimi. Kaynak Denetimi Eklentisi API katı kıldığı bir kolayca tümleştirme Visual Studio ve kullanıcı için sorunsuz bir deneyim oluşturmasını sağlar. Başka bir deyişle, kaynak denetimi eklentisi işlevler ve API ayrıntılı geri çağırmaları çoğunu uygulamalıdır.  
  
 Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API kullanarak uygulamak için şu adımları izleyin:  
  
1. Belirtilen işlevleri uygulayan bir DLL'yi oluşturmak [kaynak denetimi eklentileri](../../extensibility/source-control-plug-ins.md).  
  
2. Uygun kayıt defteri girişlerini yaparak DLL'yi kaydetme (açıklanan [nasıl yapılır: kaynak denetimi eklentisi yükleme](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)).  
  
3. Kullanıcı Arabirimi ve kaynak denetimi bağdaştırıcısı paketi (kaynak denetimi eklentileri aracılığıyla kaynak denetimi işlevlerini işleyen Visual Studio bileşeni) tarafından istendiğinde görünen bir Yardımcısı oluşturma  
  
   Komutuna yanıt olarak bir kaynak denetimi, Visual Studio IDE temel işlemleri için standart bir kullanıcı Arabirimi sunar ve bu bilgileri için kaynak denetimi eklentisi tanımlanan kaynak denetimi eklentisi API işlevleri aracılığıyla geçirir. Gelişmiş seçenekleri için kaynak denetimi eklentisi üzerinde kendi Arabirim sunmak için örneğin kaynak-denetimli bir proje için gözatma çağrılabilir. Bu kullanıcının kaynak denetimi ile ilgilenirken iki farklı olması olası kullanıcı Arabirimi stilleri ile gelebilir anlamına gelir: sunan Visual Studio kullanıcı Arabirimi ve kullanıcı arabirimini kaynak denetimi eklentisi sunar. Gelişmiş kaynak denetimi işlemleri ile en dikkat çeken budur.  
  
### <a name="drawbacks-to-implementing-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi uygulamak için dezavantajları  
  
-   Gelişmiş özellikler için olası Karışıklığı önlemek için önde gelen kullanıcı arabirimleri, iki farklı türlerde görebilirsiniz.  
  
-   Kaynak Denetimi Eklentisi Kaynak Denetimi Eklentisi API tarafından kapsanan kaynak denetimi modeli için sınırlıysa.  
  
-   Kaynak Denetimi Eklentisi API bazı kaynak denetimi senaryoları için çok kısıtlayıcı olması olabilir.  
  
### <a name="advantages-to-implementing-a-source-control-plug-in"></a>Kaynak Denetimi Eklentisi uygulamak için avantajları  
  
-   Visual Studio, kaynak denetimi eklentisi, olası karmaşık kullanıcı Arabirimi uygulama gerekmez. böylece tüm temel kaynak denetimi işlemleri için tüm kullanıcı Arabirimi sağlar.  
  
-   Katı API nedeniyle, kaynak denetimi eklentisi kolayca daha kapsamlı işlevsellik sağlamak için dış kaynak denetimi programları ile etkileşim kurabilir; Visual Studio nasıl çok fazla kaynak denetimi işlevlerini, yalnızca o kaynak denetimi eklentisi API göre gerçekleştirilir gerçekleştirilir ilgilenmez.  
  
-   Kaynak Denetimi Eklentisi Kaynak denetimi VSPackage'ı uygulamak daha kolaydır.  
  
## <a name="source-control-vspackage"></a>Kaynak denetimi VSPackage'ı  
 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Visual Studio kaynak denetimi işlevlerini üzerinde tam denetim ve Visual Studio tarafından sağlanan bir kaynak denetimi kullanıcı arabiriminin tam değiştirme ile kapsamlı tümleştirme sağlar. Kaynak denetimi VSPackage'ı Visual Studio ile kayıtlıdır ve kaynak denetimi işlevlerini sağlar. Visual Studio ile birden çok kaynak denetimi VSPackage'ları kaydedilebilir ancak bunlardan yalnızca biri herhangi bir zamanda etkin olabilir. Etkin durumdayken kaynak denetimi VSPackage'ı Visual Studio'da Görünüm ve kaynak denetimi işlevlerini üzerinde tam denetime sahiptir. Tüm diğer kaynak denetimi sistemde kayıtlı VSPackage'ları, etkin olmayan ve herhangi bir UI hiç görüntülemez.  
  
 Kaynak denetimi VSPackage'ı uygulayan bir "tümü veya hiçbiri" stratejisi gerektirir. Kaynak denetimi VSPackage'ı oluşturan, kaynak denetim arabirimleri ve yeni kullanıcı Arabirimi öğeleri (iletişim kutuları, menüler ve araç çubukları) tüm kaynak denetimi işlevini kapsayan bir dizi uygulamaya çabayı önemli ölçüde yatırım gerekir. Bkz: [bir kaynak denetimi VSPackage'ı oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md) daha fazla ayrıntı için.  
  
### <a name="drawbacks-to-implementing-a-source-control-vspackage"></a>Bir kaynak denetimi VSPackage'ı uygulamak için dezavantajları  
  
-   VSPackage'ı başarıyla Visual Studio ile tümleştirmek için karmaşık arabirimleri sayısı uygulamalıdır.  
  
-   VSPackage'ı kaynak denetimi için gereken tüm kullanıcı Arabirimi sağlamanız gerekir; Visual Studio, bu alandaki herhangi bir Yardım sağlarız.  
  
-   Kaynak denetimi VSPackage'ı Visual Studio'ya içkin şekilde bağlıdır ve tek başına programlarla işlevi gibi bir kolayca dış bir kaynak denetim programı sürümü ile paylaşılamaz şekilde çalışamaz.  
  
### <a name="advantages-to-implementing-a-source-control-vspackage"></a>Bir kaynak denetimi VSPackage'ı uygulama avantajları  
  
-   VSPackage'ı kaynak denetimi UI üzerinde tam denetim ve işlevsellik olduğu için kullanıcının kaynak denetimi için sorunsuz bir arabirim sunulur.  
  
-   VSPackage'ı belirli bir kaynak denetim modeli için sınırlı değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi](../../extensibility/internals/source-control.md)   
 [Kaynak Denetimi Eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Bir kaynak denetimi VSPackage'ı oluşturma](../../extensibility/internals/creating-a-source-control-vspackage.md)   
 [Kaynak Denetimindeki Yenilikler](../../extensibility/internals/what-s-new-in-source-control.md)