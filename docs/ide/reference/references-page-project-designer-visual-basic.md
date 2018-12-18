---
title: Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesReference
- vb.ProjectPropertiesUnusedReference
- vb.ProjectPropertiesReferencePaths
helpviewer_keywords:
- References page in Project Designer
- Project Designer, References page
- Unused References dialog box
ms.assetid: 5a47c595-e084-401c-86e1-74e0bf74fd86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 719f58ff7a8fe333f43e13ddef298ba9938ad4e5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815201"
---
# <a name="references-page-project-designer-visual-basic"></a>Başvurular Sayfası, Proje Tasarımcısı (Visual Basic)

Kullanım **başvuruları** sayfasının **Proje Tasarımcısı** başvuruları ve web başvuruları projenize içeri aktarılan ad alanlarını yönetmek için. Proje başvuruları COM bileşenlerini, XML web Hizmetleri, .NET Framework sınıf kitaplıkları veya derlemeleri ve diğer sınıf kitaplıkları için içerebilir. Başvuruları kullanma hakkında daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md).

Erişim için **başvuruları** sayfasında, bir proje düğümü seçin (değil **çözüm** düğümü) içinde **Çözüm Gezgini**. Ardından **proje**, **özellikleri** menü çubuğundaki. Proje Tasarımcısı göründüğünde tıklayın **başvuruları** sekmesi.

## <a name="uielement-list"></a>UIElement Listesi

Aşağıdaki seçenekler seçin veya projenize başvurular ve içeri aktarılan ad alanlarını kaldırma olanak sağlar.

**Kullanılmayan başvurular**

Erişim için bu düğmeye tıklayın **kullanılmayan başvurular** iletişim kutusu.

**Kullanılmayan başvurular** iletişim kutusu, projenize dahil olan, ancak aslında kod tarafından kullanılan başvuruları kaldırın olanak tanır. Listeleyen bir kılavuz içerdiği **başvuru adı**, **yolu**, ilgili, projedeki kullanılmayan ad alanı başvuruları ve diğer bilgileri. Kılavuzda tıklatıp projenizden kaldırmak istediğiniz ad alanı başvurularını seçin **Kaldır**.

**Başvuru yolları**

Erişim için bu düğmeye tıklayın **başvuru yolları** iletişim kutusu.

> [!NOTE]
> Proje sistemi bir bütünleştirilmiş kod başvurusu bulduğunda, sistem aşağıdaki sırayla şu konumlarda bakarak başvuru çözer:
>
> 1. Proje klasörü. Proje klasörü dosyaları görünür **Çözüm Gezgini** olduğunda **tüm dosyaları göster** geçerli değildir.
> 2. İçinde belirtilen klasörler **başvuru yolları** iletişim kutusu.
> 3. Dosyaları görüntüleme klasörleri **Başvuru Ekle** iletişim kutusu.
> 4. Projenin obj klasörü. (Bir veya daha fazla derlemeleri projenize bir COM başvurusu eklediğinizde, projenin obj klasöre eklenebilir.)

 **Başvurular**

 Bu liste, projede kullanılan tüm başvuruları gösterir veya kullanılmayan.

 **Add**

 Bir başvuru veya web referansı eklemek için bu düğmeye tıklayın **başvuruları** listesi.

 Seçin **başvuru** Başvuru Ekle iletişim kutusunu kullanarak projenize bir başvuru eklemek için.

 Seçin **Web başvurusu** projesi kullanarak bir web başvurusu eklemek için **Web başvurusu Ekle'yi** iletişim kutusu.

 **Kaldır**

 Bir veya daha fazla başvurularını seçin **başvuruları** listelemek ve silmek için bu düğmeye tıklayın.

 **Web başvurusunu güncelleştir**

 Bir web başvurusu seçin **başvuruları** listelemek ve güncelleştirmek için bu düğmeye tıklayın.

 **İçeri aktarılan ad alanları**

 Bu kutusuna kendi ad alanı ve tıklayın **kullanıcı içeri aktarma ekleyin** ad alanları listesine eklenecek.

 Kullanıcı içeri aktarılan ad alanları için diğer adlar oluşturabilirsiniz. Bunu yapmak için diğer ad ve ad alanı biçiminde girin *diğer*=*ad alanı*. Örneğin uzun ad kullanıyorsanız kullanışlıdır: `Http= MyOrg.ObjectLib.Internet.WebRequestMethods.Http`.

 **Kullanıcı içeri aktarma ekleyin**

 Belirtilen ad alanı eklemek için bu düğmeye tıklayın **içeri aktarılan ad alanlarını** liste kutusuna içeri aktarılan ad alanları. Düğme, yalnızca belirtilen ad alanı zaten listede değilse etkindir.

 **Ad alanları listesi**

 Tüm kullanılabilir ad alanlarının bu listede gösterilir. Projenize dahil olan ad alanları için onay kutularını seçilir.

 **Güncelleştirme kullanıcı içeri aktarma**

 Ad alanları listesinde bir kullanıcı tarafından belirtilen ad alanı seçin, içinde değiştirmek istediğiniz adı yazın **içeri aktarılan ad alanlarını** kutusuna ve ardından yeni bir ad alanına değiştirmek için bu düğmeye tıklayın. Düğme seçili ad alanı kullanılarak listeye eklenen bir ise etkinleştirilmeden **kullanıcı içeri aktarma eklemek** düğmesi. Ekleyebilirsiniz:

-   Sınıf veya ad alanları gibi <xref:System.Math?displayProperty=fullName>.

-   Diğer adlı alır, gibi `VB=Microsoft.VisualBasic`.

-   XML ad alanları gibi `<xmlns:xsl="http://www.w3.org/1999/XSL/Transform">`.

## <a name="see-also"></a>Ayrıca Bkz.

- [Bir projedeki başvuruları yönetme](../../ide/managing-references-in-a-project.md)
- [Nasıl Yapılır: İçeri Aktarılan Ad Uzaylarını Ekleme veya Kaldırma (Visual Basic)](../../ide/how-to-add-or-remove-imported-namespaces-visual-basic.md)
- [Imports Deyimi (XML Ad Alanı)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)
