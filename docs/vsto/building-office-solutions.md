---
title: Office çözümleri oluşturun
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 989014bb512ec77af908d823390b1e95b9a7872c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248237"
---
# <a name="build-office-solutions"></a>Office çözümleri oluşturun
  Genel olarak, derleme ve hata ayıklama Office projeleri derleme ve Windows Forms gibi Visual Studio'da proje türlerinde hata ayıklama ile aynı olur. Bu bölümdeki konular, mevcut farkları açıklamaktadır. Uygulamaları oluşturma hakkında genel bilgi için bkz. [derlemek ve oluşturmak Visual Studio'da](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Office deneyiminiz boyunca genişleten çözümleri geliştirme yapmakla mı ilgileniyorsunuz [birden çok platform](https://dev.office.com/add-in-availability)? Yeni kontrol [Office eklentilerini modeli](https://dev.office.com/docs/add-ins/overview/office-add-ins). Office eklentileri, VSTO eklentileri ve çözümlerle karşılaştırıldığında küçük ayak izine sahip ve neredeyse tüm web teknolojisi, HTML5, JavaScript, CSS3 ve XML gibi programlama kullanarak oluşturabilirsiniz.  
  
## <a name="project-output-for-office-projects"></a>Office projeleri için proje çıktısı  
 Office projeleri çıkış konumu *projectname*\bin\release veya *projectname*\bin\debug. Bir dağıtım dizinine oluşturulamıyor.  
  
### <a name="document-level-projects"></a>Belge düzeyi projeleri  
 Belge düzeyi projesi oluşturduğunuzda proje çıktısına aşağıdakiler dahildir:  
  
-   Proje belgenin bir kopyasını.  
  
-   Sahip başvurulmuş tüm Derlemelerle ve proje derlemesi kendi **Yereli Kopyala** özelliğini **true**.  
  
-   Dosya adı uzantısına sahip uygulama bildirimini *.manifest*. Daha fazla bilgi için [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).  
  
-   Dosya adı uzantısına sahip olan dağıtım bildirimi *.vsto*. Daha fazla bilgi için [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Bir program veritabanı (*PDB*) dosyası.  
  
> [!NOTE]  
>  Yerel bilgisayar yerine bir uzak konuma bir belge düzeyi çözüm oluşturuyorsanız, tam yolunu uygulamanın Güven Merkezi'ndeki güvenilen konumlar listesine ekleyin. Daha fazla bilgi için bkz belgelere güven verme adlı bölüme [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Uygulama düzeyi projeleri  
 Bir VSTO eklenti projesi oluşturduğunuzda, proje çıktısına aşağıdakiler dahildir:  
  
- Sahip başvurulmuş tüm Derlemelerle ve proje derlemesi kendi **Yereli Kopyala** özelliğini **true**.  
  
- Dosya adı uzantısına sahip uygulama bildirimini *.manifest*. Daha fazla bilgi için [Office çözümleri için uygulama bildirimleri](../vsto/application-manifests-for-office-solutions.md).  
  
- Dosya adı uzantısına sahip olan dağıtım bildirimi *.vsto*. Daha fazla bilgi için [Office çözümleri için dağıtım bildirimleri](../vsto/deployment-manifests-for-office-solutions.md).  
  
- Bir program veritabanı (*PDB*) dosyası proje derlemesi için.  
  
  VSTO eklentisi projeleri için derleme işlemi, ayrıca geliştirme bilgisayarında VSTO eklenti yüklemek için gerekli kayıt defteri girdileri kümesini oluşturur. Daha fazla bilgi için [VSTO eklentileri için kayıt defteri girdileri](../vsto/registry-entries-for-vsto-add-ins.md).  
  
  Form bölgeleri içeren bir Outlook VSTO eklentisi projesi oluşturun, derleme işlemi aşağıdaki ek bilgileri kayıt defterine ekler:  
  
- Bir veya daha fazla form bölgeleri ile ilişkili her ileti sınıfı için bir anahtar.  
  
- Her form bölgesi ve Outlook VSTO eklentisi adını temsil eden bir ilişkili değer için bir giriş.  
  
  Outlook form bölgeleri yüklemek için bu bilgiler gerekiyor.  
  
## <a name="referenced-assemblies"></a>Başvurulan derlemeler  
 Office çözümleri oluşturma projenizden (sınıf kitaplığı projeleri dahil) derlemelere başvurabilir. Her başvurulan derleme adında bir özelliğe sahiptir **Yereli Kopyala**. **Yerele Kopyala** derleme çıktı dizinine kopyalanır belirtir. Varsayılan olarak ayarlanmış **true**. Olan her başvurulan derleme **Yereli Kopyala** kümesine **true** çıkış dizinine kopyalanır.  
  
## <a name="security-during-the-build-process"></a>Derleme işlemi sırasında güvenlik  
 Visual Studio, derleme işlemi sırasında çözüme güven kazandırmak için geliştirme bilgisayarında güvenlik ayarlarını otomatik olarak yapılandırır. Bu çözümün, hata ayıklarken çalışmasına olanak sağlar.  
  
 Office projeleri, yayımcı doğrulamak için sertifikaları kullanır. Visual Studio otomatik olarak Office çözümleri tanımlamak için geçici bir sertifika oluşturur ve geliştirme bilgisayarında geçici sertifikasına güvenmek için yapılandırır.  
  
 Daha fazla bilgi için [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Ağ projeleri  
 Bir ağ paylaşımında derleme veya belge konumu ise yerel (kullanıcı düzeyinde) güvenlik ilkesi güncelleştirmesi çözümün çalışmasına izin vermek için yeterli değil. Bir yönetici, derlemeler ve çözüm çalışmadan önce bir ağ paylaşımında olan belgeler için tam güven makine düzeyinde vermeniz gerekir. Güvenlik İlkesi ayarlama hakkında daha fazla bilgi için bkz. [güvenli Office çözümleri](../vsto/securing-office-solutions.md).  
  
 Belge düzeyinde projeler için belgenin tam konumunu Office güvenilir klasörler listesine eklemelisiniz. Daha fazla bilgi için [belgelere güven verme](../vsto/granting-trust-to-documents.md).  
  
## <a name="change-the-platform-target"></a>Platform hedefi Değiştir  
 Varsayılan olarak, Office projeleri için platform hedefi olan **herhangi bir CPU**. Genellikle, bu ayar değiştirmemesi gerekir. İle oluşturulmuş office çözümlerini **herhangi bir CPU** Microsoft 32-bit ve 64 bit sürümlerde çalıştırma ayarı platform hedefi [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] veya [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Yalnızca 64 bit sürümlerinde Microsoft çalıştıracak bir çözüm oluşturuyorsanız, platform hedefi x64 ayarlamalısınız [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] veya [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], ve çözümünüzü yerel 64 bit API'lerini çağırır. Platform hedefi ayarlarını değiştirme hakkında daha fazla bilgi için bkz. [nasıl yapılır: Projeleri hedef platformlar için yapılandırma](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Platform hedefi x64 ayarlarsanız, çözüm Windows ya da Office 32-bit sürümlerinde çalışmaz. X64 platform hedefi bir 64 bit işlem içinde çalıştırmak için bir çözüm gerektirir.  
  
## <a name="use-the-clean-command"></a>Temizle komutunu kullanın  
 Yerleşik proje dosyalarını Geliştirme bilgisayarınızdan kaldırmak için kullanabileceğiniz **temiz** komutunu **derleme** menüde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. **Temiz** komut yapı çıkış konumunu tüm dosyaları siler. İçin uygulama düzeyi projelere **temiz** komutu, yapı işlemi tarafından oluşturulan kayıt defteri girdilerini de kaldırır.  
  
## <a name="related-topics"></a>İlgili konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Office projelerinde hata ayıklama](../vsto/debugging-office-projects.md)|Office projeleriyle ilgili sorunları gösterir.|  
|[İzlenecek yol: Excel için ilk belge düzeyi özelleştirmeyi oluşturma](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Excel için temel bir belge düzeyi özelleştirmeyi oluşturma işlemini gösterir.|  
|[Nasıl yapılır: Bir VSTO devre dışı bırakılmış eklentiyi yeniden etkinleştirme](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Bir VSTO sabit veya geçici devre dışı bırakılmış eklentiyi yeniden etkinleştirmek açıklar.|  
|[Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)|Çözümünüzdeki derlemelerin rolü ve Office çözümleri oluşturma hakkında bilgi için bağlantılar sağlar.|  
  
  