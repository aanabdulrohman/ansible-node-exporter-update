# Ansible - Update Node Exporter

Automasi update node exporter ke versi terbaru menggunakan ansible

## Fitur
- Download node exporter dari github release 
- Ekstraksi file .tar.gz
- Replace file binary `node_exporter` ke `/usr/local/bin`
- Re-start service `node_exporter`
- Kirim notifikasi ke telegram
- Hapus file archive dan folder setelah selesai

## Persyaratan
- Python 3.x di local
- Node exporter yang sudah running sebelumnya
- SSH access ke server
- Ansible 2.9+

## Catra Pakai

1. **Atur Inventory**

    ```ini
    [node_exporter]
    server1 ansible_host=your_ip_server ansible_user=username_server ansible_ssh_private_key_file=~/.ssh/id_rsa

2. **vaul.yaml**
     ```
     become_pass_server1: password_server1
     ```
     Jika perlu di enkripsi passwordnya tambahkan
     ```
     ansible-vault encrypt vars/vault.yaml
     ```
     jika ingin melihat ulang atau mengganti password gunakan view dan decrypt

3. **host.yaml**
     ```
     ansible_become_pass: "{{ become_pass_server1 }}"
     ```

5. **update-node-exporter.yaml**
     ```
     node_exporter_version: "sesuaikan versi yang di download. exp: 1.9.1"
     ```

     Cek versi terbaru [disini](https://github.com/prometheus/node_exporter/releases)
   
6. **Run Playbook**
     ```
     ansible-playbook -i inventory.ini playbook/update-node-exporter.yaml --ask-vault-pass
     ```
     Hilangkan `ask-vault-pass` jika tidak di encrypt

7. **FYI**
   
     file .tar.gz dan hasil extarct nya akan otomatis di hapus jika update berhasil





---
Contributions are welcome!
