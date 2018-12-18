---
title: 'İzlenecek yol: Kod kusurları için yönetilen kodu analiz etme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, walkthroughs
- managed code, analyzing
- code analysis tool, walkthroughs
ms.assetid: 22b99f49-1924-4fb5-a421-c8b23e5d5cd4
caps.latest.revision: 47
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0b9d6aba5997182578b43ac9edd3c889bcfc365e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912896"
---
# <a name="walkthrough-analyzing-managed-code-for-code-defects"></a>İzlenecek yol: Kod Kusurları için Yönetilen Kodu Analiz Etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu kılavuzda, Kod Analizi aracını kullanarak kod kusurları için yönetilen bir proje çözümleyin.  
  
 Bu kılavuzda Microsoft .NET Framework tasarım yönergeleri ile uyumluluk için bütünleştirilmiş kodlarınızı .NET yönetilen kodu analiz etmek için kod analizini kullanarak işlemi adım adım.  
  
 Bu kılavuzda:  
  
-   Analiz ve kod hatası uyarıları düzeltin.  
  
## <a name="prerequisites"></a>Önkoşullar  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
## <a name="create-a-class-library"></a>Bir sınıf kitaplığı oluşturma  
  
#### <a name="to-create-a-class-library"></a>Bir sınıf kitaplığı oluşturmak için  
  
1.  Üzerinde **dosya** menüsü [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], tıklayın **yeni** ve ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunun **proje türleri**, tıklayın **Visual C#**.  
  
3.  Altında **şablonları**seçin **sınıf kitaplığı**.  
  
4.  İçinde **adı** metin kutusunda, **CodeAnalysisManagedDemo** ve ardından **Tamam**.  
  
5.  Proje oluşturulduktan sonra Class1.cs dosyasını açın.  
  
6.  Class1.cs varolan metni, aşağıdaki kodla değiştirin:  
  
     `//CodeAnalysisManagedDemo //Class1.cs using System;  namespace testCode {          public class demo : Exception     {                  public static void Initialize(int size) { }         protected static readonly int _item;         public static int item { get { return _item; } }     } }`  
  
7.  Class1.cs dosyasını kaydedin.  
  
## <a name="analyze-the-project"></a>Projeyi Çözümle  
  
#### <a name="to-analyze-a-managed-project-for-code-defects"></a>Kod kusurları için yönetilen bir projesini analiz etmek için  
  
1.  CodeAnalysisManagedDemo projede seçin **Çözüm Gezgini**.  
  
2.  Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
     CodeAnalysisManagedDemo Özellikler sayfası görüntülenir.  
  
3.  Tıklayın **CodeAnalysis**.  
  
4.  Emin olun **derlemede kod analizini etkinleştir (code_analysıs sabitini tanımlar**) denetlenir.  
  
5.  Gelen **bu kural kümesini Çalıştır** aşağı açılan listesinden **Microsoft tüm kurallar**.  
  
6.  Üzerinde **dosya** menüsünde tıklatın **seçili öğeleri Kaydet**ve ManagedDemo özellikler sayfaları kapatın.  
  
7.  Üzerinde **derleme** menüsünde tıklatın **derleme ManagedDemo**.  
  
     CodeAnalysisManagedDemo proje derleme uyarıları raporlanır **Kod Analizi** ve **çıkış** windows.  
  
     Varsa **Kod Analizi** penceresinde görünmez, üzerinde **Çözümle** menüsünde seçin **Windows** ve ardından **Kod Analizi seçme**.  
  
## <a name="correct-the-code-analysis-issues"></a>Kod Analizi sorunlarını düzeltin  
  
#### <a name="to-correct-code-analysis-rule-violations"></a>Kod Analizi kural ihlallerini düzeltmek üzere  
  
1.  Üzerinde **görünümü** menüsünü tıklatın **hata listesi**.  
  
     Seçtiğiniz Geliştirici profili bağlı olarak, işaret gerekebilir **diğer Windows** üzerinde **görünümü** menüsüne ve ardından **hata listesi**.  
  
2.  İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**.  
  
3.  Ardından, özelliklerini düğümünü genişletin ve ardından AssemblyInfo.cs dosyasını açın.  
  
4.  Uyarıları gidermek için aşağıdakileri kullanın:  
  
- [CA1014: Derlemeleri CLSCompliantAttribute ile işaretle](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md): Microsoft.Design: 'Tanıtım' CLSCompliantAttribute ile işaretlenmemelidir ve değeri true olmalıdır.  
  
  -   Kod ekleme `using``System;` AssemblyInfo.cs dosyası için.  
  
       Ardından, kod ekleme `[assembly: CLSCompliant(true)]` AssemblyInfo.cs dosyasını sonuna.  
  
       Projeyi yeniden derleyin.  
  
- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: Genel demo(String)  
  
  -   Oluşturucu Ekle `public demo (String s) : base(s) { }` sınıfa `demo`.  
  
- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: Genel Tanıtım (dize, özel durum)  
  
  -   Oluşturucu Ekle `public demo (String s, Exception e) : base(s, e) { }` sınıfa `demo`.  
  
- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: tanıtım (SerializationInfo, StreamingContext) korumalı  
  
  -   Kod ekleme `using System.Runtime.Serialization;` Class1.cs dosyasının başına.  
  
       Ardından, oluşturucu Ekle `protected demo (SerializationInfo info, StreamingContext context) : base(info, context) { } to the class demo.`  
  
       Projeyi yeniden derleyin.  
  
- [CA1032: Standart özel durum oluşturucuları uygulayın](../code-quality/ca1032-implement-standard-exception-constructors.md): Microsoft.Design: Bu sınıfına aşağıdaki oluşturucuyu ekleyin: Genel demo()  
  
  -   Oluşturucu Ekle `public demo () : base() { }` sınıfa `demo` **.**  
  
       Projeyi yeniden derleyin.  
  
- [CA1709: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'TestCode için' değiştirerek ad alanı adı 'testCode' büyük küçük harfleri düzeltin.  
  
  -   Ad alanı büyük küçük harfleri değiştirme `testCode` için `TestCode`.  
  
- [CA1709: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Tanıtıma' değiştirerek tür adı 'Tanıtım' büyük küçük harfleri düzeltin.  
  
  -   Üye adını değiştirmek `Demo`.  
  
- [CA1709: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md): Microsoft.Naming: 'Öğesine' değiştirerek üyesi adı 'öğesini' büyük küçük harfleri düzeltin.  
  
  -   Üye adını değiştirmek `Item`.  
  
- [CA1710: Tanımlayıcıların sonekleri doğru soneki olmalıdır](../code-quality/ca1710-identifiers-should-have-correct-suffix.md): Microsoft.Naming: '' özel durum' sonlandırmak için yeniden adlandırma testCode.demo'.  
  
  -   Sınıfı için kendi oluşturucular adını değiştirip `DemoException`.  
  
- [CA2210: Derlemelerin geçerli tanımlayıcı adları olmalıdır](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md): 'ManagedDemo' bir tanımlayıcı ad anahtarıyla imzalayın.  
  
  -   Üzerinde **proje** menüsünü tıklatın **ManagedDemo özellikleri**.  
  
       Proje özellikleri görüntülenir.  
  
       Tıklayın **imzalama**.  
  
       Seçin **derlemeyi imzalamayı** onay kutusu.  
  
       İçinde **dize ad anahtar dosyası seç** listesinden  **\<yeni … >**.  
  
       **Katı ad anahtarı oluştur** iletişim kutusu görüntülenir.  
  
       İçinde **anahtar dosya adını**, TestKey yazın.  
  
       Bir parola girin ve ardından **Tamam**.  
  
       Üzerinde **dosya** menüsünde tıklatın **seçili öğeleri Kaydet**ve özellik sayfaları kapatın.  
  
       Projeyi yeniden derleyin.  
  
- [CA2237: ISerializable türleri SerializableAttribute ile](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md): Microsoft.Usage: Bu türü ISerializable uyguladığı 'gösteri' türüne [Serializable] özniteliğini ekleyin.  
  
  -   Ekleme `[Serializable ()]` öznitelik sınıfına `demo`.  
  
       Projeyi yeniden derleyin.  
  
  Değişiklikleri tamamladıktan sonra Class1.cs dosyasını aşağıdaki gibi görünmelidir:  
  
```  
//CodeAnalysisManagedDemo  
//Class1.cs  
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
  
## <a name="exclude-code-analysis-warnings"></a>Kod Analizi Uyarıları hariç tut  
  
#### <a name="to-exclude-code-defect-warnings"></a>Kod hata uyarılarını hariç tutmak için  
  
1. Her kalan uyarılar için aşağıdakileri yapın:  
  
   1. Kod Analizi penceresinde uyarıyı seçin.  
  
   2. Seçin **eylemleri**, ardından **ileti Gizle**ve ardından **proje gizleme dosyası**.  
  
      Daha fazla bilgi için [nasıl yapılır: menü öğesini kullanarak uyarıları bastırma](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)  
  
2. Projeyi yeniden derleyin.  
  
    Projeyi herhangi bir uyarı veya hata derler.



