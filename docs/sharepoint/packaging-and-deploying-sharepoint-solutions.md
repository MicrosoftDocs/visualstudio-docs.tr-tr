---
title: SharePoint çözümlerini paketleme ve dağıtma | Microsoft Docs
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
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c5993f09581faf6e3cedb4c71598ea26b16b699
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863275"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Paketleme ve SharePoint çözümlerini dağıtma
  Genellikle, bir SharePoint çözüm, bir çözüm paketi (.wsp) dosyası kullanarak bir SharePoint sunucusuna dağıtılır. Visual Studio, SharePoint Proje öğeleri özelliklerini düzenlemek ve SharePoint özelliklerinizi dağıtmak için bir paket oluşturmak için kullanabilirsiniz.  
  
 Bu konuda, aşağıdaki bilgiler sağlanmaktadır:  
  
-   [Özellikler ve paketleri oluşturma](#Creating)  
  
-   [Özellik ve araç desteği paketleme](#Tools)  
  
-   [SharePoint çözümlerini dağıtma](#Deploying)  
  
-   [Dosyaları SharePoint çözümlerini dağıtma](#DeployingFiles)  
  
## <a name="create-features-and-packages"></a>Özellikler ve paketler oluşturun
 Visual Studio ile ilgili SharePoint öğeleri gruplandırmak için kullanabileceğiniz bir *özellik*. Örneğin, bir kişi liste tanımı için bir özellik liste örneği ve liste tanımını içerebilir. Dağıtım amaçları için tek bir özelliği bu iki öğenin birleştirebilirsiniz. Özellikler hakkında daha fazla bilgi için bkz. [yapı taşı: Özellikler](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Ardından, bir SharePoint çözüm paketini oluşturabilirsiniz (*.wsp*) birden çok özellik paketi için site tanımları, derlemeleri ve diğer dosyaları bir biçimde SharePoint tarafından dosyaları dağıtmak için gereken dosyaları depolayan tek bir pakette Sunucu. Daha fazla bilgi için [yapı taşı: çözümleri](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
## <a name="feature-and-packaging-tool-support"></a>Özellik ve paketleme araç desteği
 Visual Studio'da SharePoint geliştirme araçları, hızla özellikleri ve daha kolay dağıtım için çözüm paketleri SharePoint dosyalarınızı düzenlemek için kullanabilirsiniz. Özellik ve çözüm paketini yapılandırmak için aşağıdaki araçları kullanabilirsiniz.  
  
-   Özellik Tasarımcısı ve paket Tasarımcısı.  
  
-   Paketleme Gezgini, bir araç penceresi.  
  
-   Çözüm Gezgini.  
  
### <a name="feature-designer-and-package-designer"></a>Özellik Tasarımcısı ve paket Tasarımcısı
 Özellikler oluşturmak, kapsamı ayarla ve diğer özellikleri, özellik Tasarımcısı kullanarak bağımlılıkları olarak işaretleyin. Tasarımcı, ayrıca her bir özellik tanımlayan son XML dosyasını görüntüler. Daha fazla bilgi için [oluşturma SharePoint özelliklerini](../sharepoint/creating-sharepoint-features.md).  
  
 Özelliği bir özel Web sitesi veya Web sitelerinin gruba ayarlayarak geçerli kendi *kapsam* özellik Tasarımcısı'nda. Tek bir Web sitesi için bir özelliği etkinleştirilmişse, özellik, yalnızca bu belirli bir Web sitede çalışır. Bir site koleksiyonu için bir özelliği etkinleştirilmişse, özellik öğeleri tüm site koleksiyonuna uygulayın. Daha fazla bilgi için [öğe kapsamı](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Diğer özelliklerini özelliğinizi kullanır, ayarlayabileceğiniz bir *özellik etkinleştirme bağımlılığı* bağımlı özellikler özelliğinizi kullanılabilir duruma getirmeden önce işaretlenecek. Özellik etkinleştirme bağımlılığı bağımlı özellikler bu kapsamda zaten etkin değilse denetler. Daha fazla bilgi için [etkinleştirme bağımlılıkları ve kapsam](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Paket Tasarımcısı'nda tek bir çözüm pakete SharePoint öğeleri gruplayın ve dağıtım sırasında Web sunucusu sıfırlandığında yapılandırın. Dağıtım sunucusu türü ayarlamak için kullanın **özellikleri** penceresi. Tasarımcı, paket içeriğini tanımlayan XML dosyasını da oluşturur. Daha fazla bilgi için [oluşturma SharePoint çözüm paketleri](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Dağıtım sırasında SharePoint sunucusuna çözüm dosyalarını kopyalamak için Internet Information Services (IIS) hizmeti durduruldu. Visual Studio'da paket Tasarımcısını kullanarak, Web sunucusunun yeniden başlatılması gerekiyor yoksa seçebilirsiniz. Çözüm bir ön uç Web sunucusuna ya da bir uygulama sunucusu dağıtılırsa yapılandırmak için kullanın **özellikleri** penceresi. Daha fazla bilgi için [çözüm öğesi (Çözüm)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Paketleme Gezgini  
 Paket Tasarımcısı ve özellik Tasarımcısı'nı tamamlamak için SharePoint dosyalarınızı özellikleri ve paketler halinde gruplandırmak için paketleme Gezgini'ni kullanabilirsiniz. Buna paket, özellikleri, SharePoint Proje hiyerarşik görünümünü görebilirsiniz öğeleri ve dosyaları. Paketleme Gezgini, aşağıdaki görevleri tamamlamak için kullanabileceğiniz bir araç penceresidir:  
  
- SharePoint Proje öğeleri ve dosyalarını açın.  
  
- Sürükleyip SharePoint Proje öğeleri bir özellikten bırakın.  
  
- Sürükleyip SharePoint Proje öğeleri ve özellikleri bir paketten diğerine bırakın.  
  
- Bir pakete yeni bir özellik ekleyin.  
  
- Bir özellik veya paket Tasarımcısı'nı açın.  
  
- Özellikleriniz ve paketleriniz doğrulayın.  
  
  Visual Studio'da SharePoint geliştirme araçları, Çözüm paketinin düzgün biçimlendirildiğini sağlamaya yardımcı olmak için doğrulama kuralları vardır. Ayrıca, kurallar doğrulayın *.wsp* çözüm dosyası başarılı bir şekilde dağıtılabilir ve bir SharePoint sunucusuna etkinleştirildi. Özellikler için XML şeması hakkında daha fazla bilgi için bkz. [özellik şemaları](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
  SharePoint Proje sistemi için özel özellik ve paket doğrulama kuralları ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: özel özellik ve paket doğrulama kuralları için SharePoint çözümleri oluşturma](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
  Paketleme Gezgini hakkında daha fazla bilgi için bkz: [nasıl yapılır: ekleme ve paketleme Gezgini'ni kullanarak, özellikler ve öğeler pakete kaldırma](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Çözüm Gezgini
 Gidin ve SharePoint proje dosyalarını açmak için Çözüm Gezgini'ni kullanabilirsiniz. Özellik Olay alıcıları özellikleri eklemek için Çözüm Gezgini'nde bağlam menüsünü kullanın ve kaynakları özellik. Ayrıca, özelliği tasarımcılar ve paket tasarımcıları için dağıtım paketlerini ve özellikleri yapılandırmak için açabilirsiniz.  
  
## <a name="deploy-sharepoint-solutions"></a>SharePoint çözümlerini dağıtma
 Özellikler ve Visual Studio'da paket özelleştirdikten sonra oluşturabileceğiniz bir *.wsp* dosyasını SharePoint sunucularına dağıtın. Visual Studio hata ayıklama ve test etmek için kullanabilirsiniz. *wsp* yalnızca geliştirme bilgisayarında SharePoint sunucusunda. İçin uzak bir SharePoint server, SharePoint çözümlerini dağıtma hakkında daha fazla bilgi için bkz. [bir çözüm dağıtma](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Dağıtım adımlarına geliştirme bilgisayarında de özelleştirebilirsiniz. Daha fazla bilgi için [dağıtma, yayımlama ve yükseltme SharePoint çözüm paketleri](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
## <a name="deploy-files-in-sharepoint-solutions"></a>Dosyaları SharePoint çözümlerini dağıtma
 SharePoint çözümünüz için bir SharePoint proje öğesi eklediğinizde, genellikle tüm dosyaları dahil gereklidir. Derlenmiş olabilecek dosyalar (kod dosyaları) çözümünün çıktı derlemesine üretip oluşturulur. Ancak, ayrıca derlenebilir olmayan dosyaları ekleme olabilir *.xml*, *.txt*, veya bir SharePoint projesi için kaynak dosyaları. Bu dosyalar otomatik olarak çözümünüzde paketlenmiş değil. Paketlenmiş emin olmak için ya da dosyaları eşlenmiş bir klasöre veya bir SharePoint proje öğesi ekleyin.  
  
 Çözüm dağıtılırken eşlenmiş bir klasöre eklenen dosyaları otomatik olarak SharePoint hive için kopyalanır. Bir SharePoint projesine eklenen dosyalar, belirtilen konuma dağıtılır **dağıtım konumu** kısmen ayarlanır her dosya için özelliğini temel alarak **dağıtım türü** özelliği. Varsayılan olarak, **dağıtım türü** özellik değeri **NoDeployment**, yani dosya çözümle birlikte dağıtılmaz. Dosyanın pakete eklemek bir özellik için başka bir değer ayarlamanız gerekir.  
  
 Örneğin, eklemek için bir *.xml* dosyasını bir SharePoint projesine, bu eylemlerden birini gerçekleştirin:  
  
- Bir SharePoint "Düzenler" eşlenen klasörü projenize ekleyin. Bu oluşturur **Çözüm Gezgini** adlı bir klasör **düzenleri** bir alt klasör proje için sahip. Ekleme *.xml* dosyasına yeni bir alt klasör. Varsayılan olarak, SharePoint dosya sisteminde dosya dağıtılır *... \TEMPLATE\LAYOUTS\\\<klasör adı >*. Eşlenmiş klasörler ekleme hakkında daha fazla bilgi için bkz: [nasıl yapılır: eşlenmiş klasörler ekleme ve kaldırma](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
- Ekleme *.xml* dosyasını bir SharePoint proje öğesi klasörüne ve ardından değiştirmek **dağıtım türü** özelliği *.xml* dosya **NoDeployment**  gibi başka bir ayarlamanın **RootFile** veya **ElementFile**. Uygun **dağıtım türü** ayarı, dosya ve proje üzerinde bağlıdır. Hakkında daha fazla bilgi için **dağıtım türü** özelliği belirleyebilmesini [geliştirme SharePoint çözümleri](../sharepoint/developing-sharepoint-solutions.md).  
  
  Çözümdeki belirli hiçbir projeye eklenen bir dosyayı geçerli değilse boş bir SharePoint projesi çözümünüze ekleyin ve ardından ek dosyalar ekleyin. Dosyaları SharePoint'te, özellikle içerik veritabanını dağıtmak için başka bir projeye bir modül eklemek ve Modülü dosyaları eklemek için alternatiftir. Daha fazla bilgi için [çözüme dosyaları dahil etmek için modül kullanma](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
 [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)   
 [Derleme ve SharePoint çözümlerinde hata ayıklama](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
