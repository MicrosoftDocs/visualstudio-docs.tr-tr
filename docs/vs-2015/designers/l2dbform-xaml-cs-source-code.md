---
title: L2DBForm.xaml.cs kaynak kodu | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6ac13d8998972ddf60576537f8b0af55d832d820
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817544"
---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs kaynak kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, içeriği ve C# kaynak kodu dosyasında L2DBForm.xaml.cs açıklamasını içerir. Bu dosyada bulunan L2XDBForm kısmi sınıf üç mantıksal bölümlere ayrılabilir: veri üyeleri ve `OnRemove` ve `OnAddBook` düğme tıklama olay işleyicileri.  
  
## <a name="data-members"></a>Veri üyeleri  
 İki özel veri üyeleri, bu sınıf L2DBForm.xaml içinde kullanılan pencere kaynaklara ilişkilendirmek için kullanılır.  
  
-   Ad alanı değişkeni `myBooks` değerine ayarlanır `"http://www.mybooks.com"`.  
  
-   Üye `bookList` L2DBForm.xaml CDATA dizesinde aşağıdaki satırı ile oluşturucu içinde başlatılır:  
  
    ```  
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
    ```  
  
## <a name="onaddbook-event-handler"></a>OnAddBook olay işleyicisi  
 Bu yöntem, aşağıdaki üç deyimi içerir:  
  
-   İlk koşul deyimi, giriş doğrulaması için kullanılır.  
  
-   İkinci deyim yeni bir oluşturur <xref:System.Xml.Linq.XElement> girilen kullanıcı dizesi değerleri **ekleme yeni kitabı** kullanıcı arabirimi (UI) bölümü.  
  
-   Son deyim L2DBForm.xaml veri sağlayıcısının bu yeni kitabı öğe ekler. Sonuç olarak, dinamik veri bağlama kullanıcı arabirimini otomatik olarak bu yeni bir öğe ile güncelleştirilir; Ek kullanıcı tarafından sağlanan kod gereklidir.  
  
## <a name="onremove-event-handler"></a>OnRemove olay işleyicisi  
 `OnRemove` İşleyicisidir daha karmaşık `OnAddBook` için iki nedenden dolayı işleyici. Ham XML korunan boşluk içerdiğinden, ilk olarak, satır başı eşleşen ayrıca rehberi girişiyle kaldırılması gerekir. İkinci bir kolaylık olarak olan silinmiş öğenin üzerinde olduğu, seçim listesinde önceki bir sıfırlanır.  
  
 Ancak seçilen kitap öğesi kaldırmanın çekirdek iş yalnızca iki deyim tarafından gerçekleştirilir:  
  
- İlk olarak, şu anda seçili öğeyi liste kutusunda ilişkili kitap öğesi alınır:  
  
  ```  
  XElement selBook = (XElement)lbBooks.SelectedItem;   
  ```  
  
- Ardından, bu öğe, veri sağlayıcısı'ndan silinir:  
  
  ```  
  selBook.Remove();  
  ```  
  
  Dinamik veri bağlama yeniden programın UI otomatik olarak güncelleştirilir sağlar.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
  
### <a name="code"></a>Kod  
  
```csharp  
using System;  
using System.Linq;  
using System.Collections;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.Text;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Input;  
using System.Xml;  
using System.Xml.Linq;  
  
namespace LinqToXmlDataBinding {  
    /// <summary>  
    /// Interaction logic for L2XDBForm.xaml  
    /// </summary>  
  
    public partial class L2XDBForm : System.Windows.Window   
    {  
        XNamespace mybooks = "http://www.mybooks.com";  
        XElement bookList;  
  
        public L2XDBForm()   
        {  
            InitializeComponent();  
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;  
        }  
  
        void OnRemoveBook(object sender, EventArgs e)   
        {  
            int index = lbBooks.SelectedIndex;  
            if (index < 0) return;  
  
            XElement selBook = (XElement)lbBooks.SelectedItem;  
            //Get next node before removing element.  
            XNode nextNode = selBook.NextNode;  
            selBook.Remove();  
  
            //Remove any matching newline node.  
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))  
            { nextNode.Remove(); }  
  
            //Set selected item.   
            if (lbBooks.Items.Count > 0)  
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }  
        }  
  
        void OnAddBook(object sender, EventArgs e)   
        {  
            if (String.IsNullOrEmpty(tbAddID.Text) ||  
                String.IsNullOrEmpty(tbAddValue.Text))  
            {  
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");  
                return;   
            }  
            XElement newBook = new XElement(  
                                mybooks + "book",  
                                new XAttribute("id", tbAddID.Text),  
                                tbAddValue.Text);  
            bookList.Add("  ", newBook, "\r\n");  
        }  
    }  
}  
  
```  
  
### <a name="comments"></a>Açıklamalar  
 Bu işleyiciler için ilişkili XAML kaynak için bkz. [L2DBForm.xaml kaynak kodu](../designers/l2dbform-xaml-source-code.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: LinqToXmlDataBinding örneği](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [L2DBForm.xaml Kaynak Kodu](../designers/l2dbform-xaml-source-code.md)



