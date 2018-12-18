---
title: Kod kusurları için yönetilen kod gözden geçirme analiz etme | Microsoft Docs
ms.date: 01/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis [Visual Studio]
- managed code, analyzing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 49c122e5cf22e9290f6dab1d45539887c68c01bd
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117725"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>İzlenecek yol: Kod çözümleme yönetilen kod kusurlarını

Bu kılavuzda, kod analizi aracı kullanarak bir yönetilen projenin kod kusurları için çözümleme.

Bu kılavuzda Microsoft .NET Framework tasarım yönergeleri ile uyumluluk için yönetilen .NET kod derlemeleri analiz etmek için Kod Analizi kullanma sürecinde adımları.

## <a name="create-a-class-library"></a>Bir sınıf kitaplığı oluşturun

### <a name="to-create-a-class-library"></a>Sınıf kitaplığı oluşturmak için

1. Üzerinde **dosya** menüsünde seçin **yeni** > **proje**.

1. İçinde **yeni proje** iletişim kutusunda, genişletin **yüklü** > **Visual C#** ve ardından **Windows Masaüstü**.

1. Seçin **sınıf kitaplığı (.NET Framework)** şablonu.

1. İçinde **adı** metin kutusunda, **CodeAnalysisManagedDemo** ve ardından **Tamam**.

1. Proje oluşturulduktan sonra açmak *Class1.cs* dosya.

1. Class1.cs varolan metni, aşağıdaki kod ile değiştirin:

   ```csharp
   using System;

   namespace testCode
   {
       public class demo : Exception
       {
           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int item { get { return _item; } }
       }
   }
   ```

1. Class1.cs dosyasını kaydedin.

## <a name="analyze-the-project"></a>Proje Çözümle

### <a name="to-analyze-a-managed-project-for-code-defects"></a>Kod kusurları için yönetilen bir proje çözümlemek için

1. CodeAnalysisManagedDemo projesinde seçin **Çözüm Gezgini**.

1. Üzerinde **proje** menüsünde tıklatın **özellikleri**.

     CodeAnalysisManagedDemo özellikleri sayfası görüntülenir.

1. Seçin **Kod Analizi** sekmesi.

1. Olduğundan emin olun **etkinleştirmek Kod Analizi derlemede** denetlenir.

1. Gelen **bu kural kümesini çalıştırmak** aşağı açılan listesinden, **Microsoft tüm kuralları**.

1. Üzerinde **dosya** menüsünde tıklatın **seçili öğeleri Kaydet**ve ardından özellikler sayfalarına kapatın.

1. Üzerinde **yapı** menüsünde tıklatın **yapı CodeAnalysisManagedDemo**.

    CodeAnalysisManagedDemo proje oluşturma Uyarıları'nda gösterilen **hata listesi** ve **çıkış** windows.

## <a name="correct-the-code-analysis-issues"></a>Kod Analizi sorunlarını gidermek

### <a name="to-correct-code-analysis-rule-violations"></a>Kod çözümleme kural ihlallerinin düzeltmek için

1. Üzerinde **Görünüm** menüsünde seçin **hata listesi**.

    Seçtiğiniz Geliştirici profili bağlı olarak, üzerine gerekebilir **diğer pencereler** üzerinde **Görünüm** menüsünde ve ardından **hata listesi**.

1. İçinde **Çözüm Gezgini**, seçin **tüm dosyaları göster**.

1. Özellikleri düğümünü genişletin ve ardından açın *AssemblyInfo.cs* dosya.

