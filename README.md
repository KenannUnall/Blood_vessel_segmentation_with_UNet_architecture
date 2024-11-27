# Blood Vessel Segmentation with U-Net Architecture

Bu proje, DRIVE (Digital Retinal Images for Vessel Extraction) veri seti üzerinde U-Net mimarisi kullanarak göz damarlarının segmentasyonunu gerçekleştirmeyi amaçlamaktadır. Göz hastalıkları ve retinopati gibi durumların erken teşhisi için bu tür segmentasyonlar büyük önem taşımaktadır.

## İçindekiler

- [Proje Hakkında](#proje-hakkında)
- [Veri Seti](#veri-seti)
- [Veri Ön İşleme](#veri-ön-i̇şleme)
- [U-Net Mimarisi](#u-net-mimarisi)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [Sonuçlar](#sonuçlar)


## Proje Hakkında

Bu proje, göz sağlığını değerlendirmek amacıyla kan damarlarının otomatik segmentasyonunu yapmayı hedeflemektedir. U-Net mimarisi, özellikle biyomedikal görüntü segmentasyonu için geliştirilmiş bir yapıdır ve bu alanda yüksek başarı oranlarına ulaşmaktadır. Proje, DRIVE veri setini kullanarak modelin eğitilmesini ve elde edilen sonuçların değerlendirilmesini kapsamaktadır.

## Veri Seti

Proje, göz damarlarını içeren retinal görüntülerden oluşan DRIVE veri setini kullanmaktadır. Veri seti, eğitim ve test için ayrı olarak düzenlenmiştir ve her görüntü ile birlikte ilgili maske görüntüleri de bulunmaktadır.

### Veri Seti İçeriği

- **Eğitim Verileri**:
  - `images`: Eğitim için kullanılan retinal görüntüler.
  - `1st_manual`: Eğitim için kullanılan maske görüntüleri.

- **Test Verileri**:
  - `images`: Test için kullanılan retinal görüntüler.
  - `1st_manual`: Test için kullanılan maske görüntüleri.

## Veri Ön İşleme

Veri ön işleme aşamasında aşağıdaki adımlar gerçekleştirilmiştir:

1. **Veri Arttırma**: Modelin genelleme yeteneğini artırmak için döndürme, yatay/vertical yansıma ve rastgele kesme gibi veri arttırma teknikleri uygulanmıştır. Bu, modelin farklı görüntü varyasyonları üzerinde eğitilmesini sağlar.
   
2. **Görüntü Boyutlandırma**: Tüm görüntüler, modelin eğitimi için uygun olan 512x512 boyutuna yeniden boyutlandırılmıştır.

3. **Format Dönüşümü**: `.tif` ve `.gif` uzantılı görüntüler, `.jpg` formatına dönüştürülmüştür.

## U-Net Mimarisi

U-Net, özellikle biyomedikal görüntü segmentasyonu için geliştirilmiş bir konvolüsyonel sinir ağı mimarisidir. Aşağıda, U-Net mimarisinin temel bileşenleri açıklanmaktadır:

- **Encoder (Aşağı Aşama)**: Görüntüdeki özellikleri çıkarmak için konvolüsyon katmanları ve maksimum havuzlama katmanları kullanılır.
- **Bottleneck (Dar Kısım)**: Görüntü temsilinin en yoğun olduğu noktadır.
- **Decoder (Yukarı Aşama)**: Özellikleri yeniden yapılandırarak daha yüksek çözünürlükte çıktılar üretir. Bu aşamada, sıkıştırılmış bilgiyi genişletmek için yukarı örnekleme ve konvolüsyon işlemleri yapılır.
- **Atlama Bağlantıları**: Encoder'dan decoder'a doğrudan bağlantılar, detayların kaybolmasını önler ve modelin daha doğru sonuçlar üretmesini sağlar.



## Kurulum

Projenin çalışabilmesi için gerekli kütüphanelerin yüklenmesi gerekir.

### Gerekli Kütüphaneler

- `numpy`
- `pandas`
- `opencv-python`
- `tqdm`
- `imageio`
- `albumentations`
- `tensorflow` veya `keras` (model eğitimi için)


## Kullanım

Projeyi kullanmak için aşağıdaki adımları takip edin:

1. **Veri Setini Yükleyin**: DRIVE veri setinizi projenin uygun dizinine yerleştirin.

2. **Google Colab veya Yerel Ortamda Çalıştırın**:
   - **Google Colab** kullanıyorsanız, gerekli kütüphaneleri ve veri setini yükleyin, ardından Google Drive'ınızı bağlayın.

3. **Not Defterini Çalıştırın**: Not defterindeki hücreleri sırayla çalıştırarak modeli eğitin ve sonuçları değerlendirin.

## Sonuçlar

Proje, eğitim sonrası elde edilen segmentasyon sonuçlarını içerir. Başarı oranları ve modelin performansı, aşağıdaki metrikler kullanılarak değerlendirilmektedir:

- **IoU (Intersection over Union)**
- **Dice Katsayısı**
- **Precision, Recall, F1-Score**

Elde edilen segmentasyon maskeleri, orijinal görüntülerle yan yana gösterilerek modelin başarı durumu görselleştirilmiştir.



