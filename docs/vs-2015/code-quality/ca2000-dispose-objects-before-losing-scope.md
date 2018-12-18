---
title: 'CA2000: Kapsamı kaybetmeden önce verileri nesneleri Dispose | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ce258af87dc9a7732200b410113ee778e0bfbccb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857867"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Kapsamı kaybetmeden önce verileri atın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Kategori|Microsoft.Reliability|  
|Yeni Değişiklik|Bölünemez|  
  
## <a name="cause"></a>Sebep  
 Yerel bir nesne bir <xref:System.IDisposable> türü oluşturulur, ancak nesne tüm başvuruları kapsam dışına çıkmadan önce nesne atılmaz.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Tüm başvuruları kapsam dışı olmadan önce atılabilir bir nesne açıkça elden değil, nesnenin çöp toplayıcı nesnenin Sonlandırıcısı çalıştığında belirsiz bir zamanda silinip. Olağanüstü bir olay ortaya çıkabilecek çünkü Sonlandırıcı engelleyecek çalışmasını nesne, nesne açıkça elden çıkarılmalıdır.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 Bu kural ihlalini düzeltmek için çağrı <xref:System.IDisposable.Dispose%2A> tüm başvuruları kapsam dışı olmadan önce nesne üzerinde.  
  
 Kullanabileceğiniz Not `using` deyimi (`Using` içinde [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) uygulayan nesneler sarmalamak için `IDisposable`. Bu şekilde kaydırılan nesneler otomatik olarak atıldı kapanışında `using` blok.  
  
 Bazı durumlar şunlardır burada using deyimi IDisposable nesneleri korumak yeterli değildir ve CA2000 oluşmasına neden olabilir.  
  
-   Atılabilir bir nesne döndürmekten gerektirir kullanarak bir dışında bir try/finally bloğu nesne oluşturulmuş blok.  
  
-   Tek kullanımlık bir nesnenin üyelerine başlatma yapılmamalıdır kullanarak bir oluşturucuda deyimi.  
  
-   Yalnızca bir özel durum işleyicisi tarafından korunan oluşturuculara iç içe geçirme. Örneğin,  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     CA2000 hiç kapalı FILESTREAM nesnesinde bir hata StreamReader nesnenin yapımı sağladığından oluşmasına neden olur.  
  
-   Dinamik nesneler gölge nesne IDisposable nesnelerin Dispose deseni uygulamak için kullanmanız gerekir.  
  
## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında  
 Nesnenizde `Dispose` gibi <xref:System.IO.Stream.Close%2A> çağıran bir yöntem çağırmadığınız sürece veya uyarıyı oluşturan yöntem nesnenizi sarmalayan bir IDisposable nesnesi getirmediği sürece bu kuraldan bir uyarıyı bastırmayın.  
  
## <a name="related-rules"></a>İlgili kuralları  
 [CA2213: Atılabilen alanlar atılmalıdır](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: Nesneleri birden çok kez atmayın](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## <a name="example"></a>Örnek  
 Atılabilir bir nesne döndüren bir yöntem uyguluyorsanız, nesneyi elden emin olmak için bir try/finally bloğu bir catch bloğu olmadan kullanın. Bir try/finally bloğu kullanarak hataya noktada oluşturulması ve bu nesneyi elden emin olmak özel durumlara izin.  
  
 OpenPort1 yönteminde ISerializable nesneyi çevirmek için SerialPort açmak için bir çağrı veya SomeMethod çağrısı başarısız olabilir. Bu uygulama üzerinde CA2000 uyarısı oluşturulur.  
  
 OpenPort2 yönteminde bildirilmiş ve ayarlanmış null iki çevirmek için SerialPort nesneleri şunlardır:  
  
- `tempPort`, yöntemi işlemleri başarılı olduğunu test etmek için kullanılır.  
  
- `port`, yöntemin dönüş değeri için kullanılır.  
  
  `tempPort` Oluşturulur ve açılır bir `try` blok ve diğer gerekli iş aynı gerçekleştirilir `try` blok. Sonunda `try` blok, açılan bağlantı noktası atanır `port` döndürülecek nesne ve `tempPort` nesne ayarlandığında `null`.  
  
  `finally` Blok değerini denetler `tempPort`. Null değilse, yöntem bir işlem başarısız oldu, ve `tempPort` tüm kaynakları serbest bırakıldığından emin olmak için kapatılır. Döndürülen bağlantı nesnesi yöntemi işlemleri başarılı ya da bir işlem başarısız olursa null olacaktır açılmış çevirmek için SerialPort nesne içerir.  
  
  [!code-csharp[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/cs/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.cs#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vb#1)]
  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope/vb/fxcop.reliability.ca2000.disposeobjectsbeforelosingscope.vboverflow.vb#1)]  
  
## <a name="example"></a>Örnek  
 Varsayılan olarak, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyici sahip tüm aritmetik işleçler için taşmayı denetle. Bu nedenle, herhangi bir Visual Basic aritmetik işlem fırlatabilir bir <xref:System.OverflowException>. Bu kurallar CA2000 gibi beklenmeyen ihlallerini neden olabilir. Örneğin, Visual Basic Derleyicisi, yönerge değil çıkarılması StreamReader neden olan bir özel durum oluşturabilir eklenmesi için denetimi taşma yayma çünkü aşağıdaki CreateReader1 işlevi bir CA2000 ihlaline neden olur.  
  
 Bunu düzeltmek için projenizdeki Visual Basic derleyici tarafından taşma denetimleri yaymayı devre dışı bırakabilir veya kodunuz aşağıdaki CreateReader2 işlevi olduğu gibi değiştirebilirsiniz.  
  
 Taşma denetimleri yaymayı devre dışı bırakmak için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**. Tıklayın **derleme**, tıklayın **Gelişmiş derleme seçenekleri**, iade edin **tamsayı taşması denetimlerini Kaldır**.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  -->  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IDisposable>   
 [Dispose Deseni](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)