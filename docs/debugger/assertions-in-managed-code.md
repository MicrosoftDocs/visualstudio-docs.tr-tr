---
title: Yönetilen koddaki onaylar | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], assertions in managed code
- Trace.Assert method
- debugging managed code, assertions
- Debug.Assert method
- Debug.Listeners property
- assertions, side effects
- Trace.Listeners property
- assertions, managed code
ms.assetid: 70ab2522-6486-4076-a1a9-e0f11cd0f3a1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 07f422348a10bbe6d5c02a50073c9486a679cfaf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49892070"
---
# <a name="assertions-in-managed-code"></a>Yönetilen Koddaki Onaylar
Onaylama işlemi, bir veya `Assert` ifadesi bağımsız değişkeni olarak belirlediğiniz bir koşulu sınar `Assert` deyimi. Koşul true olarak değerlendirilirse, herhangi bir işlem gerçekleşir. Koşul false olarak değerlendirilirse, onaylama işlemi başarısız olur. Hata ayıklama derlemesi ile çalıştırıyorsanız, programınız Kesme moduna girer.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [System.Diagnostics Namespace içinde onaylar](#BKMK_Asserts_in_the_System_Diagnostics_Namespace)  
  
 [Debug.Assert yöntemi](#BKMK_The_Debug_Assert_method)  
  
 [Debug.Assert yan etkileri](#BKMK_Side_effects_of_Debug_Assert)  
  
 [İzleme ve hata ayıklama gereksinimleri](#BKMK_Trace_and_Debug_Requirements)  
  
 [Assert bağımsız değişkenleri](#BKMK_Assert_arguments)  
  
 [Assert davranışını özelleştirme](#BKMK_Customizing_Assert_behavior)  
  
 [Yapılandırma dosyalarında onaylar ayarlama](#BKMK_Setting_assertions_in_configuration_files)  
  
##  <a name="BKMK_Asserts_in_the_System_Diagnostics_Namespace"></a> System.Diagnostics Namespace içinde onaylar  
 Visual Basic ve Visual C# içinde kullanabileceğiniz `Assert` ya da metodun <xref:System.Diagnostics.Debug> veya <xref:System.Diagnostics.Trace>, içinde olduğu <xref:System.Diagnostics> ad alanı. <xref:System.Diagnostics.Debug> Bunlar değil boyutunu artırın veya azaltın, Sürüm kodunun hızını sınıfı yöntemleri programınızı yayın sürümünde dahil edilmez.  
  
 C++ desteklemiyor <xref:System.Diagnostics.Debug> sınıfı yöntemleri. Kullanarak aynı etkiyi elde edebilirsiniz <xref:System.Diagnostics.Trace> koşullu derleme ile gibi sınıf `#ifdef DEBUG`... `#endif`.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_The_Debug_Assert_method"></a> Debug.Assert yöntemi  
 Kullanım <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> serbestçe kodunuz doğruysa true tutmak zorunda koşulları test etmek için yöntemi. Örneğin, bir tamsayı bölme işlevi yazdığınız varsayalım. Matematik kurallarıyla bölen kesinlikle sıfır olamaz. Bir onaylama işlemi kullanarak bu test:  
  
```VB  
Function IntegerDivide(ByVal dividend As Integer, ByVal divisor As Integer) As Integer  
    Debug.Assert(divisor <> 0)  
    Return CInt(dividend / divisor)  
End Function  
```  
  
```csharp  
int IntegerDivide ( int dividend , int divisor )  
    { Debug.Assert ( divisor != 0 );  
        return ( dividend / divisor ); }  
```  
  
 Bu kod hata ayıklayıcısı altında çalıştırdığınızda, onaylama işlemi ifadesi değerlendirilir, ancak sürümde değil karşılaştırma yapılır şekilde olduğunda ortadan kalkar.  
  
 Başka bir örnek aşağıda verilmiştir. Aşağıdaki gibi bir denetimi hesabı uygulayan bir sınıf vardır:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Debug.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Debug.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Hesaptan para çekme hesap bakiyesi geri almak için hazırlama tutarı karşılamak yeterli olduğundan emin olmanız gerekir. Bakiye denetlemek için onaylama yazabilirsiniz:  
  
```VB  
Dim amount, balance As Double  
balance = savingsAccount.balance  
Trace.Assert(amount <= balance)  
SavingsAccount.Withdraw(amount)  
```  
  
```csharp  
float balance = savingsAccount.Balance;  
Trace.Assert ( amount <= balance );  
savingsAccount.Withdraw ( amount );  
```  
  
 Çağrılar Not <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> yöntemi kodunuzu sürümü oluşturduğunuzda kaybolur. Bakiye denetler çağrı sürümde kaybolur anlamına gelir. Bu sorunu çözmek için değiştirmelisiniz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ile <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, hangi değil kayboluyor sürümde:  
  
 Çağrılar <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> çağrıları aksine yayım sürümünüzde yükü eklemek <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Side_effects_of_Debug_Assert"></a> Debug.Assert yan etkileri  
 Kullandığınızda <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>, tüm içinde kod emin `Assert` program sonuçlarını değişmez `Assert` kaldırılır. Aksi takdirde, yalnızca programınız yayın sürümünde görünür bir hatayı yanlışlıkla yapabilecek. Özellikle dikkat içeren işlev veya yordam hakkında bildirimler çağrıları, aşağıdaki örnek gibi:  
  
```VB  
' unsafe code  
Debug.Assert (meas(i) <> 0 )  
```  
  
```csharp  
// unsafe code  
Debug.Assert (meas(i) != 0 );  
```  
  
 Bu kullanımı <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> ilk bakışta güvenli görünebilir, ancak işlev meas her zaman bir sayaç güncelleştirmeleri varsayalım çağrılır. Yayım sürümünü derlediğinizde, sayacın güncelleştirilmiş için bu çağrıyı meas çıkarıldı. Bu işlev bir yan etkisi olan bir örnektir. Yan etkileri olan bir işlev çağrısı ortadan sürümde yalnızca görüntülenen bir hataya neden olabilir. Bu tür sorunları önlemek için işlev çağrılarında yerleştirmeyin bir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> deyimi. Bunun yerine bir geçici değişken kullanın:  
  
```VB  
temp = meas( i )  
Debug.Assert (temp <> 0)  
```  
  
```csharp  
temp = meas( i );  
Debug.Assert ( temp != 0 );  
```  
  
 Kullanırken bile <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, yine de işlev çağrıları içindeki yerleştirmekten kaçının isteyebilirsiniz bir `Assert` deyimi. Böyle çağrılar güvenli olmalıdır çünkü <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ifadeleri ortadan değil derleme. Birkaç alýþkanlýk olarak böyle yapıları kaçının ancak kullanırken bir hata yaparsanız olasılığı vardır <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Trace_and_Debug_Requirements"></a> İzleme ve hata ayıklama gereksinimleri  
 Kullanarak projenize oluşturursanız [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sihirbazlar, izleme sembol, varsayılan olarak hem sürüm hem de hata ayıklama yapılandırmaları tarafından tanımlanır. Hata ayıklama sembolü varsayılan yalnızca hata ayıklama derlemesi olarak tanımlanır.  
  
 Aksi takdirde için <xref:System.Diagnostics.Trace> çalışmak için yöntemler programınızı kaynak dosyasının en üstüne aşağıdaki birine sahip olmalıdır:  
  
- `#Const TRACE = True` Visual Basic'te  
  
- `#define TRACE` Visual C# ve C++  
  
  Veya, programınızın izleme seçeneği ile oluşturulmalıdır:  
  
- `/d:TRACE=True` Visual Basic'te  
  
- `/d:TRACE` Visual C# ve C++  
  
  Bir C# veya Visual Basic yayın yapı içinde hata ayıklama yöntemleri kullanmanız gerekiyorsa, hata ayıklama sembolü yayın yapılandırmanızda tanımlamanız gerekir.  
  
  C++ desteklemiyor <xref:System.Diagnostics.Debug> sınıfı yöntemleri. Kullanarak aynı etkiyi elde edebilirsiniz <xref:System.Diagnostics.Trace> koşullu derleme ile gibi sınıf `#ifdef DEBUG`... `#endif`. Bu sembolleri tanımlayabilirsiniz  **\<Proje > özellik sayfaları** iletişim kutusu. Daha fazla bilgi için [Visual Basic hata ayıklama yapılandırması proje ayarları değiştirme](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) veya [bir C veya C++ hata ayıklama yapılandırması proje ayarları değiştirme](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
##  <a name="BKMK_Assert_arguments"></a> Assert bağımsız değişkenleri  
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> en fazla üç bağımsız değişken almaz. Zorunlu olan ilk bağımsız değişken, kontrol etmek istediğiniz durumdur. Eğer <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName> tek bağımsız değişkenli `Assert` yöntemi koşulu denetleyen ve sonuç false ise çağrı yığınını içeriğini çıkarır **çıkış** penceresi. Aşağıdaki örnekte gösterildiği <xref:System.Diagnostics.Trace.Assert(System.Boolean)?displayProperty=fullName> ve <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=fullName>:  
  
```VB  
Debug.Assert(stacksize > 0)  
Trace.Assert(stacksize > 0)  
```  
  
```csharp  
Debug.Assert ( stacksize > 0 );  
Trace.Assert ( stacksize > 0 );   
```  
  
 İkinci ve üçüncü bağımsız değişken varsa, dize olmalıdır. Eğer <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> iki veya üç bağımsız değişken ile birinci bağımsız değişken bir durumdur. Yöntem koşulu kontrol eder ve sonuç false ise ikinci dize ve üçüncü dizeleri çıkarır. Aşağıdaki örnekte gösterildiği <xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=fullName> ve <xref:System.Diagnostics.Trace.Assert(System.Boolean,System.String)?displayProperty=fullName> kullanılan iki bağımsız değişkenleriyle:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space")  
Trace.Assert(stacksize > 0, "Out of stack space")  
```  
  
```csharp  
Debug.Assert ( stacksize > 0, "Out of stack space" );  
Trace.Assert ( stacksize > 0, "Out of stack space" );  
```  
  
 Aşağıdaki örnekte gösterildiği <xref:System.Diagnostics.Debug.Assert%2A> ve <xref:System.Diagnostics.Trace.Assert%2A>:  
  
```VB  
Debug.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:" , Format(size, "G"))  
Trace.Assert(stacksize > 0, "Out of stack space. Bytes left:", "inctemp failed on third call" )  
```  
  
```csharp  
Debug.Assert ( stacksize > 100, "Out of stack space" , "Failed in inctemp" );  
Trace.Assert ( stacksize > 0, "Out of stack space", "Failed in inctemp" );   
```  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Customizing_Assert_behavior"></a> Assert davranışını özelleştirme  
 Kullanıcı arabirimi modunda uygulamanızı çalıştırırsanız `Assert` yöntemi görüntüler **onaylama işlemi başarısız oldu** koşul başarısız olduğunda iletişim kutusu. Onaylama başarısız olduğunda gerçekleşen eylemler tarafından denetlenen <xref:System.Diagnostics.Debug.Listeners%2A> veya <xref:System.Diagnostics.Trace.Listeners%2A> özelliği.  
  
 Çıkış davranışı ekleyerek özelleştirebilirsiniz bir <xref:System.Diagnostics.TraceListener> nesnesini `Listeners` koleksiyonu kaldırarak bir <xref:System.Diagnostics.TraceListener> gelen `Listeners` koleksiyonu veya geçersiz kılma <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> , varolan bir yöntem `TraceListener` sağlamak için farklı davranır.  
  
 Örneğin, geçersiz <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> görüntüleme yerine bir olay günlüğüne yazmak için yöntemi **onaylama işlemi başarısız oldu** iletişim kutusu.  
  
 Bu şekilde çıkış özelleştirmek için programınız bir dinleyici içermelidir ve devralmanız <xref:System.Diagnostics.TraceListener> ve geçersiz kılma kendi <xref:System.Diagnostics.TraceListener.Fail%2A?displayProperty=fullName> yöntemi.  
  
 Daha fazla bilgi için [izleme dinleyicilerine](/dotnet/framework/debug-trace-profile/trace-listeners).  
  
 [Bu konudaki](#BKMK_In_this_topic)  
  
##  <a name="BKMK_Setting_assertions_in_configuration_files"></a> Yapılandırma dosyalarında onaylar ayarlama  
 Onaylamalar kodunuzu olduğu gibi program yapılandırma dosyanızda de ayarlayabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> veya <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>   
 [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)   
 [İzleme ve İşaretleme uygulamaları](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)   
 [Nasıl yapılır: izleme ve hata ayıklama ile koşullu derleme](/dotnet/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)