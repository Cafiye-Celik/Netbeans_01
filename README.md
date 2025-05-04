# Netbeans_01
kullanıcı arayüz çalışması
package com.mycompany.mavenproject1;

import javax.swing.JOptionPane;
![image](https://github.com/user-attachments/assets/6ae71772-284b-4773-adc9-ee90cab5a6f4)


public class Odev_calismasi extends javax.swing.JFrame {
    public Odev_calismasi() {
        initComponents();
    }
    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        int sayi1 = Integer.parseInt(txt_sayi1.getText());
        int sayi2 = Integer.parseInt(txt_sayi2.getText());
        double result = 0;
        
        int islem = cbm_islem.getSelectedIndex();
        if(islem == 0){
            result = sayi1 + sayi2;
        } else if (islem == 1 ){
            result = sayi1 - sayi2;
        } else if (islem == 2){
            result = sayi1* sayi2;
        } else if ( islem == 3){
            result =  sayi1 / sayi2;
        }
       
        lbl_sonuc.setText(String.valueOf(result));
      
         JOptionPane.showMessageDialog(this, " ortalama: "+ result ); //Başka bir ekranda veriyor sonucu
    }                                        
