---
title: 'CA2000: Kapsamı kaybetmeden önce verileri atın'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2000
- Dispose objects before losing scope
- DisposeObjectsBeforeLosingScope
helpviewer_keywords:
- CA2000
- DisposeObjectsBeforeLosingScope
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 041cade3d1c65a40826920b94adf012aa9a4b021
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549876"
---
# <a name="ca2000-dispose-objects-before-losing-scope"></a>CA2000: Kapsamı kaybetmeden önce verileri atın

|||
|-|-|
|TypeName|DisposeObjectsBeforeLosingScope|
|CheckId|CA2000|
|Kategori|Microsoft.Reliability|
|Yeni Değişiklik|Bölünemez|

## <a name="cause"></a>Sebep
 Yerel bir nesne bir <xref:System.IDisposable> türü oluşturulur, ancak nesne tüm başvuruları kapsam dışına çıkmadan önce nesne atılmaz.

## <a name="rule-description"></a>Kural açıklaması
 Tüm başvuruları kapsam dışı olmadan önce atılabilir bir nesne açıkça elden değil, nesnenin çöp toplayıcı nesnenin Sonlandırıcısı çalıştığında belirsiz bir zamanda silinip. Olağanüstü bir olay ortaya çıkabilecek çünkü Sonlandırıcı engelleyecek çalışmasını nesne, nesne açıkça elden çıkarılmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller nasıl düzeltilir?
 Bu kural ihlalini düzeltmek için çağrı <xref:System.IDisposable.Dispose%2A> tüm başvuruları kapsam dışı olmadan önce nesne üzerinde.

 Kullanabileceğiniz Not `using` deyimi (`Using` içinde [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) uygulayan nesneler sarmalamak için `IDisposable`. Bu şekilde kaydırılan nesneler otomatik olarak atıldı kapanışında `using` blok.

 Bazı durumlar şunlardır burada using deyimi IDisposable nesneleri korumak yeterli değildir ve CA2000 oluşmasına neden olabilir.

- Atılabilir bir nesne döndürmekten gerektirir kullanarak bir dışında bir try/finally bloğu nesne oluşturulmuş blok.

- Tek kullanımlık bir nesnenin üyelerine başlatma yapılmamalıdır kullanarak bir oluşturucuda deyimi.

- Yalnızca bir özel durum işleyicisi tarafından korunan oluşturuculara iç içe geçirme. Örneğin,

    ```csharp
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))
    { ... }
    ```

     CA2000 hiç kapalı FILESTREAM nesnesinde bir hata StreamReader nesnenin yapımı sağladığından oluşmasına neden olur.

- Dinamik nesneler gölge nesne IDisposable nesnelerin Dispose deseni uygulamak için kullanmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar bastırıldığında
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

```csharp
public SerialPort OpenPort1(string portName)
{
   SerialPort port = new SerialPort(portName);
   port.Open();  //CA2000 fires because this might throw
   SomeMethod(); //Other method operations can fail
   return port;
}

public SerialPort OpenPort2(string portName)
{
   SerialPort tempPort = null;
   SerialPort port = null;
   try
   {
      tempPort = new SerialPort(portName);
      tempPort.Open();
      SomeMethod();
      //Add any other methods above this line
      port = tempPort;
      tempPort = null;

   }
   finally
   {
      if (tempPort != null)
      {
         tempPort.Close();
      }
   }
   return port;
}
```

```vb
Public Function OpenPort1(ByVal PortName As String) As SerialPort

   Dim port As New SerialPort(PortName)
   port.Open()    'CA2000 fires because this might throw
   SomeMethod()   'Other method operations can fail
   Return port

End Function

Public Function OpenPort2(ByVal PortName As String) As SerialPort

   Dim tempPort As SerialPort = Nothing
   Dim port As SerialPort = Nothing

   Try
      tempPort = New SerialPort(PortName)
      tempPort.Open()
      SomeMethod()
      'Add any other methods above this line
      port = tempPort
      tempPort = Nothing

   Finally
      If Not tempPort Is Nothing Then
         tempPort.Close()
      End If


   End Try

   Return port

End Function
```

## <a name="example"></a>Örnek
 Varsayılan olarak, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] derleyici sahip tüm aritmetik işleçler için taşmayı denetle. Bu nedenle, herhangi bir Visual Basic aritmetik işlem fırlatabilir bir <xref:System.OverflowException>. Bu kurallar CA2000 gibi beklenmeyen ihlallerini neden olabilir. Örneğin, Visual Basic Derleyicisi, yönerge değil çıkarılması StreamReader neden olan bir özel durum oluşturabilir eklenmesi için denetimi taşma yayma çünkü aşağıdaki CreateReader1 işlevi bir CA2000 ihlaline neden olur.

 Bunu düzeltmek için projenizdeki Visual Basic derleyici tarafından taşma denetimleri yaymayı devre dışı bırakabilir veya kodunuz aşağıdaki CreateReader2 işlevi olduğu gibi değiştirebilirsiniz.

 Taşma denetimleri yaymayı devre dışı bırakmak için Çözüm Gezgini'nde proje adına sağ tıklayın ve ardından **özellikleri**. Tıklayın **derleme**, tıklayın **Gelişmiş derleme seçenekleri**, iade edin **tamsayı taşması denetimlerini Kaldır**.

  [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope-vboverflow_1.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.IDisposable>
- [Dispose Deseni](/dotnet/standard/design-guidelines/dispose-pattern)