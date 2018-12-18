---
title: 'Nasıl yapılır: Varlık sınıflarına doğrulama ekleme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91600821b3d68c04382028e469a4e1a54a5d191c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812769"
---
# <a name="how-to-add-validation-to-entity-classes"></a>Nasıl yapılır: Varlık sınıflarına doğrulama ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
*Doğrulama* varlık sınıfları olan veri nesnelerine girilen değerlerin bir nesnenin şeması ve ayrıca uygulama için belirlenen kurallara kısıtlamalarıyla uyumlu onaylanması işlemidir. Alttaki veritabanına güncelleştirmeleri göndermeden önce verileri doğrulamak hataları azaltan iyi bir uygulamadır. Ayrıca, bir uygulama ve veritabanı arasındaki gidiş gelişlerin potansiyel sayısını da azaltır.  
  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md) , ekleme, güncelleştirme sırasında çalışan ve tüm varlıkların ve ayrıca sırasında ve sonrasında tek tek sütun siler tasarımcı tarafından oluşturulan kodu genişletme açmasına olanak tanıyan kısmi yöntemler sağlar değiştirir.  
  
> [!NOTE]
>  Bu konuda, kullanarak varlık sınıflarına doğrulama ekleme için temel adımlar sağlanır [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Bir varlığa sınıfa başvuruda bulunmadan genel adımları takip etmek zor olabilir çünkü kullanan gerçek veri izlenecek yollar sağlanmıştır.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Belirli bir sütundaki değer değişiklikleri için doğrulama ekleme  
 Bu yordamda, bir sütundaki değeri değiştiğinde verileri doğrulamak gösterilmiştir. Sınıf tanımı içinde doğrulama gerçekleştirildiğinden (yerine kullanıcı arabiriminde) değeri doğrulama başarısız olmasına neden olursa bir özel durum oluşturulur. Hata işleme için sütun değerlerini değiştirmeye çalışırsa, uygulamanızın kodunda uygulayın.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>Bir sütunun değeri değişikliği sırasında verileri doğrulamak için  
  
1. Yeni bir LINQ to SQL sınıfları dosyası oluşturun veya açın (**.dbml** dosya) içinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Çift **.dbml** dosyası **Çözüm Gezgini**.)  
  
2. O/R Tasarımcısı'nda doğrulama ekleyin ve ardından istediğiniz sınıfı sağ **kodu görüntüle**.  
  
    Seçilen varlık sınıfı için bir parçalı sınıf Kod Düzenleyicisi açılır.  
  
3. Kısmi class içinde imleci yerleştirin.  
  
4. Visual Basic projeleri için:  
  
   1. Genişletin **yöntem adı** listesi.  
  
   2. Bulun **üzerinde**_COLUMNNAME_**değiştirme** doğrulama eklemek istediğiniz sütun için yöntemi.  
  
   3. Bir `On` *COLUMNNAME* `Changing` yöntemi kısmi sınıfa eklenir.  
  
   4. İlk girilen değer ve ardından sütun için girilen değer emin olmak için uygulamanız için kabul edilebilir olduğunu doğrulamak için aşağıdaki kodu ekleyin. `value` Bağımsız değişken içeren önerilen değeri, bu nedenle bunun geçerli bir değer olduğunu doğrulamak için mantığı ekleyin:  
  
      ```vb  
      If value.HasValue Then  
          ' Add code to ensure that the value is acceptable.  
          ' If value < 1 Then  
          '    Throw New Exception("Invalid data!")  
          ' End If  
      End If  
      ```  
  
      C# projeleri için:  
  
   5. C# projelerini otomatik olarak olay işleyiciler oluşturmaz, çünkü sütun değiştirme kısmi yöntemler oluşturmak için IntelliSense'i kullanabilirsiniz.  
  
       Tür `partial` ve kullanılabilir kısmi yöntemlerin listesi erişmeye sonra bir boşluk. Doğrulama için eklemek istediğiniz sütunu için sütun değiştirme yöntemi tıklayın. Sütun değiştirme kısmi bir yöntem seçtiğinizde oluşturulan kodu aşağıdaki koda benzer:  
  
      ```csharp  
      partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
          {  
             throw new System.NotImplementedException();  
          }  
  
      ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Bir varlık sınıfı için güncelleştirmeleri için doğrulama ekleme  
 Değerleri değişiklik sırasında denetlemenin yanı sıra, tam varlık sınıfı güncelleştirilecek denemesi yapıldığında veri da doğrulayabilirsiniz. Doğrulama güncelleştirme girişimi sırasında iş kurallarını bu gerekiyorsa birden fazla sütundaki değerleri karşılaştırmak sağlar. Aşağıdaki yordam, tam varlık sınıfı güncelleştirilecek denemesi yapıldığında doğrulamak gösterilmektedir.  
  
> [!NOTE]
>  Doğrulama kodu güncelleştirmelerin varlık sınıfları tamamlamak kısmi yürütüldüğünde <xref:System.Data.Linq.DataContext> sınıfı (yerine bir varlığa sınıfın kısmi sınıftaki).  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Bir varlık sınıfı için bir güncelleştirme sırasında verileri doğrulamak için  
  
1. Yeni bir LINQ to SQL sınıfları dosyası oluşturun veya açın (**.dbml** dosya) içinde [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Çift **.dbml** dosyası **Çözüm Gezgini**.)  
  
2. O/R Tasarımcı üzerinde boş bir alana sağ tıklayıp **kodu görüntüle**.  
  
    Kısmi bir sınıf için kod düzenleyicisi açılır `DataContext`.  
  
3. Kısmi sınıf için imleci yerleştirin `DataContext`.  
  
4. Visual Basic projeleri için:  
  
   1. Genişletin **yöntem adı** listesi.  
  
   2. Tıklayın **güncelleştirme**_ENTITYCLASSNAME_.  
  
   3. Bir `Update` *ENTITYCLASSNAME* yöntemi kısmi sınıfa eklenir.  
  
   4. Kullanarak ayrı ayrı sütun değerlerine erişim `instance` bağımsız değişken, aşağıdaki kodda gösterildiği gibi:  
  
      ```vb  
      If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
          Dim ErrorMessage As String = "Invalid data!"  
          Throw New Exception(ErrorMessage)  
      End If  
      ```  
  
      C# projeleri için:  
  
   5. C# projelerini otomatik olarak olay işleyiciler oluşturmaz, çünkü kısmi oluşturmak için IntelliSense'i kullanabilirsiniz `Update` *CLASSNAME* yöntemi.  
  
   6. Tür `partial` ve kullanılabilir kısmi yöntemlerin listesi erişmeye sonra bir boşluk. Güncelleştirme yöntemi, doğrulama için eklemek istediğiniz sınıf için tıklayın. Seçeneğini belirlediğinizde oluşturulan kodu aşağıdaki koda benzer bir `Update` *CLASSNAME* kısmi yöntem:  
  
      ```csharp  
      partial void UpdateCLASSNAME(CLASSNAME instance)  
      {  
          if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
          {  
              string ErrorMessage = "Invalid data!";  
              throw new System.Exception(ErrorMessage);  
          }  
      }  
      ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL araçlarını Visual Studio'da](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Verileri doğrulama](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)

