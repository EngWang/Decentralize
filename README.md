# OpenWhisk Local – k3d + Helm (2 invokers) & Standalone

Repo này là bộ script dùng để dựng **Apache OpenWhisk** trên máy cá nhân (VMware Ubuntu hoặc WSL2).

## Bước 1 – Chuẩn bị
```bash
cd openwhisk-local
chmod +x scripts/*.sh
```

## Bước 2 – Cài CLI wsk
```bash
bash scripts/01_install_wsk.sh
```

## Bước 3 – Tạo cluster k3d (tự chọn port 80 hoặc 8080)
```bash
bash scripts/10_k3d_create_cluster.sh
```

## Bước 4 – Cài OpenWhisk chart bằng Helm
```bash
bash scripts/11_helm_install_openwhisk.sh
```

## Bước 5 – Cấu hình CLI wsk
```bash
bash scripts/12_openwhisk_bootstrap.sh
```

## Bước 6 – Kiểm tra hoạt động
```bash
bash scripts/14_smoke_test.sh
```

## Dọn cụm
```bash
bash scripts/13_k3d_delete_cluster.sh
```

## Bản nhanh (Standalone)
```bash
bash scripts/02_standalone_up.sh
bash scripts/14_smoke_test.sh
bash scripts/03_standalone_down.sh
```
