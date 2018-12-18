---
title: 'Nasıl yapılır: oluşturma ve çalıştırma LinqToXmlDataBinding örneği | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3943deaf-80e2-4968-ac04-d3ef56cfad6c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9e299000cd8477ccc36829e806072cb25e115f8f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237919"
---
# <a name="how-to-build-and-run-the-linqtoxmldatabinding-example"></a>Nasıl yapılır: oluşturma ve çalıştırma LinqToXmlDataBinding örneği
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu nasıl oluşturulup LinqToXmlDataBinding Visual Studio projeyi oluşturun ve elde edilen LinqToXmlDataBinding Windows Presentation Foundation (WPF) örnek program çalıştırma gösterir.  
  
 Projeleri oluşturmak için Visual Studio'yu kullanma hakkında daha fazla bilgi için bkz. [Visual Studio'da uygulama geliştirme](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68).  
  
## <a name="creating-and-populating-the-project"></a>Oluşturma ve proje doldurma  
  
#### <a name="to-create-the-starting-project"></a>Başlangıç projesi oluşturmak için  
  
1.  Visual Studio'yu başlatın ve LinqToXmlDataBinding adlı bir C# WPF uygulaması oluşturun. Proje .NET Framework 3.5 (veya sonraki sürümler) kullanmanız gerekir.  
  
2.  Aksi halde aşağıdaki .NET derlemeleri için zaten mevcut proje başvurularını ekleyin:  
  
    -   System.Data  
  
    -   System.Data.DataSetExtensions  
  
    -   System.Xml  
  
    -   System.Xml.Linq  
  
3.  Basarak çözümü oluşturun **Ctnrl + Shift + B**, çalıştırın tuşlarına basarak **F5**. Projenin hatasız derleyip genel WPF uygulaması çalıştırın.  
  
#### <a name="to-add-custom-code-to-the-project"></a>Özel kod projesine eklemek için  
  
1.  Çözüm Gezgini'nde, L2XDBForm.xaml için gt;Window1.XAML kaynak dosyayı yeniden adlandırın. Bağımlı kaynak dosyası Window1.xaml.cs L2XDBForm.xaml.cs için otomatik olarak adlandırılmamalıdır.  
  
2.  Kaynak kod bulunamadı ' % s'dosyasında L2XDBForm.xaml konusunun kod ile değiştirin [L2DBForm.xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md). (Bu dosyayla çalışmak için XAML kaynak görünümünü kullanın.)  
  
3.  Benzer şekilde, L2XDBForm.xaml.cs kaynakta bulunan kod yerine [L2DBForm.xaml.cs kaynak kodu](../designers/l2dbform-xaml-cs-source-code.md).  
  
4.  App.xaml dosyasında "L2XDBForm.xaml" ile "gt;Window1.XAML" dizesinin tüm örnekleri değiştirin.  
  
5.  Çözüm tuşlarına basarak derleme **Ctrl + Shift + B**.  
  
## <a name="running-the-program"></a>Programı çalıştırma  
 LinqToXmlDataBinding program görüntülemek ve gömülü bir XML öğesi olarak depolanan kitap listesi işlemek kullanıcının sağlar.  
  
#### <a name="to-run-the-program-and-view-the-book-list"></a>Programı çalıştırın ve kitap listesi görüntülemek için  
  
1.  LinqToXmlDataBinding basarak çalıştırın **F5** (**hata ayıklamayı Başlat**) veya **Ctrl + F5** (**hata ayıklama olmadan Başlat**). Başlık program penceresiyle **LINQ to XML kullanarak WPF verilerini bağlama** görüntülenmesi gerekir.  
  
2.  Dosyanın üst kısmında ham görüntüler UI fark **XML** temsil eden kitap listesi. WPF kullanarak görüntülenir <xref:System.Windows.Controls.TextBlock> denetimi, klavye ve fare aracılığıyla etkileşim etkinleştirmez.  
  
3.  Etiketli ikinci dikey bölümde **kitap listesi**, görüntüler books düz metin olarak sıralı listesi. Bunu kullanan bir <xref:System.Windows.Controls.ListBox> klavye ve fare seçimi ancak etkinleştiren denetimi.  
  
#### <a name="to-add-and-delete-books-from-the-list"></a>Ekleme ve Kitaplar listeden silme  
  
1.  Mevcut bir kitap listeden silmek için onu seçip **kitap listesi** bölümünde'a tıklayın **seçili kitap kaldırmak** düğmesi. Kitap hem ham XML kaynak listelerini defteri girdisi kaldırıldı dikkat edin.  
  
2.  Yeni bir kitap listeye eklemek için değerlerini girin. **kimliği** ve **değeri** <xref:System.Windows.Controls.TextBox> son bölümüne denetimler **yeni kitabı ekleme**,'a tıklayın **Ekle Kitap** düğmesi. Not Defteri kitap ve XML listelerini listesine eklenir. Bu program, giriş değerleri doğrulamaz.  
  
#### <a name="to-edit-an-existing-book-entry"></a>Bir kitap girişi düzenlemek için  
  
1.  İkinci defteri girdisini seçin **kitap listesi** bölümü. Geçerli değerleri üçüncü bölümünde görüntülenip **seçili kitap Düzenle**.  
  
2.  Klavyeyi kullanarak değerleri düzenleyin. Kapanmaz <xref:System.Windows.Controls.TextBox> denetim odağı kaybettiğinde, değişiklikleri otomatik olarak XML kaynak ve kitap listelerini yayılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to XML örneği kullanarak WPF verilerini bağlama](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [İzlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Visual Studio'da uygulama geliştirme](http://msdn.microsoft.com/en-us/97490c1b-a247-41fb-8f2c-bc4c201eff68)



