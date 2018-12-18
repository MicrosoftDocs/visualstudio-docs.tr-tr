---
title: Değişkenler üzerinde bir izleme ayarlama | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 898c79f3985e24f52620f12dc25ad6044d05ac64
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059489"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>İzleme ve QuickWatch değişkenlerle izleyin 

Hata ayıklarken, kullanabileceğiniz **Watch** windows ve **QuickWatch** değişkenleri ve ifadeleri izlemek için. Windows, yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** windows aynı anda hata ayıklama sırasında birkaç değişkenleri görüntüleyebilir. **QuickWatch** iletişim kutusu, bir kerede tek bir değişken görüntüler ve hata ayıklama devam etmeden önce kapatılması gerekir.

Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [düzeltme hataları daha iyi yazarak C# kod](../debugger/write-better-code-with-visual-studio.md) ve [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) bu makalede geçmeden önce.

## <a name="observe-variables-with-a-watch-window"></a>İzleme penceresi değişkenleri gözlemleyin

Birden fazla açabileceğiniz **izleme** penceresinde ve birden fazla değişken bir **izleme** penceresi. 

Örneğin, bir izleme değerlerine ayarlanacak `a`, `b`, ve `c` aşağıdaki kodda yer:

```C++
int main()
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

    return 0;
}

```

1. Bir kesme noktası ayarlamak `c = a + b;` sol kenar boşluğunu tıklayarak satırı seçerek **hata ayıklama** > **iki durumlu kesme noktası**, ya basarak **F9**.
   
1. Yeşil seçerek hata ayıklamayı Başlat **Başlat** OK veya **hata ayıklama** > **hata ayıklamayı Başlat**, veya basın **F5**. Yürütme kesme noktasında duraklatır.
   
1. Açık bir **Watch** penceresini seçerek **hata ayıklama** > **Windows** > **Watch**  >   **1 izleyin**, ya basarak **Ctrl**+**Alt**+**W** > **1**.
   
   Ek açabilirsiniz **Watch** windows seçerek windows **2**, **3**, veya **4**.
   
1. İçinde **Watch** pencere, boş bir satırı seçin ve tür değişkeni `a`. İçin de aynısını yapın `b` ve `c`.
   
   ![Değişkenleri izleyin](../debugger/media/watchvariables.png "WatchVariables")
   
1. Seçerek hata ayıklamaya devam et **hata ayıklama** > **içine adımla** ya basarak **F11** ilerlemek için gerektiği şekilde. Değişken değerleri **Watch** değiştirme penceresi aracılığıyla yineleme gibi `for` döngü.
   
>[!NOTE]
>Yalnızca C++ için 
>- Bir değişken veya değişken adını kullanan bir ifade bağlamını nitelemeniz gerekebilir. İşlevi, kaynak dosya veya bir değişkenin bulunduğu modül bağlamıdır. Bağlam nitelemek varsa, [bağlam işleci (C++)](../debugger/context-operator-cpp.md) sözdiziminde **adı** içinde **Watch** penceresi. 
>  
>- YAZMAÇ adlarını ve değişken adları kullanarak ekleyebilirsiniz  **$ \<kaydetme&nbsp;adı >** veya  **@ \<kaydetme&nbsp;adı >** için **adı** içinde **Watch** penceresi. Daha fazla bilgi için [sözde değişken](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>İfadeleri İzleme penceresinde kullanma

Hata ayıklayıcıda tarafından tanınan herhangi bir geçerli ifade inceleyebileceğiniz bir **Watch** penceresi.

Örneğin, önceki bölümde kodunu üç değerlerin ortalamasını girerek alabileceğiniz `(a + b + c) / 3` içinde **Watch** penceresi:

![İfadeyi İzle](../debugger/media/watchexpression.png "ifade izleyin")

İfadeleri değerlendirme kuralları **Watch** penceresi, genellikle kod dili ifadelerinde değerlendirme kuralları olarak aynı. Bir ifade söz dizimi hatası varsa, Kod Düzenleyicisi olduğu gibi aynı derleyici hatası bekler. Örneğin, önceki ifade bir yazım yanlışı bu hatayı üretir **Watch** penceresi:

![İfade hatası izleyin](../debugger/media/watchexpressionerror.png "ifade hatası izleyin")

İki dalgalı çizgi simgesine daire görünebilir **Watch** penceresi. Bu simge, hata ayıklayıcı olası iş parçacıkları arası bağımlılık nedeniyle ifadeyi değerlendirmez anlamına gelir. Diğer iş parçacıklarını geçici olarak çalıştırmayı uygulamanıza kod değerlendirme gerektirir, ancak kesme modunda olduğundan, uygulamanızı tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarını geçici olarak çalışmasına izin vererek olabilir beklenmeyen etkileri durumunu uygulamanızı ve hata ayıklayıcı kesme noktaları ve bu iş parçacıklarında özel durumlar gibi olayları yoksay.

### <a name="bkmk_refreshWatch"></a> Gözcü değerlerini yenileme

Bir yenileme simgesi (yuvarlak ok) görünebilir **Watch** bir ifade değerlendirildiğinde penceresi. Yenileme simgesi bir hata veya güncel değil bir değeri gösterir. 

Değer yenilemek için yenile simgesini seçin veya Ara çubuğuna basın. Hata ayıklayıcısı ifadeyi yeniden dener. Ancak, değil istediğiniz veya ifade değeri Hesaplandı neden değildi bağlı olarak yeniden değerlendirmek kullanabilirsiniz. 

Yenileme simgesinin üzerine gelin veya bakın **değer** değildi ifadenin değerlendirilmesi bir nedenle sütun. Nedenler şunlardır:

- İfade, önceki örnekte olduğu gibi değerlendirilen gibi bir hata oluştu. Bir zaman aşımı oluşabilir veya bir değişken kapsam dışına olabilir.
  
- Uygulamasında bir yan etkisi tetikleyebilir bir işlev çağrısı ifadesi var. Bkz: [ifade yan etkileri](#bkmk_sideEffects).
  
- Özellikler ve örtük işlev çağrılarını otomatik olarak değerlendirilmesini devre dışı bırakıldı. 
  
Özellikler ve örtük işlev çağrılarını otomatik olarak değerlendirilmesini devre dışı olduğundan yenileme simgesi görünürse, seçerek etkinleştirebilirsiniz **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir** içinde **araçları**   >  **Seçenekleri** > **hata ayıklama** > **genel**.

Yenile simgesini kullanarak göstermek için:

1. İçinde **Araçları** > **seçenekleri** > **hata ayıklama** > **genel**, Temizle**Özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir** onay kutusu. 
   
1. Aşağıdaki kodu girin ve **Watch** penceresinde üzerinde bir izleme ayarlayın `list.Count` özelliği. 
   
   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```
   
1. Hata ayıklama başlatılamıyor. **Watch** penceresi gibi aşağıdaki iletiyi gösterir:
   
   ![Watch yenileme](../debugger/media/refreshwatch.png "Watch yenileme")
   
1. Değer yenilemek için yenile simgesini seçin veya Ara çubuğuna basın. Hata ayıklayıcı ifade reevaluates. 

### <a name="bkmk_sideEffects"></a> İfade yan etkileri 

Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya aksi halde uygulamanızı durumunu etkiler. Örneğin, aşağıdaki ifade değerlendirildiğinde değerini değiştirir `var1`:

```csharp
var1 = var2
```

Bu kodu neden olabilir bir [yan etkisi](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Yan etkileri hata ayıklama uygulamanızı çalışır değiştirerek güçleştirebilir.

Yan etkileri olan bir ifade, yalnızca ilk önce onu girdiğinizde bir kez değerlendirilir. İfade, sonra aşımı gri görünür **Watch** penceresi ve daha fazla değerlendirme devre dışı bırakıldı. Araç ipucunu veya **değer** sütun açıklar ifade bir yan etkisi neden olur. Değerin yanında görüntülenen yenile simgesini seçerek yeniden değerlendirme zorlayabilirsiniz.

Yan etkileri atamasını önlemek için bir yol otomatik İşlev değerlendirmesi açmaktır. İçinde **Araçları** > **seçenekleri** > **hata ayıklama** > **genel**, seçimini**Özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**.

İçin C# değerlendirme özellikleri ya da örtük işlev çağrılarını devre dışı bırakıldığında, yalnızca değerlendirme ekleyerek zorlayabilirsiniz **ac** biçim belirleyici bir değişkene **adı** içinde **izleyin**  penceresi. Bkz: [biçim belirleyiciler C#](../debugger/format-specifiers-in-csharp.md).

## <a name="bkmk_objectIds"></a> İzleme penceresinde nesne kimlikleri kullanın (C# ve Visual Basic)

Bazen, belirli bir nesneyi davranışını gözlemlemek istediğiniz. Örneğin, bu değişken kapsam dışına geçti sonra bir yerel değişkeni tarafından başvurulan nesne izlemek isteyebilirsiniz. İçinde C# ve Visual Basic, belirli örneklerini başvuru türleri için nesne kimliklerini oluşturabilir ve bunları kullanmak **Watch** penceresi ve kesme noktası koşulları. Nesne Kimliği hizmetlerinde hata ayıklama ortak dil çalışma zamanı tarafından (CLR) oluşturulan ve nesnesiyle ilişkili.

> [!NOTE]
> Nesne kimlikleri nesnenin çöp olarak toplanacak engellemek yoksa zayıf başvurular oluşturun. Bunlar, yalnızca geçerli hata ayıklama oturumu için geçerli olur.

Aşağıdaki kodda, `MakePerson()` yöntemi oluşturur bir `Person` yerel bir değişken kullanarak: 

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
    static List<Person> _people = new List<Person>();
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

Adını öğrenmek için `Person` içinde `DoSomething()` yöntemi, bir başvuru ekleyebilirsiniz `Person` nesne kimliği **Watch** penceresi.

1. Koddan sonra bir kesme noktası ayarlamak `Person` nesnesi oluşturuldu.
   
1. Hata ayıklama başlatılamıyor.
   
1. Yürütme kesme noktasında durakladığında açın **Yereller** penceresini seçerek **hata ayıklama** > **Windows** > **Yereller**.
   
1. İçinde **Yereller** penceresinde sağ `Person` seçin ve değişken **nesne kimliği yap**.
   
   Bir dolar işareti görmeniz gerekir (**$**) bir sayı artı **Yereller** penceresinde, nesne kimliği'dir.
   
1. Nesne kimliği ekleme **Watch** nesne kimliği sağ tıklatıp seçerek penceresi **Gözcü Ekle**.
   
1. Başka bir kesim noktası `DoSomething()` yöntemi.
   
1. Hata ayıklamaya devam et. Yürütme zaman duraklatır `DoSomething()` yöntemi **Watch** pencere görüntüler `Person` nesne.
   
   > [!NOTE]
   > Nesnenin özellikleri gibi görmek istiyorsanız `Person.Name`, özellik değerlendirmesini seçerek etkinleştirmelisiniz **Araçları** > **seçenekleri**  >   **Hata ayıklama** > **genel** > **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**.

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik Görünüm ve İzleme penceresi

Bazı komut dosyası dilleri (örneğin, JavaScript veya Python) dinamik kullanın veya [duck](https://en.wikipedia.org/wiki/Duck_typing) yazarak ve .NET 4.0 ve üzeri bir sürüm normal hata ayıklama pencerelerinde gözlemek çok zor olan nesneleri destekler.

**Watch** penceresi uygulayan türleri oluşturulan dinamik nesneler olarak bu nesneleri görüntüler <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimi. Dinamik Nesne düğümleri, dinamik dinamik Nesne üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin verme. 

Yenilemek için **dinamik Görünüm** değerleri, select [yenile simgesini](#bkmk_refreshWatch) dinamik Nesne düğümünün yanında. 

Yalnızca görüntülemek için **dinamik Görünüm** eklemek için bir nesne, bir **dinamik** içinde dinamik Nesne adından sonra Biçim belirticisi **izleme** penceresi:

- C# için: `ObjectName, dynamic`
- Visual Basic için: `$dynamic, ObjectName`

>[!NOTE]
>- C# Hata ayıklayıcı değerleri otomatik olarak yeniden değil **dinamik Görünüm** sonraki kod satırına geçtiğinizde. 
>- Visual Basic hata ayıklayıcı aracılığıyla eklenen ifadeler otomatik olarak yenilenir **dinamik Görünüm**.
>- Üyeleri değerlendirme bir **dinamik Görünüm** olabilir [yan etkileri](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). 

**Yeni bir izleme eklemek için değişken, bir dinamik nesneye bir nesne çevirir:**
  
1. Bir alt sağ bir **dinamik Görünüm**.
1. Seçin **izleme Ekle**. `object.name` Olur `((dynamic) object).name` ve yeni bir görünür **Watch** penceresi.

Hata ayıklayıcı ayrıca ekler bir **dinamik Görünüm** nesnenin alt düğümü **Otolar** penceresi. Açmak için **Otolar** , hata ayıklama sırasında penceresinde **hata ayıklama** > **Windows** > **Otolar**. 

**Dinamik Görünüm** COM nesneleri için hata ayıklamasını da geliştirir. Hata ayıklayıcı zaman alır, sarılı bir COM nesnesi için **System.comobject'e**, ekler bir **dinamik Görünüm** düğüm nesnesi.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Tek bir değişken veya QuickWatch ifadesiyle gözlemleyin

Kullanabileceğiniz **QuickWatch** tek bir değişken gözlemleyin. 

Örneğin, aşağıdaki kodu:

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

Gözlemlemek için `a` değişkeni 
   
1. Bir kesme noktası ayarlamak `a = a + b;` satır.
   
1. Hata ayıklama başlatılamıyor. Yürütme kesme noktasında duraklatır.
   
1. Değişken seçme `a` kod.
   
1. Seçin **hata ayıklama** > **QuickWatch**, basın **Shift**+**F9**, veya sağ tıklayıp **QuickWatch**. 
   
   **QuickWatch** iletişim kutusu görüntülenir. `a` Değişkendir içinde **ifade** ile kutusunda bir **değer** , **1**.
   
   ![QuickWatch değişkeni](../debugger/media/quickwatchvariable.png "QuickWatch değişkeni")
   
1. Türü gibi bir ifade değişkeni kullanarak bir ifadeyi değerlendirmek için `a + b` içinde **ifade** kutusunda ve seçin **yeniden değerlendir**.
   
   ![QuickWatch ifade](../debugger/media/quickwatchexpression.png "QuickWatch ifadesi")
   
1. Değişken veya ifadeyi eklemek için **QuickWatch** için **Watch** penceresinde **Gözcü Ekle**.
   
1. Seçin **kapatmak** kapatmak için **QuickWatch** penceresi. (**QuickWatch** olduğundan kalıcı bir iletişim kutusu açık olduğu sürece hata ayıklama devam edemiyor.)
   
1. Hata ayıklamaya devam et. Değişkeninde inceleyebileceğiniz **Watch** penceresi.

## <a name="see-also"></a>Ayrıca bkz.
 [Hata ayıklıyor?](../debugger/what-is-debugging.md)  
 [Daha iyi yazarak hataları düzeltmek C# kod](../debugger/write-better-code-with-visual-studio.md)  
 [Hata ayıklama sırasında ilk bakış](../debugger/debugger-feature-tour.md) [windows hata ayıklayıcı](../debugger/debugger-windows.md)
