---
title: 'İzlenecek yol: SharePoint için bir Web Bölümü oluşturma | Microsoft Docs'
description: SharePoint için bir Web bölümü oluşturun. Web bölümleri, kullanıcıların SharePoint site sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak doğrudan değiştirmesini sağlar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], developing
- Web Parts [SharePoint development in Visual Studio], creating
- Web Parts [SharePoint development in Visual Studio], designing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3e018085bd9900a9ee04f838b7c802afd2acc4fe
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217716"
---
# <a name="walkthrough-create-a-web-part-for-sharepoint"></a>İzlenecek yol: SharePoint için bir Web Bölümü oluşturma

Web Bölümleri, kullanıcıların SharePoint site sayfalarının içeriğini, görünümünü ve davranışını bir tarayıcı kullanarak doğrudan değiştirmesini sağlar. Bu izlenecek yol, Visual Studio 2010 ' de **Web Bölümü** öğe şablonunu kullanarak bir Web Bölümü oluşturmayı gösterir.

Web Bölümü çalışanları bir veri kılavuzunda görüntüler. Kullanıcı, çalışan verilerini içeren dosyanın konumunu belirtir. Kullanıcı, yönetici olan çalışanların yalnızca listede görünmesini sağlamak için veri kılavuzunu da filtreleyebilir.

Bu izlenecek yol aşağıdaki görevleri gösterir:

- Visual Studio **Web Bölümü** öğe şablonunu kullanarak bir Web Bölümü oluşturma.

- Web bölümünün kullanıcısı tarafından ayarlanabilir bir özellik oluşturma. Bu özellik, çalışan veri dosyasının konumunu belirtir.

- Web bölümü denetimleri koleksiyonuna denetimler ekleyerek bir Web bölümünde içerik işleme.

- İşlenmiş Web bölümünün fiiller menüsünde görünen, *fiil* olarak adlandırılan yeni bir menü öğesi oluşturma. Fiiller, kullanıcının Web bölümünde görünen verileri değiştirmesini sağlar.

- SharePoint 'te Web bölümünü test etme.

    > [!NOTE]
    > Bilgisayarınız, aşağıdaki yönergelerde yer alan Visual Studio kullanıcı arabirimi öğelerinden bazıları için farklı adlar veya konumlar gösterebilir. Sahip olduğunuz Visual Studio sürümü ve kullandığınız ayarlar bu öğeleri belirler. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Önkoşullar

- Desteklenen Microsoft Windows ve SharePoint sürümleri.

- Visual Studio 2017 veya Azure DevOps Services.

## <a name="create-an-empty-sharepoint-project"></a>Boş bir SharePoint projesi oluşturma

İlk olarak, boş bir SharePoint projesi oluşturun. Daha sonra, **Web Bölümü** öğe şablonunu kullanarak projeye bir Web Bölümü eklersiniz.

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **Yönetici olarak çalıştır** seçeneğini kullanarak başlayın.

2. Bay çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

3. **Yeni proje** iletişim kutusunda, kullanmak istediğiniz dilin altındaki **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

4. **Şablonlar** bölmesinde **SharePoint 2010 projesi**' ni seçin ve ardından **Tamam** düğmesini seçin.

     **SharePoint Özelleştirme Sihirbazı** görüntülenir. Bu sihirbaz, projenin hatalarını ayıklamak için kullanacağınız siteyi ve çözümün güven düzeyini seçmenizi sağlar.

5. **Grup çözümü olarak dağıt** seçenek düğmesini seçin ve ardından varsayılan yerel SharePoint sitesini kabul etmek için **son** düğmesini seçin.

## <a name="add-a-web-part-to-the-project"></a>Projeye bir Web Bölümü ekleme

Projeye bir **Web Bölümü** öğesi ekleyin. **Web Bölümü** öğesi, Web bölümü kod dosyasını ekler. Daha sonra Web bölümünün içeriğini işlemek için Web bölümü kod dosyasına kod ekleyeceksiniz.

1. Menü çubuğunda, **Proje**  >  **Yeni öğe Ekle**' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü şablonlar** bölmesinde, **SharePoint** düğümünü genişletin ve ardından **2010** düğümünü seçin.

3. SharePoint şablonları listesinde, **Web Bölümü** şablonunu seçin ve sonra **Ekle** düğmesini seçin.

     **Web Bölümü** öğesi **Çözüm Gezgini** görüntülenir.

## <a name="rendering-content-in-the-web-part"></a>Web bölümünde içerik işleme

Web bölümünde görünmesini istediğiniz denetimleri, Web Bölümü sınıfının denetimler koleksiyonuna ekleyerek belirtebilirsiniz.

1. **Çözüm Gezgini**' de, *WebPart1. vb* dosyasını açın (Visual Basic) veya *WebPart1. cs* (C# dilinde).

     Web bölümü kod dosyası kod düzenleyicisinde açılır.

2. Aşağıdaki yönergeleri Web bölümü kod dosyasının en üstüne ekleyin.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet1":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet1":::

3. Aşağıdaki kodu `WebPart1` sınıfına ekleyin. Bu kod aşağıdaki alanları bildirir:

   - Web bölümünde çalışanları görüntüleyen bir veri kılavuzu.

   - Denetimde görüntülenen ve veri kılavuzunu filtrelemek için kullanılan metin.

   - Veri kılavuzu verileri görüntüleyemiyor ise hata görüntüleyen bir etiket.

   - Çalışan veri dosyasının yolunu içeren bir dize.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet2":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet2":::

