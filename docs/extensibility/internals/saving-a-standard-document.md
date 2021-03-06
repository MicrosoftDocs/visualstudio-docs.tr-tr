---
title: Standart bir belge kaydetme | Microsoft Docs
description: Visual Studio IDE 'ye eklediğiniz proje türü için standart bir belge için gerçekleşen işlem hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], saving standard documents
- projects [Visual Studio SDK], saving standard documents
- persistence, saving standard documents
ms.assetid: d692fedf-b46e-4d60-84bd-578635042235
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1864ec689c1068b97775ca1a8bddbd390e7b43a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080898"
---
# <a name="saving-a-standard-document"></a>Standart Belge Kaydetme
Ortam Kaydet, farklı Kaydet ve Tümünü Kaydet komutlarını işler. Kullanıcı **Kaydet**, **farklı kaydet** veya **Dosya** menüsünden **Tümünü** Kaydet ' i seçtiğinde veya çözümü kapatdığında, bir **bütün kaydetme** işlemine neden olur.

 ![Standart düzenleyici](../../extensibility/internals/media/public.gif "Genel") Standart bir düzenleyici için Kaydet, farklı Kaydet ve tüm komut işlemesini Kaydet

 Bu işlem aşağıdaki adımlarda ayrıntılı olarak verilmiştir:

1. **Kaydet** ve **farklı kaydet** komutları seçildiğinde, ortam, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> etkin belge penceresini ve bu nedenle hangi öğelerin kaydedilmesi gerektiğini belirlemek için hizmetini kullanır. Etkin belge penceresi bilindiğinde ortam, çalışan belge tablosundaki belge için hiyerarşi işaretçisini ve öğe tanımlayıcısını (ItemId) bulur. Daha fazla bilgi için bkz. [çalışma belge tablosu](../../extensibility/internals/running-document-table.md).

    **Tümünü Kaydet** komutu seçildiğinde, ortam, kaydedilecek tüm öğelerin listesini derlemek için çalışan belge tablosundaki bilgileri kullanır.

2. Çözüm bir <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> çağrı aldığında, seçilen öğeler kümesi (yani, hizmet tarafından sunulan çoklu seçimler) boyunca yinelenir <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .

3. Seçimdeki her öğe için çözüm, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> **Kaydet** menü komutunun etkinleştirilmesi gerekip gerekmediğini belirleme yöntemini çağırmak için hiyerarşi işaretçisini kullanır. Bir veya daha fazla öğe kirli olursa **Kaydet** komutu etkinleştirilir. Hiyerarşi standart bir düzenleyici kullanıyorsa, hiyerarşi, metodu çağırarak, bu durumda, durumu düzenleyicide kirli durum için sorgulama temsilcileri <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> .

4. Kirli olan her seçili öğe için, çözüm uygun hiyerarşilerde yöntemi çağırmak için hiyerarşi işaretçisini kullanır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> .

    Hiyerarşinin belgeyi düzenlemek için standart bir düzenleyici kullanması yaygındır. Bu durumda, Bu düzenleyicinin belge veri nesnesi <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> arabirimini desteklemelidir. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A>Yöntem çağrısını aldıktan sonra proje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.SaveDocData%2A> belge veri nesnesi üzerinde yöntemini çağırarak düzenleyiciyi belgenin kaydedildiğini bilgilendirmelidir. Düzenleyici, arabirimi çağırarak, ortamın **farklı kaydet** iletişim kutusunu işlemesine izin verebilir `Query Service` <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> . Bu, arabirime bir işaretçi döndürür <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> . Daha sonra düzenleyici, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A> parametresi aracılığıyla düzenleyicinin uygulamasına bir işaretçi geçirerek yöntemi çağırmalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> `pPersistFile` . Daha sonra ortam, Kaydet işlemini gerçekleştirir ve düzenleyici için **farklı kaydet** iletişim kutusunu sağlar. Daha sonra ortam ile düzenleyiciye geri çağrı yapılır <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> .

5. Kullanıcı adsız bir belgeyi (yani, daha önce kaydedilmemiş bir belgeyi) kaydetmeye çalışıyorsa, aslında farklı Kaydet komutu gerçekleştirilir.

6. Farklı Kaydet komutu için, ortamda farklı Kaydet iletişim kutusu görüntülenir ve kullanıcıdan bir dosya adı istenir.

    Dosyanın adı değiştiyse, hiyerarşi (VSFPROPID_MkDocument) çağırarak belge çerçevesinin önbelleğe alınmış bilgilerini güncelleştirmekten sorumludur <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> .

   **Farklı kaydet** komutu belgenin konumunu taşıdıkça ve hiyerarşi belge konumuna duyarlıysa, bu durumda açık belge penceresinin sahipliğini başka bir hiyerarşiye teslim etmek için hiyerarşi sorumludur. Örneğin, proje, dosyanın proje ile bağlantılı olarak bir iç veya dış dosya (çeşitli dosya) olup olmadığını izliyorsa bu durum oluşur. Bir dosyanın sahipliğini çeşitli dosyalar projesine değiştirmek için aşağıdaki yordamı kullanın.

## <a name="changing-file-ownership"></a>Dosya sahipliğini değiştirme

#### <a name="to-change-file-ownership-to-the-miscellaneous-files-project"></a>Dosya sahipliğini çeşitli dosyalar projesiyle değiştirmek için

1. Arabirim için sorgu hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.SVsExternalFilesManager> .

     İçin bir işaretçi <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2> döndürülür.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsExternalFilesManager2.TransferDocument%2A> `pszMkDocumentNew` `punkWindowFrame` Belgeyi yeni hiyerarşiye aktarmak için (,) yöntemini çağırın. Farklı Kaydet komutunu gerçekleştiren hiyerarşi bu yöntemi çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Proje Öğelerini Açma ve Kaydetme](../../extensibility/internals/opening-and-saving-project-items.md)
