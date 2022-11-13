# SIG-Teori-Modul8-WorkingwithTerrainData

## Data
Silahkan Download Data Berikut :

[GMTED2010N10E060_300.zip](https://www.qgistutorials.com/downloads/GMTED2010N10E060_300.zip)

## Prosedur

1. Buka Lapisan ‣ Tambahkan Lapisan ‣ Tambahkan Lapisan Raster.
2. Klik pada … di bawah Source , cari dan pilih file bernama 10n060e_20101117_gmted_mea300.tif .
3. Anda akan melihat data medan yang ditampilkan di Kanvas QGIS. Setiap piksel dalam raster medan mewakili ketinggian rata-rata dalam meter di lokasi tersebut. Piksel gelap mewakili area dengan ketinggian rendah dan piksel yang lebih terang mewakili area dengan ketinggian tinggi.
4. Mari temukan bidang minat kita. Dari Wikipedia , kami menemukan bahwa koordinat untuk area yang kami minati - Gunung Everest - terletak di koordinat 27.9881° N, 86.9253° E. Perhatikan bahwa QGIS menggunakan koordinat dalam format (X, Y), jadi Anda harus menggunakan koordinat sebagai (Bujur, Lintang). Rekatkan 86.9253,27.9881 ini di bagian bawah jendela QGIS yang bertuliskan Koordinasi dan tekan Enter`. Area pandang akan dipusatkan pada koordinat ini. Untuk memperbesar, Masukkan 1:1000000 di bidang Skala dan tekan Enter. Anda akan melihat viewport memperbesar area sekitar Himalaya.
5. Kami sekarang akan memotong raster ke area yang diminati ini. Cari Klip di Processing Toolbox. Pilih di bawah algoritma GDAL.Clip Raster by extent
6. Di jendela Clip Raster by Extent , pilih 10n060e_20101117_gmted_mea300sebagai Input Layer , klik ...di Clipping extent dan pilih , klik di Clipped (extent) dan masukkan namanya sebagai . Klik Jalankan .Use Map canvas extent...mt_everest.tif .
7. Sebuah layer baru mt_everestakan muncul di kanvas. Cari Hill di Processing Toolbox . Pilih Hillshadealgoritma di bawah algoritma GDAL.
8. Di jendela Hillshade , pilih mt_everestsebagai Elevation Layer , masukkan 315.000dalam Azimuth (sudut horizontal) , masukkan 45.000dalam sudut Vertikal . Klik ...di Hillshade dan masukkan namanya sebagai mt_everest_hillshade.tif. Klik Jalankan .
9. Sebuah layer baru mt_everest_hillshadeakan muncul di kanvas.
10. Cari Contour di Processing Toolbox . Pilih Contouralgoritma di bawah algoritma GDAL.
11. Di jendela Contour , pilih mt_everestsebagai Input Layer , masukkan Interval 250antara garis kontur . Klik ...di Contours dan masukkan namanya sebagai mt_everest_contour.gpkg. Klik Jalankan .
12. Sebuah layer baru mt_everest_contourakan muncul di kanvas. Klik kanan pada layer dan klik Open Attribute Table .
13. Anda akan melihat bahwa setiap fitur baris memiliki atribut bernama ELEV . Ini adalah ketinggian dalam meter yang diwakili oleh setiap baris. Klik tajuk kolom beberapa kali untuk mengurutkan nilai dalam urutan menurun. Di sini Anda akan menemukan garis yang mewakili elevasi tertinggi dalam data kami, yaitu Mt. Everest.
14. Pilih baris atas, dan klik tombol Zoom to selection .
15. Beralih ke jendela QGIS utama. Anda akan melihat garis kontur yang dipilih disorot dengan warna kuning. Ini adalah area elevasi tertinggi dalam dataset kami.
16. Cari Smooth di Processing Toolbox . Pilih di Smoothbawah geometri Vektor.
17. Di jendela Smooth , pilih mt_everest_contoursebagai Input Layer5 , masukkan Iterasi . Klik Jalankan .

--------------------------------

Peringatan :

Algoritma pemulusan bekerja dengan menambahkan simpul ekstra di sepanjang garis. Saat Anda menambah jumlah iterasi, jumlah simpul di garis kontur bertambah banyak. Jadi berhati-hatilah dalam menggunakan jumlah iterasi yang lebih tinggi. Anda dapat mengurangi ukuran berkas keluaran dengan mengekspornya sebagai berkas bentuk dan menyederhanakan hasilnya menggunakan Mapshaper .

---------------------------------

18. Sebuah layer baru Smoothedakan muncul di kanvas. Lapisan ini akan memiliki tepi yang lebih halus dibandingkan dengan mt_everest_contourlapisan.
19. Anda juga dapat memvisualisasikan lapisan kontur dan memverifikasi analisis Anda dengan mengekspor lapisan kontur sebagai KML dan melihatnya di Google Earth. Klik kanan pada layer yang telah dihaluskan, pilih Export Save Feature As… .
20. Pilih Keyhole Markup Language [KML] sebagai Format . Klik ...di Nama file dan masukkan nama sebagai contour_smoothed.kml. Klik Oke .
21. Jelajahi file keluaran di disk Anda dan klik dua kali untuk membuka Google Earth Pro.
22. selesai.
