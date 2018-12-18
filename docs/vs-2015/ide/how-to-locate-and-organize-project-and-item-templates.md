---
title: 'Nasıl yapılır: bulma ve düzenleme proje ve öğe şablonları | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- custom template locations [Visual Studio]
- item templates, locations
- Visual Studio templates, locations
- project templates [Visual Studio], displaying
- templates [Visual Studio], locations
ms.assetid: 71f9ed52-c9c9-4818-9bce-c279ffaa0438
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2a3954e5d18db6585c8dbda017773969f96b33de
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830983"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Nasıl Yapılır: Proje ve Öğe Şablonlarını Bulma ve Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şablon dosyaları, Visual Studio tanır ve böylece şablonları görünür bir konumda yerleştirilmelidir **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları. Alt kategoriler, ayrıca kullanıcı arabiriminde görünmesi için şablonları için özel alt kategorileri oluşturabilirsiniz.  
  
## <a name="locating-templates"></a>Şablonları bulma  
 Varsayılan olarak, Visual Studio'nun proje ve öğe şablonları için iki konumları arar. Bu konumlarda, .vstemplate dosyasını içeren sıkıştırılmış bir dosya varsa, bir şablon içinde görünür **yeni proje** veya **Yeni Öğe Ekle** iletişim kutuları.  
  
### <a name="installed-templates"></a>Yüklü Şablonlar  
 Ürün ile birlikte yüklü şablonlar varsayılan olarak bulunur:  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*dil*\\*yerel ayar*\  
  
- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*dil*\\*yerel ayar\\*  
  
  Örneğin, şu dizin içeren [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] İngilizce için proje şablonları:  
  
  C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\  
  
### <a name="custom-templates"></a>Özel şablonlar  
 Özel şablonları varsayılan olarak bulunur:  
  
- \My Documents\Visual studio *sürüm*\Templates\ProjectTemplates\\*dil*\  
  
- \My Documents\Visual studio *sürüm*\Templates\ItemTemplates\\*dil*\  
  
  Örneğin, aşağıdaki dizine özel içeren [!INCLUDE[csprcs](../includes/csprcs-md.md)] proje şablonları:  
  
  C:\Documents ve Settings\Kullanıcıadı\My belgeleri\\< Visual Studio sürümü\>\Templates\ProjectTemplates\Visual C# \  
  
  Bir alt yerelleştirilmiş şablonları için özel şablonlar içermez. Özel şablonlar, varsayılan dizini değiştirebilirsiniz **seçenekleri** iletişim kutusunun **Environment\Projects ve çözümleri**.  
  
## <a name="organizing-templates"></a>Şablon düzenleme  
 Kategorileri **yeni proje** ve **Yeni Öğe Ekle** iletişim kutuları, yüklü ve özel şablon konumları mevcut dizin yapılarını yansıtır. Sizin için anlamlı bir şekilde şablonlarınızı düzenlemek için bu dizin yapılarını değiştirebilirsiniz.  
  
> [!NOTE]
>  Yeni bir kategori programlama dili düzeyinde oluşturulamıyor. Yeni kategori her bir dilin yalnızca oluşturulabilir.  
  
 Belirli bir dil için yüklü ve özel şablonlar için dizin yapıları aynı yapıda değilse (diğer bir deyişle, vardır altında diğer var olmayan dizinleri altında bir klasör) görünür kategoriler dizisine **yeni Proje** iletişim tüm kategorilerin birleşme olacaktır.  
  
### <a name="organizing-installed-templates"></a>Yüklü şablonları düzenleme  
 Yüklü Şablonlar programlama dili klasöründe alt dizinleri oluşturarak düzenleyebilirsiniz. Bu alt dizinleri görünür **yeni proje** ve **Yeni Öğe Ekle** iletişim kutusu olarak her bir dilin sanal klasörler.  
  
##### <a name="to-create-new-installed-project-template-categories"></a>Yeni yüklenen proje şablonu kategoriler oluşturmak için  
  
1. Yüklü şablon dizini dil klasörde bir klasör oluşturun. Örneğin, bir Office kategori için oluşturmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proje şablonları oluşturma şu dizin:  
  
    \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\VisualBasic\1033\Office\  
  
2. Bu kategori için tüm şablonları yeni klasöre yerleştirin.  
  
3. Tüm örneklerini kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4. Üzerinde **Başlat** menüsünde tıklayın **çalıştırma**, türü **cmd**, tıklatıp **Tamam**.  
  
5. Devenv.exe ve türü içeren dizine komut isteminde bulun **devenv /installvstemplates**.  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'i çalıştırın.  
  
7. Üzerinde **dosya** menüsünde tıklatın **yeni**ve ardından **proje**.  
  
8. Office kategori göründüğünü doğrulayın **yeni proje** iletişim kutusundaki **proje türleri** bölmesi altında [!INCLUDE[vbprvb](../includes/vbprvb-md.md)].  
  
   Proje öğesi şablonları kümesini özel bir klasöre de gruplandırabilirsiniz.  
  
##### <a name="to-create-new-installed-item-template-categories"></a>Yeni yüklenen öğe şablonu kategoriler oluşturmak için  
  
