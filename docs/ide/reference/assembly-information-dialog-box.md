---
title: Derleme Bilgileri İletişim Kutusu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1d3223e5ed1fedff174ccc40149449d8f2a4b70f
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672478"
---
# <a name="assembly-information-dialog-box"></a>Derleme Bilgileri İletişim Kutusu
**Derleme bilgileri** iletişim kutusu değerlerini belirtmek için kullanılır [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] genel bütünleştirilmiş kod öznitelikleri, projenize otomatik olarak oluşturulan AssemblyInfo dosyasında depolanır. İçinde **Çözüm Gezgini**, dosya bulunan **Projem** düğümünde [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (tıklayın **tüm dosyaları göster** görüntülemek için); altında bulunan  **Özellikleri** içinde [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Derleme öznitelikleri hakkında daha fazla bilgi için bkz: [öznitelikleri](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Bu iletişim kutusuna erişmek için bir proje düğümü seçin **Çözüm Gezgini**ve ardından **proje** menüsünde tıklatın **özellikleri**. Zaman **Proje Tasarımcısı** görünen tıklayın **uygulama** sekmesi. Üzerinde **uygulama** sayfasında **derleme bilgilerini** düğmesi.

## <a name="uielement-list"></a>UIElement Listesi
 **Başlık** bütünleştirilmiş kod bildirimi için bir başlık belirtir. Karşılık gelen <xref:System.Reflection.AssemblyTitleAttribute>.

 **Açıklama** bütünleştirilmiş kod bildirimi için isteğe bağlı bir açıklama belirtir. Karşılık gelen <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Şirket** bütünleştirilmiş kod bildirimi için bir şirket adı belirtir. Karşılık gelen <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Ürün** bütünleştirilmiş kod bildirimi için ürün adını belirtir. Karşılık gelen <xref:System.Reflection.AssemblyProductAttribute>.

 **Telif Hakkı** telif hakkı bildirimi bütünleştirilmiş kod bildirimi belirtir. Karşılık gelen <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Ticari marka** bütünleştirilmiş kod bildirimi bir ticari marka belirtir. Karşılık gelen <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Derleme sürümü** derleme sürümünü belirtir. Karşılık gelen <xref:System.Reflection.AssemblyVersionAttribute>.

 **Sürüm dosyası** derleyiciye Win32 dosya sürümü kaynak için belirli bir sürümünü kullanmak için bir sürüm numarasını belirtir. Karşılık gelen <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** derleme tanımlayan benzersiz bir GUID. Bir proje oluşturduğunuzda, Visual Studio derleme için bir GUID oluşturur. Karşılık gelen <xref:System.Guid>.

 **Nötr dil** , derlemenin desteklediği kültür belirtir. Karşılık gelen <xref:System.Resources.NeutralResourcesLanguageAttribute>. Varsayılan değer **(hiçbiri)**.

 **Derlemeyi COM görünür** bütünleştirilmiş kodundaki türler COM'a olup olmadığını belirtir Karşılık gelen <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Ayrıca Bkz.

- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Öznitelikler](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)