![image](https://github.com/user-attachments/assets/e6408a7a-336d-412a-86cf-c3aa05854948)

import java.time.LocalDate;
import java.time.Period;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;
import javax.swing.JOptionPane;


public class NineApp extends javax.swing.JFrame {

  
    public NineApp() {
        initComponents();
    }

  
    private void txt_dogumTarihiActionPerformed(java.awt.event.ActionEvent evt) {                                                
        // TODO add your handling code here:
    }                                               

    private void btn_hesaplaActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
        String dogumTarihiStr = txt_dogumTarihi.getText().trim();
        
        if(dogumTarihiStr.isEmpty()){
            JOptionPane.showMessageDialog(this, "Lütfen doğum tarihini giriniz.");
        }
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd.MM.yyyy");
        LocalDate dogumTarihi = null;
        
        try {
            dogumTarihi = LocalDate.parse(dogumTarihiStr , formatter);
           
        } catch(DateTimeParseException e){
            JOptionPane.showMessageDialog(this , "Geçersiz tarih formatı" , "Hata" , JOptionPane.ERROR_MESSAGE);
            
        }
        LocalDate bugun = LocalDate.now();
        Period yas = Period.between(dogumTarihi , bugun);
        lbl_yas.setText("Yaşınız: " + yas.getYears());
    }                                           
