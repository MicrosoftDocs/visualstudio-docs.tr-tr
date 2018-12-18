---
title: "İş Akışı Tasarımcısı - nasıl yapılır: değişken Tasarımcısı'nı kullanın"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc180df4a9be83c0f0b755bffd7ed40009b41497
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31970105"
---
# <a name="how-to-use-the-variable-designer"></a>Nasıl yapılır: değişken Tasarımcısı'nı kullanın

Değişken Tasarımcısı'nı kullanmak için değişkenler veri bağlama senaryoları ve koşullu deyimler oluşturmak için kullanılır. Tasarımcı tıklayarak erişilen **değişkenleri** tasarım tuvale sol alt köşesindeki düğmesi. Tasarımcı tablo biçiminde görünür ve her sütun üstbilgilerinin dışında sıralanabilir değişkenlerin listesini içeren **varsayılan** sütun. Her bir değişken adı, değişken türü, kapsamı ve varsayılan değer (varsa) içerir. Ad ve varsayılan değer düzenlenebilir metin alanları, ve türüne ve kapsamına aşağı açılan listeler. Değişken Tasarımcısı çağrıldığında seçtiğiniz etkinlik kapsamıdır. Bir değişken seçimi kapsamı içinde oluşturulamaz, kapsam, kapsamında oluşturulan değişkenler izin veren Seçimi en yakın üst öğede etkinliğini varsayılır. Daha fazla bilgi için bkz: [değişkenleri ve bağımsız değişkenler (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 Kullanıcının açık olarak sıralama denetimleri birini kullanır, kapatır ve değişken Tasarımcısı'nı açana veya başka bir değişken oluşturur kadar sıralama düzenini uygulanmıyor.

## <a name="to-create-a-new-variable"></a>Yeni bir değişken oluşturmak için

1.  Bir iş akışı veya etkinlik çözümü Visual Studio'da açın.

2.  Tasarım tuval üzerinde bir etkinlik akışınıza seçin.

3.  Değişken Tasarımcısı'nı tıklatarak **değişkenleri** tasarım tuvale sol alt köşesindeki düğmesi. Değişken Tasarımcısı görünür.

4.  Etiketli boş satıra tıklayın **oluşturma değişken**. Bu aşağıdaki varsayılan değerleri kullanarak yeni bir değişken ile yeni bir satır ekler: variablex için **adı** x benzersiz değişken adları oluşturmak için otomatik olarak arttırılır 1 başlangıç değeri bir tamsayı olduğu  **Dize** için **değişken türü**, ve **dizisi** için **kapsam**. Herhangi bir değer için eklenen **varsayılan**. İş akışı tasarım işlemi sırasında herhangi bir zamanda bu değerleri değiştirebilirsiniz.

    > [!NOTE]
    > Bir değişkeni silmek için değişkeni tıklayarak seçin ve tuşuna basarak **silmek** anahtarı.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Nasıl Yapılır: Bağımsız Değişken Tasarımcısını Kullanma](../workflow-designer/how-to-use-the-argument-designer.md)