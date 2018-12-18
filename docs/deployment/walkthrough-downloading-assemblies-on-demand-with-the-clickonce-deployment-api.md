---
title: "İzlenecek yol: ClickOnce dağıtım API'si ile isteğe bağlı derlemeleri indirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- assemblies, downloading [ClickOnce]
- ClickOnce deployment, on-demand download
- on-demand assemblies, ClickOnce
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6338044dff5aa5b0555b15b689c04ddd406c50f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887663"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce dağıtım API'si ile isteğe bağlı derlemeleri indirme
Varsayılan olarak, tüm derlemelerin dahil bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamayı ilk kez çalıştırdığınızda, uygulama yüklenir. Ancak, kullanıcıların küçük bir kümesi tarafından kullanılan uygulamanızın parçalarını olabilir. Bu durumda, yalnızca türlerinden oluşturduğunuzda bir derlemeyi indirmek istediğiniz. Aşağıdaki örneklerde, belirli bütünleştirilmiş kodların "isteğe bağlı" olarak, uygulamanızda işaretlenecek gösterilmiştir ve yer alan kullanarak indirmek nasıl sınıfları <xref:System.Deployment.Application> ortak dil çalışma zamanı (CLR) onları talep ettiğinde ad alanı.  
  
> [!NOTE]
>  Bu yordamı kullanmak için tam güvende çalıştırmak uygulamanız gerekir.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlerden biri gerekir:  
  
-   Windows SDK'sı. Windows SDK'sı, Microsoft Download Center'dan gelen indirilebilir.  
  
-   Visual Studio.  
  
## <a name="create-the-projects"></a>Projeleri oluşturma  
  
#### <a name="to-create-a-project-that-uses-an-on-demand-assembly"></a>İsteğe bağlı bütünleştirilmiş kodu kullanan bir proje oluşturmak için  
  
1. ClickOnceOnDemand adlı bir dizin oluşturun.  
  
2. Windows SDK komut istemi açın veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] komut istemi.  
  
3. ClickOnceOnDemand dizine geçin.  
  
4. Aşağıdaki komutu kullanarak bir ortak/özel anahtar çifti oluşturun:  
  
   ```cmd  
   sn -k TestKey.snk  
   ```  
  
5. Not Defteri veya başka bir metin düzenleyicisi kullanarak adlı bir sınıf tanımlama `DynamicClass` adlı tek bir özellik ile `Message`.  
  
    [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
    [!code-csharp[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6. Metin adlı bir dosya kaydedin *ClickOnceLibrary.cs* veya *ClickOnceLibrary.vb adıyla*için kullandığınız dile bağlı olarak *ClickOnceOnDemand* dizin.  
  
7. Dosyanın bir derleme içine derleyin.  
  
   ```csharp  
   csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
   ```  
  
   ```vb  
   vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
   ```  
  
8. Derleme için ortak anahtar belirteci almak için aşağıdaki komutu kullanın:  
  
   ```cmd  
   sn -T ClickOnceLibrary.dll  
   ```  
  
9. Düzenleyici metni kullanarak yeni bir dosya oluşturun ve aşağıdaki kodu girin. Bu kod gerekli olduğunda ClickOnceLibrary derlemesini yükleyen bir Windows Forms uygulaması oluşturur.  
  
     [!code-csharp[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Kod içinde çağrısını bulun <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Ayarlama`PublicKeyToken` daha önce aldığınız değeri.  
  
12. Dosya olarak kaydedin *Form1.cs* veya *Form1.vb*.  
  
13. Bunu aşağıdaki komutu kullanarak bir yürütülebilir dosyada derleyin.  
  
    ```csharp  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## <a name="mark-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretleyin  
  
#### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-mageuiexe"></a>MageUI.exe kullanarak isteğe bağlı olarak, ClickOnce uygulamanızı derlemeleri işaretlemek için  
  
1.  Kullanarak *MageUI.exe*, uygulama bildiriminde açıklandığı gibi oluşturmak [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Uygulama bildirimi için aşağıdaki ayarları kullanın:  
  
    -   Uygulama bildirimi adı `ClickOnceOnDemand`.  
  
    -   Üzerinde **dosyaları** sayfasında *ClickOnceLibrary.dll* satır, Ayarla **dosya türü** sütuna **hiçbiri**.  
  
    -   Üzerinde **dosyaları** sayfasında *ClickOnceLibrary.dll* satır, tür `ClickOnceLibrary.dll` içinde **grubu** sütun.  
  
2.  Kullanarak *MageUI.exe*, açıklanan şekilde bir dağıtım bildirimi oluşturmak [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım bildirimi için aşağıdaki ayarları kullanın:  
  
    -   Dağıtım bildiriminin adı `ClickOnceOnDemand`.  
  
## <a name="testing-the-new-assembly"></a>Yeni bir derleme test etme  
  
#### <a name="to-test-your-on-demand-assembly"></a>İsteğe bağlı derlemenizi test etmek için  
  
1. Karşıya yükleme, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Web sunucusuna dağıtımı.  
  
2. İle dağıtılan uygulamanızı başlatın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım bildirimine URL girerek bir Web tarayıcısı. Çağırırsanız, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama `ClickOnceOnDemand`ve kök dizinine karşıya yükleyin, URL'niz şuna benzer:  
  
   ```  
   http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
   ```  
  
3. Ana form görüntülendiğinde basın <xref:System.Windows.Forms.Button>. Bir dizedeki bir "Hello, World!" yazan bir ileti kutusu penceresini görmeniz gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 <xref:System.Deployment.Application.ApplicationDeployment>