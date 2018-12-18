---
title: İzleme ve QuickWatch Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b171352475b6c0b3bc916d27ab4ba351e84be42b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791687"
---
# <a name="watch-and-quickwatch-windows"></a>İzleme ve QuickWatch Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabilirsiniz **Watch** (**hata ayıklama / Windows / izleyin / izleyin (1, 2, 3, 4)**) ve **QuickWatch** (değişken üzerinde sağ / **hata ayıklama / QuickWatch**) değişkenleri ve ifadeleri hata ayıklama oturumu sırasında izlemek için windows.  Fark **Watch** penceresi, çeşitli değişkenleri görüntüleyebilir ancak **QuickWatch** penceresi bir kerede tek bir değişken görüntüler.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>QuickWatch sahip tek bir değişken gözleme  
 Kullanabileceğiniz **QuickWatch** penceresi tek bir değişken gözlemleyin. Örneğin, aşağıdaki kodu varsa:  
  
```csharp  
static void Main(string[] args)  
{  
    int a, b;  
    a = 1;  
    b = 2;  
    for (int i = 0; i < 10; i++)  
    {  
        a = a + b;  
    }   
}  
```  
  
 İnceleyebileceğiniz QuickWatch penceresinde gösterildiği gibi bir değişkeni:  
  
1.  Bir kesme noktası ayarlamak `a = a + b;` satır.  
  
2.  Hata ayıklama başlatılamıyor. Yürütme kesme noktasında durur.  
  
3.  Açık **QuickWatch** penceresi (sağ tıklayın ardından **hata ayıklama / QuickWatch**, veya **SHIFT + F9**). Penceresi açın ve eklemek için bir değişken **ifade** penceresinde ardından **yeniden değerlendir**. Görmelisiniz bir değişkende **değerleri** penceresiyle değeri 2'dir.  
  
4.  **QuickWatch** penceresi olan bir kalıcı iletişim kutusu penceresinin açık olduğu sürece hata ayıklama devam edemiyor bu nedenle. Değişkene ekleyebilirsiniz **Watch** tıklayarak penceresi **Gözcü Ekle**.  
  
5.  Kapat **QuickWatch** penceresi. Değeri gözlemleyin sırasında hata ayıklama devam edebilmeniz için artık **Watch** penceresi  
  
## <a name="observing-variables-with-the-watch-window"></a>İzleme penceresi değişkenleri gözleme  
 Birden çok değişkenlerle inceleyebileceğiniz **Watch** penceresi. Örneğin, aşağıdaki kodu varsa:  
  
```csharp  
static void Main(string[] args)  
{  
    int a, b, c;  
    a = 1;  
    b = 2;  
    c = 0;  
  
     for (int i = 0; i < 10; i++)  
    {  
        a++;  
        b *= 2;  
        c = a + b;  
     }  
}  
  
```  
  
 Üç değişkenlerin değerleri İzle penceresine aşağıdaki şekilde ekleyin:  
  
1. Bir kesme noktası ayarlamak `c = a + b;` satır.  
  
2. Hata Ayıklamayı Başlat (**F5**). Yürütme kesme noktasında durur.  
  
3. Gözcü penceresi açın (**hata ayıklama / Windows / izleyin / izleyin 1**, veya **CTRL + ALT + W, 1**).  
  
4. Ekle `a` ilk satırın değişkenini `b` ikinci satır, değişken ve `c` üçüncü satır değişkeni.  
  
5. Hata ayıklamaya devam et.  
  
   Değişken değerleri, yinelenecek şekilde değiştirme görmelisiniz `for` döngü.  
  
   Yerel kodda programlama yapıyorsanız, bazen bağlamını bir değişken adı veya değişken adını içeren bir ifadeyi nitelemeniz gerekebilir. , İşlev, kaynak dosyası ve bir değişkenin bulunduğu modül bağlamıdır. Bunu yapmanız gerekirsi içerik işleci sözdizimini kullanabilirsiniz. Daha fazla bilgi için C++ ifadeler bakın.  
  
## <a name="observing-expressions-with-the-watch-window"></a>İzleme penceresinde ifadelerle gözleme  
 Artık bir ifade kullanmayı deneyelim. Hata ayıklayıcı tarafından tanınan herhangi bir geçerli ifade ekleyebilirsiniz.  
  
 Örneğin, önceki bölümde listelenen kodu varsa, bu gibi üç değerlerin ortalamasını alabilirsiniz:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Genel olarak, ifadeleri değerlendirme kuralları **Watch** penceresi kodlama kendi dilinizde ifadeleri değerlendirme kuralları aynı olur. İfadeniz söz dizimi hatası varsa, Kod Düzenleyicisi'nde gördüklerinizle aynı derleyici hatası bekleyebilirsiniz. Örnek aşağıda verilmiştir:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
