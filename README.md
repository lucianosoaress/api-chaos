# api-chaos

> A reverse proxy that injects controlled chaos into any REST API.

![Status](https://img.shields.io/badge/status-in%20development-orange)
![License](https://img.shields.io/badge/license-MIT-blue)
![Node](https://img.shields.io/badge/node-%3E%3D18-green)
![Built in](https://img.shields.io/badge/built%20in-24h%20hackathon-purple)

---

## What is this?

**api-chaos** is a configurable reverse proxy that sits between your application and any REST API, injecting controlled failures on demand.

Random latency. HTTP errors. Corrupted payloads. All configurable per route, per probability, per chaos profile.

Built for developers who want to know - before production does - how their application behaves when the API it depends on starts misbehaving.

---

## The problem it solves

You write a frontend. It calls an API. The API always responds in 120ms with a clean 200.

Then production happens.

The API returns a 503 at 2am. Or responds in 4 seconds. Or sends a payload missing three fields your code assumed were always there.

**api-chaos** makes those scenarios testable, repeatable, and configurable — without touching the real API or waiting for production to surprise you.

---

## How it works

```
Your App → api-chaos proxy → Target API
               ↓
         Chaos Engine
         - Random latency (ms range)
         - HTTP error injection (500, 503, 429...)
         - Payload corruption (missing fields, wrong types)
         - All configurable per route + probability
```

Switch between chaos profiles at runtime without restarting:

| Profile     | Description                              |
|-------------|------------------------------------------|
| `quiet`     | 5% error rate — light turbulence         |
| `stormy`    | 40% error rate — degraded service        |
| `apocalypse`| 80% chaos — full resilience stress test  |

---

## Planned features

- [x] Architecture defined
- [ ] Reverse proxy core (http-proxy-middleware)
- [ ] Latency injection middleware
- [ ] HTTP error injection middleware  
- [ ] Payload corruption middleware
- [ ] Chaos profile system
- [ ] Runtime control API (enable/disable without restart)
- [ ] Real-time dashboard (requests/min, error %, avg latency)
- [ ] Swagger/OpenAPI docs
- [ ] Docker + docker-compose
- [ ] Jest test suite with statistical coverage

---

## Stack

- **Node.js 18+** + **Express**
- **http-proxy-middleware**: proxy core
- **Redis**: metrics storage
- **Jest** + **Supertest**: testing
- **Docker**: containerized setup
- **GitHub Actions**: CI/CD

---

## Status

> This project is being built in a **24-hour personal hackathon** starting **May 7, 2025**.  
> Follow the progress via commit history.

---

## License

[MIT](LICENSE)
