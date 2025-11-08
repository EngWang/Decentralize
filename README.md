# OpenWhisk Local – VMware & WSL2 (Default: k3d + Helm, 2 Invokers)

- **(Mặc định) Bản 2 – k3d + Helm (2 Invokers)**
- **Bản 1 – Standalone (test ver)**

## Yêu cầu
Ubuntu 22.04+ (VMware) hoặc WSL2 Ubuntu; Docker, Git, curl, bash. Script tự cài k3d & Helm nếu thiếu.

### Ubuntu (VMware) cài Docker nhanh
```bash
sudo apt update
sudo apt install -y docker.io docker-compose git curl
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
# đăng xuất/đăng nhập lại
```

## (Default) Bản 2 – k3d + Helm
```bash
bash scripts/01_install_wsk.sh
bash scripts/10_k3d_create_cluster.sh
bash scripts/11_helm_install_openwhisk.sh
bash scripts/12_openwhisk_bootstrap.sh
bash scripts/14_smoke_test.sh
```
API: `http://<YOUR_IP>/api/v1`

Dọn dẹp:
```bash
bash scripts/13_k3d_delete_cluster.sh
```

## Bản 1 – Standalone
```bash
bash scripts/01_install_wsk.sh
bash scripts/02_standalone_up.sh
bash scripts/14_smoke_test.sh
bash scripts/03_standalone_down.sh
```
API: `https://<YOUR_IP>:3233/api/v1`
