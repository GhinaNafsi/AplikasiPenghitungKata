# AplikasiPenghitungKata
 Tugas5-Ghina Nafsi 2210010324

# 1. Deskripsi Program
* Gunakan JTextArea dalam JScrollPane untuk input teks

* Setelah menekan tombol Hitung, hasil perhitungan berupa jumlah
kata dan karakter ditampilkan pada beberapa JLabel

# 2. Komponen GUI: 
JFrame, JPanel, JLabel, JTextArea, JScrollPane, JButton
- JPanel sebagai container utama.
- JTextArea untuk input teks dan letakkan dalam JScrollPane.
- JButton dengan label “Hitung Kata” untuk memicu perhitungan, "Cari" untuk memicu hasil pencarian kata, "Hapus" untuk menghapus input dan hasil, "Simpan File" digunakan untuk memicu penyimpanan, dan "Keluar" untuk keluar dari project.
- beberapa JLabel untuk menampilkan hasil jumlah kata, karakter, kalimat, paragraf, dan jumlah kemunculan kata.
- JTextField untuk input kata yang ingin dicari.
- JButton dengan label "Hapus"


### Hapus
 private void bDeleteActionPerformed(java.awt.event.ActionEvent evt) {                                        
      
        // Mengosongkan JTextField untuk pencarian 
        
        bDelete.addActionListener((ActionEvent e) -> {
        jTextArea1.setText("");  // Mengosongkan JTextArea
        // Mereset label hasil perhitungan
        KataTxt.setText("0");
        KarakterTxt.setText("0");
        KalimatTxt.setText("0");
        ParagrafTxt.setText("0");
        KemunculanKata.setText("0");
        InputCariKata.setText(""); 
    });
   }  

Event ActionListener pada tombol ini untuk mengosongkan teks di JTextArea dan mengatur ulang label hasil perhitungan.
Dengan penambahan tombol "Hapus" ini, Anda dapat mengosongkan JTextArea dan mereset semua label perhitungan kembali ke nol secara langsung.

# 3. Logika Program: 
Manipulasi string, Ekspresi reguler


# 4. Events:
* ActionListener untuk tombol Hitung

 private void bHitungKataActionPerformed(java.awt.event.ActionEvent evt) {                                            
       
        // Tambahkan ActionListener pada tombol "Hitung" untuk menghitung kata yag ditambahkan ke text area
    bHitungKata.addActionListener((ActionEvent e) -> {
        hitungKata(); // Memanggil metode countText() ketika tombol ditekan
    });
   }                                            

Penjelasan Kode :
hitungText() berfungsi untuk menghitung jumlah kata, karakter, kalimat, dan paragraf dalam teks.
ActionListener pada tombol "Hitung" memicu fungsi hitungText() ketika tombol ditekan.

- DocumentListener pada JTextArea memungkinkan perhitungan real-time saat teks diubah. 

// Method to count words, characters, sentences, and paragraphs
     private void hitungKata() {
       
        String text = jTextArea1.getText();

        // Hitung jumlah kata
        int wordCount = text.isEmpty() ? 0 : text.split("\\s+").length;

        // Hitung jumlah karakter
        int charCount = text.length();

        // Hitung jumlah kalimat menggunakan pemisah .!? untuk mengenali akhir kalimat
        int sentenceCount = text.isEmpty() ? 0 : text.split("[.!?]").length;

        // Hitung jumlah paragraf berdasarkan garis baru ganda sebagai pemisah
        int paragraphCount = text.isEmpty() ? 0 : text.split("\\n+").length;

        // Update JLabel dengan hasil perhitungan
        KataTxt.setText("" + wordCount);
        KarakterTxt.setText("" + charCount);
        KalimatTxt.setText("" + sentenceCount);
        ParagrafTxt.setText("" + paragraphCount);
   }

Penjelasan Kode :
Fungsi ini digunakan untuk menghitung jumlah kata, karakter, kalimat, dan paragraf:
- Jumlah Kata: Menggunakan split("\\s+") untuk hitung jumlah kata.
- Jumlah Karakter: Menggunakan text.length() untuk menghitung karakter total.
- Jumlah Kalimat: Menggunakan split("[.!?]") untuk memisahkan kalimat berdasarkan tanda baca. Perhitungan kalimat dilakukan dengan text.split("[.!?]"), yang membagi teks berdasarkan titik (.), tanda seru (!), atau tanda tanya (?). Setiap tanda ini dianggap sebagai akhir sebuah kalimat.
- Jumlah Paragraf: Menggunakan split("\\n+") untuk menghitung jumlah paragraf berdasarkan garis baru ganda sebagai pemisah. Perhitungan paragraf dilakukan dengan text.split("\\n+"), yang memisahkan teks setiap kali ada baris baru (\n). Setiap baris baru dianggap sebagai awal paragraf baru, dan jeda baris ganda (\n\n) dianggap sebagai pemisah antar paragraf.