1. Uyarılar düzeltmek için aşağıdaki ipuçlarını kullanın:

   [CA1014: Derlemeleri CLSCompliantAttribute işaretlemek](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'demo' CLSCompliantAttribute ile işaretlenmiş ve değeri true olmalıdır.

   1. Aşağıdaki kodu ekleyip `using System;` AssemblyInfo.cs dosyasına kayıt yapar.

   1. Ardından, kod ekleme `[assembly: CLSCompliant(true)]` AssemblyInfo.cs dosyanın sonuna.

   [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: ortak demo(String)

   1. Oluşturucu ekleyin `public demo (String s) : base(s) { }` sınıfına `demo`.

   [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: ortak demo (dize, özel durum)

   1. Oluşturucu ekleyin `public demo (String s, Exception e) : base(s, e) { }` sınıfına `demo`.

   [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: tanıtım (SerializationInfo, StreamingContext) korumalı

   1. Aşağıdaki kodu ekleyip `using System.Runtime.Serialization;` Class1.cs dosyası başlangıcına.

   1. Ardından, bir oluşturucu ekleyin `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`

   [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: ortak demo()

   1. Oluşturucu ekleyin `public demo () : base() { }` sınıfına `demo` **.**

   [CA1709: Tanımlayıcılar doğru ortası](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: ad alanı adı 'testCode' ın büyük/küçük harf 'TestCode' değiştirerek düzeltin.

   1. Ad alanı büyük küçük harf değiştirme `testCode` için `TestCode`.

   [CA1709: Tanımlayıcılar doğru ortası](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Demo' değiştirerek türü adı 'demo' kasasını düzeltin.

   1. Üyenin adını değiştirmek `Demo`.

   [CA1709: Tanımlayıcılar doğru ortası](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: üye adı 'öğesini' ın büyük/küçük harf 'Öğesine' değiştirerek düzeltin.

   1. Üyenin adını değiştirmek `Item`.

   [CA1710: Tanımlayıcılar doğru olmalıdır](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: '' Nda özel durum' sonlandırmak için yeniden adlandırma testCode.demo'.

   1. Sınıf ve onun kurucusuna adını değiştirmek `DemoException`.

   [CA2210: Derlemelerin geçerli olmalıdır](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'CodeAnalysisManagedDemo' bir güçlü ad anahtar ile oturum açın.

   1. Üzerinde **proje** menüsünde seçin **CodeAnalysisManagedDemo özellikleri**.

      Proje özellikleri görüntülenir.

   1. Seçin **imzalama** sekmesi.

   1. Seçin **derlemeyi imzalamak** onay kutusu.

   1. İçinde **dize ad anahtar dosyası seç** listesinde  **\<yeni... >**.

      **Güçlü ad anahtarı oluştur** iletişim kutusu görüntülenir.

   1. İçinde **anahtar dosya adını**, TestKey yazın.

   1. Bir parola girin ve ardından **Tamam**.

   1. Üzerinde **dosya** menüsünde seçin **seçili öğeleri Kaydet**ve özellik sayfaları kapatın.

   [CA2237: ISerializable türleri SerializableAttribute ile](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: 'gösteri' Bu tür ISerializable gerçekleştiren olarak yazmanız için bir [Serializable] özniteliğini ekleyin.

   1. Ekleme `[Serializable ()]` özniteliği sınıfa `demo`.

   Değişiklikleri tamamladıktan sonra Class1.cs dosyası aşağıdaki gibi görünmelidir:

   ```csharp
   using System;
   using System.Runtime.Serialization;

   namespace TestCode
   {
       [Serializable()]
       public class DemoException : Exception
       {
           public DemoException () : base() { }
           public DemoException(String s) : base(s) { }
           public DemoException(String s, Exception e) : base(s, e) { }
           protected DemoException(SerializationInfo info, StreamingContext context) : base(info, context) { }

           public static void Initialize(int size) { }
           protected static readonly int _item;
           public static int Item { get { return _item; } }
       }
   }
   ```

1. Projeyi yeniden oluşturun.

## <a name="exclude-code-analysis-warnings"></a>Kod çözümleme Uyarıları hariç tut

### <a name="to-exclude-code-defect-warnings"></a>Kod hatası uyarıları dışlamak için

1. Her kalan uyarılar için aşağıdakileri yapın:

    1. Uyarı seçin **hata listesi**.

    1. Sağ tıklatın veya bağlam menüsünü seçin **bastır** > **gizleme dosyasını**.

1. Projeyi yeniden oluşturun.

     Proje uyarı veya hata oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

[Yönetilen kod için Kod Analizi](../code-quality/code-analysis-for-managed-code-overview.md)