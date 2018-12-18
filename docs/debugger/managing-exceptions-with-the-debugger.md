---
title: Özel durumları hata ayıklayıcısı ile yönetme | Microsoft Docs
ms.custom: seodec18
ms.date: 10/09/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions
- vs.debug.exceptions.find
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors
- exception handling, during debugging
- errors [debugger]
- debugger, runtime errors
- On Error-style error handlers
- exceptions, Win32
- run-time errors, debugging
- Win32, exceptions
- run time, exceptions
- error handling
- debugging [Visual Studio], exception handling
- common language runtime, exceptions
- native run-time checks
- exceptions, debugging
ms.assetid: 43a77fa8-37d0-4c98-a334-0134dbca4ece
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 02c7fbfca9a63ac736972ebea01a854e24f90188
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057924"
---
# <a name="manage-exceptions-with-the-debugger-in-visual-studio"></a>Özel durumlar Visual Studio hata ayıklayıcısı ile yönetme

Bir özel durum bir program yürütüldüğü sırada gerçekleşen bir hata durumu göstergesidir. Hangi özel durumları veya kesmek için özel durumlar, kümeleri, hata ayıklayıcı söyleyebilirsiniz ve hangi noktada hata ayıklayıcının istersiniz. Hata ayıklayıcı keserse, size burada özel durumun oluştuğu gösterir. Ayrıca, ekleyin veya özel durumları silebilirsiniz. Çözümünü Visual Studio'da Aç **hata ayıklama > Windows > özel durum ayarları** açmak için **özel durum ayarları** penceresi.

Yanıt için en önemli özel durum işleyicileri sağlar. Ayrıca her zaman yürütme bazı özel durumlar için hata ayıklayıcının yapılandırmayı öğrenin.

Bir özel durum oluştuğunda, hata ayıklayıcı bir özel durum iletisi Yazar **çıkış** penceresi. Aşağıdaki yürütme kesilebilir ne zaman durumlarda:

- İşlenmez bir özel durum.
- Hata ayıklayıcı herhangi bir işleyici çağrılmadan önce yürütmeyi kesmek için yapılandırılır.
- Ayarladığınız [yalnızca kendi kodum](../debugger/just-my-code.md), ve hata ayıklayıcının kullanıcı kodunda işlenmez herhangi bir özel kesmek için yapılandırılır.

