---
title: 'İş Akışı Tasarımcısı - nasıl yapılır: tanımlama ve etkinlik temsilcileri kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 32546f551972cf97779e0828d8c47c9c892d39bf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916368"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Nasıl yapılır: tanımlama ve iş akışı tasarımcısında etkinlik temsilcileri kullanma

.NET framework 4.5 içeren bir kullanıma hazır Tasarımcı için <xref:System.Activities.Statements.InvokeDelegate> etkinlik. Bu tasarımcı, türetilen etkinlik temsilcileri atamak için kullanılabilir <xref:System.Activities.ActivityDelegate>, gibi <xref:System.Activities.ActivityAction> veya <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Bir etkinlik temsilci tanımlama

1. Visual Studio'da **dosya** > **yeni** > **proje**.

2. İçinde **yeni proje** iletişim kutusunda **iş akışı** solda, kategori seçip **iş akışı konsol uygulaması** proje şablonu. (İstenirse) Projeyi adlandırın ve tıklayın **Tamam**.

   > [!NOTE]
   > Görmüyorsanız **iş akışı** kategori, ilk yükleme **Windows Workflow Foundation** Visual Studio 2017'in bileşeni. Ayrıntılı yönergeler için bkz. [Windows Workflow Foundation'ı yükleme](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Projeye sağ tıklayarak **Çözüm Gezgini** seçip **Ekle** > **yeni öğe**. Seçin **iş akışı** kategori tıklayın ve ardından **etkinlik** öğe şablonu. Yeni Etkinlik adı **MyForEach.xaml** seçip **Tamam**.

   Etkinlik iş akışı Tasarımcısı'nda açılır.

4. İş Akışı Tasarımcısı'nda tıklatın **bağımsız değişkenleri** sekmesi.

5. Tıklayın **bağımsız değişken oluşturma**. Yeni bağımsız değişken adı **öğeleri**.

6. İçinde **bağımsız değişken türü** sütunundaki **[T] dizi**.

7. Tür tarayıcıda seçin **nesne** seçip **Tamam**.

8. Tıklayın **bağımsız değişken oluşturma** yeniden. Yeni bağımsız değişken adı **gövdesi**. İçinde **yönü** yeni bağımsız değişken için seçim sütunu **özelliği**.

9. Bağımsız değişken türü sütununda seçin **vyhledat Typy**

10. Tür tarayıcıya girmek **ActivityAction** içinde **tür adı** alan. Seçin **ActivityAction\<T >** ağaç görünümünde. Seçin **nesne** atamak üzere görünen açılan menüdeki **ActivityAction\<Nesne >** bağımsız değişkeni.

11. Sürükleme bir <xref:System.Activities.Statements.While> etkinliğinden **akış denetimi** bölümünü araç Tasarımcı yüzeyine bırakın.

12. Seçin <xref:System.Activities.Statements.While> etkinliği ve select **değişkenleri** sekmesi.

13. Seçin **değişken oluşturma**. Yeni değişken **dizin**.

14. İçinde **değişken türü** sütunundaki **Int32**. Bırakın **kapsam** olarak **sırada**ve **varsayılan** sütunu boş.

15. Ayarlama **koşul** özelliği <xref:System.Activities.Statements.While> etkinliğini **dizini < Items.Length;**.

16. Sürükleme bir <xref:System.Activities.Statements.InvokeDelegate> etkinliğinden **Temelleri** araç kutusuna bölümünü **gövdesi** , <xref:System.Activities.Statements.While> etkinlik.

17. Seçin **gövdesi** temsilci açılan.

18. İçinde **özellikleri** için kılavuz <xref:System.Activities.Statements.InvokeDelegate> etkinliği tıklatın **...**  düğmesine **temsilci bağımsız değişkenleri** özelliği.

19. İçinde **değer** adlı bağımsız değişkenin sütun **bağımsız değişken**, girin **öğeleri [dizin]**. Tıklayın **Tamam** kapatmak için **DelegateArguments** iletişim.

20. Sürükleme bir <xref:System.Activities.Statements.Assign> etkinlik altında yatay çizgi üzerine <xref:System.Activities.Statements.InvokeDelegate> etkinlik. <xref:System.Activities.Statements.Assign> Etkinlik oluşturulur ve <xref:System.Activities.Statements.Sequence> etkinlik otomatik olarak oluşturulur iki etkinliklerini içermesini **gövdesi** bölümünü **MyForEach** etkinlik. Bu yana dizisi gerekli **gövdesi** bölümü yalnızca tek bir etkinlik içermelidir. Otomatik olarak yeni bir oluşturma <xref:System.Activities.Statements.Sequence> etkinliği, .NET Framework 4.5, yeni bir özelliktir.

21. Ayarlama **için** özelliği <xref:System.Activities.Statements.Assign> etkinliğini **dizin**. Ayarlama **değer** özelliği **atama** etkinliğini **dizini + 1**.

    Özel **MyForEach** etkinliği çağırır içine geçirilen her değerin bir kez rastgele bir etkinlik **öğeleri** etkinliği için girdi olarak toplama değerleri koleksiyonu.

## <a name="use-the-custom-activity-in-a-workflow"></a>Bir iş akışında özel etkinlik kullanma

1.  Tuşuna basarak projeyi oluşturun **Ctrl**+**Shift**+**B**.

2.  İçinde **Çözüm Gezgini**açın **Workflow1.xaml** Tasarımcısı'nda.

3.  Sürükleme bir **MyForEach** araç kutusundan bir etkinlik Tasarımcı yüzeyine bırakın. Araç kutusu projeyle aynı ada sahip bir bölümünde bir etkinliktir.

4.  Ayarlama **öğeleri** özelliği **MyForEach** etkinliğini **yeni Object [] {1, "abc"}**.

5.  Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğinden **Temelleri** araç kutusuna bölümünü **temsilci: gövdesi** bölümünü **MyForEach** etkinlik.

6.  Ayarlama **metin** özelliği <xref:System.Activities.Statements.WriteLine> etkinliğini **Argument.ToString()**.

İş akışı yürütüldüğünde, konsol aşağıdaki çıktıyı gösterir:

**1**
**abc**