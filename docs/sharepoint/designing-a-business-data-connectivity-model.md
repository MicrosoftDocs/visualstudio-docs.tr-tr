---
title: İş verileri bağlantı modeli tasarlama | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 27b83cefdaa24e5a439352318aa149ec4e24d09d
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327248"
---
# <a name="design-a-business-data-connectivity-model"></a>İş verileri bağlantı modeli tasarlama
  İş verileri bağlantı (BDC) hizmeti için bir model için bir model dosyası varlıkları ve yöntemleri ekleyerek geliştirebilirsiniz. Bir varlık veri alanları koleksiyonunu açıklar. Örneğin, bir varlığın bir veritabanındaki bir tablo temsil edebilir. Bir yöntem ekleme, silme veya varlıklar tarafından temsil edilen veri güncelleştirme gibi bir görevi gerçekleştirir. Daha fazla bilgi için bkz: [iş verilerini SharePoint ile tümleştirmek](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="add-entities"></a>Varlıklar ekleme
 Bir varlık sürükleyerek ya da kopyalayarak ekleyebilirsiniz bir **varlık** Visual Studio'dan **araç** BDC tasarımcıya. Daha fazla bilgi için bkz: [nasıl yapılır: bir modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Varlık alanlarını bir sınıfta tanımlayın. Örneğin, adında bir alan ekleyebilirsiniz `Address` için bir `Customer` sınıfı. Projeye yeni bir sınıf ekleyin veya Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) gibi diğer araçları kullanarak oluşturduğunuz varolan bir sınıfa kullanın. Varlık adı ve varlığı temsil eden sınıf adını eşleşen başlatmanız gerekmez. Modelinizde yöntemleri tanımlarken varlık sınıfı ilgilidir.  
  
## <a name="add-methods"></a>Yöntem ekleme
 Kullanıcıların görüntüleme, ekleme, güncelleştirme veya bir liste veya modelini temel alan Web Bölümü bilgileri silmek zaman BDC hizmet modelinizi yöntemleri çağırır. Model kullanıcının gerçekleştirebileceği her görev için bir yöntem eklemeniz gerekir. Beş temel yöntemi türlerinden birini seçerek yöntemleri oluşturma **BDC yöntem ayrıntıları** penceresi. Aşağıdaki tabloda bir BDC modeli beş temel yöntemlerini açıklar.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|Bulucu|Varlık örneklerinin bir koleksiyonunu döndürür. Kullanıcı listesi veya bir Web Bölümü açıldığında çağrılır. Daha fazla bilgi için bkz: [nasıl yapılır: bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md).|  
|Belirli Bir Bulucu|Belirli bir varlık örneğini döndürür. Bir kullanıcı bir liste belirli bir öğenin ayrıntılarını görüntülediğinde çağrılır. Daha fazla bilgi için bkz: [nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Oluşturucu|Yeni veriler bir varlık veri kaynağına ekler. Kullanıcıların seçtiğinizde adlı **yeni öğe** modelini temel alan bir liste şeridinde düğmesini. Daha fazla bilgi için bkz: [nasıl yapılır: bir yaratıcı yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md).|  
|Güncelleştirici|Bir listedeki verileri değiştirir. Kullanıcılar listedeki bilgileri güncelleştirdiğinizde çağrılır. Daha fazla bilgi için bkz: [nasıl yapılır: bir güncelleyici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md).|  
|Silici|Verileri kaldırır. Kullanıcılar listeden bir öğe sildiğinizde çağrılır. Daha fazla bilgi için bkz: [nasıl yapılır: bir Silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## <a name="define-method-parameters"></a>Yöntem parametreleri tanımlayın
 Bir yöntem oluşturduğunuzda, Visual Studio yöntemi türü için uygun olan giriş ve çıkış parametrelerini ekler. Bu parametreler yalnızca yer tutucuları bağlıdır. Çoğu durumda, böylece geçirin veya dönüş doğru veri türü parametreleri değiştirmeniz gerekir. Örneğin, varsayılan olarak, bir Bulucu yöntemi bir dize döndürür. Çoğu durumda, böylece varlık koleksiyonunu döndürür bulucu yönteminin dönüş parametresi değiştirmek istediğiniz. Bu parametrenin tür tanımlayıcısını değiştirerek yapabilirsiniz. Bir tür tanımlayıcı bir parametresinin veri türü tanımlayan öznitelikleri koleksiyonudur. Daha fazla bilgi için bkz: [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Visual Studio, model parametrelerinde arasında tür tanımlayıcısı kopyalamanıza olanak sağlar. Örneğin, adlandırılmış bir tür tanımlayıcı tanımlayabilir `CustomerTD` dönüş parametresi için `GetCustomer` yöntemi. Kopyalayabilirsiniz `CustomerTD` tür tanımlayıcısı içinde **BDC Gezgini**ve bu tür tanımlayıcı giriş parametresi için yapıştırın `CreateCustomer` yöntemi. Bu, aynı tür tanımlayıcısı birden çok kez tanımlamak zorunda kalmaktan önler.  
  
## <a name="method-instances"></a>Yöntem örneği
 Bir yöntem oluşturduğunuzda, Visual Studio varsayılan yöntem örneği ekler. Yöntem örneği, bir yöntem artı parametrelerinin varsayılan değerleri başvurusudur. Tek bir yöntem birden çok yöntem örneği olabilir. Her yöntem imzası bileşimini ve varsayılan değerleri kümesi örneğidir. Daha fazla bilgi için bkz: [nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Projeyi çalıştırdığınızda yöntemi örnekleri SharePoint listesi yukarıdaki açılır listede görüntülenir. Kullanıcılar verileri görüntülemek için yöntemi örneklerini seçebilirler.  
  
 Yöntem örneği için varsayılan değerler eklemek için model XML doğrudan değiştirmeniz gerekir. Daha fazla bilgi için bkz: [DefaultValue](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## <a name="add-filter-descriptors"></a>Filtre tanımlayıcıları ekleyin
 Modelin tüketicileri bazı ölçütlere uyan bir varlık örneğini almak isteyebilirsiniz. Bu işlevselliği etkinleştirmek için bir yönteme filtre tanımlayıcısı ekleyebilirsiniz. Filtre tanımlayıcıları bunlar yürütmeden önce yöntemlere değerleri geçirerek yöntemi sonuç kümesini filtrelemek model tüketicileri etkinleştirin. Daha fazla bilgi için bkz: [nasıl yapılır: dış sistem sınırı örneklerine işlemlerinden filtre parametreler ekleme](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 SharePoint filtre değerlerini sağlamak kullanıcıların sağlayan birçok özellik sağlar. Örneğin, iş verileri Web bölümlerini bir filtre metin kutusu sağlar. Kullanıcılar, metin kutusuna bir değer girerek listesindeki verileri sınırlayabilirsiniz. Bir yöntemine filtre tanımlayıcısı ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### <a name="filter-descriptor-properties"></a>Filtre tanımlayıcısı özellikleri
 Değerini ayarlamalısınız **ilişkili tür tanımlayıcı**, **adı**, ve **türü** filtre tanımlayıcısı özelliklerini. Diğer tüm özellikleri isteğe bağlıdır.  
  
 **İlişkili tür tanımlayıcı** özelliği için bir giriş parametresi filtre tanımlayıcısı ilişkilendirir. Bir kullanıcı bir filtre değeri sağladığında, BDC hizmeti giriş parametresi kullanarak bu değeri yöntemin içine geçirir.  
  
 **Türü** özelliği, kullanmak istediğiniz filtreleme deseni açıklar. SharePoint'te, seçtiğiniz filtreleme düzeni kullanıcı arabirimi (UI) içinde görüntülenen metni etkiler. Örneğin, metnin bir karşılaştırıcı filtreleme desen **eşittir** iş veri Web Bölümü yukarıda bir denetim olarak görünür. Her filtre desen hakkında daha fazla bilgi için bkz: [, filtreleri tarafından desteklenen türleri BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Filtre tanımlayıcısı özellikleri hakkında daha fazla bilgi için bkz: [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### <a name="provide-default-values"></a>Varsayılan değerleri sağlayın
 Bazı durumlarda, kullanıcı bir filtre değeri sağlamayabilir. Yöntem örneği için varsayılan bir değer ekleyerek veya varsayılan değer yönteminizi kodda ayarlayarak varsayılan bir değer belirtebilirsiniz. Yöntem örneği için varsayılan bir değer ekleme hakkında daha fazla bilgi için bkz: [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282). Yönteminizi kodda bir giriş parametresinin varsayılan değeri ayarlamak nasıl bir örnek için bkz: [nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## <a name="validate-the-model"></a>Model doğrulama
 Geliştirme sırasında modelinizi doğrulayabilirsiniz. Visual Studio modelinizi beklendiği gibi davranmakta engelleyebilir sorunlarını tanımlar. Visual Studio'da bu sorunları görünür **hata listesi**.  
  
 BDC Tasarımcı kısayol menüsünü açarak ve ardından bir model doğrulama **doğrulama**. Model hatalar içeriyorsa, görüntülendikleri **hata listesi**. Hızlı bir şekilde hata listesinde çift tıklayarak bir hata içeren kodu imleci taşıyabilirsiniz. Alternatif olarak, seçtiğiniz **F8** veya **Shift**+**F8** art arda adım ileri veya geri listesinde hatalar arasında anahtarları.  
  
 Herhangi bir yolla model kurallarını ihlal edildiğinde doğrulama hataları ortaya çıkabilir. Örneğin, varsa **IsCollection** bir tür tanımlayıcı özelliği ayarlanmış **doğru**, ancak hiçbir alt tür tanımlayıcısı var, bir doğrulama hatası görünür. Visual Studio'da görünür bazı hatalar anlamak için bir BDC modeli kuralları başvurmak zorunda kalabilirsiniz **hata listesi**. BDC modeli kuralları hakkında daha fazla bilgi için bkz: [BDCMetadata şema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="debug-the-solution-that-contains-the-model"></a>Model içeren çözümü hata ayıklama
 Visual Studio'da kod hatalarını gibi kodunuzu ayıklayabilirsiniz. Kodunuzun hatalarını ayıklamak için kesme noktaları kodunuzda herhangi bir yerde ayarlamak ve hata ayıklayıcısı başlatın. Visual Studio SharePoint sitesini açar. SharePoint içinde bir liste veya iş verilerinizi kullanan Web bölümü oluşturun. Sonra kodunuzu geçebilirsiniz. SharePoint projeleri hata ayıklama hakkında daha fazla bilgi için bkz: [sorun giderme SharePoint çözümlerini](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 Ayrıca, projeye ekleyin özel derlemeler kodda ayıklayabilirsiniz. Ancak, özel bir derlemeyi kodda hata ayıklamak için derleme için çözüm paketi eklemeniz gerekir. Daha fazla bilgi için bkz: [nasıl yapılır: ek derlemeler ekleyip](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Özel bir derlemeyi projenize ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir BDC özelliğine özel bir derlemeyi dahil etme](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### <a name="configure-bdc-security"></a>BDC güvenliği yapılandırma
 Çözümünüzü ayıklayabilirsiniz önce SharePoint güvenlik ayarlarını değiştirmeniz gerekebilir. Bu ayarları değiştirmek için iş verileri bağlantı hizmeti uygulaması SharePoint 2010 Merkezi Yönetim Web sitesini açın. İçinde **meta veri deposu izinlere** iletişim kutusu, kullanıcı hesabını ekleyin ve ardından aşağıdaki seçeneklerden birini seçin:  
  
|Görev|Seçenek|  
|----------|------------|  
|Modelleri BDC hizmeti dağıtmak için.|Düzenle|  
|Listeler ve Web Bölümleri'ı kullanarak dış oluşturmak için modelinizde (varlık) içerik türleri.|İstemcilerde seçilebilir|  
|Oluşturma, okuma, güncelleştirme ve varlık verilerini silmek için.|Yürütme|  
  
 Bu ayarlar hakkında daha fazla bilgi için bkz: [İş Verileri Bağlantı Hizmeti Yönetimi](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 Tek tek modellerin veya dış içerik türleri için güvenlik izinleri de ayarlayabilirsiniz. Bir modelin güvenlik izinleri ayarlama hakkında daha fazla bilgi için bkz: [BDC modeli Yönetim](http://go.microsoft.com/fwlink/?LinkID=178884). Dış içerik türünün güvenlik izinleri ayarlama hakkında daha fazla bilgi için bkz: [dış içerik türü Yönetim](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Bir çözüm, yerel SharePoint sunucu üzerinde hata ayıklamak için bu ayarları kullanın. Üretim SharePoint sunucusu üzerine BDC ilgili güvenlik ayarlarını yapılandırma hakkında daha fazla bilgi için bkz: [İş Verileri Bağlantı Hizmetleri güvenliğine genel bakış](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### <a name="retract-models-that-become-corrupt"></a>Bozulduğunu modelleri Ayıkla
 Hata ayıklayıcı ilk başlattığınızda Visual Studio için SharePoint tüm modelde dağıtır. Her için bundan sonra Visual Studio SharePoint modelinde dağıtımlar arasında yaptığınız tüm değişiklikler ile güncelleştirir.  
  
 SharePoint modelden tamamen geri çekmek için Visual Studio istediğiniz durumlar olabilir. Örneğin, bir model bozuk olabilir.  SharePoint modelinize yeniden dağıtmak için ayarlanmış **Artımlı güncelleştirme** modele özelliğinin **False**, ve hata ayıklayıcısı başlatın. **Artımlı güncelleştirme** özelliği görünür **özellikleri** modelde gösteren düğümü seçtiğinizde penceresi **BDC Gezgini**. Varsayılan olarak, model adıdır **BdcModel1**.  
  
### <a name="change-identifier-names-of-entities-in-the-model"></a>Varlık modeli tanımlayıcı adlarını değiştirin
 Model dağıttıktan sonra bir tanımlayıcı adını değiştirirseniz, bir dağıtım hatası alabilirsiniz. Bu hata ayarlayarak çözümlenemiyor **Artımlı güncelleştirme** modele özelliğinin **False**. Model el ile geri çekmek ve çözümü yeniden dağıtın. Daha fazla bilgi için bkz: [sorun giderme SharePoint çözümlerini](../sharepoint/troubleshooting-sharepoint-solutions.md). Ayarlayarak bu hatayı önleyebilirsiniz **Artımlı güncelleştirme** özelliğine **False** model başlangıçta dağıtmadan önce.  
  
## <a name="locate-documentation-for-bdc-model-elements"></a>BDC modeli öğeleri belgelerine bulun
 Visual Studio modeline her bir varlık için bir XML öğesi ekler yöntemi veya oluşturduğunuz başka bir öğe. Öğesi özniteliklerini görünür özellikleri olarak **özellikleri** penceresi. Öğeleri ve model tasarlarken, Visual Studio'nun oluşturduğu öznitelikleri hakkında daha fazla bilgi için bkz: [BDCMetadata şema](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[BDC modeli tasarım araçlarına genel bakış](../sharepoint/bdc-model-design-tools-overview.md)|Bir model için BDC görsel olarak tasarlamak için kullanabileceğiniz araçlar açıklanmaktadır.|  
|[Nasıl yapılır: bir modele bir varlık ekleme](../sharepoint/how-to-add-an-entity-to-a-model.md)|Dış içerik türlerini ya da varlıkları modele eklemek gösterilmiştir.|  
|[Nasıl yapılır: bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-finder-method.md)|Bir liste veya Web Bölümü varlıkların listesini görüntülemek kullanıcıların sağlayan bir yöntem eklemek gösterilmiştir.|  
|[Nasıl yapılır: belirli bir Bulucu yöntemi ekleme](../sharepoint/how-to-add-a-specific-finder-method.md)|Belirli bir varlık ayrıntılarını görüntülemek kullanıcıların sağlayan bir yöntem eklemek gösterilmiştir.|  
|[Nasıl yapılır: bir yaratıcı yöntemi ekleme](../sharepoint/how-to-add-a-creator-method.md)|Kayıt bir veri kaynağına doğrudan bir liste veya Web Bölümü eklemek kullanıcıların sağlayan bir yöntem eklemek gösterilmiştir.|  
|[Nasıl yapılır: bir Silici yöntemi ekleme](../sharepoint/how-to-add-a-deleter-method.md)|Kullanıcıların listesinin bir kullanıcı arabirimi (UI) veya Web Bölümü seçenekleri kullanarak bir veri kaynağından verileri kaldırma olanak sağlayan bir yöntem eklemek gösterilmiştir.|  
|[Nasıl yapılır: bir güncelleyici yöntemi ekleme](../sharepoint/how-to-add-an-updater-method.md)|Kullanıcıların bir veri kaynağındaki veri kayıtlarını doğrudan bir liste veya Web Bölümü değiştirmesine olanak tanır yönteminin nasıl ekleneceğini gösterir.|  
|[Nasıl yapılır: bir yönteme parametre ekleme](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Visual Studio yöntemi Ayrıntıları penceresinde bir yönteme giriş ve dönüş parametreleri eklemek için nasıl kullanılacağını gösterir.|  
|[Nasıl yapılır: bir parametrenin tür tanımlayıcısını tanımlama](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Parametre veri türleri modelde tanımlamak gösterilmiştir.|  
|[Nasıl yapılır: yöntem örneği tanımlama](../sharepoint/how-to-define-a-method-instance.md)|BDC yürüten bir yöntemin bir örneğinin nasıl oluşturulacağını gösterir.|  
|[Nasıl yapılır: bir Bulucu yöntemine filtre tanımlayıcısı ekleme](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Kullanıcıların bir Bulucu yöntemi tarafından döndürülen örnek sayısını sınırlamak gösterilmiştir.|  
|[Varlıklar Arasında İlişkilendirme Oluşturma](../sharepoint/creating-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkiler nasıl tanımlayabilirsiniz açıklar. İş Verileri Web bölümlerini, dış listeler ve özel uygulamalar kullanıcı arabiriminde (UI) bu veri ilişkileri görüntüleyebilirsiniz.|  
|[Nasıl yapılır: varlıklar arasında ilişkilendirme oluşturma](../sharepoint/how-to-create-an-association-between-entities.md)|Modeldeki varlıklar arasındaki ilişkileri tanımlamak gösterilmiştir.|  
|[İzlenecek yol: iş verileri kullanarak bir dış liste SharePoint](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Oluşturma ve test kişiler SharePoint Dış listede görüntüler modeli gösteren adım adım yönergeler sağlar.|  
|[İş verilerini SharePoint ile tümleştirme](../sharepoint/integrating-business-data-into-sharepoint.md)|Oluşturma ve modelleri BDC hizmeti için tasarlama genel bir bakış sağlar.|  
  
