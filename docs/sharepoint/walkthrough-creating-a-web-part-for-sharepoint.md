---
title: 'İzlenecek yol: SharePoint için bir Web Bölümü oluşturma | Microsoft Docs'
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
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 09b9299c6428ef63ccf71220fc3cb599e9e3b5a9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872414"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>İzlenecek yol: SharePoint için bir web bölümü oluşturma

Web bölümleri, kullanıcıların içeriğini, görünümünü ve SharePoint sitesi sayfalarının davranışını bir tarayıcı kullanarak doğrudan değiştirmesine izin etkinleştirin. Bu izlenecek yol kullanarak bir Web Bölümü oluşturulacağını gösterir **Web Bölümü** öğe şablonu Visual Studio 2010.

Web Bölümü, bir veri kılavuzunda çalışanlar görüntüler. Kullanıcı çalışan verilerini içeren dosyanın konumunu belirtir. Böylece yöneticileri Çalışanlar yalnızca listede görüntülenen kullanıcı ayrıca veri kılavuzu filtreleyebilirsiniz.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Visual Studio kullanarak bir Web Bölümü oluşturma **Web Bölümü** öğe şablonu.

- Bir özelliği, oluşturma, Web Bölümü'nün kullanıcı tarafından ayarlanabilir. Bu özellik, çalışan veri dosyasının konumunu belirtir.

- Web bölümüne denetimler ekleyerek bir Web Bölümü içeriği oluşturma koleksiyonu denetler.

- Yeni bir menü öğesi oluşturma olarak adlandırılan bir *fiili* işlenmiş Web Bölümü fiilleri menüsünde görünür. Web bölümünde görünen verileri değiştirmek kullanıcı fiillere etkinleştirin.

- SharePoint Web bölümünü sınama.

    > [!NOTE]
    > Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

- Microsoft Windows ve SharePoint sürümleri desteklenir.

- Visual Studio 2017 veya Azure DevOps Hizmetleri.

## <a name="create-an-empty-sharepoint-project"></a>Boş bir SharePoint projesi oluşturma

İlk olarak boş bir SharePoint projesi oluşturun. Projeye kullanarak bir Web Bölümü daha sonra ekleyeceksiniz **Web Bölümü** öğe şablonu.