4. Aşağıdaki kodu `WebPart1` sınıfına ekleyin. Bu kod, Web bölümüne adlı özel bir özellik ekler `DataFilePath` . Özel özellik, Kullanıcı tarafından SharePoint 'te ayarlanarak kullanılabilecek bir özelliktir. Bu özellik, veri kılavuzunu doldurmak için kullanılan bir XML veri dosyasının konumunu alır ve ayarlar.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet3":::

5. `CreateChildControls` yöntemini aşağıdaki kodla değiştirin. Bu kod aşağıdaki görevleri gerçekleştirir:

   - Önceki adımda bildirdiğiniz veri kılavuzunu ve etiketini ekler.

   - Veri kılavuzunu, çalışan verileri içeren bir XML dosyasına bağlar.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet4":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet4":::

6. Sınıfına aşağıdaki yöntemi ekleyin `WebPart1` . Bu kod aşağıdaki görevleri gerçekleştirir:

   - İşlenmiş Web Bölümünün Web Bölümü fiiller menüsünde görünen bir fiil oluşturur.

   - Kullanıcı fiiller menüsünde fiil seçtiğinde oluşan olayı işler. Bu kod, veri kılavuzunda görünen çalışanların listesini filtreler.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/spext_webpart/webpart1/webpart1.cs" id="Snippet5":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spext_webpart/webpart1/webpart1.vb" id="Snippet5":::

## <a name="test-the-web-part"></a>Web bölümünü test etme

Projeyi çalıştırdığınızda, SharePoint sitesi açılır. Web Bölümü, SharePoint 'teki Web Bölümü galerisine otomatik olarak eklenir. Web bölümünü herhangi bir Web Bölümü sayfasına ekleyebilirsiniz.

1. Aşağıdaki XML 'i bir not defteri dosyasına yapıştırın. Bu XML dosyası, Web bölümünde görünecek örnek verileri içerir.

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

2. Not defteri 'nde, menü çubuğunda **Dosya**  >  **farklı kaydet**' i seçin.

3. **Farklı kaydet** iletişim kutusunda, **farklı kaydet türü** listesinde **tüm dosyalar**' ı seçin.

4. **Dosya adı** kutusuna **data.xml** girin.

5. **Klasörlere gözatamazsınız** düğmesini kullanarak herhangi bir klasör seçin ve ardından **Kaydet** düğmesini seçin.

6. Visual Studio 'da **F5** tuşunu seçin.

     SharePoint sitesi açılır.

7. **Site eylemleri** menüsünde **diğer seçenekler**' i seçin.

8. **Oluştur** sayfasında, **Web Bölümü sayfası** türünü seçin ve ardından **Oluştur** düğmesini seçin.

9. **Yeni Web Bölümü sayfası** sayfasında **SampleWebPartPage. aspx** sayfasını adlandırın ve **Oluştur** düğmesini seçin.

     Web Bölümü sayfası görüntülenir.

10. Web Bölümü sayfasında herhangi bir bölgeyi seçin.

11. Sayfanın üst kısmında **Ekle** sekmesini seçin ve ardından **Web Bölümü** düğmesini seçin.

12. **Kategoriler** bölmesinde **özel** klasörü seçin, **WebPart1** Web bölümünü seçin ve sonra **Ekle** düğmesini seçin.

     Web Bölümü sayfada görüntülenir.

## <a name="test-the-custom-property"></a>Özel özelliği test etme

Web bölümünde görünen veri kılavuzunu doldurmak için, her çalışanla ilgili verileri içeren XML dosyasının yolunu belirtin.

1. Web bölümünün sağ tarafında görüntülenen oku seçin ve açılan menüden **Web bölümünü Düzenle** ' yi seçin.

     Web Bölümü özelliklerini içeren bir bölme sayfanın sağ tarafında görünür.

2. Bölmesinde, **çeşitli** düğümünü genişletin, daha önce oluşturduğunuz XML dosyasının yolunu girin, **Uygula** düğmesini seçin ve sonra **Tamam** düğmesini seçin.

     Bir çalışanlar listesinin Web bölümünde göründüğünü doğrulayın.

## <a name="test-the-web-part-verb"></a>Web Bölümü fiilini test etme

Web Bölümü fiiller menüsünde görünen bir öğe seçerek yönetici olmayan çalışanları gösterin ve gizleyin.

1. Web bölümünün sağ tarafında görüntülenen oku seçin ve ardından açılan menüden **yöneticileri göster** ' i seçin.

     Web bölümünde yalnızca Yöneticiler olan çalışanlar görüntülenir.

2. Oku yeniden seçin ve açılan menüden **tüm çalışanları göster** ' i seçin.

     Tüm çalışanlar Web bölümünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

SharePoint için Web [bölümleri oluşturma](../sharepoint/creating-web-parts-for-sharepoint.md) 
 [Nasıl yapılır: SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part.md) 
 [Nasıl yapılır: tasarımcı kullanarak SharePoint Web Bölümü oluşturma](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md) 
 [Izlenecek yol: tasarımcı kullanarak SharePoint için bir Web Bölümü oluşturma](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
