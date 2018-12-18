---
title: Özel Kod Analizi kural kümesi oluşturma
ms.date: 11/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 061ceec7a513a0d4c92f06fad5ef730100dbfb8e
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000222"
---
# <a name="customize-a-rule-set"></a>Bir kural kümesi özelleştirme

Kod Analizi için belirli proje gereksinimlerini karşılamak için özel bir kural oluşturabilirsiniz.

## <a name="create-a-custom-rule-set"></a>Özel kural kümesi oluşturma

Özel bir kural oluşturmak için yerleşik bir kural kümesi açabilirsiniz **kural kümesi düzenleyici**. Burada, ekleme veya kaldırma belirli kurallar ve kural ihlal edildiğinde gerçekleşen eylemi değiştirebilirsiniz&mdash;Örneğin, bir uyarı veya hata gösterir.

1. İçinde **Çözüm Gezgini**, projeye sağ tıklayın ve ardından **özellikleri**.

2. Üzerinde **özellikleri** sayfaları, select **Kod Analizi** sekmesi.

3. İçinde **bu kural kümesini Çalıştır** aşağı açılan listesinde, aşağıdakilerden birini yapın:

   - Özelleştirmek istediğiniz kural kümesi seçin.

     \- veya -

   - Seçin  **\<Gözat … >** mevcut bir kuralı kümesini belirlemek için listesinde değil.

4. Seçin **açık** kuralları kural kümesi Düzenleyicisi'nde görüntülemek için.

Öğesinden yeni bir kural kümesi dosyası da oluşturabilirsiniz **yeni dosya** iletişim:

1. Seçin **dosya** > **yeni** > **dosya**, veya basın **Ctrl**+**N**.

2. İçinde **yeni dosya** iletişim kutusunda **genel** solda, kategori seçip **Kod Analizi kural kümesi**.

3. **Aç**'ı seçin.

   Yeni *.ruleset* dosyası kural kümesi Düzenleyicisi'nde açılır.

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>Birden çok kural kümelerinden özel bir kural oluşturun

1. Çözüm Gezgini'nde projeye sağ tıklayın ve ardından **özellikleri**.

2. Üzerinde **özellikleri** sayfaları, select **Kod Analizi** sekmesi.

3. Seçin  **\<birden çok kural kümeleri... seçin >** gelen **bu kural kümesini Çalıştır**.

4. İçinde **Ekle veya Kaldır kural kümeleri** kural ayarlar seçin iletişim kutusunda, istediğiniz yeni kural kümesinde eklenecek.

   ![Ekleme veya kaldırma kural kümelerini iletişim kutusu](media/add-remove-rule-sets.png)

5. Seçin **Kaydet**, için bir ad girin *.ruleset* dosya ve ardından **Kaydet**.

   Yeni kural kümesi seçili **bu kural kümesini Çalıştır** listesi.

6. Seçin **açın** yeni kural kural kümesi Düzenleyicisi'nde kümesi açın.

### <a name="rule-precedence"></a>Kural önceliği

- Aynı kural listelenen iki veya daha fazla kez farklı önem dereceleri ile bir kural olarak, derleyici bir hata oluşturur. Örneğin:

   ```xml
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" />
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

- Aynı kural listelenen iki veya daha çok kez bir kural kümesi içinde *aynı* önem derecesi, aşağıdaki uyarıyı karşılaşabilirsiniz **hata listesi**:

   **CA0063: kural kümesi dosyası yüklenemedi. '\[,] .ruleset ' veya onun bağlantılı kural birini dosyaları ayarlayın. Dosya, kural kümesi şemasına uymuyor.**

- Kural kümesini kullanarak bir alt kural içeriyorsa bir **INCLUDE** etiketi ve alt ve üst kural kümelerini iki listesinden aynı kural ancak farklı önem dereceleri ile ardından üst kural kümesindeki önem öncelik kazanır. Örneğin:

   ```xml
   <!-- Parent rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules for ClassLibrary21" Description="Code analysis rules for ClassLibrary21.csproj." ToolsVersion="15.0">
     <Include Path="classlibrary_child.ruleset" Action="Default" />
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Warning" /> <!-- Overrides CA1021 severity from child rule set -->
     </Rules>
   </RuleSet>

   <!-- Child rule set -->
   <?xml version="1.0" encoding="utf-8"?>
   <RuleSet Name="Rules from child" Description="Code analysis rules from child." ToolsVersion="15.0">
     <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
       <Rule Id="CA1021" Action="Error" />
     </Rules>
   </RuleSet>
   ```

## <a name="name-and-description"></a>Ad ve açıklama

Düzenleyicide açık olan bir kural kümesi görünen adını değiştirmek için **özellikleri** penceresini seçerek **görünümü** > **Özellikler penceresi** menü çubuğundaki. Görünen ad girin **adı** kutusu. Ayrıca kural kümesi için bir açıklama girebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bir kural kümesi olduğuna göre sonraki adım, ekleme veya kaldırma kuralları veya önem derecesini kural ihlalleri değiştirme kuralları Özelleştir sağlamaktır.

> [!div class="nextstepaction"]
> [Kuralları kural kümesi Düzenleyici'sini değiştirme](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Yönetilen Kod Projesi İçin Kod Çözümlemesini Yapılandırma](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [Kod çözümleme kural kümesi başvurusu](../code-quality/rule-set-reference.md)