1. Başlangıç [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kullanarak **yönetici olarak çalıştır** seçeneği.

2. ADAM çubuğunda **dosya** > **yeni** > **proje**.

3. İçinde **yeni proje** iletişim kutusunda **SharePoint** kullanın ve ardından istediğiniz dili düğümünde **2010** düğümü.

4. İçinde **şablonları** bölmesinde seçin **SharePoint 2010 projesi**ve ardından **Tamam** düğmesi.

     **SharePoint Özelleştirme Sihirbazı** görünür. Bu sihirbaz, proje ve çözüm güven düzeyini hata ayıklamak için kullanacağınız siteyi seçmenizi sağlar.

5. Seçin **Grup çözümü olarak Dağıt** seçenek düğmesini ve ardından **son** varsayılan yerel SharePoint sitesini kabul etmek için düğmeyi.

## <a name="add-a-web-part-to-the-project"></a>Projeye bir web bölümü ekleyin

Ekleme bir **Web Bölümü** projeye öğe. **Web Bölümü** öğesi Web Bölümü kod dosyası ekler. Daha sonra Web Bölümü içeriğini işlemek için Web Bölümü kod dosyasına kod ekleyeceksiniz.

1. Menü çubuğunda, **proje** > **Yeni Öğe Ekle**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusundaki **yüklü şablonlar** bölmesinde genişletin **SharePoint** düğümünü seçip **2010** düğümü.

3. SharePoint şablonları listesinde seçin **Web Bölümü** şablonu seçip **Ekle** düğmesi.

     **Web Bölümü** öğesi görünür **Çözüm Gezgini**.

## <a name="rendering-content-in-the-web-part"></a>Web bölümü içeriği oluşturma

Web Bölümü sınıfı denetimler koleksiyonuna ekleyerek Web bölümünde görünmesini istediğiniz hangi denetimlerin belirtebilirsiniz.

1. İçinde **Çözüm Gezgini**açın *WebPart1.vb* (Visual Basic'te) veya *WebPart1.cs* (C# dilinde).

     Web Bölümü kod dosyası Kod Düzenleyicisi'nde açılır.

2. Web Bölümü kod dosyasının en üstüne aşağıdaki deyimleri ekleyin.

     [!code-csharp[SP_WebPart#1](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#1)]
     [!code-vb[SP_WebPart#1](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#1)]

3. Aşağıdaki kodu ekleyin `WebPart1` sınıfı. Bu kod, aşağıdaki alanları bildirir:

   - Çalışanlar Web bölümünde görüntülenecek veri kılavuzu.

   - Veri Kılavuzu filtrelemek için kullanılan bir denetimde görünen metin.

   - Bir etiket veri kılavuzu verileri görüntülemek kuramazsa, bir hata gösterir.

   - Çalışan veri dosyasının yolunu içeren bir dize.

     [!code-csharp[SP_WebPart#2](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#2)]
     [!code-vb[SP_WebPart#2](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#2)]

4. Aşağıdaki kodu ekleyin `WebPart1` sınıfı. Bu kodu adlı özel bir özellik ekler `DataFilePath` Web Bölümü. Özel bir özellik SharePoint'te kullanıcı tarafından ayarlanabilen bir özelliğidir. Bu özellik, alır ve veri kılavuzu doldurmak için kullanılan bir XML veri dosyasının konumunu ayarlar.

     [!code-csharp[SP_WebPart#3](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#3)]
     [!code-vb[SP_WebPart#3](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#3)]

5. Değiştirin `CreateChildControls` yöntemini aşağıdaki kod ile. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Önceki adımda, veri kılavuzu ve bildirdiğiniz etiketi ekler.

   - Veri Kılavuzu çalışan verilerini içeren bir XML dosyasına bağlar.

     [!code-csharp[SP_WebPart#4](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#4)]
     [!code-vb[SP_WebPart#4](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#4)]

6. Aşağıdaki yöntemi ekleyin `WebPart1` sınıfı. Bu kod aşağıdaki görevleri gerçekleştirir:

   - İşlenmiş Web Bölümünü Web Bölümü fiilleri menüde görüntülenen fiil oluşturur.

   - Kullanıcı fiillere menüde fiili seçtiğinde başlatan olayını işler. Bu kod, veri kılavuzunda görüntülenen çalışanlar listesini filtreler.

     [!code-csharp[SP_WebPart#5](../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs#5)]
     [!code-vb[SP_WebPart#5](../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb#5)]

## <a name="test-the-web-part"></a>Web bölümünü sınama

Projeyi çalıştırdığınızda, SharePoint sitesi açılır. Otomatik olarak Web bölümünü SharePoint içindeki Web Bölümü Galerisi'ne eklenir. Web bölümü herhangi bir Web Bölümü sayfasına ekleyebilirsiniz.

1. Aşağıdaki XML bir not defteri dosyasına yapıştırın. Bu XML dosyası içinde Web Bölümü görünür örnek veriler içerir.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
        <employees xmlns="http://schemas.microsoft.com/vsto/samples">
           <employee>
               <name>David Hamilton</name>
               <hireDate>2001-05-11</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Karina Leal</name>
               <hireDate>1999-04-01</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Nancy Davolio</name>
               <hireDate>1992-05-01</hireDate>
               <title>Sales Associate</title>
           </employee>
           <employee>
               <name>Steven Buchanan</name>
               <hireDate>1955-03-04</hireDate>
               <title>Manager</title>
           </employee>
           <employee>
               <name>Suyama Michael</name>
               <hireDate>1963-07-02</hireDate>
               <title>Sales Associate</title>
           </employee>
        </employees>
    ```

2. Not Defteri'nde, menü çubuğunda, **dosya** > **Kaydet**.

3. İçinde **Kaydet** iletişim kutusundaki **farklı kaydetme türü** listesinde **tüm dosyaları**.

4. İçinde **dosya adı** kutusuna **data.xml**.

5. Kullanarak herhangi bir klasör seçin **klasörlere Gözat** düğmesine ve ardından **Kaydet** düğmesi.

6. Visual Studio'da **F5** anahtarı.

     SharePoint sitesi açılır.

7. Üzerinde **Site eylemleri** menüsünde seçin **diğer seçenekler**.

8. İçinde **Oluştur** sayfasında **Web Bölümü sayfası** yazın ve ardından **Oluştur** düğmesi.

9. İçinde **yeni Web Bölümü sayfası** sayfasında, sayfanın adını **SampleWebPartPage.aspx**ve ardından **Oluştur** düğmesi.

     Web Bölümü sayfası görüntülenir.

10. Web Bölümü sayfada herhangi bir bölge seçin.

11. Sayfanın en üstünde **Ekle** sekmesine ve ardından **Web Bölümü** düğmesi.

12. İçinde **kategorileri** bölmesinde seçin **özel** klasörü seçin **WebPart1** Web Bölümü ve ardından **Ekle** düğmesi.

     Web Bölümü sayfada görüntülenir.

## <a name="test-the-custom-property"></a>Özel özellik test

Web bölümünde görünen veri kılavuzu doldurmak için her çalışan hakkında veri içeren XML dosyasının yolunu belirtin.

1. Web Bölümü'nün sağ tarafta açılan oku seçin ve ardından **Web Bölümünü Düzenle** görünen menüden.

     Web Bölümü için özellikleri içeren bir bölme, sayfanın sağ tarafında görünür.

2. Bölmesinde, **çeşitli** düğümünü seçin, daha önce oluşturduğunuz XML dosyasının yolunu girin **Uygula** düğmesine ve ardından **Tamam** düğmesi.

     Çalışanların listesi Web bölümünde göründüğünden emin olun.

## <a name="test-the-web-part-verb"></a>Web bölümü fiili test

Gösterebilir ve Web Bölümü fiilleri menüde görünen bir öğeye tıklayarak Yöneticileri olmayan çalışanların gizleyebilirsiniz.

1. Web Bölümü'nün sağ tarafta açılan oku seçin ve ardından **yalnızca yöneticileri Göster** görünen menüden.

     Yalnızca yöneticileri çalışanlar Web bölümünde görüntülenir.

2. Oku tekrar seçin ve ardından **Göster tüm çalışanlar** görünen menüden.

     Tüm çalışanların Web bölümünde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint için Web bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md)  
[Nasıl yapılır: bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md)  
[Nasıl yapılır: Tasarımcı kullanarak bir SharePoint web bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)  
[İzlenecek yol: Tasarımcı kullanarak bir web bölümü SharePoint için oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
