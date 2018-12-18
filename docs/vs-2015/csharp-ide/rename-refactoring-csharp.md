---
title: (C#) yeniden düzenlemeyi yeniden adlandırma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d88cf6d88f23a3a079d5f9a556c316a204c9ef27
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274969"
---
# <a name="rename-refactoring-c"></a>Yeniden Düzenlemeyi (C#) yeniden adlandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Yeniden adlandırma** alanlar, yerel değişkenler, yöntemleri, ad alanları, özellikleri ve türleri gibi kod simgeleri tanımlayıcıları yeniden adlandırmak için kolay bir yolunu sağlayan Visual Studio tümleşik geliştirme ortamı (IDE) yeniden düzenleme bir özelliktir. **Yeniden adlandırma** açıklamalarında ve Dizelerdeki adlarını değiştirmek için ve bir tanımlayıcının çağrıları ve bildirimleri değiştirmek için kullanılabilir.  
  
> [!NOTE]
>  Yeniden adlandırma düzenlemesi gerçekleştirmeye çalışmadan önce kaynak denetimi Visual Studio için kullanılırken, kaynakları en son sürümünü alın.  
  
 Yeniden adlandırma düzenlemesi aşağıdaki Visual Studio özellikleri kullanılabilir:  
  
|Özellik|IDE içinde yeniden düzenleme davranışı|  
|-------------|----------------------------------------|  
|Kod Düzenleyicisi|Kod simgeleri belirli türlerde işaretçiyi getirdiğinizde Kod Düzenleyicisi'nde, yeniden adlandırma düzenlemesi kullanılabilir. İmleci bu konumda olduğunda, çağırabilirsiniz **Yeniden Adlandır** klavye kısayolunu (CTRL + R, CTRL + R) yazarak ya da seçerek komutunu **Yeniden Adlandır** akıllı etiket, kısayol menüsünden veya komutu **Yeniden düzenleme** menüsü.|  
|Sınıf Görünümü|Sınıf Görünümü'nde bir tanımlayıcı seçin, yeniden adlandırma düzenlemesi kısayol menüsünden kullanılabilir ve **yeniden düzenleme** menüsü.|  
|Nesne Tarayıcısı|Nesne Tarayıcısı'nda bir tanımlayıcı seçin, yeniden adlandırma düzenlemesi yalnızca kullanılabilir **yeniden düzenleme** menüsü.|  
|Windows Form Tasarımcısı'nın özellik Kılavuzu|İçinde **özellik kılavuzunda** Windows Forms tasarımcısına denetim adının değiştirilmesi bu denetim için bir yeniden adlandırma işlemi başlatır. **Yeniden Adlandır** iletişim kutusu görünmez.|  
|Çözüm Gezgini|İçinde **Çözüm Gezgini**, **Yeniden Adlandır** komutu kısayol menüsünde kullanılabilir. Seçili kaynak dosyasının dosya adı ile aynı sınıf adı olan bir sınıf içeriyorsa, aynı anda kaynak dosyayı yeniden adlandırın ve yeniden adlandırma düzenlemesi yürütmek için bu komutu kullanabilirsiniz.<br /><br /> Örneğin, varsayılan Windows tabanlı bir uygulama oluşturup, ardından Form1.cs TestForm.cs için yeniden adlandırın TestForm.cs ve Form1 sınıfı için kaynak dosya adı Form1.cs değiştirir ve tüm başvuruları sınıfı için TestForm adlandırılacak. **Not:** **geri** komut (CTRL + Z) yalnızca kodda yeniden adlandırma düzenlemesi Geri Al ve dosya adı, özgün adına geri değişiklik olur. <br /><br /> Seçili kaynak dosyası adı dosya adıyla aynı olan bir sınıf içermiyorsa **Yeniden Adlandır** komutunu **Çözüm Gezgini** yalnızca kaynak dosyayı yeniden adlandırır ve yeniden adlandırma yürütülmez yeniden düzenleme.|  
  
## <a name="rename-operations"></a>İşlemleri yeniden adlandırın.  
 Yürüttüğünüzde **Yeniden Adlandır**, yeniden düzenleme altyapısı aşağıdaki tabloda açıklandığı gibi her kod simge için belirli bir yeniden adlandırma işlemi gerçekleştirir.  
  
|Kod simgesi|İşlemi yeniden adlandırın.|  
|-----------------|----------------------|  
|Alan|Bildirimler ve kullanımları alan yeni bir adla değiştirir.|  
|yerel değişken|Bildirimler ve değişken kullanımları yeni bir adla değiştirir.|  
|Yöntem|Yeni bir adla adı yöntemi ve bu yöntem tüm başvurularını değiştirir. **Not:** kapsamda genişletme yöntemi statik bir yöntem veya bir örnek yöntemi kullanılıp kullanılmadığı bağımsız olarak tüm örneklerine yöntemin bir genişletme yöntemi yeniden adlandırdığınızda, yeniden adlandırma işlemi yayar. Daha fazla bilgi için [genişletme yöntemleri](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Ad Alanı|Yeni adın bildiriminde ad değişikliklerini tüm `using` deyimleri ve tam olarak nitelenmiş adlar. **Not:** bir ad alanı yeniden adlandırılırken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de güncelleştirir **varsayılan Namespace** özelliği **uygulama** sayfasının **Proje Tasarımcısı**. Bu özellik, seçerek sıfırlanamaz **geri** gelen **Düzenle** menüsü. Sıfırlamak için **varsayılan Namespace** özellik değeri özelliğinde değiştirmelisiniz **Proje Tasarımcısı**. Daha fazla bilgi için [uygulama sayfası](../ide/reference/application-page-project-designer-csharp.md).|  
|Özellik|Bildirimler ve kullanımları özelliğinin yeni ad ile değiştirir.|  
|Tür|Tüm bildirimleri ve türdeki tüm kullanımları oluşturucular ve Yıkıcılar dahil olmak üzere yeni ad ile değiştirir. Kısmi türler için yeniden adlandırma işlemi için tüm bölümleri yayılır.|  
  
#### <a name="to-rename-an-identifier"></a>Bir tanımlayıcı yeniden adlandırmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `RenameIdentifier`ve ardından `Program` ile aşağıdaki kod örneği.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  İmleci üzerine getirin `MethodB`, yöntem bildiriminde veya yöntem çağrısı.  
  
3.  Gelen **yeniden düzenleme** menüsünde **Yeniden Adlandır**. **Yeniden Adlandır** iletişim kutusu görüntülenir.  
  
     Ayrıca, imleç sağ işaret **yeniden düzenleyin** bağlam menüsünü ve ardından **Yeniden Adlandır** görüntülemek için **Yeniden Adlandır** iletişim kutusu.  
  
4.  İçinde **yeni adı** alanına `MethodC`.  
  
5.  Seçin **açıklamalarda arama** onay kutusu.  
  
6.  **Tamam**'ı tıklatın.  
  
7.  İçinde **Değişiklikleri Önizle** iletişim kutusu, tıklayın **Uygula**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Akıllı etiketleri kullanarak bir tanımlayıcı yeniden adlandırmak için  
  
1.  Adlı bir konsol uygulaması oluşturun `RenameIdentifier`ve ardından `Program` ile aşağıdaki kod örneği.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Öğesinin bildiriminde `MethodB`yazın veya yöntem tanımlayıcısının üzerine geri al. Akıllı etiket istemi bu tanımlayıcının altında görünür.  
  
    > [!NOTE]
    >  Yalnızca bir tanımlayıcının bildirimi akıllı etiketleri kullanarak yeniden adlandırma düzenlemesi de çağırabilirsiniz.  
  
3.  SHIFT + ALT + F10 klavye kısayolunu yazın ve ardından akıllı etiket menüsündeki görüntülemek için aşağı ok tuşuna basın.  
  
     veya  
  
     Akıllı etiketi görüntülemek için akıllı etiketin üzerine fare işaretçisini taşıyın. Ardından akıllı etiket üzerine fare işaretçisini Taşı ve aşağı akıllı etiket menüsündeki görüntülemek için OKA tıklayın.  
  
4.  Seçin **Yeniden Adlandır '\<identifer1 >' için '\<identifier2 >'** kodunuzda değişiklik önizlemesi olmadan yeniden adlandırma düzenlemesi çağırmak için menü öğesi. Tüm başvuruları  **\<identifer1 >** şekilde otomatik olarak güncelleştirilecek  **\<identifier2 >**.  
  
     veya  
  
     Seçin **Önizleme ile yeniden adlandır** kodunuzda değişiklik önizlemesi ile yeniden adlandırma düzenlemesi çağırmak için menü öğesi. **Değişiklikleri Önizle** iletişim kutusu görüntülenir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="renaming-implemented-or-overridden-members"></a>Uygulanan veya geçersiz kılınan üye yeniden adlandırma  
 Olduğunda, **Yeniden Adlandır** uygular/geçersiz kılmalar veya uygulanan/geçersiz tarafından diğer türlerde üyeleri bir üye [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yeniden adlandırma işlemi basamaklı güncelleştirmeleri neden ifadesini içeren bir iletişim kutusu görüntüler. Tıklarsanız **devam**, yeniden düzenleme altyapısı yinelemeli olarak bulur ve temel tüm üyeleri yeniden adlandırır ve türetilmiş türleri uygulayan/geçersiz kılmaları ilişkileri adlandırılan üyesiyle.  
  
 Aşağıdaki kod örneğinde uygular/geçersiz kılmaları ilişkilerle üyeleri içerir.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 Önceki örnekte, yeniden adlandırma `C.Method()` da yeniden adlandırır `Ibase.Method()` çünkü `C.Method()` uygulayan `Ibase.Method()`. Ardından, yeniden düzenleme altyapısı yinelemeli olarak bu görür `Ibase.Method()` tarafından uygulanan `Derived.Method()` ve yeniden adlandırır `Derived.Method()`. Yeniden düzenleme altyapısı adlandırmaz `Base.Method()`, çünkü `Derived.Method()` geçersiz `Base.Method()`. Yeniden düzenleme altyapısı yoksa burada durdurulur **yeniden adlandırma, aşırı** iade **Yeniden Adlandır** iletişim kutusu.  
  
 Varsa **yeniden adlandırma, aşırı** seçiliyse, yeniden düzenleme altyapısı yeniden adlandırır `Derived.Method(int i)` aşırı `Derived.Method()`, `Base.Method(int i)` tarafından geçersiz olduğundan `Derived.Method(int i)`, ve `Base.Method()` çünkü bu bir aşırı yüklemesini `Base.Method(int i)`.  
  
> [!NOTE]
>  Başvurulan bir derlemede tanımlanan üye yeniden adlandırdığınızda, yeniden adlandırma yapı hatalarına neden olacak bir iletişim kutusu açıklar.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Anonim türler özelliklerini yeniden adlandırma  
 Anonim türler özelliğinde yeniden adlandırdığınızda, yeniden adlandırma işlemi için aynı özelliklere sahip olan diğer anonim türler özelliklerinde yayılır. Aşağıdaki örnekler, bu davranış görülmektedir.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 Önceki kodda, yeniden adlandırma `ID` değiştirecek `ID` her iki deyimde aynı temel anonim tür sahip oldukları.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 Önceki kodda, yeniden adlandırma `ID` yalnızca bir örneğini yeniden adlandıracak `ID` çünkü `companyIDs` ve `orderIDs` aynı özelliklere sahip değildir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden düzenlemesi (C#)](../csharp-ide/refactoring-csharp.md)   
 [Anonim Tipler](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)