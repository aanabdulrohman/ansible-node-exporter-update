# Ansible - Update Node Exporter

Automasi update node exporter ke versi terbaru menggunakan ansible

## Fitur
- Download node exporter dari github release (rubah link di playbook/update-node-exporter.yaml menjadi versi terbaru [disini](https://github.com/prometheus/node_exporter/releases)
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