##  <a name="bkmk_refreshWatch"></a> Güncel değil Gözcü değerlerini yenileme  
 Bazı durumlarda (iki ok olan bir daire veya iki dalgalı çizgiler daire) bir yenileme simgesi görebilirsiniz ne zaman bir ifade değerlendirme içinde **Watch** penceresi.  Örneğin, özellik değerlendirmesini devre dışı varsa (**Araçlar / Seçenekler / hata ayıklama / özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**), ve şu kodu görürsünüz:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Bir izleme ayarlarsanız `Count` özellik listesinde, aşağıdaki gibi bir şey görmeniz gerekir:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Bu, bir hata veya güncel değil bir değeri gösterir. Genellikle, simgesine tıklayarak değeri yenileyebilirsiniz ancak bazı durumlarda yenileme değil de tercih edebilirsiniz. İlk değeri değil neden değerlendirildiğinde bilmeniz gerekir.  
  
 Simgenin üzerine, bir araç ipucu ifadesi değil neden değerlendirildiğinde hakkında bilgi sağlar.  Circling oklar görünüyorsa, ifade aşağıdaki nedenlerden birinden dolayı değerlendirildiği değil:  
  
- İfade değerlendirildiğinde gibi • bir hata oluştu. Örneğin, bir zaman aşımı oluşmuş olabilir veya bir değişken kapsam dışına silinmiş olabilir.  
  
