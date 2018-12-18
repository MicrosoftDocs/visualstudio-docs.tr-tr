---
title: Sınıf tasarımcısında Visual C++ sınıfları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritancelinelabel
helpviewer_keywords:
- Class Designer [Visual Studio], classes
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d4193dda70aeda8534b9dc2fa3428ca08a9d89fa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285694"
---
# <a name="visual-c-classes-in-class-designer"></a>Sınıf Tasarımcısında Visual C++ Sınıfları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Tasarımcısı, C++ sınıflarını destekler ve C++ sınıfları birden çok devralma ilişkisi olabilir dışında Visual Basic ve Visual C# sınıfı şekiller, aynı şekilde yerel C++ sınıfları görselleştirir. Daha fazla alanlar ve yöntemler sınıfında göstermek veya alanından tasarruf etmek için daraltılabilir sınıf şeklinin genişletebilirsiniz.  
  
> [!NOTE]
>  Sınıf Tasarımcısı, birleşimler (bellek tahsis sınıfı özel bir tür yalnızca Birliği'nin en büyük veri üyesi için gerekli miktarıdır) desteklemez.  
  
## <a name="simple-inheritance"></a>Basit devralma  
 Birden fazla sınıf bir sınıf diyagramına sürükleyin ve sınıfların sınıf devralma ilişkisi olan bir ok bunları birbirine bağlar. Yönde taban sınıfının ok işaret eder. Aşağıdaki sınıflar, bir sınıf diyagramında görüntülendiğinde, örneğin, bir ok, B'den y: için işaret eden bağlanır  
  
```  
class A {};  
class B : A {};  
```  
  
 Ayrıca yalnızca Sınıf B sınıf diyagramına sürükleyin, sınıf şeklinin B için sağ tıklayın ve ardından **temel sınıfları Göster**. Bu, onun temel sınıfından görüntüler: A.  
  
## <a name="multiple-inheritance"></a>Birden Çok Devralma  
 Sınıf Tasarımcısı görselleştirme birden çok sınıf devralma ilişkilerinin destekler. *Birden çok devralma* türetilmiş bir sınıf birden fazla temel sınıfın özniteliklerine sahip olduğunda kullanılır. Birden çok devralma bir örneği verilmiştir:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Birden fazla sınıf sınıf diyagramına sürükleyin ve sınıfları birden çok sınıf devralma ilişkisi, bir ok bunları birbirine bağlar. Temel sınıflar yönünde ok işaret eder.  
  
 Sınıf şeklinin sağ tıklatıp **temel sınıfları Göster** seçilen sınıf için temel sınıflarını görüntüler.  
  
> [!NOTE]
>  **Türetilmiş sınıfları Göster** komutu, C++ kodu için desteklenmiyor. Türetilen sınıfların sınıf genişletme türü düğümünü genişleterek görünümüne giderek görüntüleyebilirsiniz **türetilen türler** alt ve sonra bu türleri sınıf diyagramına sürükleyebilir sürükleyerek.  
  
 Birden çok sınıf devralma hakkında daha fazla bilgi için bkz: [(NOTINBUILD) birden çok devralma](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca) ve [birden çok temel sınıflar](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740).  
  
## <a name="abstract-classes"></a>Soyut sınıflar  
 Sınıf Tasarımcısı, soyut sınıflar ("soyut temel sınıflar" olarak da adlandırılan) destekler. Bu, hiçbir zaman örneği ancak kendisinden başka sınıflar türetilip sınıflardır. Bu belgedeki "Birden çok devralma" bir örnek kullanarak örneği `Bird` sınıfına aşağıdaki gibi ayrı nesneleri:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Ancak, örneklemek istediğinize değil `Swimmer` ayrı ayrı nesneler olarak sınıf. Yalnızca diğer tür hayvan sınıfı, örneğin, türetmeniz planladığınız `Penguin`, `Whale`, ve `Fish`. Bu durumda, bildirirsiniz `Swimmer` sınıfı soyut bir temel sınıf olarak.  
  
 Bir sınıfı soyut olarak bildirmek için kullanabileceğiniz `abstract` anahtar sözcüğü. Özet olarak işaretlenmiş veya soyut bir sınıf, dahil edilen üyeleri sanal ve soyut sınıftan türeyen sınıflar tarafından uygulanmalıdır.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 En az bir saf sanal işlevi dahil ederek bir sınıfı soyut olarak da bildirebilirsiniz:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Bir sınıf diyagramında sınıf adı bu bildirimleri görüntülediğinizde `Swimmer` ve kendi saf sanal işlevi `swim` italik gösterimi ile birlikte bir soyut sınıf şeklinde görüntülenen **soyut sınıf**. Bir noktalı çizgi kenarlığını olması dışında soyut sınıf tür şeklini, normal bir sınıfın aynı olduğuna dikkat edin.  
  
 Soyut bir temel sınıftan türetilmiş bir sınıf, taban sınıftaki her saf sanal işlevi geçersiz kılmanız gerekir veya türetilmiş bir sınıf örneği oluşturulamıyor. Bu nedenle, örneğin, türetirseniz bir `Fish` gelen sınıfı `Swimmer` sınıfı `Fish` geçersiz kılmanız gerekir `swim` yöntemi:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Bu kod bir sınıf diyagramında görüntülediğinizde, Sınıf Tasarımcısı bir devralma satırından çizer `Fish` için `Swimmer`.  
  
## <a name="anonymous-classes"></a>Anonim sınıflar  
 Sınıf Tasarımcısı, anonim sınıflarını destekler. *Anonim sınıf türleri* sınıfları bir tanımlayıcı olarak bildirilir. Bunlar bir oluşturucu veya yıkıcı olamaz, İşlevler için bağımsız değişken olarak geçirilemez ve işlevlerden dönüş değerleri döndürülemez. Anonim bir sınıf, bir sınıf adı aşağıdaki örnekte olduğu gibi bir typedef adı değiştirmek için kullanabilirsiniz:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Yapılar, anonim olarak da olabilir. Sınıf Tasarımcısı, anonim sınıflarını görüntüler ve ilgili türü olarak aynı yapıları. Bildirme ve anonim sınıfları ve yapıları görüntüle olsa da, Sınıf Tasarımcısı, belirttiğiniz etiket adını kullanmaz. Bu, sınıf görünümü oluşturan adı kullanacaksınız. Sınıf veya yapı sınıf görünümü ve Sınıf Tasarımcısı bir öğe olarak görünür adlı **__unnamed**.  
  
 Anonim sınıflar hakkında daha fazla bilgi için bkz. [anonim sınıf türleri](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8).  
  
## <a name="template-classes"></a>Şablon sınıfları  
 Sınıf Tasarımcısı görselleştirme şablon sınıfının destekler. İç içe geçmiş bildirimleri desteklenir. Aşağıdaki tabloda, bazı tipik bildirimlerini gösterir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Şablon sınıfı|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Şablon sınıfı|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|  
  
 Aşağıdaki tabloda, kısmi özelleştirme bazı örnekler gösterilmektedir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Şablon sınıfı|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Şablon sınıfı|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Şablon sınıfı|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Şablon sınıfı|  
  
 Aşağıdaki tabloda, kısmi özelleştirmede devralma bazı örnekler gösterilmektedir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Şablon sınıfı<br /><br /> `B`<br /><br /> örneği<br /><br /> (nokta sınıfı için)<br /><br /> `C`<br /><br /> örneği<br /><br /> (nokta sınıfı için)|  
  
 Aşağıdaki tabloda, şablon işlevleri kısmi özelleştirmede bazı örnekler gösterilmektedir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> FUNC\<T, U > (+ 1 aşırı yükleme)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Şablon sınıfı<br /><br /> `B<T2>`<br /><br /> Şablon sınıfı<br /><br /> (B altında bir sınıf içinde barındırılan **iç içe türler**)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> örneği<br /><br /> C ->\<int ><br /><br /> `C<T>`<br /><br /> Şablon sınıfı|  
  
 Aşağıdaki tabloda, şablon devralma bazı örnekler gösterilmektedir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> örneği<br /><br /> B -&GT;<br /><br /> `C<int>`<br /><br /> örneği<br /><br /> (B altında C sınıfı içinde barındırılan **iç içe türler**)<br /><br /> `C<T>`<br /><br /> Şablon sınıfı|  
  
 Aşağıdaki tabloda, kurallı özel sınıfın bağlantı bazı örnekler gösterilmektedir.  
  
|Kod öğesi|Sınıf Tasarımcısı görünümü|  
|------------------|-------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> örneği<br /><br /> C ->\<int ><br /><br /> `C<int>`<br /><br /> örneği<br /><br /> `C<T>`<br /><br /> Şablon sınıfı<br /><br /> `D`<br /><br /> örneği<br /><br /> C ->\<kayan noktalı sayı >|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> Min \<T >|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual C++ kodu (Sınıf Tasarımcısı) ile çalışma](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Sınıflar ve yapılar](http://msdn.microsoft.com/library/516dd496-13fb-4f17-845a-e9ca45437873)   
 [Anonim sınıf türleri](http://msdn.microsoft.com/library/9ba667b2-8c2a-4c29-82a6-fa120b9233c8)   
 [(NOTINBUILD) Birden çok devralma](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Birden çok taban sınıfı](http://msdn.microsoft.com/library/a30c69fe-401c-4a87-96a0-e0da70c7c740)   
 [Şablonlar](http://msdn.microsoft.com/library/90fcc14a-2092-47af-9d2e-dba26d25b872)



