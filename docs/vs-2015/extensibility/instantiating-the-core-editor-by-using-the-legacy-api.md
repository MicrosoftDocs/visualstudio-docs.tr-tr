---
title: Eski API'yi kullanarak çekirdek Düzenleyici örnekleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - instantiating editor
ms.assetid: dda23b18-96ef-43c6-b0dc-06d15cbe5cbb
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d092994ad66d96a3fe7141cb898c7ef9b811eaf5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765784"
---
# <a name="instantiating-the-core-editor-by-using-the-legacy-api"></a>Eski API'yi kullanarak çekirdek Düzenleyici örnekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyici metin düzenleme ekleme, silme, kopyalama ve yapıştırma gibi işlevleri sorumludur. Bu işlevler, metin renklendirme, girinti ve IntelliSense deyim tamamlama gibi dil Hizmetleri tarafından sağlanan ile birleştirir.  
  
 Üç yoldan biriyle çekirdek Düzenleyici örneği örneği oluşturabilir:  
  
- Açıkça çekirdek örneği bir pencerede Düzenleyicisi oluşturun.  
  
- Çekirdek Düzenleyici örneği döndüren bir düzenleyici fabrikası sağlayın  
  
- Proje hiyerarşisindeki dosyasını açın.  
  
  Aşağıdaki bölümlerde, eski API'SİNİN Düzenleyici örneği oluşturmak için nasıl kullanılacağı açıklanmaktadır.  
  
## <a name="explicitly-opening-a-core-editor-instance"></a>Açıkça bir çekirdek Düzenleyici örneği açma  
 Çekirdek Düzenleyici örneği açıkça alınırken:  
  
- Elde bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> düzenlenmekte olan belge veri nesnesini tutacak.  
  
- Bir satır yönelimli gösterimini belge veri nesnesi oluşturma bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> alanından arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> arabirimi.  
  
- Ayarlama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> varsayılan uygulaması örneği için belge veri nesnesi olarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> arabirimi kullanılarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetBuffer%2A> yöntemi.  
  
   Konak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> örneğini bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> kullanarak arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateToolWindow%2A> yöntemi.  
  
  Bu noktada, görüntüleme <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> arabirimi çekirdek Düzenleyici örneği içeren bir pencere sağlar.  
  
  Olmamasından kısayol tuşları olması veya gelişmiş özelliklere erişim ancak, bu çok yararlı bir örneği değil. Kısayol tuşları ve gelişmiş özelliklere erişim elde etmek için:  
  
- Kullanım <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> dil hizmeti ve düzenleyici kullanan belge veri nesnesi ilişkilendirmek için yöntemi.  
  
- Kendi kısayol tuşları oluşturabilir veya ayarlayarak Sistem varsayılanı kullanın <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> nesnelerin özelliklerini görüntüleme. Bunu yapmak için <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetGuidProperty%2A> yöntemiyle <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> özelliği.  
  
   Edinmek ve standart kısayol tuşlarını kullanmak için bunları .vsct dosyası kullanarak oluşturun. Daha fazla bilgi için [Visual Studio komut tablosu (. Vsct) dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="how-to-use-an-editor-factory-to-obtain-the-core-editor"></a>Çekirdek Düzenleyici almak için bir düzenleyici fabrikası kullanma  
 Bir düzenleyici fabrikası kullanarak bir çekirdek Düzenleyici uygularken <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi açıkça barındırmak için önceki bölümde açıklanan tüm adımları izleyin. bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> kullanarak bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> belge veri nesnesi bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> nesne.  
  
 Metni görüntülemek için elde bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> alanından arabirim <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> nesne ve çağrı <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi.  
  
 Düzenleyici için dil hizmeti sağlamak için çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> yöntemi içinde <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi.  
  
 Varsayılan kısayol tuşları, önceki bölümde aksine elde etmek için tarafından döndürülen komut içeriğini kullanın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> çekirdek Düzenleyicisi'nden alınırken yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi.  
  
 Varsa <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> yöntemi, metin düzenleyici olarak aynı komutu GUID döndürür, çekirdek Düzenleyici örneği, otomatik olarak varsayılan kısayol tuşlarını alır.  
  
 Genel bilgi için bkz. [izlenecek yol: bir çekirdek düzenleyici oluşturma ve bir düzenleyici dosya türü kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek Düzenleyicisi içinde](../extensibility/inside-the-core-editor.md)   
 [Açma ve proje öğelerini kaydetme](../extensibility/internals/opening-and-saving-project-items.md)   
 [İzlenecek Yol: Temel Düzenleyici Oluşturma ve Düzenleyici Dosya Türü Kaydetme](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)

