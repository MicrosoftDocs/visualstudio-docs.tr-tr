---
title: 'İzlenecek yol: bir modeli erişen metin şablonunda hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ca80111415c869543297ed24707ae27f0490f07b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924895"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>İzlenecek yol: Modele Erişen Metin Şablonunda Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kaynak kodu veya oluşturulan kodun derlediğinde şablon altyapısı dönüştürürken, Değiştir veya metin şablonları bir etki alanına özgü dil çözümünde eklediğinizde, hatalar alabilirsiniz. Aşağıdaki örneklerde bir metin şablonunda hata ayıklama için yapabileceğiniz şeylerden bazıları gösterilmektedir.  
  
> [!NOTE]
>  Metin hakkında daha fazla bilgi için genel olarak, bkz: şablonları [kod oluşturma ve T4 metin şablonları](../modeling/code-generation-and-t4-text-templates.md). Metin şablonları hata ayıklama hakkında daha fazla bilgi için bkz. [izlenecek yol: bir metin şablonunda hata ayıklama](http://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Bir etki alanına özgü dil çözümü oluşturma  
 Bu yordamda aşağıdaki özelliklere sahip bir etki alanına özgü dil çözümü oluşturun:  
  
- Ad: DebuggingTestLanguage  
  
- Çözüm şablonu: en az bir dil  
  
- Dosya uzantısı: .ddd  
  
- Şirket adı: Fabrikam  
  
  Bir etki alanına özgü dil çözümü oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir etki alanına özgü dil çözümü oluşturma](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Bir metin şablonu oluşturma  
 Bir metin şablonu çözümünüze ekleyin.  
  
#### <a name="to-create-a-text-template"></a>Bir metin şablonu oluşturmak için  
  
1.  Çözümü derleyin ve hata ayıklayıcıda çalıştırmaya başlayın. (Üzerinde **derleme** menüsünde tıklayın **çözümü yeniden derle**ve ardından **hata ayıklama** menüsünde tıklayın **hata ayıklamayı Başlat**.) Hata ayıklama projeyi Visual Studio'nun yeni bir örneğini açar.  
  
2.  Adlı bir metin dosyası Ekle `DebugTest.tt` hata ayıklama projeye.  
  
3.  Emin olun **özel araç** DebugTest.tt özelliği ayarlandığında `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Bir metin şablonundan bir model erişim yönergeleri hata ayıklama  
 Bir model ifadeleri ve bir metin şablonu ifadelerinde erişebilmeniz için önce üretilen bir yönerge işlemcisine çağırmanız gerekir. Üretilen bir yönerge işlemcisine çağırma sınıfları modelinizde metin şablonunun kod özellikleri olarak kullanılabilmesini sağlar. Daha fazla bilgi için [metin şablonlarından modellere erişme](../modeling/accessing-models-from-text-templates.md).  
  
 Aşağıdaki yordamlarda, hatalı bir yönerge adı ya da bir yanlış özellik adını hata ayıklayacaktır.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Hatalı bir yönerge adı hata ayıklama  
  
1.  DebugTest.tt kodu aşağıdaki kodla değiştirin:  
  
    > [!NOTE]
    >  Bir hata kodunu içerir. Hata ayıklama için kullanıma sunuyoruz.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  İçinde **Çözüm Gezgini**DebugTest.tt sağ tıklayın ve ardından **özel aracı Çalıştır**.  
  
     **Hata listesi** penceresinde bu hata görüntülenir:  
  
     **'DebuggingTestLanguageDirectiveProcessor' adlı işlemci, 'modelRoot' adlı yönergeyi desteklemiyor. Dönüştürme çalışmaz.**  
  
     Bu durumda, hatalı bir yönerge adı yönerge çağrıyı içerir. Belirttiğiniz `modelRoot` , ancak doğru yönergesi adına yönerge adı olarak `DebuggingTestLanguage`.  
  
3.  Hataya çift **hata listesi** koda gitmek penceresi.  
  
4.  Kodu düzeltmek için yönerge adına değiştirme `DebuggingTestLanguage`.  
  
     Değişiklik vurgulanır.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  İçinde **Çözüm Gezgini**DebugTest.tt sağ tıklayın ve ardından **özel aracı Çalıştır**.  
  
     Artık sistem metin şablonunun dönüştürür ve karşılık gelen çıkış dosyası oluşturur. Herhangi bir hata görmeyeceğiniz **hata listesi** penceresi.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Bir hatalı özellik adı hata ayıklama  
  
1.  DebugTest.tt kodu aşağıdaki kodla değiştirin:  
  
    > [!NOTE]
    >  Bir hata kodunu içerir. Hata ayıklama için kullanıma sunuyoruz.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  İçinde **Çözüm Gezgini**DebugTest.tt sağ tıklayın ve ardından **özel aracı Çalıştır**.  
  
     **Hata listesi** penceresi görüntülenir ve bu hatalardan birini görüntüler:  
  
     (C#)  
  
     **Dönüştürme derleniyor: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' 'ExampleModel' için bir tanım içermiyor**  
  
     (Visual Basic)  
  
     **Dönüştürme derleniyor: 'ExampleModel' üyesi değil ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     Bu durumda, bir yanlış özellik adı metin şablon kodunu içerir. Belirttiğiniz `ExampleModel` özellik adı, ancak doğru özelliği adıdır `LibraryModel`. Doğru özellik adında bulabilirsiniz parametresi, aşağıdaki kodda gösterildiği gibi sağlar:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Koda gitmek için Hata Listesi penceresindeki hataya çift tıklayın.  
  
4.  Bu kodu düzeltmek için özellik adına değiştirme `LibraryModel` metin şablonunun kod.  
  
     Değişiklikler vurgulanır.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  İçinde **Çözüm Gezgini**DebugTest.tt sağ tıklayın ve ardından **özel aracı Çalıştır**.  
  
     Artık sistem metin şablonunun dönüştürür ve karşılık gelen çıkış dosyası oluşturur. Herhangi bir hata görmeyeceğiniz **hata listesi** penceresi.



