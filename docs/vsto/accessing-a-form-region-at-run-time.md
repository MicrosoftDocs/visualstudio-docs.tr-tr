---
title: Form bölgesine çalışma zamanında erişme
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: f2c1f3e80f5ca4015a19b5eee7f2f4c673dcc615
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52304486"
---
# <a name="access-a-form-region-at-runtime"></a>Form bölgesine çalışma zamanında erişme

|Uygulandığı öğe:|  
|----------------|  
|Bu konudaki bilgiler, yalnızca aşağıdaki Microsoft Office proje türleri ve sürümleri için geçerlidir. Daha fazla bilgi için [Office uygulaması ve proje türüne göre kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Proje türü**<br /><br /> -VSTO eklentisi projeleri<br /><br /> **Microsoft Office sürümü**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Kullanım `Globals` erişim form bölgeleri için bir sınıf her yerden Outlook projenizin içinde. Hakkında daha fazla bilgi için `Globals` sınıfı [Office projelerindeki nesnelere genel erişim](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Belirli bir Outlook Inspector penceresinde görünen erişim form bölgeleri  
 Belirli bir Outlook denetçi'deki görünen tüm form bölgelerine erişmek için çağrı `FormRegions` özelliği `Globals` geçirin ve sınıfı bir <xref:Microsoft.Office.Interop.Outlook.Inspector> Inspector'ı temsil eden nesne.  

 Aşağıdaki örnekte, o anda odağı içeren denetçi'deki görünen form bölgelerine koleksiyonunu alır. Bu örnek adlı bir koleksiyon bir form bölgesinin ardından erişen `formRegion1` ve metin kutusunda görüntülenen metin ayarlar `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Belirli bir Outlook Gezgini penceresinde görüntülenen erişim form bölgeleri  
 Belirli bir Outlook Explorer'da görünen tüm form bölgelerine erişmek için çağrı `FormRegions` özelliği `Globals` geçirin ve sınıfı bir <xref:Microsoft.Office.Interop.Outlook.Explorer> Gezgini temsil eden nesne.  

 Aşağıdaki örnekte, o anda odağı içeren Explorer'da görünen form bölgelerine koleksiyonunu alır. Bu örnek adlı bir koleksiyon bir form bölgesinin ardından erişen `formRegion1` ve metin kutusunda görüntülenen metin ayarlar `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="access-all-form-regions"></a>Tüm form bölgelerine erişmek  
 Tüm gezginleri ve tüm denetçiler görünen tüm form bölgelerine erişmek için çağrı `FormRegions` özelliği `Globals` sınıfı.  

 Aşağıdaki örnek, tüm gezginleri ve tüm denetçiler görünen form bölgelerine koleksiyonunu alır. Bu örnek adlı bir form bölgesi ardından erişen `formRegion1` ve metin kutusunda görüntülenen metin ayarlar `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="access-controls-on-a-form-region"></a>Form bölgesini üzerinde erişim denetimleri  
 Kullanarak bir form bölgesi erişim denetimlerine `Globals` sınıfı, gerekir denetimleri için erişilebilir hale getirme kodu form bölgesi kod dosyası dışında.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Form bölgesi Tasarımcısı'nda tasarlanan form bölgeleri  
 İçin C#, erişmek istediğiniz her denetimin değiştiricisini değiştirin. Bunu yapmak için her denetimi form bölgesi Tasarımcısı'nda seçin ve değiştirme **değiştiriciler** özelliğini **dahili** veya **genel** içinde **özellikleri** penceresi. Örneğin, değiştirirseniz **değiştiricisi** özelliği `textBox1` için **dahili**, erişebileceğiniz `textBox1` yazarak `Globals.FormRegions.FormRegion1.textBox1`.  

 Visual Basic için değiştiricisi değiştirmeniz gerekmez.  

### <a name="imported-form-regions"></a>İçeri aktarılan form bölgeleri  
 Erişim değiştiricisi her denetimin form bölgesinin Outlook'ta tasarlanan form bölgesini içeri aktardığınızda, özel haline gelir. Form bölgesi tasarımcısı, bir içeri aktarılan form bölgesini değiştirmek için kullanamazsınız çünkü değiştiricisini bir denetimin bir yolu yoktur **özellikleri** penceresi.  

 Form bölgesi kod dosyası dışındaki bir denetime erişimi etkinleştirmek için bu denetim döndürülecek form bölgesi kod dosyasında bir özellik oluşturun.  

 Özellikleri oluşturma hakkında daha fazla bilgi için C#, bkz: [nasıl yapılır: bildirme ve kullanım okuma yazma özellikleri &#40;C&#35; Programlama Kılavuzu&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Visual Basic'de özellikler oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir özelliği (Visual Basic) oluşturma](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Ayrıca bkz.  
 [Outlook form bölgeleri oluşturma yönergeleri](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [İzlenecek yol: Outlook form bölgesi tasarlama](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Nasıl yapılır: bir Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Outlook form bölgelerindeki özel eylemler](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Form bölgesini Outlook ileti sınıfıyla ilişkilendirme](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [İzlenecek yol: Outlook'ta tasarlanan form bölgesini içeri aktarma](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Nasıl yapılır: Outlook'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Outlook form bölgeleri oluşturma](../vsto/creating-outlook-form-regions.md)   
 [Şerit, çalışma zamanında erişme](../vsto/accessing-the-ribbon-at-run-time.md)  
