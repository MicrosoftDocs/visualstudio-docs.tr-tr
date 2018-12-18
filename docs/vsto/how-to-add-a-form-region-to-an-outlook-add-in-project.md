---
title: 'Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 875644c10b07eb9c2b338b5a3cdfc827a76a7b34
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549044"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme
  Standart veya özel bir Microsoft Office Outlook form kullanarak genişletmek için bir form bölgesi oluşturmak **yeni Outlook Form bölgesi** Sihirbazı. Yeni bir form bölgesi oluşturmak ve Visual Studio kullanıcı arabiriminde tasarım veya Outlook'ta tasarlanan form bölgesini içeri aktarabilir ve Visual Basic veya C# kodu ekleyin.  
  
 Başka bir Outlook projesinde kullanılan bir Outlook form bölgesi varsa, onu geçerli Outlook VSTO eklenti projenizde kullanarak tekrar kullanabilirsiniz **varolan öğeyi Ekle** iletişim kutusu. Daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>Yeni bir form bölgesini Outlook projesine eklemek için  
  
1.  Bir Outlook VSTO eklenti projesindeki oluşturun veya açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: Visual Studio oluşturma Office projelerinde](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  İçinde **Çözüm Gezgini**, Outlook VSTO eklenti projesi düğümünü seçin.  
  
3.  Üzerinde **proje** menüsünde tıklatın **Yeni Öğe Ekle**.  
  
4.  İçinde **Yeni Öğe Ekle** iletişim kutusunda **Outlook Form bölgesi**.  
  
5.  Form bölgesi için bir ad yazın **adı** kutusuna ve ardından **Ekle**.  
  
     **NewOutlook Form bölgesi** Sihirbazı'nı başlatır.  
  
6.  Üzerinde **nasıl form bölgesi oluşturmak istediğinizi seçin** sayfasında, yönetilen denetimleri görsel tasarımcıya sürükleyerek form bölgesi tasarlama veya Outlook'ta tasarlanan form bölgesini içeri istediğinizi seçin.  
  
    > [!NOTE]  
    >  Outlook'ta tasarlanan form bölgesini içeri aktarmak seçtiğiniz sonra bir Outlook Form depolama konumunu belirtmeniz gerekir (*.ofs*) dosyası. Yönetilen denetimleri Outlook'ta tasarım bir form bölgesi eklenemiyor; yalnızca var olan kullanıcı Arabirimi arka plan kod ekleyebilirsiniz. Daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
7.  Üzerinde **oluşturmak istediğiniz form bölgesini seçin** sayfasında, form bölgesi türlerini gözden geçirin ve seçin ve ardından **sonraki**. Form bölgesi türleri hakkında daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
8.  Üzerinde **açıklayıcı metin sağlayın ve görüntüleme tercihlerini seçin** sayfasında **adı** form bölgesi için bir ad yazın. Değişim ve Tümünü Değiştir form bölgesi türleri için **başlık** ve **açıklama** kutularıdır de kullanılabilir.  
  
     Form bölgesini dağıttığınız zaman ad, başlık ve açıklama Outlook'ta göründüğü hakkında daha fazla bilgi için bkz: [oluşturma Outlook form bölgeleri](../vsto/creating-outlook-form-regions.md).  
  
9. Form bölgesi görünmesini istediğiniz bir veya daha fazla görüntü modu seçin.  
  
     Tüm form bölgesi türleri Inspector, görünebilir içinde (öğeleri oluşturma) modunu oluşturun ve (öğeleri görüntüleme için) okuma modunda. Ayrıca bitişik, değişim ve Tümünü Değiştir form bölgesi türleri Okuma Bölmesi'nde yer alabilir.  
  
10. **İleri**'ye tıklayın.  
  
11. Üzerinde **bu form bölgesini görüntüleyecek ileti sınıflarını tanımlayın** sayfasında, standart Outlook ileti sınıflarını seçin veya bir veya daha fazla özel ileti sınıfları adlarını yazın ve ardından **son**. Daha fazla bilgi için bkz: [form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Form bölgesine çalışma zamanında erişme](../vsto/accessing-a-form-region-at-run-time.md)   
 [Outlook çözümleri](../vsto/outlook-solutions.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Yönergeler için Outlook form bölgeleri oluşturma](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)  
  