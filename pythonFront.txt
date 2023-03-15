from classlar import *
hayvanat = HayvanatBahcesi()

#sql = "INSERT INTO hayvan_turleri (tur_id, tur_adi, tur_yasadigi_kita, tur_beslenme_sekli, tur_bakim_saati) VALUES (%s, %s,%s,%s,%s)"          #veri ekleme
#val = (4, "surungen","amerika","ne gelirse","123123")                                                                                          #veri ekleme
#mycursor.execute(sql, val)                                                                                                                     #veri ekleme
#cnx.commit()                                                                                                                                   #veri ekleme
#print(mycursor.rowcount, "record inserted.")                                                                                                   #veri ekleme

#sql = "DELETE FROM hayvan_turleri WHERE tur_id = 0"              #veri silme
#mycursor.execute(sql)                                            #veri silme
#cnx.commit()                                                     #veri silme
#print(mycursor.rowcount, "record(s) deleted")                    #veri silme


#mycursor.execute("SELECT * FROM hayvan_turleri")                 #veri cagirma
#myresult = mycursor.fetchall()                                   #veri cagirma
#for x in myresult:                                               #veri cagirma
#  print(x)                                                       #veri cagirma


#sql = "UPDATE hayvan_turleri SET address = 'Canyon 123' WHERE address = 'Valley 345'"                                        #veri guncelleme
#mycursor.execute(sql)                                                                                                   #veri guncelleme
#cnx.commit()                                                                                                           #veri guncelleme
#print(mycursor.rowcount, "record(s) affected")                                                                          #veri guncelleme


my_dict={"hayvan_turleri": ["tur_id", "tur_adi", "tur_yasadigi_kita", "tur_beslenme_sekli", "tur_bakim_saati"]
         ,"bakicilar":["bakici_id", "bakici_isim", "bakici_soyisim", "bakici_calisma_saati", "bakici_ev_adresi"],
         "bilet":["bilet_id", "bilet_tarihi", "bilet_turu"]}

while True:
    try:
        işlem = int(input("""------------------\nİşlem Seçiniz: \n  1:Tabloya Veri Ekle \n  2:Tablonun Tüm Verilerini Getir\n  3:ID'ye Göre Veri Getir
  4:ID'ye Gore Veri Güncelleme\n  5:ID'ye Gore Veri Silme\nQ:Çıkış\n"""))

        if işlem == 1:
            print("hayvan_turleri \n bakicilar \n bilet")
            veriekle = input("Veri Eklemek Istediginiz tabloyu seciniz:")
            if veriekle == "hayvan_turleri":
                tur_id = input("Tur_ID giriniz : ")
                tur_adi = input("Tur adini giriniz : ")
                tur_yasadigi_kita = input("Tur yasadigi kita giriniz : ")
                tur_beslenme_sekli = input("Tur beslenme sekli giriniz : ")
                tur_bakim_saati = input("Tur bakim saatini giriniz : ")

                hayvan = Tur(tur_id , tur_adi , tur_yasadigi_kita , tur_beslenme_sekli, tur_bakim_saati)
                hayvanat.veriEkle(hayvan)

            elif veriekle == "bakicilar":
                bakici_id = input("Bakici_ID Giriniz : ")
                bakici_isim = input("Bakici ismi Giriniz : ")
                bakici_soyisim = input("Bakici soyismi Giriniz : ")
                bakici_calisma_saati = input("Bakici calisma saati Giriniz : ")
                bakici_ev_adresi = input("Bakici ev adresi Giriniz : ")
                bakici = Bakici(bakici_id, bakici_isim, bakici_soyisim, bakici_calisma_saati, bakici_ev_adresi)
                hayvanat.veriEkle(bakici)

            elif veriekle == "bilet":
                bilet_id = input("Bilet_ID giriniz : ")
                bilet_tarihi = input("Bilet tarihi giriniz : ")
                bilet_turu = input("Bilet turu giriniz : ")
                bilet = Bilet(bilet_id, bilet_tarihi, bilet_turu)
                hayvanat.veriEkle(bilet)

        elif işlem == 2:  #veri getirme

            hayvanat.veriGetir()

        elif işlem == 3:                                                                                            #id ye gore  vagirma
            hayvanat.idVeriGetir()


        elif işlem == 4:                                                                             #veri guncelleme
            hayvanat.veriGuncelle()


        elif işlem == 5:                                                                                                                 #veri silme
            hayvanat.veriSilme()

        else:
            break
    except Exception as e:
        print(e)
        break

