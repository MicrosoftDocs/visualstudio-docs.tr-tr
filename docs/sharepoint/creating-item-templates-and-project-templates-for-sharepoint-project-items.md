---
title: SharePoint Proje öğeleri için öğe şablonları ve proje şablonları oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, creating custom templates
- .spdata files
- projects [SharePoint development in Visual Studio], creating custom templates
- SharePoint projects, creating custom templates
- SharePoint development in Visual Studio, creating custom project and item templates
- project items [SharePoint development in Visual Studio], creating custom templates
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d181891fb36645e4f246aa0c2238c12ea1dc4903
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296014"
---
# <a name="create-item-templates-and-project-templates-for-sharepoint-project-items"></a>Öğe şablonları ve SharePoint Proje öğeleri için proje şablonları oluşturma
  Özel bir SharePoint proje öğesi türü tanımladığınızda, öğe şablonu veya bir proje şablonu ile ilişkilendirebilirsiniz. Bu ilişkilendirme, proje öğesi Visual Studio'da kullanmak diğer geliştiricilerin sağlar. Ayrıca, şablon için bir sihirbaz oluşturabilirsiniz.

 Örneğin, Visual Studio Proje şablonu veya bir SharePoint sitesine bir alan eklemek için öğe şablonu içermez. Bir alanı temsil eden bir SharePoint proje öğesi türü tanımlama ve ardından diğer geliştiriciler alanı öğesini bir SharePoint projesine eklemek için kullanabileceğiniz bir öğe şablonu oluşturun. Alternatif olarak, geliştiriciler alan öğesi olan yeni bir SharePoint Proje oluşturabilmesi için proje şablonu oluşturabilirsiniz. Her iki durumda da geliştiriciler, şablonunuzu kullandığınızda görünen bir sihirbaz sağlayabilir. Bu sihirbaz, yeni bir öğe veya proje yapılandırma geliştiricilerden bilgi toplayabilirsiniz.

 Öğe şablonları ve proje şablonları *.zip* bir proje öğesi veya proje oluşturmak için Visual Studio tarafından kullanılan dosyalar içeren dosyaları. Öğe şablonları ve proje şablonları temelleri hakkında daha fazla bilgi için bkz: [proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md).

## <a name="create-item-templates"></a>Öğe şablonları oluşturma
 Bir SharePoint proje öğesi için öğe şablonu oluşturduğunuzda, bazı, her zaman gerekli dosyaları ve belirli proje öğesi türleri tarafından kullanılan isteğe bağlı dosyalar vardır. Nasıl bir SharePoint proje öğesi türü tanımlama ve bunun için bir öğe şablonu oluşturmak izlenecek yol için bkz: [izlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).

 Aşağıdaki tabloda, bir SharePoint proje öğesi için öğe şablonu oluşturmak için gereken dosyaları listeler.

