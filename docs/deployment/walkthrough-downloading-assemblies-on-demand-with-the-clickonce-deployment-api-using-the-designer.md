---
title: Tasarımcı kullanarak isteğe bağlı derlemeleri indirme (ClickOnce API)
description: Tasarımcı kullanarak, ClickOnce uygulamanızda belirli derlemeleri isteğe bağlı olarak nasıl işaretleyeceğinizi ve ortak dil çalışma zamanı için gereken durumlarda bunları indirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7bb30b26e859708d295a31bd45b310897e4bcaac
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217001"
---
# <a name="walkthrough-download-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer"></a>İzlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'SI ile isteğe bağlı derlemeleri Indirme
Varsayılan olarak, uygulama ilk çalıştırıldığında bir uygulamaya dahil edilen tüm derlemeler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] indirilir. Ancak, uygulamanızın küçük bir kullanıcı kümesi tarafından kullanılan bölümleri olabilir. Bu durumda, bir derlemeyi yalnızca türlerinden birini oluştururken indirmek istersiniz. Aşağıdaki izlenecek yol, uygulamanızda belirli derlemelerin "isteğe bağlı" olarak nasıl işaretleneceğini ve <xref:System.Deployment.Application> ortak dil çalışma zamanı tarafından talep edildiğinde ad alanındaki sınıfları kullanarak nasıl indirileceğini gösterir.

> [!NOTE]
> Bu yordamı kullanmak için uygulamanızın tam güvende çalışması gerekir.

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın. Daha fazla bilgi için bkz. [ayarları sıfırlama](../ide/environment-settings.md#reset-settings).

## <a name="create-the-projects"></a>Projeleri oluşturma

### <a name="to-create-a-project-that-uses-an-on-demand-assembly-with-visual-studio"></a>Visual Studio ile isteğe bağlı derleme kullanan bir proje oluşturmak için

1. İçinde yeni bir Windows Forms projesi oluşturun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . **Dosya** menüsünde, **Ekle**' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın. İletişim kutusunda bir **sınıf kitaplığı** projesi seçin ve adlandırın `ClickOnceLibrary` .

   > [!NOTE]
   > Visual Basic, proje özelliklerini, bu proje için kök ad alanını `Microsoft.Samples.ClickOnceOnDemand` tercih ettiğiniz bir ad alanı olarak değiştirecek şekilde değiştirmenizi öneririz. Kolaylık olması için bu izlenecek yolda bulunan iki proje aynı ad alanında yer alan.

2. Adlı tek bir özelliği olan adlı bir sınıf tanımlayın `DynamicClass` `Message` .

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceLibrary/VB/Class1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceLibrary/CS/Class1.cs" id="Snippet1":::

3. **Çözüm Gezgini** Windows Forms projesi seçin. Derlemeye bir başvuru ve projeye bir <xref:System.Deployment.Application> proje başvurusu ekleyin `ClickOnceLibrary` .

   > [!NOTE]
   > Visual Basic, proje özelliklerini, bu proje için kök ad alanını `Microsoft.Samples.ClickOnceOnDemand` tercih ettiğiniz bir ad alanı olarak değiştirecek şekilde değiştirmenizi öneririz. Kolaylık olması için, bu yönergedeki iki proje aynı ad alanında yer alır.

4. Forma sağ tıklayın, menüden **kodu görüntüle** ' ye tıklayın ve aşağıdaki başvuruları forma ekleyin.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet1":::

5. Bu derlemeyi isteğe bağlı olarak indirmek için aşağıdaki kodu ekleyin. Bu kod, bir derleme kümesinin genel bir sınıf kullanarak bir grup adına nasıl eşlendiğini gösterir <xref:System.Collections.DictionaryBase.Dictionary%2A> . Bu kılavuzda yalnızca tek bir derlemeyi indirdiğimiz için grubumuza yalnızca bir derleme var. Gerçek bir uygulamada, büyük olasılıkla uygulamanızdaki tek bir özellikle ilgili tüm derlemeleri aynı anda indirmek istersiniz. Eşleme tablosu, bir özelliğe ait olan tüm dll 'Leri indirme grubu adıyla ilişkilendirerek bunu kolayca yapmanızı sağlar.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet2":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet2":::

6. **Görünüm** menüsünde **araç kutusu**' na tıklayın. <xref:System.Windows.Forms.Button> **Araç kutusundan** bir öğesini form üzerine sürükleyin. Düğmeye çift tıklayın ve olay işleyicisine aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceOnDemand/CS/Form1.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceOnDemand/VB/Form1.vb" id="Snippet3":::

## <a name="mark-assemblies-as-optional"></a>Derlemeleri isteğe bağlı olarak işaretle

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-visual-studio"></a>Visual Studio 'Yu kullanarak derlemeleri ClickOnce uygulamanızda isteğe bağlı olarak işaretlemek için

1. **Çözüm Gezgini** Windows Forms projesine sağ tıklayın ve **Özellikler**' e tıklayın. **Yayımla** sekmesini seçin.

2. **Uygulama dosyaları** düğmesine tıklayın.

3. *ClickOnceLibrary.dll* listesini bulun. **Yayımla durumu** açılan kutusunu **dahil et** olarak ayarlayın.

4. **Grup** açılan kutusunu genişletin ve **Yeni**' yi seçin. Adı `ClickOnceLibrary` Yeni grup adı olarak girin.

5. Uygulamanızı [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)yayımlama bölümünde açıklandığı gibi yayımlamaya devam edin.

### <a name="to-mark-assemblies-as-optional-in-your-clickonce-application-by-using-manifest-generation-and-editing-tool--graphical-client-mageuiexe"></a>Bildirim Oluşturma ve Düzenleme Aracı — grafik Istemcisi (MageUI.exe) kullanarak ClickOnce uygulamanızda derlemeleri isteğe bağlı olarak işaretlemek için

1. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [İzlenecek yol: ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi bildirimlerinizi oluşturun.

2. MageUI.exe kapatmadan önce, dağıtımınızın uygulama bildirimini içeren sekmeyi seçin ve bu sekmenin içinde **dosyalar** sekmesini seçin.

3. Uygulama dosyaları listesinde ClickOnceLibrary.dll bulun ve **dosya türü** sütununu **none** olarak ayarlayın. **Grup** sütunu için, yazın `ClickOnceLibrary.dll` .

## <a name="test-the-new-assembly"></a>Yeni derlemeyi test etme

İsteğe bağlı derlemenizi test etmek için:

1. Uygulamanızı ile birlikte dağıtılan şekilde başlatın [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

2. Ana formunuz göründüğünde, ' a basın <xref:System.Windows.Forms.Button> . İleti kutusu penceresinde "Merhaba, Dünya!" okuyan bir dize görmeniz gerekir

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Deployment.Application.ApplicationDeployment>
