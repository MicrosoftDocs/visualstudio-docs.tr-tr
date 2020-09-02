---
title: Yeniden düzenleme (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667509"
---
# <a name="refactoring-c"></a>Yeniden Düzenleme (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yeniden düzenleme, kodun dış davranışını değiştirmeden kodun iç yapısı değiştirilerek yazıldıktan sonra kodunuzu geliştirme işlemidir.

 Visual C# yeniden **düzenleme** menüsünde aşağıdaki yeniden düzenleme komutlarını sağlar:

- [Ayıklama Yöntemi Yeniden Düzenlemesi (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Yeniden Düzenlemeyi (C#) Yeniden Adlandırma](../csharp-ide/rename-refactoring-csharp.md)

- [Alan Yeniden Düzenlemesini Yalıtma (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Ayıklama Arabirimi Yeniden Düzenlemesi (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Parametreleri Kaldır Yeniden Düzenlemesi (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Parametreleri Yeniden Sırala (C#) yeniden düzenlemesi](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Çoklu projeli yeniden düzenleme
 Visual Studio, aynı çözümde olan projeler için çoklu proje yeniden düzenlemeyi destekler. Dosyalar arasındaki başvuruları izleyen yeniden düzenleme işlemleri, aynı dilin tüm projeleri üzerinde bu başvuruları düzeltmelidir. Bu, tüm projeden projeye başvurular için geçerlidir. Örneğin, bir sınıf kitaplığına başvuran bir konsol uygulamanız varsa, bir sınıf kitaplığı türünü yeniden adlandırdığınızda (yeniden `Rename` düzenleme işlemini kullanarak), konsol uygulamasındaki sınıf kitaplığı türü başvuruları da güncelleştirilir.

## <a name="changes-preview"></a>Değişiklikleri Önizle
 Birçok yeniden düzenleme işlemi, bu değişikliklere işlemeden önce kodunuzda bir yeniden düzenleme işleminin gerçekleştireceği tüm başvuru değişikliklerini gözden geçirmeniz için bir fırsat sağlar. Bu yeniden düzenleme işlemleri için yeniden düzenleme iletişim kutusunda bir **başvuru değişiklikleri Önizleme** seçeneği görüntülenir. Bu seçeneği belirledikten ve yeniden düzenleme işlemini kabul ettikten sonra **Değişiklikleri Önizle Iletişim kutusu** görüntülenir. **Değişiklikleri Önizle** iletişim kutusunun iki görünümü olduğunu unutmayın. Alt görünüm, yeniden düzenleme işlemi nedeniyle kodunuzu tüm başvuru güncelleştirmeleriyle görüntüleyecektir. **Değişiklikleri Önizle** Iletişim kutusunda **iptal 'e** basmak yeniden düzenleme işlemini durdurur ve kodunuzda hiçbir değişiklik yapılmaz.

## <a name="refactoring-warnings"></a>Yeniden düzenleme uyarıları
 Derleyicinin programınızı tamamen anlayabilmesi ve yeniden düzenleme altyapısının tüm uygun başvuruları güncelleştiremeyebilir olması halinde, uyarı iletişim kutusu görüntülenir. Bu uyarı iletişim kutusu, değişiklikleri işlemeden önce kodunuzu **Önizleme iletişim kutusunda** önizlemeniz için bir fırsat de sağlar.

> [!NOTE]
> Bir yöntem bir sözdizimi hatası (IDE 'nin kırmızı dalgalı alt çizgiyle gösterdiği) içeriyorsa, yeniden düzenleme altyapısı bu yöntemin içindeki bir öğeye yönelik başvuruları güncelleştirmeyecektir. Aşağıdaki örnekte bu davranış gösterilmektedir.

 Varsayılan olarak, başvuru değişikliklerinin önizlemesini yapmadan bir yeniden düzenleme işlemi çalıştırırsanız ve programınızda bir derleme hatası algılanırsa, geliştirme ortamı bu uyarı iletişim kutusunu görüntüler.

 **Önizleme başvurusu değişiklikleri** etkin olan bir yeniden düzenleme işlemi yürütüyecekseniz ve programınızda bir derleme hatası algılanırsa, geliştirme ortamı, yeniden **düzenleme uyarısı** Iletişim kutusunun altında, **Değişiklikleri Önizle** iletişim kutusunun alt kısmında aşağıdaki uyarı iletisini görüntüler:

 **Projeniz veya bağımlılıklarından biri şu anda derlenmiyor. Başvurular güncelleştirilmemiş olabilir.**

 Bu yeniden düzenleme uyarısı yalnızca, **başvuru değişikliklerini Önizle** seçeneğini sağlayan yeniden düzenleme işlemleri için kullanılabilir.

## <a name="error-tolerant-refactoring-and-verification-results"></a>Hataya dayanıklı yeniden düzenleme ve doğrulama sonuçları
 Yeniden düzenleme hataya dayanıklıdır. Diğer bir deyişle, derlenemez bir projede yeniden düzenleme yapabilirsiniz. Ancak, bu durumlarda yeniden düzenleme işlemi belirsiz başvuruları doğru şekilde güncelleştirmeyebilir.

 Yeniden düzenleme motorunun derleme hatalarını algıladığında veya yeniden düzenleme işleminin yanlışlıkla bir kod başvurusunun, ilk bağlandıklarından farklı bir şeye bağlanmasına neden olduğunu tespit ederse **doğrulama sonuçları** iletişim kutusu sizi bilgilendirebilir.

 Doğrulama sonuçları özelliğini etkinleştirmek için, **Araçlar** menüsünde **Seçenekler**' e tıklayın. **Seçenekler** Iletişim kutusunda **metin düzenleyici**' yi genişletin ve ardından **C#**' ı genişletin. **Gelişmiş** ' e tıklayın ve yeniden **düzenleme sonuçlarını doğrula** onay kutusunu seçin.

 **Doğrulama sonuçları** iletişim kutusu iki tür yeniden bağlama sorunu arasındaki farkı ayırır.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Tanımı artık yeniden adlandırılmış simge olmayacak olan başvurular
 Bu tür yeniden bağlama sorunu, bir başvuru artık yeniden adlandırılmış bir sembole başvurmuyorsa oluşur. Örneğin, aşağıdaki kodu göz önünde bulundurun:

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

 Yeniden adlandırmak için yeniden düzenleme kullanırsanız `a` `b` , bu iletişim kutusu görüntülenir. Yeniden adlandırılmış değişken başvurusu `a` artık alana bağlamak yerine oluşturucuya geçirilen parametreye bağlanır.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Tanımı şimdi yeniden adlandırılmış simge olacak olan başvurular
 Daha önce yeniden adlandırılmış simgeye başvurmayan bir başvuru artık yeniden adlandırılmış simgeye başvurursa bu tür yeniden bağlama sorunu oluşur. Örneğin, aşağıdaki kodu göz önünde bulundurun:

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

 Yeniden adlandırmak için yeniden düzenleme kullanırsanız `OtherMethod` `Method` , bu iletişim kutusu görüntülenir. ' Deki başvuru `Main` artık `int` bir parametreyi kabul eden aşırı yüklenmiş yöntem yerine bir parametreyi kabul eden aşırı yüklenmiş yönteme başvurur `object` .

## <a name="see-also"></a>Ayrıca Bkz.
 [C# için Visual Studio geliştirme ortamını kullanma](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [nasıl yapılır: C# yeniden düzenleme parçacıklarını geri yükleme](../ide/how-to-restore-csharp-refactoring-snippets.md)