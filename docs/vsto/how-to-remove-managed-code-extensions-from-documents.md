---
title: 'Nasıl yapılır: belgelerden kaldırma yönetilen kod uzantıları'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a57384fa22e810be27969bb5164e1951dccd1bf2
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35677731"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Nasıl yapılır: belgelerden kaldırma yönetilen kod uzantıları
  Bir belge veya Microsoft Office Word veya Microsoft Office Excel için belge düzeyi özelleştirmesinde parçası olan bir çalışma kitabı özelleştirme bütünleştirilmiş kodu programlı olarak kaldırabilirsiniz. Kullanıcılar, ardından belgeleri açın ve içeriğini görüntülemek, ancak belgeye eklediğiniz herhangi bir özel kullanıcı arabirimi (UI) görüntülenmez ve kodunuzu çalışmaz.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Aşağıdakilerden birini kullanarak özelleştirme bütünleştirilmiş kodu kaldırabilirsiniz `RemoveCustomization` tarafından sağlanan yöntemleri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Kullandığınız yöntemine bağlıdır, çalışma zamanında özelleştirme çıkarmak istediğiniz (diğer bir deyişle, Word sırasında özelleştirmelerinde kodu çalıştırarak belgesi veya Excel çalışma kitabı açıldıktan), veya kapatılmış bir belge veya bir belgeden özelleştirme kaldırmak istiyorsanız, i Microsoft Office'in yüklü olmayan bir sunucuya s.  
  
 ![video bağlantısı](../vsto/media/playvideo.gif "video bağlantı") ilgili video gösterimi için bkz. [yapmak ı: ekleme veya ayırma Word belgesinden bir VSTO derleme?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>Çalışma zamanında özelleştirme derlemeyi kaldırmak için  
  
1.  Özelleştirme kodunuzda arama <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> yöntemi (için Word) veya <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> (Excel için) yöntemi. Yalnızca özelleştirme artık gerekli olmadığında, bu yöntem çağrılmalıdır.  
  
     Kodunuzda bu yöntemi çağırdığınız özelleştirme nasıl kullanıldığına bağlıdır. Örneğin, müşterilerin sizin özelleştirmenizin özellikleri kullanırsanız, bunlar belgeyi yalnızca belgenin kendisini (özelleştirmeye değil) ihtiyaç duyan diğer istemcilere göndermek hazır olana kadar çağıran bazı kullanıcı Arabirimi sağlayabilir `RemoveCustomization` tıkladığında bu. İlk açıldığında, ancak özelleştirmenin doğrudan müşteriler tarafından erişilen diğer tüm özellikleri sağlamaz özelleştirme belgeyi verilerle doldurur, alternatif olarak, ardından RemoveCustomization özelleştirme olan en kısa sürede çağırabilirsiniz Belge başlatma biter.  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Kapalı veya bir sunucudaki bir belge özelleştirme derlemesini kaldırmak için  
  
1.  Bir konsol uygulaması veya Windows Forms projesi gibi Microsoft Office gerektirmeyen bir proje başvurusu Ekle *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* derleme.  
  
2.  Aşağıdaki **içeri aktarmalar** veya **kullanarak** kod dosyanızın üstüne deyimi.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Statik çağrı <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> yöntemi <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> sınıfı ve parametresi için çözüm belge yolu belirtin.  
  
     Aşağıdaki kod örneğinde adlı bir belgeden özelleştirme kaldırma varsayar *WordDocument1.docx* masaüstünde olmasıdır.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Projeyi oluşturmak ve uygulamayı özelleştirme kaldırmak istediğiniz bilgisayarda çalıştırın. Bilgisayarda yüklü Office çalışma zamanı için Visual Studio 2010 Araçları yüklü olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ServerDocument sınıfını kullanarak bir sunucu üzerinde belgeleri yönetme](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Nasıl yapılır: yönetilen ekleme kodu belgelere uzantıları](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  