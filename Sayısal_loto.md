![image](https://github.com/user-attachments/assets/fd582361-d32b-4e3f-8424-5e6b7b096211)


package com.mycompany.mavenproject1;

import java.util.ArrayList;
import java.util.Collections;
import java.util.HashSet;
import java.util.Random;
import javax.swing.JLabel;
import javax.swing.JOptionPane;

/**
 *
 * @author cafiy
 */
public class EightApp_1 extends javax.swing.JFrame {
    private ArrayList<Integer> kullaniciSayilari = new ArrayList<>();
    private JLabel[] sonucEtiketleri;
    private ArrayList<Integer> cekilisSonucu = new ArrayList<>();

    public EightApp_1() {
        initComponents();
        sonucEtiketleri = new JLabel[]{lbl_sayi1 , lbl_sayi2 , lbl_sayi3, lbl_sayi4, lbl_sayi5, lbl_sayi6};
        
    }
                       
                    

    private void btn_CekilisActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
       if(kullaniciSayilari.size() != 6){
           JOptionPane.showMessageDialog(this, "Önce 6 adet sayı girirniz.","Uyarı", JOptionPane.WARNING_MESSAGE);
           return;
       }
       cekilisSonucu.clear();
       Random random = new Random();
       HashSet<Integer> uretilenSayilar = new HashSet<>();
       
       while(uretilenSayilar.size() < 6){
           int rastgeleSayi = random.nextInt(50) + 1; //1-50 arası rastgele sayı 
           uretilenSayilar.add(rastgeleSayi);
           
       }
       cekilisSonucu.addAll(uretilenSayilar);
      // Collections.sort(cekilisSonucu); //Çekiliş sonucunu sırala
       //for( int dongu : cekilisSonucu){
         JOptionPane.showMessageDialog(this, "Çekiliş Sonucu: " + cekilisSonucu, "Çekiliş Sonucu" , JOptionPane.INFORMATION_MESSAGE);  
       //}
       
       
        // Kullanıcı tahminleriyle karşılaştır ve doğru sayıyı göster
       int dogruTahminSayisi = 0;
       for ( int kullaniciSaayisi : kullaniciSayilari){
           boolean bulundu = false;
           for( int cekilisSayisi : cekilisSonucu){
               if(kullaniciSaayisi == cekilisSayisi){
                   dogruTahminSayisi++;
                   bulundu = true;
                   break;
               }
           }
       }
       //for( int tahmin : kullaniciSayilari){
       //    if(cekilisSonucu.contains(tahmin)){
       //        dogruTahminSayisi++;
       //    }
      // }
       JOptionPane.showMessageDialog(this , "Doğru Tahmin Sayısı: " + dogruTahminSayisi , "Sonuç" , JOptionPane.INFORMATION_MESSAGE);

    }                                           

    private void btn_KullaniciActionPerformed(java.awt.event.ActionEvent evt) {                                              
        // TODO add your handling code here:
        kullaniciSayilari.clear();
        HashSet<Integer> girilenSayilar = new HashSet<>(); //TEKRAR EDEN SAYILARI ÖNELEMEK İÇİN
        for(int i = 0; i< sonucEtiketleri.length; i++){
            String giris = JOptionPane.showInputDialog(this , (i+1) + ". sayıyı girirniz: " , JOptionPane.QUESTION_MESSAGE);
            if(giris != null && !giris.trim().isEmpty()){
                try {
                    int sayi = Integer.parseInt(giris.trim());
                    if( sayi >= 1 && sayi <= 50){
                       if(girilenSayilar.add(sayi)){  // Sayı daha önce girilmediyse kümeye ekle
                           kullaniciSayilari.add(sayi);
                           sonucEtiketleri[i].setText(String.valueOf(sayi)); // Label'da göster
                          
                       } else{
                           JOptionPane.showMessageDialog(this , " Bu sayoya daha önce girdiniz. " ," HATA" , JOptionPane.ERROR_MESSAGE);
                           //kullaniciSayilari.clear();
                           for(JLabel etiket : sonucEtiketleri ){
                               //etiket.setText("");  //HATA DURUMUNDA ETİKETLERİ TEMİZLE
                           }
                           return; //METOTTAN ÇIK
                       }
                    } else {
                        JOptionPane.showMessageDialog (this , "Sayı 1- 50 arasında olmalı." , "HATA", JOptionPane.ERROR_MESSAGE);
                        //kullaniciSayilari.clear();
                        for(JLabel etiket : sonucEtiketleri){
                          //  etiket.setText(""); //HATA DURUMUNDAN ETİKETLERİ TEMİZLE
                        }
                        return; //METTOTTAN ÇIK
                    }
                } catch(NumberFormatException e){
                    JOptionPane.showMessageDialog(this, "Gçerli bir sayı giriniz." , "HATA" , JOptionPane.ERROR_MESSAGE);
                   // kullaniciSayilari.clear();
                    for(JLabel etiket : sonucEtiketleri){
                      //  etiket.setText(""); //Hata durumunda etiketleri temizle
                        
                    }
                    return; //Metootan çık
                }
            } else{
                JOptionPane.showMessageDialog(this," Lütfen bir sayı giriniz." , "Hata" , JOptionPane.ERROR_MESSAGE);
               // kullaniciSayilari.clear();
                for(JLabel etiket : sonucEtiketleri){
                  //  etiket.setText(""); //HATA DURUMUNDA ETİKETLERİ TEMİZLE
                }
                return; //Metottan çık
            }
        }
        if(kullaniciSayilari.size()==6){
            JOptionPane.showMessageDialog(this, "Girilen sayılar: " + kullaniciSayilari , "Başarılı" , JOptionPane.INFORMATION_MESSAGE);
            
        }
       
        
        
    }                                             

    /**
     * @param args the command line arguments
     */
   

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new EightApp_1().setVisible(true);
            }
        });
    }