|Gerekli bir dosya|Açıklama|
|-------------------|-----------------|
|Bir *.spdata* dosyası|Bu XML dosyasını, içeriği ve proje öğesi varsayılan davranışını belirtir. Bu dosya öğesi şablonuna dahil edilmelidir. İçeriği hakkında daha fazla bilgi için *.spdata* dosyaları görmek [SharePoint proje öğesi şema başvurusu](../sharepoint/sharepoint-project-item-schema-reference.md).|
|A *.vstemplate* dosya.|Bu dosyayı Visual Studio şablonu görüntülemek için gereken bilgileri sağlar **Yeni Öğe Ekle** iletişim kutusu ve bir proje öğesi şablonu oluşturmak için. Bu dosya öğesi şablonuna dahil edilmelidir. Daha fazla bilgi için [Visual Studio şablon meta veri dosyaları](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|Uygulayan bir Visual Studio uzantı derlemesini <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> arabirimi.|Bu derleme proje öğesi çalışma zamanı davranışını tanımlar. Bu derleme, VSIX paketinde öğe şablonu ile eklenmesi gerekir. Daha fazla bilgi için [özel SharePoint proje öğesi türleri tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md) ve [Visual Studio'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|

 Aşağıdaki tabloda bazı öğesi şablonuna dahil en sık kullanılan isteğe bağlı dosyalar listelenmektedir. Bazı proje öğesi türleri, burada listelenmeyen diğer dosyaları gerektirebilir.


| İsteğe bağlı dosya | Açıklama |
|----------------------| - |
| *Elements.XML* | A *özellik öğesinin* dosya. Bu dosya, kullanıcı Arabirimi ve proje öğesi tarafından oluşturulan özelleştirme davranışını tanımlar. Özelleştirme, liste örnekleri, içerik türleri veya özel eylemler gibi her tür, bu dosyanın içeriğini tanımlayan farklı bir şeması vardır. Daha fazla bilgi için [yapı taşı: Özellikler](http://go.microsoft.com/fwlink/?LinkId=169183) ve [özellik şemaları](http://go.microsoft.com/fwlink/?LinkId=169192). |
| *Schema.XML* | Liste tanımları için şema dosyası. Daha fazla bilgi için [yapı taşı: listelerin ve belge kitaplıklarını](http://go.microsoft.com/fwlink/?LinkId=177792) ve [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793). |
| *.WebPart* | A *Web Bölümü tanımı* dosya. Bu dosya, bir Web Bölümü için özellik ayarlarını içerir. Daha fazla bilgi için [yapı taşı: Web Bölümleri](http://go.microsoft.com/fwlink/?LinkId=177791). |
| *.ascx* | Bir ASP.NET UserControl dosyası. Bu dosya, bir görsel Web Bölümü, kullanıcı arabirimini tanımlar. |
| *.aspx* | ASP.NET sayfası dosyası. Bu dosya, bir uygulama sayfası tanımlayan XML işaretlemesini içerir. |
| *.cs* veya *.vb* dosyaları | Bu kod dosyaları Görselden erişilebilir bir programlama modeli olan SharePoint özelleştirmeleri davranışını tanımlamak C# veya uygulama sayfaları, Web Bölümleri ve iş akışları gibi Visual Basic kodu. |

## <a name="create-project-templates"></a>Proje şablonları oluşturma
 Bir SharePoint Proje şablonu oluşturduğunuzda, belirli proje türleri tarafından kullanılan gerekli ve isteğe bağlı dosyaları her zaman olan bazı dosyalar vardır. Genellikle, SharePoint projeleri, en az bir SharePoint proje öğesi içerir. Ancak bu gerekli değildir. Örneğin, bir SharePoint Proje şablonu, yalnızca diğer projelerde oluşturulan SharePoint çözümlerini dağıtmak için kullanılması amaçlanmıştır tanımlayabilirsiniz.

 Nasıl bir SharePoint proje öğesi türü tanımlama ve bunun için bir proje şablonu oluşturmak izlenecek yol için bkz: [izlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).

 Aşağıdaki tabloda, bir SharePoint Proje şablonunda içermesi gereken dosyaları listeler.

|Gerekli bir dosya|Açıklama|
|-------------------|-----------------|
|A *.vstemplate* dosyası|Bu dosyayı Visual Studio şablonu görüntülemek için gereken bilgileri sağlar **yeni proje** iletişim kutusu ve şablondan bir proje oluşturmaktır. Daha fazla bilgi için [Visual Studio şablon meta veri dosyaları](/previous-versions/visualstudio/visual-studio-2010/xsxc3ete\(v\=vs.100\)).|
|A *.csproj* veya *.vbproj* dosyası|Bu proje dosyasıdır. Bu içeriği ve proje yapılandırma ayarlarını tanımlar.|
|*Package.Package*|Bu dosya, dağıtım paketi için proje tanımlar. Projeniz için çözüm paketini özelleştirme için paket Tasarımcısı'nı kullandığınızda Visual Studio çözüm paketiyle ilgili verileri bu dosyada depolar.<br /><br /> Özel SharePoint Proje şablonu oluşturduğunuzda, yalnızca en düşük gerekli içeriği dahil öneririz *Package.package* dosya ve çözüm paketine API'leri kullanarak yapılandırdığınız <xref:Microsoft.VisualStudio.SharePoint.Packages> Proje şablonu ile ilişkili bir uzantı ad alanı. Bunu yaparsanız, proje şablonu yapısı için gelecekteki değişiklikleri korunan *Package.package* dosya. Nasıl oluşturulacağını gösteren bir örnek için bir *Package.package* yalnızca gerekli minimum içerik dosya getirin, bkz: [izlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Değişiklik yapmak istiyorsanız *Package.package* doğrudan dosya, şema kullanarak içeriği doğrulayabilirsiniz *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\PackageModelSchema.xsd* .|
|*Package.Template.xml*|Bu dosya için çözüm bildirim dosyası temelini (*manifest.xml*) için SharePoint çözüm paketini (*.wsp*) projeden oluşturulur. Proje türünüzü kullanıcıları tarafından değiştirilmesi hedeflenmemiştir bazı davranışı belirtmek istiyorsanız bu dosyaya içerik ekleyebilirsiniz. Daha fazla bilgi için [yapı taşı: çözümleri](http://go.microsoft.com/fwlink/?LinkId=169186) ve [çözüm şema](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> Projeden bir çözüm paketi oluşturduğunuzda, Visual Studio içeriğini birleştirir *Package.package* ve *Package.Template.xml* çözüm dosyasına bildirim dosyası. Çözüm paketleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevleri kullanarak bir SharePoint çözüm paketini oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

 Aşağıdaki tabloda, proje şablonuna dahil isteğe bağlı dosyaları listeler.

|İsteğe bağlı dosya|Açıklama|
|-------------------|-----------------|
|SharePoint proje öğeleri|SharePoint proje öğesi türleri tanımlayan bir veya daha fazla .spdata dosyaları dahil edebilirsiniz. Her *.spdata* eşleşen bir dosya olmalıdır <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> VSIX paketini proje şablonunda yer aldığı bir uzantı derlemesinin uygulamasında. Daha fazla bilgi için [öğe şablonları oluşturma](#creatingitemtemplates).<br /><br /> Genellikle, SharePoint projeleri, en az bir SharePoint proje öğesi içerir. Ancak bu gerekli değildir.|
|*\<featureName > .feature*|Bu dosya, dağıtım için çeşitli proje öğeleri gruplandırmak için kullanılan bir SharePoint özelliği tanımlar. Projenizde bir özellik özelleştirmek için Özellik Tasarımcısı'nı kullandığınızda, Visual Studio bu dosyada özelliği hakkında daha fazla veri depolar. Proje öğeleri farklı gruplamanızı istiyorsanız, birden çok içerebilir *.feature* dosyaları.<br /><br /> Özel SharePoint Proje şablonu oluşturduğunuzda, yalnızca en düşük gerekli içeriği her dahil olmasını öneririz *.feature* dosya ve API'leri kullanarak özellikleri yapılandırmak <xref:Microsoft.VisualStudio.SharePoint.Features> ad alanında bir Proje şablonu ile ilişkili uzantı. Bunu yaparsanız, proje şablonu yapısı için gelecekteki değişiklikleri korunan *.feature* dosya. Nasıl oluşturulacağını gösteren bir örnek için bir *.feature* yalnızca gerekli minimum içerik dosya getirin, bkz: [izlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> Değişiklik yapmak istiyorsanız bir *.feature* doğrudan dosya, şema kullanarak içeriği doğrulayabilirsiniz *% Program Files (x86)%\Microsoft Visual Studio 11.0\Xml\Schemas\FeatureModelSchema.xsd*.|
|*\<featureName >. Template.XML*|Bu dosya için özellik bildirimi dosyasını temelini (*gt;Feature.xml*) projeden oluşturulan her bir özellik. Proje türünüzü kullanıcıları tarafından değiştirilmesi hedeflenmemiştir bazı davranışı belirtmek istiyorsanız bu dosyaya içerik ekleyebilirsiniz. Daha fazla bilgi için [yapı taşı: Özellikler](http://go.microsoft.com/fwlink/?LinkId=169183) ve [gt;Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795) dosyaları.<br /><br /> Projeden bir çözüm paketi oluşturduğunuzda, Visual Studio her çift içeriğini birleştirir  *\<featureName > .feature* dosya ve  *\<featureName >. Template.xml* dosyalarına bir özellik bildirimi dosyasını. Çözüm paketleri oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: MSBuild görevleri kullanarak bir SharePoint çözüm paketini oluşturma](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).|

## <a name="create-wizards-for-item-templates-and-project-templates"></a>Sihirbazlar için öğe şablonları ve proje şablonları oluşturma
 Bir SharePoint proje öğesi türü tanımlama ve bir öğe veya proje şablonuyla ilişkilendirin sonra bir sihirbaz oluşturabilirsiniz. Sihirbaz, bir geliştirici SharePoint proje öğesi projeye eklenecek öğe şablonu kullandığında veya bir geliştirici SharePoint proje öğesi içeren yeni bir proje oluşturmak için proje şablonu kullandığında görüntüler. Sihirbaz, geliştiricilerden bilgi toplamaya ve yeni bir SharePoint proje öğesi başlatmak için kullanılabilir.

 Sihirbazlar için öğe şablonları ve proje şablonları oluşturma işlemini gösteren izlenecek yollar için bkz. [izlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) ve [izlenecek yol: bir site oluşturun Proje şablonu, bölüm 2 ile sütunu proje öğesi](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [İzlenecek yol: bir öğe şablonu, bölüm 1 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [İzlenecek yol: bir öğe şablonu, bölüm 2 ile özel bir eylem proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [İzlenecek yol: bir proje şablonu, bölüm 1 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [İzlenecek yol: bir proje şablonu, bölüm 2 ile bir site sütunu proje öğesi oluşturma](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
