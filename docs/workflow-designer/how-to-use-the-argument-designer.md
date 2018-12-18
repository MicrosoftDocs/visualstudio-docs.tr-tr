---
title: "İş Akışı Tasarımcısı - nasıl yapılır: bağımsız değişken Tasarımcısı'nı kullanın"
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 868fc13474e90be219cf1acebc00074641df142e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755528"
---
# <a name="how-to-use-the-argument-designer"></a>Nasıl yapılır: bağımsız değişken Tasarımcısı'nı kullanın

.NET Framework'ün önceki sürümleriyle karşılaştırıldığında, bağımsız değişken Tasarımcısı veri içine ve dışına bir etkinlik akışı izin vermek kolaylaştırır. Tasarımcı tıklayarak erişilen **bağımsız değişkenleri** tasarım tuvale sol alt köşesindeki düğmesi. Tasarımcı tablo biçiminde görünür ve her sütun üstbilgilerinin dışında sıralanabilir bağımsız değişkenlerin listesini içeren **varsayılan değer** sütun. Her değişken adı, içinde/çıkış /-çıkış/özellik yönü, türü ve varsayılan ifade değeri (varsa) içerir. Ad ve varsayılan ifade değeri düzenlenebilir metin alanları, ve türü ve yön aşağı açılan listeler. Daha fazla bilgi için bkz: [değişkenleri ve bağımsız değişkenler (.NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Yeni bir değişken oluşturmak için

1.  Bir iş akışı veya etkinlik çözümü Visual Studio'da açın.

2.  Bağımsız değişkenler Tasarımcısı'nı tıklatarak **bağımsız değişkenleri** tasarım tuvale sol alt köşesindeki düğmesi. Bağımsız değişkenler Tasarımcısı görünür.

3.  Etiketli boş satıra tıklayın **bağımsız değişkeni oluşturma**. Bu aşağıdaki varsayılan değerleri kullanarak yeni bir bağımsız değişkeniyle yeni bir satır ekler: argumentx için **adı** x benzersiz bağımsız değişken adları oluşturmak için otomatik olarak arttırılır 1 başlangıç değeri bir tamsayı olduğu **içinde**  için **yönü**, ve **dize** için **bağımsız değişken türü**. Herhangi bir değer için eklenen **varsayılan değer**. İş akışı tasarım işlemi sırasında herhangi bir zamanda bu değerleri değiştirebilirsiniz.

    > [!NOTE]
    > Bağımsız değişken silmek için bağımsız değişken tıklayarak seçin ve tuşuna basarak **silmek** anahtarı.

## <a name="see-also"></a>Ayrıca bkz.

- [İş Akışı Tasarımcısını Kullanma](../workflow-designer/using-the-workflow-designer.md)
- [Değişkenler ve Bağımsız Değişkenler](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)