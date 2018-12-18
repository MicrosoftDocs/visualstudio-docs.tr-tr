---
title: Karışık Minimum kurallar kural kümesi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 203422047ec1293e109a34699953897000893902
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389470"
---
# <a name="mixed-minimum-rules-rule-set"></a>Karışık Minimum Kurallar kural kümesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft karışık Minimum kurallar potansiyel güvenlik boşluklarını ve Uygulama Kilitlenmesi gibi Common Language Runtime destekleyen C++ projelerinizin en kritik sorunlara odaklanır. Common Language Runtime destekleyen C++ projeleriniz için oluşturduğunuz herhangi bir özel kural kümesi bu kural kümesini içermelidir.  


|                                            Kural                                             |                                                  Açıklama                                                  |
|---------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                              [C6001](../code-quality/c6001.md)                              |                                          Başlatılmamış belleği kullanma                                           |
|                              [C6011](../code-quality/c6011.md)                              |                                          Boş işaretçiye başvuruluyor                                           |
|                              [C6029](../code-quality/c6029.md)                              |                                            Denetlenmemiş değer kullanımı                                             |
|                              [C6053](../code-quality/c6053.md)                              |                                          Çağrıdan Sıfırla sonlandırma                                           |
|                              [C6059](../code-quality/c6059.md)                              |                                               Bozuk birleştirme                                               |
|                              [C6063](../code-quality/c6063.md)                              |                                  Biçimlendirme işlevinde dize bağımsız değişkeni eksiktir                                   |
|                              [C6064](../code-quality/c6064.md)                              |                                  Biçimlendirme işlevinde eksik tamsayı değişkeni                                  |
|                              [C6066](../code-quality/c6066.md)                              |                                  Biçimlendirme işlevinde eksik işaretçi değişkeni                                  |
|                              [C6067](../code-quality/c6067.md)                              |                              Dize işaretçisi değişkeni biçimlendirme işlevinde eksik                               |
|                              [C6101](../code-quality/c6101.md)                              |                                        Başlatılmamış bellek döndürülüyor                                         |
|                              [C6200](../code-quality/c6200.md)                              |                                         Dizin arabelleği üst sınırını aşıyor                                          |
|                              [C6201](../code-quality/c6201.md)                              |                                      Dizin, yığın arabelleği üst sınırını aşıyor                                       |
|                              [C6270](../code-quality/c6270.md)                              |                                   Biçimlendirme işlevinde kayan bağımsız değişken eksik                                   |
|                              [C6271](../code-quality/c6271.md)                              |                                       Biçimlendirme işlevinde fazladan değişken                                       |
|                              [C6272](../code-quality/c6272.md)                              |                                     Biçimlendirme işlevinde kayan nokta olmayan değişken                                     |
|                              [C6273](../code-quality/c6273.md)                              |                                    Biçimlendirme işlevinde tamsayı olmayan değişken                                     |
|                              [C6274](../code-quality/c6274.md)                              |                                   Biçimlendirme işlevinde karakter olmayan değişken                                   |
|                              [C6276](../code-quality/c6276.md)                              |                                              Geçersiz dize dönüştürmesi                                              |
|                              [C6277](../code-quality/c6277.md)                              |                                          Geçersiz CreateProcess çağrısı                                           |
|                              [C6284](../code-quality/c6284.md)                              |                                  Biçimlendirme işlevinde geçersiz nesne değişkeni                                   |
|                              [C6290](../code-quality/c6290.md)                              |                                      Mantıksal Not bit düzeyinde- ve önceliği                                       |
|                              [C6291](../code-quality/c6291.md)                              |                                       Mantıksal Not bit düzeyinde- veya önceliği                                       |
|                              [C6302](../code-quality/c6302.md)                              |                             Biçimlendirme işlevinde geçersiz karakter dizesi değişkeni                              |
|                              [C6303](../code-quality/c6303.md)                              |                           Biçimlendirme işlevinde geçersiz geniş karakter dizesi değişkeni                           |
|                              [C6305](../code-quality/c6305.md)                              |                                         Eşleşmeyen boyut ve sayı kullanımı                                         |
|                              [C6306](../code-quality/c6306.md)                              |                                   Geçersiz değişken bağımsız değişken işlev çağrısı                                   |
|                              [C6328](../code-quality/c6328.md)                              |                                       Olası bağımsız değişken uyumsuzluğu                                        |
|                              [C6385](../code-quality/c6385.md)                              |                                                 Okuma taşması                                                  |
|                              [C6386](../code-quality/c6386.md)                              |                                                 Yazma taşması                                                 |
|                              [C6387](../code-quality/c6387.md)                              |                                            Geçersiz parametre değeri                                            |
|                              [C6500](../code-quality/c6500.md)                              |                                          Geçersiz öznitelik özelliği                                           |
|                              [C6501](../code-quality/c6501.md)                              |                                     Çakışan öznitelik özellik değerleri                                     |
|                              [C6503](../code-quality/c6503.md)                              |                                           Başvuru Null olamaz                                           |
|                              [C6504](../code-quality/c6504.md)                              |                                              İşaretçi olmayan değişkende null                                              |
|                              [C6505](../code-quality/c6505.md)                              |                                               Void üzerinde MustCheck                                               |
|                              [C6506](../code-quality/c6506.md)                              |                                      İşaretçi olmayan veya dizi değişkende arabellek boyutu                                      |
|        [C6507](http://msdn.microsoft.com/en-us/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       Null uyumsuzluğu sıfır başvurma                                       |
|                              [C6508](../code-quality/c6508.md)                              |                                           Sabit üzerinde yazma erişimi                                            |
|                              [C6509](../code-quality/c6509.md)                              |                                          Önkoşulda return kullanıldı                                          |
|                              [C6510](../code-quality/c6510.md)                              |                                        İşaretçi olmayan değişkende null                                         |
|                              [C6511](../code-quality/c6511.md)                              |                                          MustCheck olmalıdır Evet veya Hayır                                          |
|                              [C6513](../code-quality/c6513.md)                              |                                       Arabellek boyutu olmadan öğe boyutu                                        |
|                              [C6514](../code-quality/c6514.md)                              |                                        Arabellek boyutu dize boyutunu aşıyor                                         |
|                              [C6515](../code-quality/c6515.md)                              |                                          İşaretçi olmayan değişkende arabellek boyutu                                           |
|                              [C6516](../code-quality/c6516.md)                              |                                          Öznitelikte özellik yok                                           |
|                              [C6517](../code-quality/c6517.md)                              |                                       Okunabilir olmayan arabellekte geçerli boyut                                       |
|                              [C6518](../code-quality/c6518.md)                              |                                     Yazılabilir olmayan arabellekte yazılabilir boyut                                      |
|        [C6519](http://msdn.microsoft.com/en-us/2b6326b0-0539-4d26-8fb1-720114933232)        |                  Geçersiz ek açıklama: 'NeedsRelease' özelliğinin değer olmalıdır Evet veya Hayır                   |
|        [C6521](http://msdn.microsoft.com/en-us/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)        |                                        Geçersiz boyut dize başvurma                                        |
|                              [C6522](../code-quality/c6522.md)                              |                                           Geçersiz boyut dize türü                                            |
|        [C6523](http://msdn.microsoft.com/en-us/11397a31-b224-46b0-afb7-d49ca576a3bb)        |                                         Geçersiz boyut dize parametresi                                         |
|                              [C6525](../code-quality/c6525.md)                              |                                   Geçersiz boyutta dize ulaşılamayan konumu                                    |
|        [C6526](http://msdn.microsoft.com/en-us/59c590c7-0098-4166-a1ac-87f324596002)        |                                        Geçersiz boyut dize arabellek türü                                        |
|                              [C6527](../code-quality/c6527.md)                              |              Geçersiz ek açıklama: 'NeedsRelease' özelliği void türünün değerleri üzerinde kullanılamaz               |
|                              [C6530](../code-quality/c6530.md)                              |                                       Biçim dizesi stili tanınmıyor                                        |
|                              [C6540](../code-quality/c6540.md)                              | Bu işlev üzerindeki öznitelik ek açıklamaları kullanımı tüm, var olan __declspec ek açıklamalarını geçersiz kılar  |
|                              [C6551](../code-quality/c6551.md)                              |                              Geçersiz boyut belirtimi: ifade ayrıştırılamıyor                              |
|                              [C6552](../code-quality/c6552.md)                              |                              Geçersiz Deref = veya Notref =: ifade ayrıştırılamıyor                               |
|                              [C6701](../code-quality/c6701.md)                              |                                  Değer geçerli bir Yes/No/Maybe değeri değil.                                  |
|                              [C6702](../code-quality/c6702.md)                              |                                        Değer bir dize değeri değil.                                        |
|                              [C6703](../code-quality/c6703.md)                              |                                           Değer bir sayı değil                                           |
|                              [C6704](../code-quality/c6704.md)                              |                                    Beklenmeyen ek açıklama ifadesi hatası                                     |
|                              [C6705](../code-quality/c6705.md)                              |     Bağımsız değişkenler ek açıklaması için beklenen sayıda gerçek bağımsız değişkenler için ek açıklama sayısı eşleşmiyor      |
|                              [C6706](../code-quality/c6706.md)                              |                                  Ek açıklama için beklenmeyen ek açıklama hatası                                   |
|                             [C28021](../code-quality/c28021.md)                             |                                Not eklenen parametrenin bir işaretçi olmalıdır                                |
|                             [C28182](../code-quality/c28182.md)                             |         NULL işaretçisinin başvurusunun kaldırılması. Başka bir işaretçi yaptığınız gibi işaretçi aynı NULL değerini içeriyor.          |
|                             [C28202](../code-quality/c28202.md)                             |                                    Statik olmayan üyeye geçersiz başvuru                                     |
|                             [C28203](../code-quality/c28203.md)                             |                                     Sınıf üyesine belirsiz başvuru.                                      |
|                             [C28205](../code-quality/c28205.md)                             |                           \_Başarı\_ veya \_CONTINUE\_ geçersiz bir bağlamda kullanılan                            |
|                             [C28206](../code-quality/c28206.md)                             |                                   İşlenen noktaları sol, '->' kullanın                                   |
|                             [C28207](../code-quality/c28207.md)                             |                                       Sol işlenen bir struct, Kullan '.'                                       |
|                             [C28210](../code-quality/c28210.md)                             |                 Ek açıklamalar __on_failure bağlamının açık bağlam içinde olmamalıdır                  |
|                             [C28211](../code-quality/c28211.md)                             |                                 Statik bağlam adı SAL_context için bekleniyor                                  |
|                             [C28212](../code-quality/c28212.md)                             |                                  Ek açıklaması için beklenen işaretçi ifadesi                                   |
|                             [C28213](../code-quality/c28213.md)                             | \_Use_decl_annotations\_ ek açıklaması, değiştirilmeden önceki bildirime başvuru için kullanılmalıdır. |
|                             [C28214](../code-quality/c28214.md)                             |                                   Öznitelik parametre adları p1... olmalıdır p9                                   |
|                             [C28215](../code-quality/c28215.md)                             |                    Typefix zaten typefix'e sahip bir parametreye uygulanamaz                    |
|                             [C28216](../code-quality/c28216.md)                             |        CheckReturn ek açıklaması yalnızca belirli işlev parametresi için koşul sonralarına uygulanır.         |
|                             [C28217](../code-quality/c28217.md)                             |            İşlev için ek açıklama için parametre sayısı dosyada bulunanla eşleşmiyor.             |
|                             [C28218](../code-quality/c28218.md)                             |             İşlev parametresi için ek açıklamanın parametresi dosyada bulunanla eşleşmiyor.              |
|                             [C28219](../code-quality/c28219.md)                             |                 Ek açıklama parametresi ek açıklaması için beklenen numaralandırma üyesi                 |
|                             [C28220](../code-quality/c28220.md)                             |                  Tamsayı ifadesi parametre ek açıklaması içinde ek açıklaması için beklenen                   |
|                             [C28221](../code-quality/c28221.md)                             |                        AÇIKLAMADAKİ parametre için beklenen dize ifade                         |
|                             [C28222](../code-quality/c28222.md)                             |                               __yes, \__hayır, veya \_ek açıklaması için beklenen _maybe                               |
|                             [C28223](../code-quality/c28223.md)                             |                       Ek açıklaması için beklenen belirteç/tanımlayıcı bulunamadı parametresi                        |
|                             [C28224](../code-quality/c28224.md)                             |                                        Ek açıklama parametreleri gerektirir                                         |
|                             [C28225](../code-quality/c28225.md)                             |                     Açıklamada doğru sayıda gerekli parametre bulunamadı                      |
|                             [C28226](../code-quality/c28226.md)                             |                          Ek açıklama da aynı zamanda (geçerli bildirim içinde) PrimOp olamaz                          |
|                             [C28227](../code-quality/c28227.md)                             |                          Ek Açıklama aynı zamanda PrimOp olamaz (önceki bildirime bakın)                           |
|                             [C28228](../code-quality/c28228.md)                             |                             Ek açıklama parametresi: ek açıklamalarda tür kullanılamaz                              |
|                             [C28229](../code-quality/c28229.md)                             |                                    Ek açıklama parametreleri desteklemiyor                                     |
|                             [C28230](../code-quality/c28230.md)                             |                                     Parametresinin türü üyesi yok.                                      |
|                             [C28231](../code-quality/c28231.md)                             |                                       Ek açıklama yalnızca dizede geçerlidir                                       |
|                             [C28232](../code-quality/c28232.md)                             |                               Ön, sonrası veya herhangi bir ek açıklamaya uygulanmamıştır                               |
|                             [C28233](../code-quality/c28233.md)                             |                                    Ön, sonrası veya bir bloğa uygulanır                                     |
|                             [C28234](../code-quality/c28234.md)                             |                              __at ifadesi geçerli işleve uygulanmıyor                               |
|                             [C28235](../code-quality/c28235.md)                             |                               İşlev bir ek açıklama olarak tek başına duramaz.                                |
|                             [C28236](../code-quality/c28236.md)                             |                                Ek açıklama bir ifadede kullanılamaz                                 |
|                             [C28237](../code-quality/c28237.md)                             |                              Parametre üzerindeki ek açıklama artık desteklenmiyor                               |
|                             [C28238](../code-quality/c28238.md)                             |      Parametre üzerindeki ek açıklama birden fazla değer, stringValue ve longValue sahiptir. Kullanma paramn = xxx       |
|                             [C28239](../code-quality/c28239.md)                             |  Parametre üzerindeki ek açıklama hem değer, stringValue veya longValue vardır; ve paramn = xxx. Kullanma yalnızca paramn = xxx   |
|                             [C28240](../code-quality/c28240.md)                             |                             Parametre üzerindeki ek açıklama param2 ancak param1 yok                              |
|                             [C28241](../code-quality/c28241.md)                             |                          Parametre üzerindeki işlev için ek açıklama tanınmıyor                           |
|                             [C28243](../code-quality/c28243.md)                             |   Daha fazla parametre üzerindeki işlev gerektirir asıl türün izin verdiğinden başvuru   |
|                             [C28245](../code-quality/c28245.md)                             |                     İşlevi için ek açıklama 'this' bir olmayan üye işlev üzerinde açıklama ekler                     |
|                             [C28246](../code-quality/c28246.md)                             |                İşlev için parametre ek açıklama, parametre türü eşleşmiyor.                 |
|                             [C28250](../code-quality/c28250.md)                             |                    İşlev için tutarsız ek açıklama: önceki örnek hatalı.                     |
|                             [C28251](../code-quality/c28251.md)                             |                       İşlev için tutarsız ek açıklama: Bu örnek hatalı.                       |
|                             [C28252](../code-quality/c28252.md)                             |           İşlev için tutarsız ek açıklama: parametre başka ek açıklamalara Bu örneği üzerinde sahip.           |
|                             [C28253](../code-quality/c28253.md)                             |           İşlev için tutarsız ek açıklama: parametre başka ek açıklamalara Bu örneği üzerinde sahip.           |
|                             [C28254](../code-quality/c28254.md)                             |                               ek açıklamalarda dynamic_cast <> (') desteklenmiyor                                |
|                             [C28262](../code-quality/c28262.md)                             |                    İşlevi, ek açıklaması için Ek açıklamada bir söz dizimi hatası bulundu                     |
|                             [C28263](../code-quality/c28263.md)                             |                 İç ek açıklaması için koşullu Ek açıklamada bir söz dizimi hatası bulundu                 |
|       [C28264](http://msdn.microsoft.com/en-us/bf6ea983-a06e-4752-a042-747a7dbf338c)        |                                    Sonuç listesi değerlerini sabit olması gerekir.                                     |
|                             [C28267](../code-quality/c28267.md)                             |                    Açıklamalarda bir söz dizimi hatası, ek açıklama işlevi bulunamadı.                    |
|                             [C28272](../code-quality/c28272.md)                             |      İşlev için ek açıklama, incelerken parametresi işlev bildirimiyle tutarsız      |
|                             [C28273](../code-quality/c28273.md)                             |                    İşlev için ipuçları işlev bildirimiyle tutarsız                     |
|                             [C28275](../code-quality/c28275.md)                             |                                   Parametre \_Macro_value\_ null                                    |
|                             [C28279](../code-quality/c28279.md)                             |                           Simge için bir 'begin' bir 'end'olmadan ' bulundu                            |
|                             [C28280](../code-quality/c28280.md)                             |                           Sembol için bir 'end' eşleşmeyen bir 'begin' bulundu                           |
|                             [C28282](../code-quality/c28282.md)                             |                                    Biçim dizeleri önkoşullarda olmalıdır                                    |
|                             [C28285](../code-quality/c28285.md)                             |                                    İşlev için parametrede söz dizimi hatası                                    |
|                             [C28286](../code-quality/c28286.md)                             |                                    İşlevi, sonunun yakınında sözdizimi hatası                                    |
|                             [C28287](../code-quality/c28287.md)                             |                İşlev için söz dizimi hatası, \_adresindeki\_() ek açıklama (tanınmayan parametre adı)                |
|                             [C28288](../code-quality/c28288.md)                             |                  İşlev için söz dizimi hatası, \_adresindeki\_() ek açıklama (geçersiz parametre adı)                   |
|                             [C28289](../code-quality/c28289.md)                             |                İşlevi için: ReadableTo veya WritableTo parametre olarak bir limit-spec'e sahip değil                |
|                             [C28290](../code-quality/c28290.md)                             |           işlevi için ek açıklama gerçek parametre sayısından daha fazla External içeriyor            |
|                             [C28291](../code-quality/c28291.md)                             |                        POST null/notnull deref düzeyi 0 işlevi için anlamsız olur.                        |
|                             [C28300](../code-quality/c28300.md)                             |                            İşleci için uyumsuz olan türlerde ifade işlenenleri                             |
|                             [C28301](../code-quality/c28301.md)                             |                               İşlevin ilk bildirimi için hiçbir ek açıklama.                               |
|                             [C28302](../code-quality/c28302.md)                             |                             Ek \_Deref\_ üzerindeki ek açıklama işleci bulundu.                              |
|                             [C28303](../code-quality/c28303.md)                             |                           Belirsiz \_Deref\_ üzerindeki ek açıklama işleci bulundu.                            |
|                             [C28304](../code-quality/c28304.md)                             |                     Yanlış yerleştirilmiş bir \_Notref\_ belirtece uygulanan işleci bulundu.                      |
|                             [C28305](../code-quality/c28305.md)                             |                                Bir belirteç ayrıştırılırken bir hata Keşfedildi.                                 |
|                             [C28350](../code-quality/c28350.md)                             |                  Ek açıklama koşullu olarak uygun olmayan bir durumu betimliyor.                   |
|                             [C28351](../code-quality/c28351.md)                             |         Ek açıklama bir dinamik değerin (değişkenin) koşulda burada kullanılamaz açıklar.          |
|  [CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)  |                             Atılabilir alanlara sahip türler atılabilir olmalıdır                             |
|                 [CA1821](../code-quality/ca1821-remove-empty-finalizers.md)                 |                                            Boş Sonlandırıcıları kaldırın                                            |
|          [CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)           |                                     Atılabilen alanlar atılmalıdır                                      |
| [CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) |                            Eşittir işlecini ValueType.equals'ı geçersiz kılarak üzerinde                            |