# 5. Variasi:
* Tambahkan fitur untuk menghitung jumlah kalimat dan paragraf
 // Hitung jumlah kata
~~~
  int wordCount = text.isEmpty() ? 0 : text.split("\\s+").length;

        // Hitung jumlah karakter
        int charCount = text.length();

        // Hitung jumlah kalimat menggunakan pemisah .!? untuk mengenali akhir kalimat
        int sentenceCount = text.isEmpty() ? 0 : text.split("[.!?]").length;

        // Hitung jumlah paragraf berdasarkan garis baru ganda sebagai pemisah
        int paragraphCount = text.isEmpty() ? 0 : text.split("\\n+").length;

        // Update JLabel dengan hasil perhitungan
        KataTxt.setText("" + wordCount);
        KarakterTxt.setText("" + charCount);
        KalimatTxt.setText("" + sentenceCount);
        ParagrafTxt.setText("" + paragraphCount);

* Implementasikan fungsi pencarian kata tertentu dalam teks

 private void btnCariActionPerformed(java.awt.event.ActionEvent evt) {                                        
    // Add ActionListener to search button
        btnCari.addActionListener((ActionEvent e) -> {
            CariKata();
        });
    }   
~~~
Penjelasan :
Metode CariKata() menghitung jumlah kemunculan kata yang sesuai di dalam teks dan memperbarui jumlahkemunculankata.

 // Method to search a specific word
   
   private void SearchKata() {
        
        String text = jTextArea1.getText();
        String searchWord = InputCariKata.getText();
        int count = 0;

        if (!searchWord.isEmpty()) {
            String[] words = text.split("\\s+");
            for (String word : words) {
                if (word.equalsIgnoreCase(searchWord)) {
                    count++;
                }
            }
        }
        
        KemunculanKata.setText(" " + count);
   }
   
  
* Sediakan opsi untuk menyimpan teks dan hasil perhitungan ke file

private void bSaveFileActionPerformed(java.awt.event.ActionEvent evt) {                                          
       
       //untuk tombol atau button simpan file
        bSaveFile.addActionListener((ActionEvent e) -> {
            SimpanFile();
        });
   }        

Metode SimpanFile() membuat file hasil_penghitungan.txt dan menulis teks yang diinput beserta hasil perhitungan.
Jika penyimpanan berhasil, pesan konfirmasi akan ditampilkan.

// Method to save the text and results to a file
   private void SaveFile() {
      
        JFileChooser fileChooser = new JFileChooser();
    fileChooser.setDialogTitle("Simpan Hasil Penghitungan");
    int userSelection = fileChooser.showSaveDialog(this);
    
    if (userSelection == JFileChooser.APPROVE_OPTION) {
        try (FileWriter writer = new FileWriter(fileChooser.getSelectedFile())) {
       
            writer.write("Teks:\n" + jTextArea1.getText() + "\n\n");
            writer.write("Jumlah Kata: " + KataTxt.getText() + "\n");
            writer.write("Jumlah Karakter: " + KarakterTxt.getText() + "\n");
            writer.write("Jumlah Kalimat: " + KalimatTxt.getText() + "\n");
            writer.write("Jumlah Paragraf: " + ParagrafTxt.getText() + "\n");
            writer.write("Pencarian Kata '" + InputCariKata.getText() + "': " + KemunculanKata.getText() + "\n");
            JOptionPane.showMessageDialog(this, "Hasil berhasil disimpan ke hasil_penghitungan.txt");
        } catch (IOException e) {
            JOptionPane.showMessageDialog(this, "Gagal menyimpan file: " + e.getMessage());
        }
        }
   }

Dengan kode ini, sebuah dialog JFileChooser akan muncul sehingga Anda bisa memilih atau menentukan lokasi penyimpanan file hasil penghitungan sesuai keinginan.


## Contoh Gambar Project Setelah di Run

<img width="932" alt="PenghitungKata" src="https://github.com/user-attachments/assets/d15449e1-2815-4abc-9913-4618af482bcd">

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    10    |
|  2  | Logika Program   |    20    |
|  3  |  Events          |    10    |
|  4  | Kesesuaian UI    |    20    |
|  5  | Memenuhi Variasi |    40    |
|     | TOTAL        | 100 |

## Pembuat

NAMA : GHINA NAFSI
NPM : 2210010324
KELAS : 5A TI REG PAGI BJM

Nama  : Siti Safira
NPM   : 2210010336
