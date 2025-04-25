
# 🌐 NGINX Reverse Proxy + Let's Encrypt Companion (Docker Compose)

This `docker-compose.yml` sets up a fully automated **NGINX reverse proxy** with **Let's Encrypt SSL** using the community-trusted [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [letsencrypt-nginx-proxy-companion](https://github.com/nginx-proxy/acme-companion).

---

## ✅ Features

- 🔁 Automatically reverse proxies multiple containers
- 🔐 Automatic Let's Encrypt SSL certificates
- 🧠 Uses labels on services to configure virtual hosts
- 📦 Fully containerized, zero manual config
- 💾 Stores certs & config in persistent volumes

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://your-repo-url
cd your-project-directory
```

### 2. Create external Docker network (if not exists)

```bash
docker network create nginx-proxy
```

> ⚠️ All services you want to proxy must be on the **same external network**

### 3. Start the proxy

```bash
docker compose up -d
```

---

## 🌍 How to use with your apps

In any container you'd like to expose:

- Add the container to the same external network `nginx-proxy`
- Add these environment variables:

```env
VIRTUAL_HOST=example.com
LETSENCRYPT_HOST=example.com
LETSENCRYPT_EMAIL=your@email.com
```

---

## 📁 Volumes Used

| Volume   | Purpose                         |
|----------|---------------------------------|
| `certs`  | Stores issued SSL certificates  |
| `vhost`  | NGINX vhost config for each app |
| `html`   | Default web root                |
| `dhparam`| SSL DH parameters               |

---

## 🔐 Ports

- `80` – HTTP
- `443` – HTTPS

---

## 📌 Tips

- DNS for `VIRTUAL_HOST` must point to your server IP
- Restarting `nginx-proxy` will auto reload all certs & configs
- You can inspect logs using:

```bash
docker logs nginx-proxy
docker logs nginx-proxy-le
```

---

## 🧼 Clean Up

```bash
docker compose down -v
docker network rm nginx-proxy
```

---

## 📘 Reference

- [nginx-proxy GitHub](https://github.com/nginx-proxy/nginx-proxy)
- [Let's Encrypt Companion](https://github.com/nginx-proxy/acme-companion)

---

Ready to reverse proxy like a pro! 🧙‍♂️🚀
