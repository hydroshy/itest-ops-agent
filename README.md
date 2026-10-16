# ITEST Operations Agent (`ops-agent`)

Dịch vụ độc lập (Sidecar Agent) phục vụ giám sát, điều phối vòng đời Docker container và cập nhật phiên bản cho hệ thống ITEST Platform.

---

## 1. Tính năng cốt lõi
- **Container Lifecycle Management**: Khởi động, dừng, restart và giám sát trạng thái container qua Docker Engine socket `/var/run/docker.sock`.
- **Git Release & Rollout**: Hỗ trợ fetch và checkout các phiên bản release trực tiếp.
- **Web UI & REST API**: Cung cấp giao diện quản trị nhanh và API tại cổng `3099`.
- **Database Diagnostic**: Kiểm tra tình trạng kết nối tới cơ sở dữ liệu PostgreSQL.

---

## 2. Cấu trúc thư mục
```text
ops-agent/
├── Dockerfile           # Multi-stage image Alpine Node 20
├── docker-compose.yml   # Khởi chạy sidecar kết nối mạng itest-system_lorawan_net
├── package.json         # Dependencies: bcryptjs, pg
├── server.js            # HTTP Server & Docker socket communication
├── ui.js                # Embedded Web UI
└── README.md            # Tài liệu hướng dẫn
```

---

## 3. Hướng dẫn khởi chạy
### Cách 1: Khởi chạy bằng Node.js trực tiếp
```bash
cd ops-agent
npm install
node server.js
```

### Cách 2: Khởi chạy bằng Docker Compose
```bash
cd ops-agent
docker compose up -d --build
```
Truy cập giao diện Ops Agent tại: `http://localhost:3099` (hoặc kiểm tra health qua `http://localhost:3099/health`).
