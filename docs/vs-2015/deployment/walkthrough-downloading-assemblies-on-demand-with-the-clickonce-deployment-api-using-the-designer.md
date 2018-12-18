---
title: "İzlenecek yol: ClickOnce dağıtım API'si Tasarımcısı'nı kullanarak ile isteğe bağlı derlemeleri indirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- Windows applications, ClickOnce deployments
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: 59a0dd5f-1cab-4f2f-b780-0ab7399905d5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 923951196487c9dc3f08b61879271fc71be373e4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245069"
---
# <a name="walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Varsayılan olarak, tüm derlemelerin dahil bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamayı ilk kez çalıştırdığınızda, uygulama yüklenir. Bununla birlikte, küçük bir grup kullanıcı tarafından kullanılan uygulamanızın parçalarını olabilir. Bu durumda, yalnızca türlerinden oluşturduğunuzda bir derlemeyi indirmek istediğiniz. Aşağıdaki örneklerde, belirli bütünleştirilmiş kodların "isteğe bağlı" olarak, uygulamanızda işaretlenecek gösterilmiştir ve yer alan kullanarak indirmek nasıl sınıfları <xref:System.Deployment.Application> bunları ortak dil çalışma zamanı talep ettiğinde ad alanı.  
  
> [!NOTE]
>  Bu yordamı kullanmak için tam güvende çalıştırmak uygulamanız gerekir.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-projects"></a>Proje oluşturma  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Visual Studio ile isteğe bağlı bütünleştirilmiş kodu kullanan bir proje oluşturmak için  
  
1.  Yeni bir Windows Forms projesi oluşturun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Üzerinde **dosya** menüsünde **Ekle**ve ardından **yeni proje**. Seçin bir **sınıf kitaplığı** adlandırın ve proje iletişim kutusunda `ClickOnceLibrary`.  
  
    > [!NOTE]
    >  Bu proje için kök ad alanı değiştirmek için proje özelliklerini değiştirmek tavsiye ederiz Visual Basic'te `Microsoft.Samples.ClickOnceOnDemand` veya tercih ettiğiniz bir ad alanı. Kolaylık olması için bu kılavuzda iki proje aynı ad alanında görüntülenir.  
  
2.  Adlı bir sınıf tanımlama `DynamicClass` adlı tek bir özellik ile `Message`.  
  
     [!code-csharp[ClickOnceLibrary#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs#1)]
     [!code-vb[ClickOnceLibrary#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb#1)]  
  
3.  Windows Forms projesinde seçin **Çözüm Gezgini**. Bir başvuru ekleyin <xref:System.Deployment.Application> derleme ve bir proje başvurusu `ClickOnceLibrary` proje.  
  
    > [!NOTE]
    >  Bu proje için kök ad alanı değiştirmek için proje özelliklerini değiştirmek tavsiye ederiz Visual Basic'te `Microsoft.Samples.ClickOnceOnDemand` veya tercih ettiğiniz bir ad alanı. Kolaylık olması için bu kılavuzda iki proje aynı ad alanında bulunur.  
  
4.  Formun sağ tıklayın, **kodu görüntüle** menüsünde ve formu aşağıdaki başvuruları ekleyin.  
  
     [!code-csharp[ClickOnceOnDemand#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#1)]
     [!code-vb[ClickOnceOnDemand#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#1)]  
  
5.  İsteğe bağlı olarak bu derlemeyi indirmek için aşağıdaki kodu ekleyin. Bu kod bir derleme kümesi kullanarak genel bir grup adı eşlemeyle ilgili bilgi gösterir <xref:System.Collections.DictionaryBase.Dictionary%2A> sınıfı. Biz yalnızca bu izlenecek yolda tek bir derleme indirme olduğundan, bizim grubunda yalnızca bir bütünleştirilmiş kod yoktur. Gerçek bir uygulamada, büyük olasılıkla, uygulamanızda aynı anda tek bir özellik ile ilgili tüm derlemeleri yüklemeye istersiniz. Eşleme tablosu indirme grubu adı ile bir özelliğe ait tüm DLL'ler ile ilişkilendirilmesi yoluyla bunu kolayca yapmanızı sağlar.  
  
     [!code-csharp[ClickOnceOnDemand#2](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#2)]
     [!code-vb[ClickOnceOnDemand#2](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#2)]  
  
6.  Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**. Sürükleme bir <xref:System.Windows.Forms.Button> gelen **araç kutusu** forma. Düğmeyi çift tıklatın ve aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
     [!code-csharp[ClickOnceOnDemand#3](../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs#3)]
     [!code-vb[ClickOnceOnDemand#3](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb#3)]  
  
## <a name="marking-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretleme  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Visual Studio kullanarak isteğe bağlı olarak, ClickOnce uygulamanızı derlemeleri işaretlemek için  
  
1.  Windows Forms projeye sağ **Çözüm Gezgini** tıklatıp **özellikleri**. Seçin **Yayımla** sekmesi.  
  
2.  Tıklayın **uygulama dosyaları** düğmesi.  
  
3.  ClickOnceLibrary.dll için bulun. Ayarlama **yayımlama durumu** açılan kutusuna **INCLUDE**.  
  
4.  Genişletin **grubu** açılır liste kutusundan seçip alt **yeni**. Bir ad girin `ClickOnceLibrary` yeni grup adı.  
  
5.  Açıklanan şekilde uygulamanızı yayımlamaya devam [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Bildirim oluşturma ve düzenleme Aracı'nı kullanarak isteğe bağlı olarak, ClickOnce uygulamanızı derlemeleri işaretlemek için-grafik istemcisi (MageUI.exe)  
  
1.  Oluşturma, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] açıklandığı bildirimlerini [izlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  MageUI.exe kapatmadan önce dağıtımınızın uygulama bildirimi içeren sekmesini seçip bu sekmede **dosyaları** sekmesi.  
  
3.  Uygulama dosyaları listesinde ClickOnceLibrary.dll'i bulun ve ayarlayın, **dosya türü** sütuna **hiçbiri**. İçin **grubu** sütununa, `ClickOnceLibrary.dll`.  
  
## <a name="testing-the-new-assembly"></a>Yeni bir derleme test etme  
  
#### <a name="to-test-your-on-demand-assembly"></a>İsteğe bağlı derlemenizi test etmek için  
  
1.  İle dağıtılan uygulamanızı başlatın [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].  
  
2.  Ana form görüntülendiğinde basın <xref:System.Windows.Forms.Button>. Bir dizede, "Hello, World!" okuyan bir ileti kutusu penceresini görmeniz gerekir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application.ApplicationDeployment>



