---
title: 'Nasıl yapılır: tanımlama ve iş akışı tasarımcısında etkinlik temsilcileri kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f99816153870884f868a6b229068bdc281408337
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865498"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Nasıl yapılır: tanımlama ve iş akışı tasarımcısında etkinlik temsilcileri kullanma
[!INCLUDE[net_v45](../includes/net-v45-md.md)] için yeni bir out-of-box Tasarımcı içerir <xref:System.Activities.Statements.InvokeDelegate> etkinlik. Bu tasarımcı, türetilen etkinlik temsilcileri atamak için kullanılabilir <xref:System.Activities.ActivityDelegate>, gibi <xref:System.Activities.ActivityAction> veya <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Bir etkinlik temsilci tanımlama  
  
1. İçinde [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]seçin **dosya**, **yeni**, **proje**. Seçin **iş akışı** solda, düğüm ve **iş akışı konsol uygulaması** sağdaki şablonu. (İstenirse) Projeyi adlandırın ve tıklayın **Tamam**.  
  
2. Projeye sağ tıklayarak **Çözüm Gezgini** seçip **Ekle**, **yeni öğe...** . Seçin **iş akışı** solda, düğüm ve **etkinlik** sağdaki şablonu. Yeni Etkinlik adı **MyForEach.xaml** tıklatıp **Tamam**. Etkinlik iş akışı Tasarımcısı'nda açılır.  
  
3. İş Akışı Tasarımcısı'nda tıklatın **bağımsız değişkenleri** sekmesi.  
  
4. Tıklayın **bağımsız değişken oluşturma**. Yeni bağımsız değişken adı **öğeleri**.  
  
5. İçinde **bağımsız değişken türü** sütunundaki **[T] dizi**.  
  
6. Tür tarayıcıda seçin **nesne**. Tıklayın **Tamam**.  
  
7. Tıklayın **bağımsız değişken oluşturma** yeniden. Yeni bağımsız değişken adı **gövdesi**. İçinde **yönü** yeni bağımsız değişken için seçim sütunu **özelliği**.  
  
8. Bağımsız değişken türü sütununda seçin **vyhledat Typy...**  
  
9. Tür tarayıcıya girmek **ActivityAction** içinde **tür adı** alan. Seçin **ActivityAction\<T >** ağaç görünümünde. Seçin **nesne** atamak üzere görünen açılan menüdeki **ActivityAction\<Nesne >** bağımsız değişkeni.  
  
10. Sürükleme bir <xref:System.Activities.Statements.While> etkinliğinden **akış denetimi** bölümünü araç Tasarımcı yüzeyine bırakın.  
  
11. Seçin <xref:System.Activities.Statements.While> etkinliği ve select **değişkenleri** sekmesi.  
  
12. Seçin **değişken oluşturma**. Yeni değişken **dizin**.  
  
13. İçinde **değişken türü** sütunundaki **Int32**. Bırakın **kapsam** olarak **sırada**ve **varsayılan** sütunu boş.  
  
14. Ayarlama **koşul** özelliği <xref:System.Activities.Statements.While> etkinliğini **dizini < Items.Length;**.  
  
15. Sürükleme bir <xref:System.Activities.Statements.InvokeDelegate> etkinliğinden **Temelleri** araç kutusuna bölümünü **gövdesi** , <xref:System.Activities.Statements.While> etkinlik.  
  
16. Seçin **gövdesi** temsilci açılan.  
  
17. İçinde **özellikleri** için kılavuz <xref:System.Activities.Statements.InvokeDelegate> etkinliği tıklatın **...** düğmesini **temsilci bağımsız değişkenleri** özelliği.  
  
18. İçinde **değer** adlı bağımsız değişkenin sütun **bağımsız değişken**, girin **öğeleri [dizin]**. Tıklayın **Tamam** kapatmak için **DelegateArguments** iletişim.  
  
19. Sürükleme bir <xref:System.Activities.Statements.Assign> etkinlik altında yatay çizgi üzerine <xref:System.Activities.Statements.InvokeDelegate> etkinlik. <xref:System.Activities.Statements.Assign> Etkinlik oluşturulur ve <xref:System.Activities.Statements.Sequence> etkinlik otomatik olarak oluşturulur iki etkinliklerini içermesini **gövdesi** bölümünü **MyForEach** etkinlik. Bu yana dizisi gerekli **gövdesi** bölümü yalnızca tek bir etkinlik içermelidir. Otomatik olarak yeni bir oluşturma <xref:System.Activities.Statements.Sequence> yeni özelliği olan bir etkinliktir [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Ayarlama **için** özelliği <xref:System.Activities.Statements.Assign> etkinliğini **dizin**. Ayarlama **değer** özelliği **atama** etkinliğini **dizini + 1**.  
  
    Özel **MyForEach** etkinliği artık içine geçirilen her değerin bir kez rastgele bir etkinlik çağırma **öğeleri** etkinliği için girdi olarak toplama değerleri koleksiyonu.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Bir iş akışında özel etkinlik kullanma  
  
1. Tuşuna basarak projeyi oluşturun **Ctrl + Shift + B**.  
  
2. İçinde **Çözüm Gezgini**açın **Workflow1.xaml** Tasarımcısı'nda.  
  
3. Sürükleme bir **MyForEach** araç kutusundan bir etkinlik Tasarımcı yüzeyine bırakın. Etkinlik araç kutusunu projeyle aynı ada sahip bir bölümünde olacaktır.  
  
4. Ayarlama **öğeleri** özelliği **MyForEach** etkinliğini **yeni Object [] {1, "abc"}**.  
  
5. Sürükleme bir <xref:System.Activities.Statements.WriteLine> etkinliğinden **Temelleri** araç kutusuna bölümünü **temsilci: gövdesi** bölümünü **MyForEach** etkinlik.  
  
6. Ayarlama **metin** özelliği <xref:System.Activities.Statements.WriteLine> etkinliğini **Argument.ToString()**.  
  
   İş akışı yürütüldüğünde, konsolda şunu verecektir:  
  
   **1**   
   **abc**