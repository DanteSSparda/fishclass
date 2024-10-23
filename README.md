Balık türlerini sınıflandırmak amacıyla bir derin öğrenme modeli geliştirdim. Bu projede, öncelikle NumPy, Pandas ve Matplotlib gibi kütüphanelerle veri analizi ve görselleştirme işlemlerini gerçekleştirdim. Veri doğrulama ve etiket ön işleme için Scikit-Learn kütüphanesini kullandım. Model oluşturma ve eğitim aşamalarında ise TensorFlow'dan yararlandım.

Veri seti olarak Kaggle’da bulunan büyük ölçekli bir balık veri setini kullandım. Verileri yüklemek için os.walk fonksiyonu ile veri setindeki tüm görüntüleri taradım ve her bir görüntüyü ilgili balık türü etiketiyle birlikte bir DataFrame’e aktardım. Verileri işlerken, her görüntüyü 224x224 boyutlarına yeniden ölçeklendirdim ve 0-1 arasında normalize ettim. Görüntü etiketlerini, sınıflandırma işlemine uygun hale getirmek için OneHotEncoder ile one-hot encoding formatına dönüştürdüm.

Modeli oluştururken, giriş katmanında Flatten() ile görüntüleri tek boyutlu hale getirdim. Ardından iki adet tam bağlantılı katman ekledim; ilk katmanda 256 nöron, ikinci katmanda ise 128 nöron kullandım ve her iki katmanda da aktivasyon fonksiyonu olarak relu tercih ettim. Overfitting’i önlemek amacıyla bu katmanlara Dropout katmanları ekledim. Çıkış katmanında, balık türlerini sınıflandırmak için 9 nöronlu bir Dense katman kullandım ve softmax aktivasyon fonksiyonunu tercih ettim.

Modeli Adam optimizasyon algoritması ve categorical_crossentropy kaybı ile eğittim. Eğitim sırasında, modelin validation verisindeki kaybını izlemek için early stopping mekanizmasını devreye soktum. 3 epoch boyunca doğrulama kaybında iyileşme görülmediğinde, modelin eğitimini durdurdum ve en iyi ağırlıkları geri yükledim.

Modelin performansını değerlendirmek için eğitim ve doğrulama kayıplarını ve doğruluklarını grafiksel olarak analiz ettim. Model, test verisi üzerinde test edildi ve belirli bir doğruluk oranına ulaştı. Sınıflandırma performansını daha iyi anlamak adına classification_report ve confusion_matrix ile detaylı analizler yaptım. Bu süreç sonunda, balık görüntülerini doğru bir şekilde sınıflandırabilen bir model geliştirmiş oldum.

https://www.kaggle.com/code/yusufcannan/fish-class
