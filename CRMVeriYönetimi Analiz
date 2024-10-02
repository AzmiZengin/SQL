TABLOLAR
	SELECT*FROM Cariler;
	SELECT*FROM Depolar;
	SELECT*FROM Faturalar;
	SELECT*FROM Odemeler;
	SELECT*FROM SatinAlma;
	SELECT*FROM Satislar;
	SELECT*FROM Urunler;
------------------------------------------------
Toplam Müşteri Sayısı
SELECT COUNT(*) AS ToplamMusteri FROM Cariler WHERE CariTuru = 'Müşteri';

Toplam Tedarikçi Sayısı
SELECT COUNT(*) AS ToplamTedarikci FROM Cariler WHERE CariTuru = 'Tedarikçi';

Toplam Ürün Sayısı
SELECT COUNT(*) AS ToplamUrun FROM Urunler;
En Yüksek Fiyatlı Ürün
SELECT UrunAdi, MAX(Fiyat) AS EnYuksekFiyat FROM Urunler group by UrunAdi;

En Düşük Fiyatlı Ürün
SELECT UrunAdi, MIN(Fiyat) AS EnDusukFiyat FROM Urunler group by UrunAdi ;

Stokta Olan Ürünler
SELECT COUNT(*) AS StoktaOlanUrunler FROM Urunler WHERE StokMiktari > 0;


Müşteri İletişim Bilgileri
SELECT Adi, Soyadi, Email, Telefon FROM Cariler WHERE CariTuru = 'Müşteri';

İlk 5 Satış
SELECT TOP 5 * FROM Satislar ORDER BY SatisTarihi DESC;

Toplam Satış Miktarı
SELECT SUM(SatisMiktari) AS ToplamSatisMiktari FROM Satislar;

Fatura Durumları
SELECT FaturaDurumu, COUNT(*) AS FaturaSayisi FROM Faturalar GROUP BY FaturaDurumu;

Her Depodaki Ürün Sayısı
SELECT D.DepoAdi, COUNT(U.UrunID) AS UrunSayisi;

FROM Depolar D
LEFT JOIN Urunler U ON D.DepoID = U.DepoID
GROUP BY D.DepoAdi;

Son Sipariş Tarihleri
SELECT DISTINCT SiparisTarihi FROM Siparisler ORDER BY SiparisTarihi DESC;

Ürün Kategorileri
SELECT DISTINCT Kategori FROM Urunler;

 Toplam Ödeme Tutarı
 SELECT SUM(OdemeTutari) AS ToplamOdeme FROM Odemeler;

 Aylık Satış Geliri
 SELECT 
    YEAR(SatisTarihi) AS Yil,
    MONTH(SatisTarihi) AS Ay,
    SUM(ToplamFiyat) AS AylikGelir
FROM 
    Satislar
GROUP BY 
    YEAR(SatisTarihi), MONTH(SatisTarihi);


En Çok Satılan Ürünler
SELECT 
    U.UrunAdi,
    SUM(S.SatisMiktari) AS ToplamSatis
FROM 
    Satislar S
JOIN 
    Urunler U ON S.UrunID = U.UrunID
GROUP BY 
    U.UrunAdi
ORDER BY 
    ToplamSatis DESC;

Müşteri Başına Ortalama Satış
SELECT 
    C.Adi,
    C.Soyadi,
    AVG(S.ToplamFiyat) AS OrtalamaSatis
FROM 
    Cariler C
JOIN 
    Satislar S ON C.CariID = S.CariID
GROUP BY 
    C.Adi, C.Soyadi;

 Stok Farkını Gösterme
SELECT 
    UrunAdi,
    StokMiktari,
    MinimumStokSeviyesi,
    (StokMiktari - MinimumStokSeviyesi) AS StokFark
FROM 
    Urunler;

Minimum Stok Seviyesinin Altında Ürün Olup Olmadığını Kontrol Etme
SELECT 
    COUNT(*) AS UrunSayisi
FROM 
    Urunler
WHERE 
    StokMiktari < MinimumStokSeviyesi;
