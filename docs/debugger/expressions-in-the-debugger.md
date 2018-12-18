---
title: Hata ayıklayıcıdaki ifadeler | Microsoft Docs
ms.custom: ''
ms.date: 02/07/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 035d66590c6b6087c56887a4eaa2b0538406f87b
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257260"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısındaki ifadeler
Visual Studio hata ayıklayıcı bir ifade girdiğinizde çalışan ifade değerlendiricilerini içerir **QuickWatch** iletişim kutusu, **Watch** penceresinde veya **hemen** penceresi. İş yerinizde de ifade değerlendiricilerini olan **kesme noktaları** penceresi ve hata ayıklayıcı içindeki diğer pek çok yerde.
  
 Aşağıdaki bölümlerde, Visual Studio tarafından desteklenen diller için ifade değerlendirme sınırlamaları açıklanmaktadır.
  
## <a name="f-expressions-are-not-supported"></a>F#ifadeler desteklenmez.  
 F#ifadeleri tanınmıyor. Hata ayıklaması yapıyorsanız F# kod, gereksinim, ifadelere çevrilecek C# deyimler bir hata ayıklayıcı penceresini ya da iletişim kutusuna ulaşmadan önce söz dizimi. Gelen ifadeleri Çevir ne zaman F# için C#, unutmayın mutlaka C# kullanır `==` eşitlik için test etmek için işleci sırada F# tek kullanır `=`.  
  
