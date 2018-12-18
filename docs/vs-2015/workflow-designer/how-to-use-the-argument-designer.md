---
title: 'Nasıl yapılır: bağımsız değişken Tasarımcısını kullanma | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 81b24b8c0344cc6a8cf1559126a4faf0bc2b6f4e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206628"
---
# <a name="how-to-use-the-argument-designer"></a>Nasıl yapılır: bağımsız değişken Tasarımcısını kullanma
Önceki sürümlere göre [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], bağımsız değişken tasarımcısını veri ekleme çıkarma bir etkinlik akışı izin vermek kolaylaştırır. Tasarımcı tıklayarak erişilen **bağımsız değişkenleri** tasarım tuvalin sol alt köşesindeki düğme. Tasarımcı, bir tablo biçiminde görünür ve her bir sütun üst bilgileri dışında sıralanabilir bağımsız değişkenlerinin listesi içeren **varsayılan değer** sütun. Her bağımsız değişken adı, / out/içinde-out/özellik yönü, türü ve varsayılan ifade değeri (varsa) içerir. Adı ve varsayılan ifade değeri düzenlenebilir metin alanları ve türü ve Yön açılan listeler. [!INCLUDE[crabout](../includes/crabout-md.md)] bağımsız değişkenleri, görmek [değişkenleri ve bağımsız değişkenler](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).  
  
### <a name="to-create-a-new-argument"></a>Yeni bir değişken oluşturmak için  
  
1.  İş akışı veya etkinliği bir çözüm açın [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Bağımsız değişkenler Tasarımcısı'nı tıklatarak **bağımsız değişkenleri** tasarım tuvalin sol alt köşesindeki düğme. Bağımsız değişken tasarımcısını görünür.  
  
3.  Etiketli boş satırı tıklatın **bağımsız değişken oluşturma**. Bu aşağıdaki varsayılan değerleri kullanarak yeni bir değişken ile yeni bir satır ekler: argumentx için **adı** x benzersiz bağımsız değişken adları oluşturmak için otomatik olarak artırılır 1 başlangıç değeri bir tamsayı olduğu **içinde**  için **yönü**, ve **dize** için **bağımsız değişken türü**. Hiçbir değer için eklenen **varsayılan değer**. İş akışı tasarım işlemi sırasında herhangi bir zamanda bu değerleri değiştirebilirsiniz.  
  
    > [!NOTE]
    >  Bir değişkeni silmek için bağımsız değişken tıklayarak seçin ve tuşuna **Sil** anahtarı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş akışı Tasarımcısını kullanma](../workflow-designer/using-the-workflow-designer.md)   
 [Değişkenler ve Bağımsız Değişkenler](http://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)