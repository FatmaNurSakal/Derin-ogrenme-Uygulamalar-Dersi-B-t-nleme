## 🏆 En İyi Model ve Sonuç Analizi

Bu çalışmada **SimpleCNN, CustomCNN, ResNet-18 (Aug OFF / ON), ViT-Tiny ve ConvNeXt-Tiny**
modelleri **aynı veri, aynı ön işleme ve aynı giriş boyutu (224×224)** kullanılarak
adil (fair) şekilde karşılaştırılmıştır.

Değerlendirme, **test seti** üzerinde aşağıdaki metriklerle yapılmıştır:

- Accuracy
- Precision (macro)
- Recall (macro)
- F1-score (macro)
- ROC-AUC (multiclass OVR)

Tüm nicel sonuçlar `metrics.txt` ve `metrics_table.png` dosyalarından elde edilmiştir.

---

### 📊 Genel Metrik Karşılaştırması (Tüm Modeller)

<p align="center">
  <img src="results/presentation_assets/metrics/metrics_table.png" width="80%" />
</p>

Yukarıdaki tabloda görüldüğü üzere:

- **ConvNeXt-Tiny (Augmentation ON)** modeli,
  Accuracy ve F1-score açısından **en yüksek genel performansı** göstermiştir.
- **ViT-Tiny**, güçlü bir Transformer olmasına rağmen CIFAR-10 gibi küçük veri setlerinde
  ConvNeXt-Tiny kadar kararlı sonuç üretememiştir.
- **ResNet-18**, augmentation açıkken augmentation kapalı duruma göre
  belirgin bir performans artışı sağlamıştır.
- **SimpleCNN** ve **CustomCNN**, daha basit mimariler oldukları için
  modern mimarilere kıyasla daha düşük doğruluk ve F1 üretmiştir.

Bu sonuçlar, **modern mimarilerin (özellikle ConvNeXt)** uygun veri artırma ile
küçük veri setlerinde dahi klasik CNN’lere üstünlük sağlayabildiğini göstermektedir.

---

## 🖼️ Model Bazlı Görsel Sonuçlar

Aşağıda her model için sırasıyla:

- **Loss eğrisi**
- **Accuracy eğrisi**
- **Confusion Matrix**
- **Inference Grid (doğru / yanlış tahmin örnekleri)**

yan yana gösterilmiştir.

---

### 🔹 ConvNeXt-Tiny (Augmentation ON)
📁 `runs/convnext_tiny_aug_on_20260117_163226`

<p align="center">
  <img src="results/runs/convnext_tiny_aug_on_20260117_163226/curves/loss.png" width="23%" />
  <img src="results/runs/convnext_tiny_aug_on_20260117_163226/curves/accuracy.png" width="23%" />
  <img src="results/runs/convnext_tiny_aug_on_20260117_163226/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/convnext_tiny_aug_on_20260117_163226/figures/inference_grid.png" width="23%" />
</p>

> ConvNeXt-Tiny, hem eğitim sürecinde kararlı yakınsama göstermiş
> hem de test setinde en yüksek genel doğruluğu elde etmiştir.

---

### 🔹 CustomCNN (Augmentation ON)
📁 `results/runs/customcnn_aug_on_20260117_030434`

<p align="center">
  <img src="results/runs/customcnn_aug_on_20260117_030434/curves/loss.png" width="23%" />
  <img src="results/runs/customcnn_aug_on_20260117_030434/curves/accuracy.png" width="23%" />
  <img src="results/runs/customcnn_aug_on_20260117_030434/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/customcnn_aug_on_20260117_030434/figures/inference_grid.png" width="23%" />
</p>

> CustomCNN, SimpleCNN’e göre daha iyi performans göstermiş ancak
> derin ve ön-eğitimli mimarilere kıyasla sınırlı kalmıştır.

---

### 🔹 ResNet-18 (Augmentation OFF)
📁 `runs/resnet18_aug_off_20260117_220415`

<p align="center">
  <img src="results/runs/resnet18_aug_off_20260117_220415/curves/loss.png" width="23%" />
  <img src="results/runs/resnet18_aug_off_20260117_220415/curves/accuracy.png" width="23%" />
  <img src="results/runs/resnet18_aug_off_20260117_220415/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/resnet18_aug_off_20260117_220415/figures/inference_grid.png" width="23%" />
</p>

> Veri artırma olmadan eğitilen ResNet-18,
> augmentation kullanılan versiyona göre daha düşük genelleme göstermiştir.

---

### 🔹 ResNet-18 (Augmentation ON)
📁 `runs/resnet18_aug_on_20260117_130421`

<p align="center">
  <img src="results/runs/resnet18_aug_on_20260117_130421/curves/loss.png" width="23%" />
  <img src="results/runs/resnet18_aug_on_20260117_130421/curves/accuracy.png" width="23%" />
  <img src="results/runs/resnet18_aug_on_20260117_130421/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/resnet18_aug_on_20260117_130421/figures/inference_grid.png" width="23%" />
</p>

> Augmentation, ResNet-18’in hem doğruluk hem de hata dağılımını
> belirgin şekilde iyileştirmiştir.

---

### 🔹 SimpleCNN (Augmentation ON)
📁 `runs/simplecnn_aug_on_20260117_004754`

<p align="center">
  <img src="results/runs/simplecnn_aug_on_20260117_004754/curves/loss.png" width="23%" />
  <img src="results/runs/simplecnn_aug_on_20260117_004754/curves/accuracy.png" width="23%" />
  <img src="results/runs/simplecnn_aug_on_20260117_004754/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/simplecnn_aug_on_20260117_004754/figures/inference_grid.png" width="23%" />
</p>

> Basit mimarisi nedeniyle SimpleCNN,
> karmaşık sınıfları ayırt etmede zorlanmıştır.

---

### 🔹 ViT-Tiny (Augmentation ON)
📁 `runs/vit_tiny_aug_on_20260117_150214`

<p align="center">
  <img src="results/runs/vit_tiny_aug_on_20260117_150214/curves/loss.png" width="23%" />
  <img src="results/runs/vit_tiny_aug_on_20260117_150214/curves/accuracy.png" width="23%" />
  <img src="results/runs/vit_tiny_aug_on_20260117_150214/figures/confusion_matrix.png" width="23%" />
  <img src="results/runs/vit_tiny_aug_on_20260117_150214/figures/inference_grid.png" width="23%" />
</p>

> ViT-Tiny, Transformer mimarisine rağmen
> veri miktarı sınırlı senaryoda ConvNeXt kadar güçlü sonuç üretememiştir.

---