## <a name="c-expressions"></a>C++ deyimleri  
 C++ ifadeleri bağlamı işleçleri kullanma hakkında daha fazla bilgi için bkz: [bağlam işleci (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>C++'ta desteklenmeyen ifadeler  
  
#### <a name="constructors-destructors-and-conversions"></a>Oluşturucular, Yıkıcılar ve dönüştürmeler  
 Açıkça veya dolaylı olarak, bir nesne için bir oluşturucu veya yıkıcı çağrılamıyor. Örneğin, aşağıdaki ifade açıkça bir oluşturucu çağırır ve bir hata mesajıyla sonuçlanır:  
  
```C++  
my_date( 2, 3, 1985 )  
```  
  
 Dönüştürme hedefi bir sınıf ise bir dönüştürme işlevi çağrılamıyor. Böyle bir dönüştürme, bir nesnenin yapımı içerir. Örneğin, varsa `myFraction` örneğidir `CFraction`, işlev dönüştürme işleci tanımlar `FixedPoint`, aşağıdaki ifade hatayla sonuçlanır:  
  
```C++  
(FixedPoint)myFraction  
```  
  
 Yeni bir çağrı veya delete işleçleri olamaz. Örneğin, aşağıdaki ifade desteklenmez:  
  
```C++  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Önişlemci makroları  
 Önişlemci makroları hata ayıklayıcıda desteklenmiyor. Örneğin, bir sabiti `VALUE` olarak bildirilir: `#define VALUE 3`, kullanamazsınız `VALUE` içinde **izleme** penceresi. Bu sınırlama önlemek için değiştirmelisiniz `#define`numaralandırmalar ile kullanıcının ve mümkün olduğunda çalışır.  
  
### <a name="using-namespace-declarations"></a>ad alanı bildirimi kullanarak  
 Kullanamazsınız `using namespace` bildirimleri.  Bir tür adı veya değişken geçerli bir ad alanı dışında erişmek için tam adı kullanmanız gerekir.  
  
### <a name="anonymous-namespaces"></a>Anonim ad alanları  
 Anonim ad desteklenmez. Aşağıdaki kodu varsa, ekleme yapamazsınız `test` için izleme penceresinde:  
  
```C++  
namespace mars   
{   
    namespace  
    {  
        int test = 0;   
    }   
}   
int main()   
{   
    // Adding a watch on test does not work.   
    mars::test++;   
    return 0;   
}  
  
```  
  
###  <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Durumunu korumak üzere hata ayıklayıcı iç işlevleri kullanma  
 Hata ayıklayıcı iç işlevleri size uygulama durumunu değiştirmeden ifadelerinde belirli C/C++ işlevleri çağırmak için bir yol sağlar.  
  
 Hata ayıklayıcı iç işlevleri:  
  
- Güvenli olması garanti: hata ayıklayıcı iç işlev yürütülürken bozuk olmadıklarından ayıklanmakta olan işlem.  
  
- Hatta burada yan etkileri ve işlev değerlendirmesi izin verilmeyen senaryolarda tüm ifadelerde izin verilir.  
  
- Normal işlev çağrıları bir mini döküm hata ayıklama gibi mümkün olmadığı senaryolarda çalışır.  
  
  Hata ayıklayıcı iç işlevleri da değerlendirilirken ifadeleri daha kullanışlı hale getirebilirsiniz. Örneğin, `strncmp(str, "asd")` bir kesme noktası koşulu yazmak kolaydır `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )  
  
|Alan|İç işlevleri|  
|----------|-------------------------|  
|**Dize uzunluğu**|strlen, wcslen, strnlen, wcsnlen|  
|**Dize karşılaştırması**|strcmp wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Dize arama**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Bu işlevler, Windows 8 üzerinde çalıştırılması ayıklanmakta olan işlem gerekir. Bir Windows 8 cihazında döküm dosyalarında hata ayıklanırken ayrıca Visual Studio bilgisayarı olmasını gerektirir Windows 8 çalıştıran. Ancak, Windows 8 cihazını uzaktan ayıklıyorsanız, Visual Studio bilgisayarı Windows 7 çalışabilir.|  
|**Çeşitli**|__log2<br /><br /> Günlük taban 2 daha düşük en yakın tamsayıya yuvarlanır, belirtilen bir tamsayı döndürür.|  
  
## <a name="ccli---unsupported-expressions"></a>C + +/ CLI - desteklenmeyen ifadeler  
  
-   İşaretçiler içeren atamaları veya kullanıcı tanımlı atamalar desteklenmez.  
  
-   Nesne karşılaştırma ve ataması desteklenmez.  
  
-   Aşırı yüklenmiş işleçler ve aşırı yüklenmiş işlevler desteklenmez.  
  
-   Kutulama ve kutudan çıkarma desteklenmez.  
  
-   `Sizeof` işleci desteklenmiyor.  
  
## <a name="c---unsupported-expressions"></a>C# - desteklenmeyen ifadeler  
  
### <a name="dynamic-objects"></a>Dinamik nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Ne zaman, uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresinde bir dinamik görünüm düğümü eklenir değerlendirilir. Dinamik görünüm düğümü, nesne üyelerini gösterir ancak üye değerlerinin düzenlenmesine izin vermez.  
  
 Dinamik nesneler aşağıdaki özellikleri desteklenmez:  
  
-   Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve `*=`  
  
-   Sayısal yayınları ve tür bağımsız değişkeni atamaları dahil olmak üzere birçok yayınları  
  
-   Yöntem çağrıları ikiden fazla bağımsız değişken  
  
-   Özellik alıcılar ikiden fazla bağımsız değişken  
  
-   Özellik ayarlayıcılarına bağımsız değişken  
  
-   Bir dizin oluşturucu için atama  
  
-   Boole işleçleri `&&` ve `||`  
  
### <a name="anonymous-methods"></a>Anonim Yöntemler  
 Yeni anonim yöntemler oluşturulması desteklenmiyor.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - desteklenmeyen ifadeler  
  
### <a name="dynamic-objects"></a>Dinamik nesneler  
 Statik olarak dinamik olarak yazılan hata ayıklayıcı ifadelerinde değişkenleri kullanabilirsiniz. Ne zaman, uygulayan nesneler <xref:System.Dynamic.IDynamicMetaObjectProvider> İzleme penceresinde bir dinamik görünüm düğümü eklenir değerlendirilir. Dinamik görünüm düğümü, nesne üyelerini gösterir ancak üye değerlerinin düzenlenmesine izin vermez.  
  
 Dinamik nesneler aşağıdaki özellikleri desteklenmez:  
  
-   Bileşik işleçleri `+=`, `-=`, `%=`, `/=`, ve `*=`  
  
-   Sayısal yayınları ve tür bağımsız değişkeni atamaları dahil olmak üzere birçok yayınları  
  
-   Yöntem çağrıları ikiden fazla bağımsız değişken  
  
-   Özellik alıcılar ikiden fazla bağımsız değişken  
  
-   Özellik ayarlayıcılarına bağımsız değişken  
  
-   Bir dizin oluşturucu için atama  
  
-   Boole işleçleri `&&` ve `||`  
  
### <a name="local-constants"></a>Yerel sabitleri  
 Yerel sabitleri desteklenmez.  
  
### <a name="import-aliases"></a>İçeri aktarma diğer adları  
 İçeri aktarma diğer adları desteklenmez.  
  
### <a name="variable-declarations"></a>Değişken bildirimleri  
 Windows Hata Ayıklayıcı'daki yeni açık değişkenleri bildiremezsiniz. Ancak, yeni örtük değişkenler içinde atayabilirsiniz **hemen** penceresi. Bu örtük değişkenler hata ayıklama oturumu için kapsamlı ve hata ayıklayıcının dışında erişilebilir değildir. Örneğin, deyim `o = 5` örtük olarak yeni bir değişken oluşturur `o` ve 5 değerini atayın. Bu örtük değişkenler türlerinin **nesne** sürece türü, hata ayıklayıcı tarafından çıkarılan.  
  
### <a name="unsupported-keywords"></a>Desteklenmeyen anahtar sözcükleri  
  
-   `AddressOf`  
  
-   `End`  
  
-   `Error`  
  
-   `Exit`  
  
-   `Goto`  
  
-   `On Error`  
  
-   `Resume`  
  
-   `Return`  
  
-   `Select/Case`  
  
-   `Stop`  
  
-   `SyncLock`  
  
-   `Throw`  
  
-   `Try/Catch/Finally`  
  
-   `With`  
  
-   Namespace veya modül düzeyinde anahtar sözcükler gibi `End Sub` veya `Module`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C++ içindeki Biçim belirticileri](../debugger/format-specifiers-in-cpp.md)   
 [Bağlam işleci (C++)](../debugger/context-operator-cpp.md)   
 [C# içindeki Biçim belirticileri](../debugger/format-specifiers-in-csharp.md)   
 [Sözde değişkenler](../debugger/pseudovariables.md)