1.  Yüklü şablon dizini dil klasörde bir klasör oluşturun. Örneğin, bir Web kategorisi için oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] öğe şablonları oluşturma şu dizin:  
  
     \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\CSharp\1033\Web\  
  
2.  Bu kategori için tüm şablonları yeni klasöre yerleştirin.  
  
3.  Tüm örneklerini kapatın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  Üzerinde **Başlat** menüsünde tıklayın **çalıştırma**, türü **cmd**, tıklatıp **Tamam**.  
  
5.  Devenv.exe ve türü içeren dizine komut isteminde bulun **devenv/Setup**.  
  
6.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'i çalıştırın.  
  
7.  Bir proje oluşturun veya varolan bir projeyi açın.  
  
8.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
9. Web kategori göründüğünü doğrulayın **Yeni Öğe Ekle** iletişim kutusundaki **proje türleri** bölmesi.  
  
### <a name="organizing-custom-templates"></a>Özel şablonları düzenleme  
 Özel şablonlar özel bir şablon konumda yeni klasörler ekleyerek kendi kategoriler halinde düzenlenebilir. **Yeni proje** iletişim kutusu, şablon kategorilere yaptığınız değişiklikleri yansıtır.  
  
##### <a name="to-create-new-custom-project-template-categories"></a>Yeni özel Proje şablonu kategoriler oluşturmak için  
  
1. Özel proje şablonu dizini dil klasöründe bir klasör oluşturun. Örneğin, bir HelloWorld kategorisi için oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] şablonları, şu dizin oluşturma:  
  
    \My belgeleri\\< Visual Studio sürümü\>\Templates\ProjectTemplates\CSharp\HelloWorld\  
  
2. Bu kategori için tüm şablonları yeni klasöre yerleştirin.  
  
3. Üzerinde **dosya** menüsünde tıklatın **yeni**ve ardından **proje**.  
  
4. HelloWorld kategori göründüğünü doğrulayın **yeni proje** iletişim kutusundaki **proje türleri** bölmesi altında [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
   Özel öğe şablonları kümesini özel bir klasöre de gruplandırabilirsiniz.  
  
##### <a name="to-create-new-custom-item-template-categories"></a>Yeni özel öğe şablonu kategoriler oluşturmak için  
  
1.  Özel öğesi şablon dizini dil klasöründe bir klasör oluşturun. Örneğin, bir HelloWorld kategorisi için oluşturmak için [!INCLUDE[csprcs](../includes/csprcs-md.md)] şablonları şu dizin oluşturmanız:  
  
     \My belgeleri\\< Visual Studio sürümü\>\Templates\ItemTemplates\CSharp\HelloWorld\  
  
2.  Bu kategori için tüm şablonları yeni klasöre yerleştirin.  
  
3.  Bir proje oluşturun veya varolan bir projeyi açın.  
  
4.  Üzerinde **proje** menüsünü tıklatın **Yeni Öğe Ekle**.  
  
5.  HelloWorld kategori göründüğünü doğrulayın **Yeni Öğe Ekle** iletişim kutusundaki **proje türleri** bölmesi.  
  
### <a name="displaying-templates-in-parent-categories"></a>Ana kategoride şablonları görüntüleme  
 Alt kategoriler kullanarak kendi üst kategorilerde görüntülenecek şablonlarında etkinleştirebilirsiniz `NumberOfParentCategoriesToRollUp` .vstemplate dosyasında öğe. Bu adımlar, proje şablonları ve öğe şablonları için aynıdır.  
  
##### <a name="to-display-templates-in-parent-categories"></a>Üst kategorilerdeki şablonları görüntülemek için  
  
1.  Şablonu içeren .zip dosyasını bulun.  
  
2.  .Zip dosyasını çıkartın.  
  
3.  İçindeki .vstemplate dosyasını açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
4.  İçinde `TemplateData` öğe, Ekle bir `NumberOfParentCategoriesToRollUp` öğesi. Örneğin, aşağıdaki kodu, üst kategori görünür, ancak bundan daha yüksek şablonu sağlar.  
  
    ```  
    <TemplateData>  
        ...  
        <NumberOfParentCategoriesToRollUp>  
            1  
        </NumberOfParentCategoriesToRollUp>  
        ...  
    </TemplateData>  
    ```  
  
5.  .vstemplate dosyasını kaydedip kapatın.  
  
6.  Şablonunuzda dosyaları seçin, seçime sağ tıklayın, **göndermek için**ve ardından **sıkıştırılmış (daraltılmış) klasör**. Dosyaları bir .zip dosyasına sıkıştırılır.  
  
7.  Ayıklanan şablon dosyalarını ve eski şablonu .zip dosyasını silin.  
  
8.  Yeni bir .zip dosyası silinen .zip dosyasını olduğu dizine yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)   
 [NumberOfParentCategoriesToRollUp (Visual Studio şablonları)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)   
 [Nasıl yapılır: Proje şablonları oluşturma](../ide/how-to-create-project-templates.md)   
 [Nasıl Yapılır: Öğe Şablonları Oluşturma](../ide/how-to-create-item-templates.md)



