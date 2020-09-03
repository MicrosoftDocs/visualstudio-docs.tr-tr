---
title: 'Nasıl yapılır: Içeri aktarmalar tasarımcısını kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47b5055cca0b00e7fdec49947df13b473a090aaf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659091"
---
# <a name="how-to-use-the-imports-designer"></a>Nasıl Yapılır: İçeri Aktarmalar Tasarımcısını Kullanma
İçeri aktarmalar Tasarımcısı, ifadeleriniz içinde kullanacağınız türler için ad alanları girmenize olanak sağlar. **İçeri aktarmalar veya Visual Basic** .net ve C# ' deki anahtar sözcükleri **kullanarak** çok benzer şekilde, Imports tasarımcısında ad alanlarını belirtmek, tam nitelikli bir sürüm türü adı yerine ifadenizde bir tür adı girmenizi sağlar.

 İçeri aktarmalar Tasarımcısı, Kullanıcı arabirimindeki her iki değişikliğe ve iş akışı kaydedildiğinde yapılan değişikliklere tepki verir. İş akışı kaydedildiğinde, ad alanları içeri aktarmalar tasarımcısına otomatik olarak eklenebilir. Bu araçlar şunlardır:

- Değişken ve bağımsız değişken bildirimlerinde kullanılan her türlü tür için ad alanları.

- İfadelerde kullanılan herhangi bir tür için ad alanları.

- İş akışını serileştirmek için gereken diğer ad alanları (örneğin, iş akışında bırakılan özel etkinlikler tarafından kullanılan ad alanları).

  İş akışı kaydedildiğinde, önceki listede açıklanan mantık nedeniyle el ile sildiğiniz bazı ad alanlarının içeri aktarma tasarımcısına otomatik olarak yeniden eklendiğini fark edebilirsiniz.

### <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>İçeri aktarılan ad alanları listesine bir ad alanı eklemek için

1. [!INCLUDE[vs2010](../includes/vs2010-md.md)]Veya bir yeniden barındırılan iş akışı uygulamasında BIR WCF iş akışı hizmeti uygulaması, iş akışı konsol uygulaması veya etkinlik kitaplığı projesi açın.

2. Ana tuvalin alt kısmındaki **Içeri aktarmalar** ' a tıklayın. Içeri aktarmalar Tasarımcısı görüntülenir.

3. Içeri aktarmalar tasarımcısının en üstündeki aşağı açılan liste denetiminden bir ad alanı girin veya seçin.

     Siz yazarken, yazılan karakterlerle eşleşen geçerli ad alanlarının listesi görüntülenir.

4. Ad alanını listeye eklemek için **ENTER** tuşuna basın.

5. Listeden bir ad alanı kaldırmak istiyorsanız, ad alanını seçin ve klavyenizdeki **Delete** tuşuna basın. Bir ad alanı yalnızca herhangi bir nedenle ad alanı geçersizse silinebileceğini unutmayın. Örneğin, ad alanını içeren derlemeye artık proje tarafından başvurulmuyorsa.