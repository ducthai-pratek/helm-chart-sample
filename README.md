# Helm Chart: vietscop

Đây là Helm chart dùng để triển khai ứng dụng `vietscop` trên Kubernetes. Chart này giúp bạn dễ dàng cấu hình, triển khai và quản lý các tài nguyên liên quan đến ứng dụng.

## Cấu trúc thư mục

```
vietscop/
├── Chart.yaml
├── values.yaml
├── values/
│   ├── dev-vietscop.yaml
│   └── prod-vietscop.yaml
└── templates/
    ├── deployment.yaml
    ├── ingress.yaml
    └── service.yaml
```

### Giải thích từng file

- **Chart.yaml**: Thông tin metadata về chart (tên, version, mô tả, ...).
- **values.yaml**: File cấu hình giá trị mặc định cho chart. Bạn có thể chỉnh sửa file này hoặc override khi cài đặt.
- **values/dev-vietscop.yaml**: Giá trị cấu hình dành cho môi trường phát triển (development).
- **values/prod-vietscop.yaml**: Giá trị cấu hình dành cho môi trường sản xuất (production).
- **templates/deployment.yaml**: Mẫu (template) để tạo resource Deployment cho ứng dụng.
- **templates/service.yaml**: Mẫu để tạo resource Service (expose ứng dụng ra ngoài).
- **templates/ingress.yaml**: Mẫu để tạo resource Ingress (cấu hình truy cập từ ngoài vào ứng dụng qua HTTP/HTTPS).

## Hướng dẫn cài đặt & sử dụng

### 1. Cài đặt Helm (nếu chưa có)

Tham khảo: https://helm.sh/docs/intro/install/

### 2. Cài đặt chart

**Cách 1: Dùng giá trị mặc định**

```bash
helm install vietscop ./vietscop
```

**Cách 2: Dùng file values cho môi trường cụ thể**

- Môi trường phát triển:
  ```bash
  helm install vietscop ./vietscop -f vietscop/values/dev-vietscop.yaml --namespace dev --create-namespace
  ```
- Môi trường sản xuất:
  ```bash
  helm install vietscop ./vietscop -f vietscop/values/prod-vietscop.yaml --namespace prod --create-namespace
  ```

**Cách 3: Ghi đè giá trị trực tiếp**

```bash
helm install vietscop ./vietscop --set key1=value1,key2=value2
```

### 3. Nâng cấp chart

```bash
helm upgrade vietscop ./vietscop -f vietscop/values/prod-vietscop.yaml
```

### 4. Xoá chart

```bash
helm uninstall vietscop
```