> [!NOTE]
> ASP.NET hata sayfalarını bir tarayıcıda gösteren bir üst düzey özel durum işleyicisine sahiptir. Bu sürece yürütme sonu gelmez **yalnızca kendi kodum** açıktır. Bir örnek için bkz. [kullanıcının işlemediği özel durumları devam etmek için hata ayıklayıcının işlemi durdurmasını](#BKMK_UserUnhandled) aşağıda.

<!-- Two consecutive notes are intentional here...-->

> [!NOTE]
> Üzerinde hata stili hata işleyicilerini kullansanız bile, bir Visual Basic uygulamasında hata ayıklayıcı tüm hataları özel durumlar olarak yönetir.

## <a name="tell-the-debugger-to-break-when-an-exception-is-thrown"></a>Bir özel durum oluştuğunda hata ayıklayıcının söyleyin

Bir işleyici çağrılmadan önce özel durumu inceleyebilirsiniz. Bu nedenle, hata ayıklayıcı burada bir özel durum, bir noktada yürütmeyi kesebilirsiniz.

İçinde **özel durum ayarları** penceresi (**hata ayıklama > Windows > özel durum ayarları**), özel durumlar kategorisi için düğümü genişletin **ortak dil çalışma zamanı özel durumları**. O kategorideki belirli bir özel durum için onay kutusu gibi seçip **System.AccessViolationException**. Bir tüm özel durumlar kategorisi belirleyebilirsiniz.

![AccessViolationException işaretli](../debugger/media/exceptionsettingscheckaccess.png "ExceptionSettingsCheckAccess")

> [!TIP]
> Belirli özel durumları kullanarak bulabilirsiniz **arama** penceresinde **özel durum ayarları** araç çubuğunu veya kullanım için belirli ad alanlarını filtrelemek için arayın (gibi **System.IO**).

Bir özel durum seçerseniz **özel durum ayarları** penceresi, hata ayıklayıcı yürütme özel durumun, olup, işlendiğini ne olursa olsun her yerde bozar. Artık özel durum bir ilk fırsat özel durum olarak adlandırılır. Örneğin, birkaç senaryo şunlardır:

- Aşağıdaki C# konsol uygulamasında, Main yöntemi oluşturur bir **AccessViolationException** içinde bir `try/catch` blok.

  ```csharp
  static void Main(string[] args)
  {
      try
      {
          throw new AccessViolationException();
          Console.WriteLine("here");
      }
      catch (Exception e)
      {
          Console.WriteLine("caught exception");
      }
      Console.WriteLine("goodbye");
  }
  ```

  Varsa **AccessViolationException** iade **özel durum ayarları**, yürütme bozar `throw` bu kodu hata ayıklayıcıda çalıştırdığınızda satır. Ardından, yürütme devam edebilirsiniz. Konsol, iki satır görüntülenmesi gerekir:

  ```cmd
  caught exception
  goodbye
  ```

  Ancak, görüntülemez `here` satır.

- Bir C# konsol uygulaması iki yöntem sahip bir sınıf ile bir sınıf kitaplığı başvuruyor. Bir yöntem, bir özel durum oluşturur ve ikinci yöntem aynı özel durum oluşturur, ancak bunu işlemiyor, işler.

  ```csharp
  public class Class1
  {
      public void ThrowHandledException()
      {
          try
          {
              throw new AccessViolationException();
          }
          catch (AccessViolationException ave)
          {
              Console.WriteLine("caught exception" + ave.Message);
          }
      }

      public void ThrowUnhandledException()
      {
          throw new AccessViolationException();
      }
  }
  ```

  Konsol uygulaması Main() yöntemi aşağıda verilmiştir:

  ```csharp
  static void Main(string[] args)
  {
      Class1 class1 = new Class1();
      class1.ThrowHandledException();
      class1.ThrowUnhandledException();
  }
  ```

  Varsa **AccessViolationException** iade **özel durum ayarları**, yürütme bozar `throw` hem de satır **ThrowHandledException()** ve **ThrowUnhandledException()** çalıştırdığınızda bu kodu hata ayıklayıcıda.

Özel durum ayarlarını varsayılan ayarlara geri yüklemek için seçin **listeyi varsayılan ayarlara geri** düğmesi:

![Özel durum Ayarları'nda Varsayılanları Geri Yükle](../debugger/media/restoredefaultexceptions.png "RestoreDefaultExceptions")

## <a name="BKMK_UserUnhandled"></a>Kullanıcı tarafından işlenmeyen özel durumları devam etmek için hata ayıklayıcının işlemi durdurmasını

.NET veya JavaScript kodu ile hata ayıklaması yapıyorsanız [yalnızca kendi kodum](../debugger/just-my-code.md), başka bir yerde işlenir ancak kullanıcı kodunda işlenmeyen özel durumlar üzerinde kesme önlemek için hata ayıklayıcı söyleyebilirsiniz.

1. İçinde **özel durum ayarları** penceresinde bir sütun etiketi sağ tıklayarak kısayol menüsünü açın ve ardından **Sütunları Göster > Ek Eylemler**. (Devre dışı açtıysanız **yalnızca kendi kodum**, bu komut görmezsiniz.) Adlı üçüncü bir sütunda **ek eylemler** görünür.

   ![Ek Eylemler sütunundaki](../debugger/media/additionalactionscolumn.png "AdditionalActionsColumn")

   Gösteren bir özel durum için **kullanıcı kodunda işlenmediğinde devam** hata ayıklayıcı bu sütunda, bu özel durum kullanıcı kodunda işlenmez, ancak harici olarak işlenir devam eder.

2. Belirli bir özel durum için bu ayarı değiştirmek için özel durum seçin, kısayol menüsünü göstermek için sağ tıklatın ve seçin **devam yaparken işlenmemiş kullanıcı kodunda**. Siz de tüm ortak dil çalışma zamanı özel durumları gibi özel durumların tamamını bir kategori ayarı değişebilir).

   ![** Kullanıcı kodu ** ayarını işlenmediğinde devam et](../debugger/media/continuewhenunhandledinusercodesetting.png "ContinueWhenUnhandledInUserCodeSetting")

Örneğin, ASP.NET web uygulamaları için bir HTTP 500 durum kodu dönüştürerek özel durumları işleme ([ASP.NET Web API'SİNDE özel durum işleme](http://www.asp.net/web-api/overview/error-handling/exception-handling)), hangi değil yardımcı olabilir, özel durumun kaynağı belirlemek. Aşağıdaki örnekte, kullanıcı kodu çağrıda `String.Format()` oluşturan bir <xref:System.FormatException>. Yürütme aşağıdaki gibi ayırır:

![Kullanıcı keser&#45;işlenmeyen özel durum](../debugger/media/exceptionunhandledbyuser.png "ExceptionUnhandledByUser")

## <a name="add-and-delete-exceptions"></a>Ekleme ve özel durumları silme

Ekleme ve özel durumları silebilirsiniz. Bir kategoriye bir özel durum türünü silmek için özel durum seçip seçin **seçili özel durumu listeden silin** düğmesine (eksi işareti) **özel durum ayarları** araç çubuğu. Özel durum sağ tıklatın ve seçin **Sil** kısayol menüsünden. Bir özel durum silme, hata ayıklayıcı bu durum oluştuğunda kesme olmaz denetlenmeyen, özel durum olarak aynı etkiye sahiptir.

Bir özel durum eklemek için:

1. İçinde **özel durum ayarları** penceresinde özel durum kategorileri birini seçin (örneğin, **ortak dil çalışma zamanı**).

2. Seçin **Seçili kategoriye bir özel durum ekleyin** (artı) düğmesini.

   ![** Ekle bir özel durum seçilen kategori ** düğmesine](../debugger/media/addanexceptiontotheselectedcategorybutton.png "AddAnExceptionToTheSelectedCategoryButton")

3. Özel durumun adını yazın (örneğin, **System.UriTemplateMatchException**).

   ![Özel durum adı](../debugger/media/typetheexceptionname.png "TypeTheExceptionName")

   Özel durum listesine (alfabetik sırada) eklenir ve otomatik olarak işaretli.

GPU bellek erişimi özel durumlarını, JavaScript çalışma zamanı özel durumları veya Win32 özel durumlar kategorisi için bir özel durum ekleyin hata kodu ve açıklama ekleyin.

> [!TIP]
> İmlanızı kontrol edin! **Özel durum ayarları** penceresini değil eklenen bir özel durum varlığını denetleyin. Yazarsanız, bu nedenle **Sytem.UriTemplateMatchException**, bir giriş için başka bir özel durum alırsınız (için **System.UriTemplateMatchException**).

Bunlar için belirli bir çözümü uygulamak için özel durum ayarları çözümün .suo dosyasında kalır. Belirli bir özel durum ayarları çözümlerinde yeniden kullanamazsınız. Eklenen özel durumlar artık kalıcıdır; Silinen bir özel durum değil. Bir özel durum, yakın eklediğinizde ve çözümü yeniden açın ve özel durum kalmaya devam eder. Ancak, bir özel durum silin ve çözümü Kapat/yeniden, özel durum yeniden görünür.

**Özel durum ayarları** penceresi, C# ancak Visual Basic'de genel özel durum türlerini destekler. Özel durumlar gibi kesmek `MyNamespace.GenericException<T>`, özel durum olarak eklemelisiniz **MyNamespace.GenericException'1**. Diğer bir deyişle, bu kodu gibi bir özel durum oluşturulduktan sonra:

```csharp
public class GenericException<T> : Exception
{
    public GenericException() : base("This is a generic exception.")
    {
    }
}
```

Özel durum ekleyebilirsiniz **özel durum ayarları** önceki yordamı kullanarak:

![Genel özel durumu ekleniyor](../debugger/media/addgenericexception.png "AddGenericException")

## <a name="add-conditions-to-an-exception"></a>Bir özel durum koşulları ekleme

Kullanım **özel durum ayarları** penceresinde koşulları özel durumlarını ayarlama. Şu anda desteklenen koşullar dahil etmek veya hariç tutmak için bir özel durum için modül adlarını içerir. Modül adlarını koşul olarak ayarlayarak, yalnızca belirli kod modülleri üzerinde özel durum için kesme seçebilirsiniz. Belirli modüller hakkında en son önlemek seçebilirsiniz.

> [!NOTE]
> Bir özel durum koşulları ekleme yeni [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Koşullu özel durumlar eklemek için:

1. Seçin **koşulları Düzenle** düğmesi özel durum Ayarları penceresinde veya özel durum'ı sağ tıklatın ve seçin **koşulları Düzenle**.

   ![Bir özel durum koşullarını](../debugger/media/dbg-conditional-exception.png "DbgConditionalException")

2. Özel durum için gerekli olan ek koşullar eklemek için seçin **koşul Ekle** yeni her koşul için. Ek koşul satılar görünür.

   ![Ek koşullar için bir özel durum](../debugger/media/extraconditionsforanexception.png "ExtraConditionsForAnException")

3. Koşul her satır için modül adını yazın ve karşılaştırma işleci listeye değiştirmek **eşittir** veya **eşit değildir**. Joker karakterler belirtebilirsiniz (**\\***) birden çok modül belirtmek için bir ad.

4. Bir koşulu silmek istiyorsanız seçin **X** koşul satırın sonunda.

## <a name="see-also"></a>Ayrıca bkz.

[Özel durumdan sonra yürütmeye devam etme](../debugger/continuing-execution-after-an-exception.md)<br/>
[Nasıl yapılır: Özel durumdan sonra sistem kodunu inceleme](../debugger/how-to-examine-system-code-after-an-exception.md)<br/>
[Nasıl yapılır: Yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)<br/>
[C çalışma zamanı kitaplığını kullanmadan çalışma zamanı denetimlerini kullanma](../debugger/using-run-time-checks-without-the-c-run-time-library.md)<br/>
[Öğretici: Visual Studio kullanarak hata ayıklamayı öğrenin](../debugger/getting-started-with-the-debugger.md)