- • İfade işlev çağrısı, bir uygulamada bir yan etkisi tetikleyebilir içerir (bkz [yan etkiler ve ifadeler](#bkmk_sideEffects)).  
  
- Özellikler ve hata ayıklayıcı tarafından dolaylı işlev çağrıları otomatik olarak değerlendirilmesini devre dışı bırakılmış durumdadır (**Araçlar / Seçenekler / hata ayıklama / özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**), ve ardından bir ifade olamaz otomatik olarak değerlendirilir.  
  
  Değer yenilemek için Yenile simgesine tıklayın veya Ara çubuğuna basın. Hata ayıklayıcısı ifadeyi yeniden dener. Özellikler ve örtük yan etkileri otomatik olarak değerlendirilmesini kapatıldığı için yenileme simgesi görüntüleniyorsa, ifade değerlendirilir.  
  
  İş parçacıkları benzer iki dalgalı çizgiler daire bir simgeyi görürseniz, olası bir iş parçacıkları arası bağımlılık nedeniyle ifade Hesaplandı değil. Diğer bir deyişle, kodu değerlendirme, geçici olarak çalışması için uygulamanızı diğer iş parçacıkları gerektirir. Kesme modunda olduğunda, uygulamanızdaki tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarını geçici olarak çalışmasına izin vererek olabilir beklenmeyen etkiler, programınızın durumunu ve kesme noktaları ve bu iş parçacıkları üzerinde oluşturulan özel durumlar gibi olayları yok saymak hata ayıklayıcı neden olur.  
  
##  <a name="bkmk_sideEffects"></a> Yan etkiler ve ifadeler  
 Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya aksi halde, programınızın durumunu etkileyebilir. Örneğin, aşağıdaki ifade değerlendirildiğinde değerini değiştirir `var1`:  
  
```  
var1 = var2  
```  
  
 Bu adlı bir [yan etkisi](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Yan etkileri hata ayıklama daha zor, programınızın çalışma yöntemlerini değiştirerek yapabilirsiniz.  
  
 Yan etkileri olduğu bilinen bir ifade, yalnızca ilk önce onu girdiğinizde bir kez değerlendirilir. Sonraki değerlendirmeler devre dışıdır. Değerin yanında görüntülenen bir güncelleştirme simgesini tıklatarak el ile bu davranışı geçersiz kılabilirsiniz.  
  
 Tüm yan etkileri önlemek için bir yol olan otomatik İşlev değerlendirmesi'ni açmak için (**Araçlar / Seçenekler / hata ayıklama / özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**).  
  
 Değerlendirme özellikleri ya da örtük işlev çağrılarını devre dışı bırakıldığında kullanarak değerlendirme zorlayabilirsiniz **ac** biçim belirleyici (için yalnızca C#). Bkz: [biçim belirleyiciler C#](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>Nesne kimlikleri kullanarak izleme penceresinde (C# ve Visual Basic)  
 Belirli bir nesneyi davranışını gözlemlemek istediğiniz zaman zamanlar vardır; Örneğin, bu değişken kapsam dışına geçti sonra bir yerel değişkeni tarafından başvurulan nesne izlemek isteyebilirsiniz. C# ve Visual Basic nesne kimlikleri belirli örneklerini başvuru türleri için oluşturabilir ve bunları İzleme penceresinde ve kesme noktası koşulları kullanın. Nesne Kimliği hizmetlerinde hata ayıklama ortak dil çalışma zamanı tarafından (CLR) oluşturulan ve nesnesiyle ilişkili.  
  
> [!NOTE]
>  Nesne kimlikleri, zayıf başvuru oluşturmak ve nesnenin çöp olarak toplanacak yüklenmesini engellemez. Bunlar, yalnızca geçerli hata ayıklama oturumu için geçerli olur.  
  
 Aşağıdaki kodda bir yöntem oluşturur bir `Person` ne yaptığını öğrenmek yerel bir değişken, ancak kullanarak istediğiniz `Person`ait farklı bir yöntemde adıdır:  
  
```csharp  
class Person  
{  
    public Person(string name)  
    {  
        Name = name;  
    }  
    public string Name { get; set; }  
}  
  
public class Program  
{  
    List<Person> _people = new List<Person>();  
    public static void Main(string[] args)  
    {  
        MakePerson();  
        DoSomething();  
    }  
  
    private static void MakePerson()  
    {  
        var p = new Person("Bob");  
        _people.Add(p);  
    }  
  
    private static void DoSomething()  
    {  
        // more processing  
         Console.WriteLine("done");  
    }  
}  
  
```  
  
 Bir başvuru ekleyebilirsiniz `Person` nesnesine **Watch** penceresi aşağıdaki gibi:  
  
1.  Bir kesme noktası kodda nesne oluşturulduktan sonra biraz zaman ayarlayın.  
  
2.  Hata ayıklamayı başlatmak ve yürütme bir kesme noktasına durdurulduğunda, değişkeni bulun **Yereller** penceresinde sağ tıklatın ve seçin **nesne kimliği yap**.  
  
3.  Görmelisiniz bir **$** bir sayıyı artı **Yereller** penceresi. Bu nesne kimliğidir.  
  
4.  Nesne Kimliği İzle penceresine ekleyin.  
  
5.  Nesnenin davranışını gözlemlemek istediğiniz bir kesme noktası ayarlayın.  Yukarıdaki kod, olurdu içinde `DoSomething()` yöntemi.  
  
6.  Hata ayıklamaya devam et ve yürütme durduğunda `DoSomething()` yöntemi **Watch** pencere görüntüler `Person` nesne.  
  
> [!NOTE]
>  Nesnenin özellikleri gibi görmek istiyorsanız `Person.Name` yukarıdaki örnekte, özellik değerlendirmesini etkinleştirmiş olmanız gerekir.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>Kayıtları kullanarak izleme penceresinde (yalnızca C++)  
 Yerel kod hata ayıklaması yapıyorsanız, değişken adları kullanarak yanı sıra yazmaç adlarını ekleyebilirsiniz  **$ \<adını kaydetmek >** veya  **@ \<adını kaydetmek >**.  Daha fazla bilgi için [sözde değişken](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView ve İzleme penceresi  
 Bazı komut dosyası dilleri (örn, JavaScript veya Python) dinamik kullanın veya [yazarak duck](https://en.wikipedia.org/wiki/Duck_typing), ve .NET dillerinde (sürüm 4.0 ve üzeri) destek sahip olabileceği için normal hata ayıklama pencerelerini kullanarak gözlemek çok zor olan nesneler çalışma zamanı özellikleri ve yöntemleri görüntülenemiyor.  
  
 İzleme penceresinde uygulayan bir tür oluşturan bir veya bir nesne görüntülendiğinde <xref:System.Dynamic.IDynamicMetaObjectProvider>, özel bir hata ayıklayıcı ekler **dinamik Görünüm** düğüme **Otolar** görüntüler. Bu düğüm, dinamik dinamik Nesne üyelerini gösterir ancak üye değerlerinin düzenlenmesine izin vermez.  
  
 Bir alt sağ tıklattığınızda, bir **dinamik Görünüm** ve **Gözcü Ekle**, hata ayıklayıcısı bir dinamik nesneye bir nesne bıraktığı yeni bir gözleme değişkeni ekler. Diğer bir deyişle, **nesne adı** olur (**(dinamik) nesne). Ad**.  
  
 Üyeleri değerlendirme bir **dinamik Görünüm** yan etkileri olabilir. Yan etkileri nelerdir açıklaması için bkz [yan etkiler ve ifadeler](#bkmk_sideEffects). C# için hata ayıklayıcıyı otomatik olarak gösterilen değerler hesaplanmaz **dinamik Görünüm** yeni bir kod satırına geçtiğinizde. Visual Basic için ifade eklenen **dinamik Görünüm** otomatik olarak yenilenir.  
  
 Dinamik görünüm değerleri yenileme hakkında yönergeler için bkz: [güncel yenileme Gözcü değerlerini](#bkmk_refreshWatch).  
  
 Yalnızca görüntülemek istiyorsanız **dinamik Görünüm** bir nesne için kullanabileceğiniz **dinamik** biçim belirticisi:  
  
- C# ' ta: **ObjectName dinamik**  
  
- Visual Basic:: **$dynamic, ObjectName**  
  
  **Dinamik Görünüm** COM nesneleri için hata ayıklama deneyimini de geliştirir. Hata ayıklayıcısı içinde sarmalanmış bir COM nesnesi karşılaştığında **System.comobject'e**, ekler bir **dinamik Görünüm** düğüm nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Pencereleri](../debugger/debugger-windows.md)





