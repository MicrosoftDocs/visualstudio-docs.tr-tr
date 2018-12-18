---
title: Yeniden düzenlemesi (C#) | Microsoft Docs
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
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4f74017a067d4681eb14ba4eb826df504497430
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262320"
---
# <a name="refactoring-c"></a>Yeniden Düzenleme (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeniden düzenleme, kod dış davranışını değiştirmeden kodu iç yapısını değiştirerek yazıldıktan sonra kodu geliştirme işlemidir.  
  
 Visual C# yeniden düzenleme aşağıdaki komutları hakkında sağlar **yeniden düzenleme** menüsü:  
  
-   [Ayıklama Yöntemi Yeniden Düzenlemesi (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Yeniden Düzenlemeyi (C#) Yeniden Adlandırma](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Alan Yeniden Düzenlemesini Yalıtma (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Ayıklama Arabirimi Yeniden Düzenlemesi (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Parametreleri Kaldır Yeniden Düzenlemesi (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Parametreleri Yeniden Sırala (C#) Yeniden Düzenlemesi](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Birden çok proje yeniden düzenleme  
 Visual Studio, birden çok proje aynı Çözümdeki projeler için yeniden düzenleme destekler. Tüm dosyalardaki başvuruları düzeltmek yeniden düzenleme işlemleri, aynı dili tüm projeler genelinde bu başvuruları düzeltin. Bu, herhangi bir projeden projeye başvurular için çalışır. Örneğin, bir sınıf kitaplığı, bir sınıf kitaplığı türü yeniden adlandırdığınızda başvuran bir konsol uygulaması varsa (kullanarak `Rename` yeniden düzenleme işlemi), konsol uygulamasındaki sınıf kitaplığı türü başvuruları de güncellenir.  
  
## <a name="changes-preview"></a>Değişiklikleri Önizleme  
 Çok sayıda yeniden düzenleme işlemleri, bu değişiklikleri yapmadan önce kodunuza, bir yeniden düzenleme işlemi gerçekleştirecek tüm başvuru değişikliklerini gözden geçirmeniz bir fırsat sağlar. Bu yeniden düzenleme işlemleri, bir **başvuru değişiklik önizlemesi** seçeneği, yeniden düzenleme iletişim kutusunda görüntülenir. Bu seçeneğin belirlenmesi ve yeniden düzenleme işlemi kabul edildikten sonra **değişiklikleri Önizleme iletişim kutusu** görünür. Dikkat **Değişiklikleri Önizle** iletişim kutusunda iki görünüm vardır. Kodunuzu yeniden düzenleme işlemi nedeniyle tüm başvuru güncelleştirmeleri ile alt görünümü görüntülenir. Tuşuna basarak **iptal** üzerinde **Değişiklikleri Önizle** iletişim kutusunu yeniden düzenleme işlemi durdurur ve kodunuzda hiçbir değişiklik yapılmaz.  
  
## <a name="refactoring-warnings"></a>Uyarıları yeniden düzenleme  
 Derleyici, programınızın tam bir anlayışa sahip değil ve yeniden düzenleme altyapısı tüm uygun başvuruları güncelleştirilemeyebilir mümkündür, uyarı iletişim kutusu görüntülenir. Bu uyarı iletişim kutusunda da kodunuzda önizlemek bir fırsat sağlar **Değişiklikleri Önizle** değişiklikleri göndermeden önce iletişim kutusu.  
  
> [!NOTE]
>  Bir yöntem (gösteren IDE dalgalı kırmızı alt çizgi ile) bir sözdizimi hatası içeriyorsa, yeniden düzenleme altyapısı yöntemin içindeki bir öğeye yönelik tüm başvuruları güncelleştirmez. Aşağıdaki örnek, bu davranış gösterir.  
  
 Varsayılan olarak çalışırsa, başvuru Önizleme olmadan bir yeniden düzenleme işlemi değiştirir ve bir derleme hatası programınızda algılanır ve sonra geliştirme ortamı bu uyarı iletişim kutusu görüntüler.  
  
 Sahip bir yeniden düzenleme işlemi yürütüyorsa **başvuru değişikliklerini önizle** etkin ve bir derleme hatası programınızda algılandığında ve geliştirme ortamını sonunda aşağıdaki uyarı iletisi görüntülenir **Değişiklikleri Önizle** iletişim kutusunda, görüntülemek yerine **yeniden düzenleme uyarısı** iletişim kutusunda:  
  
 **Projenizi veya onun bağımlılıklarından biri şu anda oluşturmaz. Başvuruları güncelleştirilmeyebilir.**  
  
 Bu yeniden düzenleme uyarısı yalnızca yeniden düzenleme sağlayan işlemleri için kullanılabilir **başvuru değişikliklerini önizle** seçeneği.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Hataya dayanıklı yeniden düzenleme ve sonuçları doğrulama  
 Yeniden düzenleme, hata toleransı değil. Diğer bir deyişle, bir derleme bir projede yeniden düzenleme gerçekleştirebilirsiniz. Ancak, bu gibi durumlarda yeniden düzenleme işlemi belirsiz başvuru doğru güncelleştirilemeyebilir.  
  
 **Doğrulama sonuçları** iletişim kutusu size bildirebilir düzenleme altyapısı derleme hataları tespit ya da bir yeniden düzenleme işlemi yanlışlıkla ne olduğunu öğesinden farklı bir şey bağlamak bir kod başvurusu neden bulur Başlangıçta (sorunu yeniden bağlama için) bağlı.  
  
 Açmak için doğrulama sonuçlarını, üzerinde özellik **Araçları** menüsünde tıklatın **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **metin düzenleyici**ve ardından **C#**. Tıklayın **Gelişmiş** seçip **doğrulama sonuçlarını, yeniden düzenleme** onay kutusu.  
  
 **Doğrulama sonuçları** iletişim kutusu, sorunları yeniden bağlama iki tür arasındaki farkı ayırır.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Tanımı yeniden adlandırılmış sembol olmayacak başvuruları  
 Yeniden adlandırılan sembole başvuru artık başvurduğunda bu tür bir sorunu yeniden bağlama gerçekleşir. Örneğin, aşağıdaki kodu düşünün:  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Yeniden adlandırmak için yeniden düzenleme kullanırsanız `a` için `b`, bu iletişim kutusu görüntülenir. Yeniden adlandırılan değişkenine başvuru `a` artık alana bağlamak yerine oluşturucusuna geçirilen parametreyi bağlar.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Tanımları, yeniden adlandırılmış sembol artık olacak başvurular  
 Yeniden adlandırılmış, daha önce yeniden adlandırılmış artık başvurmuyor başvuru başvurduğunuzda, bu tür bir sorunu yeniden bağlama gerçekleşir. Örneğin, aşağıdaki kodu düşünün:  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Yeniden adlandırmak için yeniden düzenleme kullanırsanız `OtherMethod` için `Method`, bu iletişim kutusu görüntülenir. Başvuru `Main` artık kabul eden aşırı yüklenmiş Metoda başvuran bir `int` parametre kabul eden aşırı yüklenmiş yöntem yerine bir `object` parametresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# için Visual Studio geliştirme ortamını kullanma](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Nasıl Yapılır: C# Yeniden Düzenleme Kod Parçacıklarını Geri Yükleme](../ide/how-to-restore-csharp-refactoring-snippets.md)